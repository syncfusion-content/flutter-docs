---
layout: post
title: Pull to Refresh in Flutter DataGrid | DataTable | Syncfusion
description: Learn about how to add more data at runtime by using pull to refresh support and how to show refresh indicator programmatically in Syncfusion Flutter DataGrid.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Pull to Refresh in Flutter DataGrid

The Flutter DataTable provides support to add more data at runtime by using the PullToRefresh feature.
You can simply enable the PullToRefresh option by setting the `SfDataGrid.allowPullToRefresh` property to `true` and override the `DataGridSource.handleRefresh` method to include the data which is going to add to the data source at runtime and then notify the data grid about the changes.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

@override
Widget build(BuildContext context) {
  return SfDataGrid(
    allowPullToRefresh: true,
    source: employeeDataSource,
    columns: <GridColumn>[
      GridTextColumn(columnName: 'id', label: Text('ID')),
      GridTextColumn(columnName: 'name', label: Text('Name')),
      GridTextColumn(columnName: 'designation', label: Text('Designation')),
      GridTextColumn(columnName: 'salary', label: Text('Salary')),
    ],
  );
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

class EmployeeDataSource extends DataGridSource {
  List<DataGridRow> employeeData;
  EmployeeDataSource({List<Employee> employeesData}) {
    getData(employeesData);
  }
  getData(List<Employee> employeesData) {
    employeeData = employeesData
        .map<DataGridRow>((e) => DataGridRow(cells: [
              DataGridCell<int>(columnName: 'id', value: e.id),
              DataGridCell<String>(columnName: 'name', value: e.name),
              DataGridCell<String>(
                  columnName: 'designation', value: e.designation),
              DataGridCell<int>(columnName: 'salary', value: e.salary)
            ]))
        .toList();
  }

  @override
  List<DataGridRow> get rows => employeeData;

  @override
  DataGridRowAdapter buildRow(DataGridRow row) {
    return DataGridRowAdapter(
        cells: row.getCells().map<Widget>((e) {
      if (e.columnName == 'image') {
        return e.value;
      } else {
        return Container(
          alignment: Alignment.center,
          padding: EdgeInsets.all(8.0),
          child: Text(e.value.toString()),
        );
      }
    }).toList());
  }

  @override
  Future<void> handleRefresh() async {
    await Future.delayed(Duration(seconds: 5));
    _addMoreRows(employees, 15);
    notifyListeners();
  }

  void _addMoreRows() {
    employeeData.addAll([
      Employee(10001, 'James', 'Project Lead', 20000),
      Employee(10002, 'Kathryn', 'Manager', 30000),
      Employee(10003, 'Lara', 'Developer', 15000),
      Employee(10004, 'Michael', 'Designer', 15000),
      Employee(10005, 'Martin', 'Developer', 15000),
    ]
        .map<DataGridRow>((e) => DataGridRow(cells: [
              DataGridCell(columnName: 'id', value: e.id),
              DataGridCell(columnName: 'name', value: e.name),
              DataGridCell(columnName: 'designation', value: e.designation),
              DataGridCell(columnName: 'salary', value: e.salary),
            ]))
        .toList());
  }
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows default view of refresh indicator](images/pull-to-refresh/flutter-datagrid-pull-to-refresh.gif)

## Customizing the refresh indicator

SfDataGrid displays the [RefreshIndicator](https://api.flutter.dev/flutter/material/RefreshIndicator-class.html) for `pull to refresh` action. So, you can set the color and background color of refresh indicator by using [ThemeData.accentColor](https://api.flutter.dev/flutter/material/ThemeData/accentColor.html) and  [ThemeData.canvasColor](https://api.flutter.dev/flutter/material/ThemeData/canvasColor.html) properties.

You can also change the stroke width and displacement of refresh indicator by using `SfDataGrid.refreshIndicatorStrokeWidth` and `SfDataGrid.refreshIndicatorDisplacement` properties.

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
        GridTextColumn(columnName: 'id', label: Text('ID')),
        GridTextColumn(columnName: 'name', label: Text('Name')),
        GridTextColumn(columnName: 'designation', label: Text('Designation')),
        GridTextColumn(columnName: 'salary', label: Text('Salary')),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows customized refresh indicator](images/pull-to-refresh/flutter-datagrid-customized-pull-to-refresh-indicator.gif)

## Programmatic Pull to Refresh

If you want to refresh data without showing a refresh indicator, you can pass `false` to the `showRefreshIndicator` optional parameter of `refresh` method. By doing this, `DataGridSource.handleRefresh` method will be called without showing the `RefreshIndicator` in UI.

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
        GridTextColumn(columnName: 'id', label: Text('ID')),
        GridTextColumn(columnName: 'name', label: Text('Name')),
        GridTextColumn(columnName: 'designation', label: Text('Designation')),
        GridTextColumn(columnName: 'salary', label: Text('Salary')),
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

class EmployeeDataSource extends DataGridSource {
  List<DataGridRow> employeeData;
  EmployeeDataSource({List<Employee> employeesData}) {
    getData(employeesData);
  }
  getData(List<Employee> employeesData) {
    employeeData = employeesData
        .map<DataGridRow>((e) => DataGridRow(cells: [
              DataGridCell<int>(columnName: 'id', value: e.id),
              DataGridCell<String>(columnName: 'name', value: e.name),
              DataGridCell<String>(
                  columnName: 'designation', value: e.designation),
              DataGridCell<int>(columnName: 'salary', value: e.salary)
            ]))
        .toList();
  }

  @override
  List<DataGridRow> get rows => employeeData;

  @override
  DataGridRowAdapter buildRow(DataGridRow row) {
    return DataGridRowAdapter(
        cells: row.getCells().map<Widget>((e) {
      if (e.columnName == 'image') {
        return e.value;
      } else {
        return Container(
          alignment: Alignment.center,
          padding: EdgeInsets.all(8.0),
          child: Text(e.value.toString()),
        );
      }
    }).toList());
  }

  @override
  Future<void> handleRefresh() async {
    await Future.delayed(Duration(seconds: 5));
    _addMoreRows(employees, 15);
    notifyListeners();
  }

  void _addMoreRows() {
    employeeData.addAll([
      Employee(10001, 'James', 'Project Lead', 20000),
      Employee(10002, 'Kathryn', 'Manager', 30000),
      Employee(10003, 'Lara', 'Developer', 15000),
      Employee(10004, 'Michael', 'Designer', 15000),
      Employee(10005, 'Martin', 'Developer', 15000),
    ]
        .map<DataGridRow>((e) => DataGridRow(cells: [
              DataGridCell(columnName: 'id', value: e.id),
              DataGridCell(columnName: 'name', value: e.name),
              DataGridCell(columnName: 'designation', value: e.designation),
              DataGridCell(columnName: 'salary', value: e.salary),
            ]))
        .toList());
  }
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows programmatic refresh indicator](images/pull-to-refresh/flutter-datagrid-programmatic-pull-to-refresh.gif)