---
layout: post
title: Getting started for Syncfusion Flutter DataGrid | DataTable
description: Learn how to create the Syncfusion Flutter DataGrid and it's basic features such as data binding, column definition and selection.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Getting Started with Flutter DataGrid (SfDataGrid)

This section explains the steps required to add the DataGrid widget and its features. This section covers only basic features needed to get started with the Syncfusion Flutter DataGrid widget. 

## Add Flutter DataGrid to an application

Create a simple project using the instruction given in the  [Getting Started with your first Flutter app](https://flutter.dev/docs/get-started/test-drive?tab=vscode#create-app) documentation.

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
        GridNumericColumn(mappingName: 'id',  headerText:'ID'),
        GridTextColumn(mappingName: 'name', headerText: 'Name'),
        GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
        GridNumericColumn(mappingName: 'salary', headerText: 'Salary'),
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

Create the collection of Employee data with the required number of data objects. Here, the `populateData` method which is used to populate the data objects is initialized in `initState()`.

{% tabs %}
{% highlight Dart %} 
   
final List<Employee> _employees = <Employee>[];
  
@override
void initState() {
  super.initState();
  populateData();
}
  
void populateData() {
  _employees.add(Employee(10001, 'James', 'Project Lead', 20000));
  _employees.add(Employee(10002, 'Kathryn', 'Manager', 30000));
  _employees.add(Employee(10003, 'Lara', 'Developer', 15000));
  _employees.add(Employee(10004, 'Michael', 'Designer', 15000));
  _employees.add(Employee(10005, 'Martin', 'Developer', 15000));
  _employees.add(Employee(10006, 'Newberry', 'Developer', 15000));
  _employees.add(Employee(10007, 'Balnc', 'Developer', 15000));
  _employees.add(Employee(10008, 'Perry', 'Developer', 15000));
  _employees.add(Employee(10009, 'Gable', 'Developer', 15000));
  _employees.add(Employee(10010, 'Grimes', 'Developer', 15000));
}

{% endhighlight %}
{% endtabs %}

## Creating DataSource for DataGrid

[DataGridSource](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource-class.html) is used to obtain the row data for the `SfDataGrid`. So, create the DataSource from the DataGridSource and override the following APIs in it,

* **`dataSource`** - To fetch the number of rows available for data population. Also, it is used to fetch the corresponding data object to process the selection.
* **`getValue`** - To fetch the value for each cell.

`DataGridSource` objects are expected to be long-lived, not recreated with each build.

{% tabs %}
{% highlight Dart %} 

final List<Employee> _employees = <Employee>[];

final EmployeeDataSource_employeeDataSource = EmployeeDataSource();

class EmployeeDataSource extends DataGridSource<Employee> {
  @override
  List<Employee> get dataSource => _employees
  
  @override
  getValue(Employee employee, String columnName) {
    switch (columnName) {
      case 'id':
        return employee.id;
        break;
      case 'name':
        return employee.name;
        break;
      case 'salary':
        return employee.salary;
        break;
      case 'designation':
        return employee.designation;
        break;
      default:
        return ' ';
        break;
    }
  }
}

{% endhighlight %}
{% endtabs %}

Create an instance of `DataGridSource` and set this object to `source` property of `SfDataGrid`.

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfDataGrid(
    source: _employeeDataSource,
  ));
}

{% endhighlight %}
{% endtabs %}

## Defining columns

`SfDataGrid` supports to show different data types (int, double, String and DateTime) in different types of columns. You can add the column collection to the `columns` property. 
You can also load any widget in a column using the [GridWidgetColumn](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridWidgetColumn-class.html) and [cellBuilder](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/cellBuilder.html) property in `SfDataGrid`.

{% tabs %}
{% highlight Dart %} 

final EmployeeDataSource _employeeDataSource = EmployeeDataSource();
  
@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDataGrid(
      source: _employeeDataSource,
      columns: [
        GridNumericColumn(mappingName: 'id', headerText: 'ID'),
        GridTextColumn(mappingName: 'name', headerText: 'Name'),
        GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
        GridNumericColumn(mappingName: 'salary', headerText: 'Salary'),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows different column types](images/getting-started/getting-started-flutter-datagrid.png)

## Selection

`SfDataGrid` allows you to select one or more rows. The [selectionMode](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/selectionMode.html) property can be set to specify whether a user can select single row, or multiple rows. 

{% tabs %}
{% highlight Dart %} 
    
final EmployeeDataSource _employeeDataSource = EmployeeDataSource();

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDataGrid(
      source: _employeeDataSource,
      columns: [
        GridNumericColumn(mappingName: 'id', headerText: 'ID'),
        GridTextColumn(mappingName: 'name', headerText: 'Name'),
        GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
        GridNumericColumn(mappingName: 'salary', headerText: 'Salary'),
      ],
      selectionMode: SelectionMode.multiple,
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows rows with selection](images/getting-started/flutter-datagrid-selection.png)

The information about the rows that are selected can be retrieved using [selectedIndex](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/selectedIndex.html), [selectedRow](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/selectedRow.html) and [selectedRows](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/selectedRows.html) properties in [DataGridController](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController-class.html). You need to initialize the `DataGridController` object to the [controller](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/controller.html) property of `SfDataGrid`.

`DataGridController` objects are expected to be long-lived, not recreated with each build.

{% tabs %}
{% highlight Dart %} 

final EmployeeDataSource _employeeDataSource = EmployeeDataSource();

final DataGridController _controller = DataGridController();

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Column(
      children: [
        RaisedButton(
            child: Text('Get Selection Information'),
            onPressed: () {
              int selectedIndex = _controller.selectedIndex;
              Object selectedRow = _controller.selectedRow;
              List<Object> selectedRows = _controller.selectedRows;
              print(selectedIndex);
              print(selectedRow);
              print(selectedRows);
            }),
        Expanded(
          child: SfDataGrid(
            source: _employeeDataSource,
            columns: [
              GridNumericColumn(mappingName: 'id', headerText: 'ID'),
              GridTextColumn(mappingName: 'name', headerText: 'Name'),
              GridTextColumn(
                  mappingName: 'designation', headerText: 'Designation'),
              GridNumericColumn(mappingName: 'salary', headerText: 'Salary'),
            ],
            controller: _controller,
            selectionMode: SelectionMode.multiple,
          ),
        ),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

>**NOTE**  
  `SfDataGrid` supports selection via keyboard interaction for the Web platform when `selectionMode` is not `none`.
