---
layout: post
title: Data Binding in Syncfusion Flutter DataGrid | DataTable
description: Learn about data binding support, manipulate the data and how to refresh the cell in Syncfusion Flutter DataGrid
platform: flutter
control: SfDataGrid
documentation: ug
---

# Data binding in Flutter DataGrid (SfDataGrid)

[SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) requires the [DataGridSource](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource-class.html) to obtain the row data. In order to bind data source of the SfDataGrid, set an instance of the `DataGridSource` to the [source](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/source.html) property.`source` property must not be null.

 The following APIs in the `DataGridSource` are mandatory to process the data,

 * [rows] - The number of rows in a datagrid and row selection depends on the [rows]. So, set the `DataGridRow` collection required for datagrid in
`rows`.
* [buildRow]- The widget needed for the cells is obtained from `DataGridRowAdapter`.

`DataGridSource` objects are expected to be long-lived, not recreated with each build.

The following example shows how to create the `DataGridSource`,

{% tabs %}
{% highlight dart %} 

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource() {
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

  List<DataGridRow> dataGridRows;

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

final EmployeeDataSource _employeeDataSource = EmployeeDataSource();
  
@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDataGrid(
      source: _employeeDataSource,
      columnWidthMode: ColumnWidthMode.lastColumnFill,
      columns: <GridColumn>[
        GridTextColumn(
          columnName: 'id',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              'ID',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridTextColumn(
          columnName: 'name',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerLeft,
            child: Text(
              'Name',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridTextColumn(
          columnName: 'designation',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerLeft,
            child: Text(
              'Designation',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridTextColumn(
          columnName: 'salary',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              'Salary',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Data manipulation in Flutter DataGrid (SfDataGrid)

`SfDataGrid` provides support to update or refresh the DataGrid when an underlying data is updated i.e. CRUD operation is performed in an underlying data.

If row is added, removed or replaced in an underlying datasource, you can call the [notifyListeners](https://api.flutter.dev/flutter/foundation/ChangeNotifier/notifyListeners.html). 

In the following example, row is added and `notifyListeners` is called in `onPressed` callback of the `FlatButton`.

N> `notifyListeners` should be called from inside the `DataGridSource`.

{% tabs %}
{% highlight Dart %} 
        
final List<Employee> _employees = <Employee>[];

final EmployeeDataSource _employeeDataSource = EmployeeDataSource();

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Column(
      children: [
        FlatButton(
            child: const Text('Add row'),
            onPressed: () {
              _employees
                  .add(Employee(10011, 'Steve', 'Designer', 15000));
              _employeeDataSource.buildDataGridRows();
              _employeeDataSource.updateDataGridSource();
            }),
        SfDataGrid(
          source: _employeeDataSource,
          columns: <GridColumn>[
            GridTextColumn(
              columnName: 'id',
              label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'ID',
                  overflow: TextOverflow.ellipsis,
                ),
              ),
            ),
            GridTextColumn(
              columnName: 'name',
              label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Name',
                  overflow: TextOverflow.ellipsis,
                ),
              ),
            ),
            GridTextColumn(
              columnName: 'designation',
              label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Designation',
                  overflow: TextOverflow.ellipsis,
                ),
              ),
            ),
            GridTextColumn(
              columnName: 'salary',
              label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'Salary',
                  overflow: TextOverflow.ellipsis,
                ),
              ),
            ),
          ],
        ),
      ],
    ),
  );
}

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource(List<Employee> employees) {
    buildDataGridRows();
  }

  void buildDataGridRows() {
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

  List<DataGridRow> dataGridRows;

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

If the value of the specific cell is updated, you can `notifyDataSourceListeners` method with [RowColumnIndex](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/RowColumnIndex-class.html) argument where it refers the corresponding row and column index of the cell. 
So, DataGrid refreshes the corresponding cell alone.

In the following example, cell value is updated and `notifyDataSourceListeners` is called in `onPressed` callback of the `FlatButton`.

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
    body: Column(
      children: [
        FlatButton(
            child: const Text('Update cell value'),
            onPressed: () {
              _employees[0].salary = 25000;
              _employeeDataSource.dataGridRows[0] = DataGridRow(cells: [
                DataGridCell(value: employees[0].id, columnName: 'id'),
                DataGridCell(value: employees[0].name, columnName: 'name'),
                DataGridCell(
                    value: employees[0].designation,
                    columnName: 'designation'),
                DataGridCell(
                    value: employees[0].salary, columnName: 'salary'),
              ]);

              _employeeDataSource.updateDataGridSource(
                  rowColumnIndex: RowColumnIndex(0, 3));
            }),
        SfDataGrid(
          source: _employeeDataSource,
          columns: <GridColumn>[
            GridTextColumn(
              columnName: 'id',
              label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'ID',
                  overflow: TextOverflow.ellipsis,
                ),
              ),
            ),
            GridTextColumn(
              columnName: 'name',
              label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Name',
                  overflow: TextOverflow.ellipsis,
                ),
              ),
            ),
            GridTextColumn(
              columnName: 'designation',
              label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Designation',
                  overflow: TextOverflow.ellipsis,
                ),
              ),
            ),
            GridTextColumn(
              columnName: 'salary',
              label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'Salary',
                  overflow: TextOverflow.ellipsis,
                ),
              ),
            ),
          ],
        ),
      ],
    ),
  );
}

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource() {
    buildDataGridRows();
  }

  void buildDataGridRows() {
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

  void updateDataGridSource({RowColumnIndex rowColumnIndex}) {
    notifyDataSourceListeners(rowColumnIndex: rowColumnIndex);
  }
}

{% endhighlight %}
{% endtabs %}
