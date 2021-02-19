---
layout: post
title: Pull to Refresh in Flutter DataGrid | DataTable | Syncfusion
description: Learn about how to add more data at runtime by using pull to refresh support and how to show refresh indicator programmatically in Syncfusion Flutter DataGrid.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Pull to Refresh in Flutter DataGrid

The datagrid provides support to add more data at runtime by using the PullToRefresh feature.
You can simply enable the PullToRefresh option by setting the `SfDataGrid.allowPullToRefresh` property to `true` and override the `DataGridSource.handleRefresh` method to include the data which is going to add to the data source at runtime and then notify the data grid about the changes. When the PullToRefresh is enabled, the control supports refreshing the data source while doing the pull to refresh action.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

@override
Widget build(BuildContext context) {
  return SfDataGrid(
    allowPullToRefresh: true,
    source: employeeDataSource,
    columns: <GridColumn>[
      GridNumericColumn(mappingName: 'id', headerText: 'ID'),
      GridTextColumn(mappingName: 'name', headerText: 'Name'),
      GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
      GridNumericColumn(mappingName: 'salary', headerText: 'Salary'),
    ],
  );
}

final List<String> _names = <String>[
  'Welli',
  'Blonp',
  'Folko',
  'Furip',
  'Folig',
  'Picco',
  'Frans',
  'Warth',
  'Linod',
  'Simop',
  'Merep',
  'Riscu',
  'Seves',
  'Vaffe',
  'Alfki'
];

final List<String> _designation = <String>[
  'Project Lead',
  'Developer',
  'Manager',
  'Designer',
  'System Analyst',
  'CEO'
];

List<Employee> _addMoreRows(List<Employee> employeeData, int count) {
  final Random _random = Random();
  int startIndex = employeeData.isNotEmpty ? employeeData.length : 0,
      endIndex = startIndex + count;
  for (int i = startIndex; i < endIndex; i++) {
    employeeData.add(Employee(
      1000 + i,
      _names[_random.nextInt(_names.length - 1)],
      _designation[_random.nextInt(_designation.length - 1)],
      10000 + _random.nextInt(10000),
    ));
  }
  return employeeData;
}

class EmployeeDataSource extends DataGridSource<Employee> {
  @override
  List<Employee> get dataSource => employees;

  @override
  Object getValue(Employee employee, String columnName) {
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

  @override
  Future<void> handleRefresh() async {
    await Future.delayed(Duration(seconds: 5));
    _addMoreRows(employees, 15);
    notifyListeners();
  }
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows default view of refresh indicator](images/pull-to-refresh/flutter-datagrid-pull-to-refresh.gif)

## Customizing the refresh indicator

Color and background color of refresh indicator can be customized by using the `ThemeData.accentColor` and  `ThemeData.canvasColor` properties.
Stroke width and displacement of refresh indicator can be customized by using `SfDataGrid.refreshIndicatorStrokeWidth` and `SfDataGrid.refreshIndicatorDisplacement` properties.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

@override
Widget build(BuildContext context) {
  return Theme(
    data: ThemeData(
      accentColor: Colors.white,
      canvasColor: Colors.lightBlue,
    ),
    child: SfDataGrid(
      allowPullToRefresh: true,
      source: employeeDataSource,
      refreshIndicatorStrokeWidth: 3.0,
      refreshIndicatorDisplacement: 60.0,
      columns: <GridColumn>[
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

![flutter datagrid shows customized refresh indicator](images/pull-to-refresh/flutter-datagrid-customized-pull-to-refresh-indicator.gif)

## Programmatic Pull to Refresh

The data grid provides the support to show refresh indicator programmatically. You can simply call refresh indicator by providing `GlobalKey` value to the `SfDataGrid` and call `GlobalKey.refresh()` method to show refresh indicator programmatically. The global key type should be `SfDataGridState`. By default, it shows a refresh indicator whenever it is called. If you want to refresh data without showing a refresh indicator, you can set false to the `showRefreshIndicator` optional parameter like `GlobalKey.refresh(false)`.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

final GlobalKey<SfDataGridState> key = GlobalKey<SfDataGridState>();

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: Text('DataGrid Demo'),
    ),
    body: SfDataGrid(
      key: key,
      allowPullToRefresh: true,
      source: employeeDataSource,
      columns: <GridColumn>[
        GridNumericColumn(mappingName: 'id', headerText: 'ID'),
        GridTextColumn(mappingName: 'name', headerText: 'Name'),
        GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
        GridNumericColumn(mappingName: 'salary', headerText: 'Salary'),
      ],
    ),
    floatingActionButton: FloatingActionButton(
      child: Icon(Icons.refresh),
      onPressed: () {
        key.currentState.refresh();
      },
    ),
  );
}

final List<String> _names = <String>[
  'Welli',
  'Blonp',
  'Folko',
  'Furip',
  'Folig',
  'Picco',
  'Frans',
  'Warth',
  'Linod',
  'Simop',
  'Merep',
  'Riscu',
  'Seves',
  'Vaffe',
  'Alfki'
];

final List<String> _designation = <String>[
  'Project Lead',
  'Developer',
  'Manager',
  'Designer',
  'System Analyst',
  'CEO'
];

List<Employee> _addMoreRows(List<Employee> employeeData, int count) {
  final Random _random = Random();
  int startIndex = employeeData.isNotEmpty ? employeeData.length : 0,
      endIndex = startIndex + count;
  for (int i = startIndex; i < endIndex; i++) {
    employeeData.add(Employee(
      1000 + i,
      _names[_random.nextInt(_names.length - 1)],
      _designation[_random.nextInt(_designation.length - 1)],
      10000 + _random.nextInt(10000),
    ));
  }
  return employeeData;
}

class EmployeeDataSource extends DataGridSource<Employee> {
  @override
  List<Employee> get dataSource => employees;

  @override
  Object getValue(Employee employee, String columnName) {
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

  @override
  Future<void> handleRefresh() async {
    await Future.delayed(Duration(seconds: 5));
    _addMoreRows(employees, 15);
    notifyListeners();
  }
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows programmatic refresh indicator](images/pull-to-refresh/flutter-datagrid-programmatic-pull-to-refresh.gif)