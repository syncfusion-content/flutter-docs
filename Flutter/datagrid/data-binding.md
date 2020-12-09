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

 * [dataSource](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/dataSource.html) - The number of rows in a datagrid and row selection depends
 on the [dataSource]. So, set the collection required for datagrid in
`dataSource`.
* [getValue](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/getValue.html) - The data needed for the cells is obtained from
`getValue`.

`DataGridSource` objects are expected to be long-lived, not recreated with each build.

The following example shows how to create the `DataGridSource`,

{% tabs %}
{% highlight dart %} 

final List<Employee> _employees = <Employee>[];

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

The following example shows how to set the `source` property in `SfDataGrid`

{% tabs %}
{% highlight dart %}

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
    appBar: AppBar(
      title: const Text('Syncfusion Flutter DataGrid'),
    ),
    body: Column(
      children: [
        FlatButton(
            child: const Text('Add row'),
            onPressed: () {
              _employees.add(Employee(10011, 'Steve', 'Designer', 15000));
              _employeeDataSource.updateDataGridSource();
            }),
        SfDataGrid(
          source: _employeeDataSource,
          columns: <GridColumn>[
            GridNumericColumn(mappingName: 'id', headerText: 'ID'),
            GridTextColumn(mappingName: 'name', headerText: 'Name'),
            GridTextColumn(
                mappingName: 'designation', headerText: 'Designation'),
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary'),
          ],
        ),
      ],
    ),
  );
}

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
              _employeeDataSource.updateDataGridSource(
                  rowColumnIndex: RowColumnIndex(0, 3));
            }),
        SfDataGrid(
          source: _employeeDataSource,
          columns: <GridColumn>[
            GridNumericColumn(mappingName: 'id', headerText: 'ID'),
            GridTextColumn(mappingName: 'name', headerText: 'Name'),
            GridTextColumn(
                mappingName: 'designation', headerText: 'Designation'),
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary'),
          ],
        ),
      ],
    ),
  );
}

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

  void updateDataGridSource({RowColumnIndex rowColumnIndex}) {
    notifyDataSourceListeners(rowColumnIndex: rowColumnIndex);
  }
}

{% endhighlight %}
{% endtabs %}
