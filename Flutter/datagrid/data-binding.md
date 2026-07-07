---
layout: post
title: Data Binding in Flutter DataGrid | DataTable | Syncfusion
description: Learn how to set the Data source for Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Data Binding in Flutter DataGrid (SfDataGrid)

The [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) requires the [DataGridSource](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource-class.html) to obtain the row data. To bind the data source of the SfDataGrid, set an instance of the `DataGridSource` to the [source](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/source.html) property. The `source` property must not be null.

 The following APIs in the `DataGridSource` are mandatory to process the data,

 * [rows](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/rows.html) - The number of rows in a Datagrid and row selection depends on the `rows.` Set the `DataGridRow` collection required for Datagrid in `rows`.
 
* [buildRow](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/buildRow.html) - The widgets for cells are built using `DataGridRowAdapter`.

`DataGridSource` objects are expected to be long-lived, not recreated with each build.

> **Note:** Ensure the `columnName` property in `DataGridCell` matches the `columnName` in the corresponding `GridColumn` definitions. This alignment is essential for the DataGrid to correctly display and manage the data.

The following example shows how to create the `DataGridSource`,

{% tabs %}
{% highlight dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';
import 'package:flutter/material.dart';

class Employee {
  Employee(this.id, this.name, this.designation, this.salary);
  final int id;
  final String name;
  final String designation;
  final int salary;
}

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource({required List<Employee> employees}) {
    dataGridRows = employees
        .map<DataGridRow>((dataGridRow) => DataGridRow(cells: [
              DataGridCell<int>(columnName: 'id', value: dataGridRow.id),
              DataGridCell<String>(columnName: 'name', value: dataGridRow.name),
              DataGridCell<String>(
                  columnName: 'designation', value: dataGridRow.designation),
              DataGridCell<int>(
                  columnName: 'salary', value: dataGridRow.salary),
            ]))
        .toList();
  }

  List<DataGridRow> dataGridRows = [];

  @override
  List<DataGridRow> get rows => dataGridRows;

  @override
  DataGridRowAdapter? buildRow(DataGridRow row) {
    return DataGridRowAdapter(
        cells: row.getCells().map<Widget>((dataGridCell) {
      return Container(
          alignment: (dataGridCell.columnName == 'id' ||
                  dataGridCell.columnName == 'salary')
              ? Alignment.centerRight
              : Alignment.centerLeft,
          padding: EdgeInsets.symmetric(horizontal: 16.0),
          child: Text(
            dataGridCell.value.toString(),
            overflow: TextOverflow.ellipsis,
          ));
    }).toList());
  }
}

{% endhighlight %}
{% endtabs %}

The following example shows how to set the `source` property in `SfDataGrid`

{% tabs %}
{% highlight dart %}

List<Employee> getEmployeeData() {
  return [
    Employee(1001, 'James', 'Project Manager', 20000),
    Employee(1002, 'Kathryn', 'Manager', 30000),
    Employee(1003, 'Lara', 'Developer', 15000),
    Employee(1004, 'Michael', 'Developer', 15000),
    Employee(1005, 'Martin', 'Developer', 15000),
  ];
}

late EmployeeDataSource _employeeDataSource;
List<Employee> _employees = <Employee>[];

@override
void initState() {
  super.initState();
  _employees = getEmployeeData();
  _employeeDataSource = EmployeeDataSource(employees: _employees);
}

  @override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfDataGrid(
          source: _employeeDataSource,
          columnWidthMode: ColumnWidthMode.lastColumnFill,
          columns: <GridColumn>[
              GridColumn(
                  columnName: 'id',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.centerRight,
                      child: Text(
                        'ID',
                        overflow: TextOverflow.ellipsis,
                      ))),
              GridColumn(
                  columnName: 'name',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.centerLeft,
                      child: Text(
                        'Name',
                        overflow: TextOverflow.ellipsis,
                      ))),
              GridColumn(
                  columnName: 'designation',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.centerLeft,
                      child: Text(
                        'Designation',
                        overflow: TextOverflow.ellipsis,
                      ))),
              GridColumn(
                  columnName: 'salary',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.centerRight,
                      child: Text(
                        'Salary',
                        overflow: TextOverflow.ellipsis,
                      )))
            ]));
}

