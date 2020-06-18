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

{% highlight dart %} 

    import 'package:syncfusion_flutter_datagrid/datagrid.dart';

{% endhighlight %}

## Initialize DataGrid

Add the SfDataGrid widget as a child of any widget. Here, `SfDataGrid` widget is initialized as a child of Expanded widget. `SfDataGrid` requires the `source` and `columns` properties. You can find the more details on these properties in further topics.

{% highlight dart %} 

    @override
     Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Syncfusion DataGrid'),
      ),
      body: Center(
          child: Expanded(
            child:SfDataGrid(
                    source: _employeeDataSource,
                    columns: [
                      GridNumericColumn(mappingName: 'id',  headerText:'ID'),
                      GridTextColumn(mappingName: 'name', headerText: 'Name'),
                      GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
                      GridNumericColumn(mappingName: 'salary', headerText: 'Salary'),
                    ],                                                   
                  ),
          ),
      ),
    );
    }

{% endhighlight %}

## Creating Data for an application

The `SfDataGrid` is depending upon the data. Create a simple datasource for `SfDataGrid` as shown in the following code example.

{% highlight dart %} 

    class Employee {
    Employee(this.id, this.name, this.designation, this.salary);
    final int id;
    final String name;
    final String designation;
    final int salary;
    }

{% endhighlight %}

Create the collection of Employee data with the required number of data objects. Here, the `populateData` method which is used to populate the data objects is initialized in `initState()`.

{% highlight dart %} 

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
    }

{% endhighlight %}

## Creating DataSource for DataGrid

`DataGridSource` is used to obtain the row data for the ‘SfDataGrid’. So, create the DataSource from the DataGridSource and override the following APIs in it,

* **`dataSource`** - To Fetch the number of rows available for data population. Also, it is used to fetch the corresponding data object to process the selection.
* **`getCellValue`** - To fetch the value for each cell.

`DataGridSource` objects are expected to be long-lived, not recreated with each build.

{% highlight dart %} 

    final List<Employee> _employees =<Employee>[];
    
    final EmployeeDataSource_employeeDataSource= EmployeeDataSource ();
     
     class EmployeeDataSource extend DataGridSource {
      @override
       List<Object> get dataSource => _employees;
      @override
        getCellValue(int rowIndex, String columnName) {
      switch (columnName) {
        case 'id':
         return _employees[rowIndex].id;
          break;
        case 'name':
         return _employees[rowIndex].name;
          break;
        case 'salary':
         return _employees[rowIndex].salary;
          break;
        case 'designation':
         return _employees[rowIndex].designation;
          break;
        default:
         return ' ';
          break;
      }
    }

{% endhighlight %}

Create an instance of `DataGridSource` and set this object to `source` property of `SfDataGrid`.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Syncfusion DataGrid'),
      ),
      body: Center(
          child: Expanded(
            child:SfDataGrid(
                    source: _employeeDataSource,
          ),
      ),
    );
    }

{% endhighlight %}

## Defining columns

`SfDataGrid` supports to show different data types (int, double, String and DateTime) in different types of columns. You can add the column collection to the `columns` property. 
You can also load any widget in a column using the `GridWidgetColumn` and `cellBuilder` property in `SfDataGrid`.

{% highlight dart %} 

    final EmployeeDataSource _employeeDataSource = EmployeeDataSource();
  
    @override
     Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Syncfusion DataGrid'),
      ),
      body: Center(
          child: Expanded(
            child:SfDataGrid(
                    source: _employeeDataSource,
                    columns: [
                      GridNumericColumn(mappingName: 'id',  headerText:'ID'),
                      GridTextColumn(mappingName: 'name', headerText: 'Name'),
                      GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
                      GridNumericColumn(mappingName: 'salary', headerText: 'Salary'),
                    ],                      
                  ),
          ),
      ),
    );
     }

{% endhighlight %}

![flutter datagrid shows different column types](images/getting-started/getting-started-flutter-datagrid.png)

## Selection

SfDataGrid allows you to select one or more rows. The `selectionMode` property can be set to specify whether a user can select single row, or multiple rows. 

{% highlight dart %} 

   final EmployeeDataSource _employeeDataSource = EmployeeDataSource();

     @override
      Widget build(BuildContext context) {
        return Scaffold(
         appBar: AppBar(
           title: Text('Syncfusion DataGrid'),
            ),
         body: Center(
          child: Expanded(
            child:SfDataGrid(
                    source: _employeeDataSource,
                    columns: [
                      GridNumericColumn(mappingName: 'id',  headerText:'ID'),
                      GridTextColumn(mappingName: 'name', headerText: 'Name'),
                      GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
                      GridNumericColumn(mappingName: 'salary', headerText: 'Salary'),
                    ],
                    selectionMode: SelectionMode.multiple,                                                   
                  ),
          ),
      ),
    );
     }

{% endhighlight %}

![flutter datagrid shows rows with selection](images/getting-started/flutter-datagrid-selection.png)

The information about the rows that are selected can be retrieved using `selectedIndex`, `selectedRow`` and selectedRows` properties in `DataGridController`. You need to initialize the `DataGridController` object to the `controller` property of SfDataGrid.
` DataGridController` objects are expected to be long-lived, not recreated with each build.

{% highlight dart %} 

final EmployeeDataSource _employeeDataSource = EmployeeDataSource();

final DataGridController _controller = DataGridController();

    @override
      Widget build(BuildContext context) {
         return Scaffold(
           appBar: AppBar(
             title: Text('Syncfusion DataGrid'),
             ),
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

_note_ : `SfDataGrid` supports selection via keyboard interaction for the Web platform when `selectionMode` is not `none`.
