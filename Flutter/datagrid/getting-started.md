---
layout: post
title: Getting started with Flutter DataGrid | DataTable | Syncfusion
description: Learn here about getting started with Syncfusion Flutter DataGrid (SfDataGrid) widget, its basic features, and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Getting started with Flutter DataGrid (SfDataGrid)

This section explains the steps required to add the DataGrid widget and its features. This section covers only basic features needed to get started with the Syncfusion Flutter DataGrid widget.

To get start quickly with Flutter DataGrid, you can check on this video:
<style>#FlutterDataGridVideoTutorial{width : 90% !important; height: 400px !important }</style>
<iframe id='FlutterDataGridVideoTutorial' src='https://www.youtube.com/embed/-ULsEfjxFuY'></iframe>

## Add Flutter DataGrid to an application

Create a simple project using the instruction given in the  [Getting Started with your first Flutter app](https://docs.flutter.dev/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion Flutter DataGrid dependency to your pubspec.yaml file.

{% highlight dart %} 

    dependencies:

    syncfusion_flutter_datagrid: ^xx.x.xx

{% endhighlight %}

N> Here **xx.x.xx** denotes the current version of [`Syncfusion Flutter DataGrid`](https://pub.dev/packages/syncfusion_flutter_datagrid/versions) package.

**Get packages**

Run the following command to get the required packages.

{% highlight dart %} 

    $ flutter pub get

{% endhighlight %}

**Import package**

Import the following package in your Dart code.

{% tabs %}
{% highlight Dart %} 

    import 'package:syncfusion_flutter_datagrid/datagrid.dart';

{% endhighlight %}
{% endtabs %}

## Initialize DataGrid

Add the SfDataGrid widget as a child of any widget. [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) requires the [source](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/source.html) and [columns](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/columns.html) properties. You can find the more details on these properties in further topics.

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDataGrid(
      source: _employeeDataSource,
      columns: [
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
                ))),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}
## Creating Data for an application

The `SfDataGrid` is depending upon the data. Create a simple datasource for `SfDataGrid` as shown in the following code example.

{% tabs %}
{% highlight Dart %} 

class Employee {
  Employee(this.id, this.name, this.designation, this.salary);
  final int id;
  final String name;
  final String designation;
  final int salary;
}

{% endhighlight %}
{% endtabs %}

Create the collection of Employee data with the required number of data objects. Here, the `getEmployeeData` method which is used to populate the data objects is initialized in `initState()`.

{% tabs %}
{% highlight Dart %} 

late EmployeeDataSource _employeeDataSource;

List<Employee> _employees = <Employee>[];

@override
void initState() {
  super.initState();
  _employees = getEmployeeData();
  _employeeDataSource = EmployeeDataSource(employees: _employees);
}
  
List<Employee> getEmployeeData() {
  return [
    Employee(10001, 'James', 'Project Lead', 20000),
    Employee(10002, 'Kathryn', 'Manager', 30000),
    Employee(10003, 'Lara', 'Developer', 15000),
    Employee(10004, 'Michael', 'Designer', 15000),
    Employee(10005, 'Martin', 'Developer', 15000),
    Employee(10006, 'Newberry', 'Developer', 15000),
    Employee(10007, 'Balnc', 'Developer', 15000),
    Employee(10008, 'Perry', 'Developer', 15000),
    Employee(10009, 'Gable', 'Developer', 15000),
    Employee(10010, 'Grimes', 'Developer', 15000)
  ];
}

{% endhighlight %}
{% endtabs %}

## Creating DataSource for DataGrid

[DataGridSource](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource-class.html) is used to obtain the row data for the `SfDataGrid`. So, create the DataSource from the DataGridSource and override the following APIs in it,

* **`rows`** - Fetches the rows available for data population. Also, it is used to fetch the corresponding data object to process the selection. This contains the collection of `DataGridRow` where each row contains the collection of `DataGridCell`. Each cell should have the cell value in `value` property. `value` is used to perform the sorting for columns.

* **`buildRow`** - Fetches the widget for each cell with `DataGridRowAdapter`.

`DataGridSource` objects are expected to be long-lived, not recreated with each build.

{% tabs %}
{% highlight Dart %} 

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

Create an instance of `DataGridSource` and set this object to `source` property of `SfDataGrid`.

{% tabs %}
{% highlight Dart %} 

late EmployeeDataSource _employeeDataSource;

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfDataGrid(
      source: _employeeDataSource,
  ));
}

{% endhighlight %}
{% endtabs %}

>**NOTE**  
  You can download the demo application from [GitHub](https://github.com/SyncfusionExamples/getting-started-with-flutter-datagrid).

## Defining columns

`SfDataGrid` supports to add any widget in a column using the `GridColumn` property. You can add the column collection to the `columns` property.

{% tabs %}
{% highlight Dart %} 
  
@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfDataGrid(source: _employeeDataSource, columns: [
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

![flutter datagrid shows different column types](images/getting-started/getting-started-flutter-datagrid.png)

## Selection

`SfDataGrid` allows you to select one or more rows. The [selectionMode](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/selectionMode.html) property can be set to specify whether a user can select single row, or multiple rows. 

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfDataGrid(
    source: _employeeDataSource,
    columns: [
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
              ))),
    ],
    selectionMode: SelectionMode.multiple,
  ));
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows rows with selection](images/getting-started/flutter-datagrid-selection.png)

The information about the rows that are selected can be retrieved using [selectedIndex](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/selectedIndex.html), [selectedRow](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/selectedRow.html) and [selectedRows](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/selectedRows.html) properties in [DataGridController](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController-class.html). You need to initialize the `DataGridController` object to the [controller](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/controller.html) property of `SfDataGrid`.

`DataGridController` objects are expected to be long-lived, not recreated with each build.

{% tabs %}
{% highlight Dart %} 

final DataGridController _controller = DataGridController();

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Column(children: [
    TextButton(
        child: Text('Get Selection Information'),
        onPressed: () {
          int selectedIndex = _controller.selectedIndex;
          DataGridRow selectedRow = _controller.selectedRow!;
          List<DataGridRow> selectedRows = _controller.selectedRows;
          print(selectedIndex);
          print(selectedRow);
          print(selectedRows);
        }),
    Expanded(
        child: SfDataGrid(
      source: _employeeDataSource,
      columns: [
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
                ))),
      ],
      controller: _controller,
      selectionMode: SelectionMode.multiple,
    ))
  ]));
}

{% endhighlight %}
{% endtabs %}

>**NOTE**  
  `SfDataGrid` supports selection via keyboard interaction for the Web and Desktop platform when `selectionMode` is not `none`.