{% endhighlight %}
{% endtabs %}

> **Note:** `ColumnWidthMode.lastColumnFill` automatically adjusts the width of the last column to fill any remaining space in the DataGrid.

## Data manipulation in Flutter DataGrid (SfDataGrid)

`SfDataGrid` provides support to update or refresh the DataGrid when underlying data is updated via CRUD operations.

> **Note:**
- `notifyListeners` must be called from inside the `DataGridSource`. Since it is a protected method, wrap it in a public method like `updateDataGridSource` that can be called from the widget level.
- Requires `syncfusion_flutter_datagrid` package version 20.0.0 or later.

If a row is added, removed, or replaced in an underlying data source, call the [notifyListeners](https://api.flutter.dev/flutter/foundation/ChangeNotifier/notifyListeners.html) method to notify the DataGrid to refresh. 

In the following example, a row is added, and `notifyListeners` is called through the `updateDataGridSource` method in the `onPressed` callback of the `TextButton`.

{% tabs %}
{% highlight Dart %} 

List<Employee> getEmployeeData() {
  return [
    Employee(1001, 'James', 'Project Manager', 20000),
    Employee(1002, 'Kathryn', 'Manager', 30000),
    Employee(1003, 'Lara', 'Developer', 15000),
  ];
}

List<Employee> _employees = <Employee>[];
final EmployeeDataSource _employeeDataSource = EmployeeDataSource();

@override
void initState() {
  super.initState();
  _employees = getEmployeeData();
  _employeeDataSource.buildDataGridRows(_employees);
}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Column(children: [
    TextButton(
        child: const Text('Add row'),
        onPressed: () {
          _employees.add(Employee(10011, 'Steve', 'Designer', 15000));
          _employeeDataSource.buildDataGridRows(_employees);
          _employeeDataSource.updateDataGridSource();
        }),
    SfDataGrid(source: _employeeDataSource, columns: <GridColumn>[
      GridColumn(
          columnName: 'id',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerRight,
              child: Text(
                'ID',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'name',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerLeft,
              child: Text(
                'Name',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'designation',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerLeft,
              child: Text(
                'Designation',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'salary',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerRight,
              child: Text(
                'Salary',
                overflow: TextOverflow.ellipsis,
              )))
    ])
  ]));
}

class EmployeeDataSource extends DataGridSource {
  void buildDataGridRows(List<Employee> employees) {
    dataGridRows = employees
        .map<DataGridRow>((dataGridRow) => DataGridRow(cells: [
              DataGridCell<int>(columnName: 'id', value: dataGridRow.id),
              DataGridCell<String>(columnName: 'name', value: dataGridRow.name),
              DataGridCell<String>(
                  columnName: 'designation', value: dataGridRow.designation),
              DataGridCell<int>(
                  columnName: 'salary', value: dataGridRow.salary),
            ]))
        .toList();
  }

  List<DataGridRow> dataGridRows = [];

  @override
  List<DataGridRow> get rows => dataGridRows;

  @override
  DataGridRowAdapter? buildRow(DataGridRow row) {
    return DataGridRowAdapter(
        cells: row.getCells().map<Widget>((dataGridCell) {
      return Container(
          alignment: (dataGridCell.columnName == 'id' ||
                  dataGridCell.columnName == 'salary')
              ? Alignment.centerRight
              : Alignment.centerLeft,
          padding: EdgeInsets.symmetric(horizontal: 16.0),
          child: Text(
            dataGridCell.value.toString(),
            overflow: TextOverflow.ellipsis,
          ));
    }).toList());
  }

  void updateDataGridSource() {
    notifyListeners();
  }
}

{% endhighlight %}
{% endtabs %}

If the value of a specific cell is updated, you can call the `notifyDataSourceListeners` method with the [RowColumnIndex](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/RowColumnIndex-class.html) argument to refresh only that specific cell, improving performance by avoiding unnecessary full DataGrid refreshes. The `RowColumnIndex` takes two parameters: row index and column index (both 0-based).

In the following example, a cell value is updated, and `notifyDataSourceListeners` is called in the `onPressed` callback of the `TextButton` with `RowColumnIndex(0, 3)` to refresh only the salary cell in the first row.

{% tabs %}
{% highlight Dart %} 

List<Employee> getEmployeeData() {
  return [
    Employee(1001, 'James', 'Project Manager', 20000),
    Employee(1002, 'Kathryn', 'Manager', 30000),
    Employee(1003, 'Lara', 'Developer', 15000),
  ];
}

List<Employee> _employees = <Employee>[];
final EmployeeDataSource _employeeDataSource = EmployeeDataSource();

@override
void initState() {
  super.initState();
  _employees = getEmployeeData();
  _employeeDataSource.buildDataGridRows(_employees);
}

@override
Widget build(BuildContext context) {
  return Scaffold(
      appBar: AppBar(
        title: const Text('Syncfusion Flutter DataGrid'),
      ),
      body: Column(children: [
        TextButton(
            child: const Text('Update cell value'),
            onPressed: () {
              _employees[0].salary = 25000;
              _employeeDataSource.dataGridRows[0] = DataGridRow(cells: [
                DataGridCell(value: _employees[0].id, columnName: 'id'),
                DataGridCell(value: _employees[0].name, columnName: 'name'),
                DataGridCell(
                    value: _employees[0].designation,
                    columnName: 'designation'),
                DataGridCell(value: _employees[0].salary, columnName: 'salary'),
              ]);
              _employeeDataSource.updateDataGridSource(
                  rowColumnIndex: RowColumnIndex(0, 3));
            }),
        SfDataGrid(source: _employeeDataSource, columns: <GridColumn>[
          GridColumn(
              columnName: 'id',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'ID',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'name',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Name',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'designation',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Designation',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'salary',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'Salary',
                    overflow: TextOverflow.ellipsis,
                  )))
        ])
      ]));
}

