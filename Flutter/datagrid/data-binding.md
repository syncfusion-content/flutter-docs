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

 * [rows](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/rows.html) - The number of rows in a Datagrid and row selection depends on the `rows.` So, set the `DataGridRow` collection required for Datagrid in `rows`.
 
* [buildRow](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/buildRow.html) - The widget needed for the cells is obtained from `DataGridRowAdapter`.

`DataGridSource` objects are expected to be long-lived, not recreated with each build.

The following example shows how to create the `DataGridSource`,

{% tabs %}
{% highlight dart %} 

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

## Data manipulation in Flutter DataGrid (SfDataGrid)

`SfDataGrid` provides support to update or refresh the DataGrid when an underlying data is updated i.e. CRUD operation is performed in an underlying data.

If the row is added, removed, or replaced in an underlying Data source, call the [notifyListeners](https://api.flutter.dev/flutter/foundation/ChangeNotifier/notifyListeners.html). 

In the following example, the row is added, and `notifyListeners` is called in the `onPressed` callback of the `TextButton`. As the `notifyListeners` is the protected method, the `updateDataGridSource` method the `notifyListeners` method. So, users can call the `updateDataGridSource` methods in the widget level to refresh the Datagrid.

N> `notifyListeners` should be called from inside the `DataGridSource`.

{% tabs %}
{% highlight Dart %} 
        
final List<Employee> _employees = <Employee>[];

final EmployeeDataSource _employeeDataSource = EmployeeDataSource();

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Column(children: [
    TextButton(
        child: const Text('Add row'),
        onPressed: () {
          _employees.add(Employee(10011, 'Steve', 'Designer', 15000));
          _employeeDataSource.buildDataGridRows();
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
  EmployeeDataSource() {
    buildDataGridRows();
  }

  void buildDataGridRows() {
    dataGridRows = _employees
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

If the value of the specific cell is updated, you can `notifyDataSourceListeners` method with the [RowColumnIndex](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/RowColumnIndex-class.html) argument, which refers to the corresponding row and column index of the cell. 
So, DataGrid refreshes the corresponding cell alone.

In the following example, the cell value is updated, and `notifyDataSourceListeners` is called in the `onPressed` callback of the `TextButton.`

{% tabs %}
{% highlight Dart %} 

final List<Employee> _employees = <Employee>[];

final EmployeeDataSource _employeeDataSource = EmployeeDataSource();

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
  EmployeeDataSource() {
    buildDataGridRows();
  }

  void buildDataGridRows() {
    dataGridRows = _employees
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

  void updateDataGridSource({required RowColumnIndex rowColumnIndex}) {
    notifyDataSourceListeners(rowColumnIndex: rowColumnIndex);
  }
}

{% endhighlight %}
{% endtabs %}