class EmployeeDataSource extends DataGridSource {
  void buildDataGridRows(List<Employee> employees) {
    dataGridRows = employees
        .map<DataGridRow>((dataGridRow) => DataGridRow(cells: [
              DataGridCell<int>(columnName: 'id', value: dataGridRow.id),
              DataGridCell<String>(columnName: 'name', value: dataGridRow.name),
              DataGridCell<String>(
                  columnName: 'designation', value: dataGridRow.designation),
              DataGridCell<int>(
                  columnName: 'salary', value: dataGridRow.salary),
            ]))
        .toList();
  }

  List<DataGridRow> dataGridRows = [];

  @override
  List<DataGridRow> get rows => dataGridRows;

  @override
  DataGridRowAdapter? buildRow(DataGridRow row) {
    return DataGridRowAdapter(
        cells: row.getCells().map<Widget>((dataGridCell) {
      return Container(
          alignment: (dataGridCell.columnName == 'id' ||
                  dataGridCell.columnName == 'salary')
              ? Alignment.centerRight
              : Alignment.centerLeft,
          padding: EdgeInsets.symmetric(horizontal: 16.0),
          child: Text(
            dataGridCell.value.toString(),
            overflow: TextOverflow.ellipsis,
          ));
    }).toList());
  }

  void updateDataGridSource({RowColumnIndex? rowColumnIndex}) {
    if (rowColumnIndex != null) {
      notifyDataSourceListeners(rowColumnIndex: rowColumnIndex);
    } else {
      notifyListeners();
    }
  }
}

{% endhighlight %}
{% endtabs %}

> **Note:** Use `notifyDataSourceListeners` with a specific `RowColumnIndex` for better performance when updating individual cells. Use `notifyListeners` only when the entire row or multiple cells need to be refreshed.
