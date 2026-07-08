---
layout: post
title: Grouping in Flutter DataGrid | DataTable | Syncfusion
description: Learn all about grouping and multi-grouping data through columns in the Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
--- 

# Grouping in Flutter DataGrid (SfDataGrid)

Grouping in a DataGrid involves organizing and categorizing data based on specific criteria or field values. This feature enables you to group related records together, forming a hierarchical structure within the [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html). Each group is represented by the `CaptionSummaryRow` that displays at the top of each group and holds the caption summary value of that group.

By default, the DataGrid doesn't show the group's caption summary value. To display the caption summary value, you need to override the [DataGridSource.buildGroupCaptionCellWidget](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/buildGroupCaptionCellWidget.html) method. This method receives the caption summary value as a parameter, allowing you to return the necessary widget containing the summary value.

> **Note:** Ensure that you have a populated `DataGridSource` with data rows and columns configured. For custom grouping scenarios, you may need the `collection` package for utility methods like `firstWhereOrNull()`.

## Programmatic grouping

### Add column group

To enable column grouping, add the `ColumnGroup` instance through the `[DataGridSource.addColumnGroup](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/addColumnGroup.html) method.

The `ColumnGroup` object consists of the following properties:

* `name`: The column name of the `GridColumn` to be grouped.
* `sortGroupRows`: Determines whether to group the column with ascending sorting or not.

The following code demonstrates how to apply grouping to a column:

{% tabs %}
{% highlight Dart %} 

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_datagrid/datagrid.dart';

class SfDataGridDemoState extends State<SfDataGridDemo> {
  List<Employee> employees = <Employee>[];
  late EmployeeDataSource employeeDataSource;

  @override
  void initState() {
    super.initState();
    employees = getEmployeeData();
    employeeDataSource = EmployeeDataSource(employeeData: employees);
    employeeDataSource
        .addColumnGroup(ColumnGroup(name: 'Designation', sortGroupRows: true));
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: SfDataGrid(
          source: employeeDataSource,
          allowExpandCollapseGroup: true,
          columns: <GridColumn>[
            GridColumn(
                columnName: 'ID',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('ID'))),
            GridColumn(
                columnName: 'Name',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Name'))),
            GridColumn(
                columnName: 'Designation',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child:
                        Text('Designation', overflow: TextOverflow.ellipsis))),
            GridColumn(
                columnName: 'Salary',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Salary'))),
          ]),
    );
  }
}

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource({required List<Employee> employeeData}) {
    dataGridRows = employeeData
        .map<DataGridRow>((e) => DataGridRow(cells: [
              DataGridCell<int>(columnName: 'ID', value: e.id),
              DataGridCell<String>(columnName: 'Name', value: e.name),
              DataGridCell<String>(
                  columnName: 'Designation', value: e.designation),
              DataGridCell<double>(columnName: 'Salary', value: e.salary),
            ]))
        .toList();
  }

  List<DataGridRow> dataGridRows = [];

  @override
  List<DataGridRow> get rows => dataGridRows;

  @override
  DataGridRowAdapter buildRow(DataGridRow row) {
    return DataGridRowAdapter(
        cells: row.getCells().map<Widget>((e) {
      return Container(
        alignment: Alignment.center,
        padding: EdgeInsets.all(8),
        child: Text(
          e.value.toString(),
        ),
      );
    }).toList());
  }

  @override
  Widget? buildGroupCaptionCellWidget(
      RowColumnIndex rowColumnIndex, String summaryValue) {
    return Container(
        padding: EdgeInsets.symmetric(horizontal: 12, vertical: 15),
        child: Text(summaryValue));
  }
}

{% endhighlight %}
{% endtabs %}

<img alt="Flutter datagrid shows the single level grouping" src="images/grouping/flutter-datagrid-add-group.gif" width="400"/>

### Remove column group

To disable column grouping for a particular column, remove that `ColumnGroup` instance using the [DataGridSource.removeColumnGroup](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/removeColumnGroup.html) method.

{% tabs %}
{% highlight Dart %} 

import 'package:collection/collection.dart';
import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_datagrid/datagrid.dart';

  List<Employee> employees = <Employee>[];
  late EmployeeDataSource employeeDataSource;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: Column(
        children: [
          ElevatedButton(
            onPressed: () {
              setState(() {});
              ColumnGroup? group = employeeDataSource.groupedColumns
                  .firstWhereOrNull((element) => element.name == 'Salary');
              if (group != null) {
                employeeDataSource.removeColumnGroup(group);
              }
            },
            child: Text('Remove Salary Column Group'),
          ),
          Expanded(
            child: SfDataGrid(
              source: employeeDataSource,
              allowExpandCollapseGroup: true,
              columns: <GridColumn>[
                GridColumn(
                  columnName: 'ID',
                  label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('ID'),
                  ),
                ),
                GridColumn(
                  columnName: 'Name',
                  label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Name'),
                  ),
                ),
                GridColumn(
                  columnName: 'Designation',
                  label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Designation', overflow: TextOverflow.ellipsis),
                  ),
                ),
                GridColumn(
                  columnName: 'Salary',
                  label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Salary'),
                  ),
                ),
              ],
            ),
          ),
        ],
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

### Clear all column groups

To clear all the column groups, simply call the [DataGridSource.clearColumnGroups](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/clearColumnGroups.html) method.

{% tabs %}
{% highlight Dart %} 

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_datagrid/datagrid.dart';

class SfDataGridDemoState extends State<SfDataGridDemo> {
  List<Employee> employees = <Employee>[];
  late EmployeeDataSource employeeDataSource;

  @override
  void initState() {
    super.initState();
    employees = getEmployeeData();
    employeeDataSource = EmployeeDataSource(employeeData: employees);
    employeeDataSource.addColumnGroup(
      ColumnGroup(name: 'Designation', sortGroupRows: true),
    );
    employeeDataSource.addColumnGroup(
      ColumnGroup(name: 'Salary', sortGroupRows: false),
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: Column(
        children: [
          ElevatedButton(
            onPressed: () {
              setState(() {});
              employeeDataSource.clearColumnGroups();
            },
            child: const Text('Clear all column groups'),
          ),
          Expanded(
            child: SfDataGrid(
              source: employeeDataSource,
              allowExpandCollapseGroup: true,
              columns: <GridColumn>[
                GridColumn(
                  columnName: 'ID',
                  label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: const Text('ID'),
                  ),
                ),
                GridColumn(
                  columnName: 'Name',
                  label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: const Text('Name'),
                  ),
                ),
                GridColumn(
                  columnName: 'Designation',
                  label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: const Text(
                      'Designation',
                      overflow: TextOverflow.ellipsis,
                    ),
                  ),
                ),
                GridColumn(
                  columnName: 'Salary',
                  label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: const Text('Salary'),
                  ),
                ),
              ],
            ),
          ),
        ],
      ),
    );
  }
}

{% endhighlight %}
{% endtabs %}

## Multi-level grouping

The `SfDataGrid` allows grouping of data against one or more columns by adding multiple columns to the [DataGridSource.addColumnGroup](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/addColumnGroup.html) property. This feature organizes data into a hierarchical tree structure based on identical values within those columns.

Initially, data is grouped according to the first column added to the `DataGridSource.addColumnGroup` property. Subsequently, when additional columns are included, each new column is grouped in consideration of the existing group(s), creating a tree-like hierarchy:
    
{% tabs %}
{% highlight Dart %}

  @override
  void initState() {
    super.initState();
    employees = getEmployeeData();
    employeeDataSource = EmployeeDataSource(employeeData: employees);
    employeeDataSource
        .addColumnGroup(ColumnGroup(name: 'Designation', sortGroupRows: true));
    employeeDataSource
        .addColumnGroup(ColumnGroup(name: 'Salary', sortGroupRows: false));
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: SfDataGrid(
          source: employeeDataSource,
          allowExpandCollapseGroup: true,
          columns: <GridColumn>[
            GridColumn(
                columnName: 'ID',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text(
                      'ID'))),
            GridColumn(
                columnName: 'Name',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Name'))),
            GridColumn(
                columnName: 'Designation',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child:
                        Text('Designation', overflow: TextOverflow.ellipsis))),
            GridColumn(
                columnName: 'Salary',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Salary'))),
          ]),
    );
  }
        
{% endhighlight %}
{% endtabs %}

<img alt="Flutter datagrid shows the multi level grouping" src="images/grouping/flutter-datagrid-multi-level grouping.gif" width="400"/>

## Callbacks

The `SfDataGrid` provides the following callbacks to notify the grouping stages:

### GroupExpanding

The [SfDataGrid.groupExpanding](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/groupExpanding.html) callback is invoked when the group is being expanded. You can return false from this callback to restrict the group from being expanded.

{% tabs %}
{% highlight Dart %}

  @override
  void initState() {
    super.initState();
    employees = getEmployeeData();
    employeeDataSource = EmployeeDataSource(employeeData: employees);
    employeeDataSource
        .addColumnGroup(ColumnGroup(name: 'Designation', sortGroupRows: true));
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: SfDataGrid(
          source: employeeDataSource,
          allowExpandCollapseGroup: true,
          groupExpanding: (group) {
            print('Group expanding: ${group.key}');
            print('Group level: ${group.groupLevel}');
            return true;
          },
          columns: <GridColumn>[
            GridColumn(
                columnName: 'ID',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('ID'))),
            GridColumn(
                columnName: 'Name',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Name'))),
            GridColumn(
                columnName: 'Designation',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child:
                        Text('Designation', overflow: TextOverflow.ellipsis))),
            GridColumn(
                columnName: 'Salary',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Salary'))),
          ]),
    );
  }
        
{% endhighlight %}
{% endtabs %}

### GroupExpanded

The [SfDataGrid.groupExpanded](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/groupExpanded.html) callback is invoked when the group is expanded.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: SfDataGrid(
          source: employeeDataSource,
          allowExpandCollapseGroup: true,
          groupExpanded: (group) {
            print('Group expanding: ${group.key}');
            print('Group level: ${group.groupLevel}');
          },
          columns: <GridColumn>[
            GridColumn(
                columnName: 'ID',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('ID'))),
            GridColumn(
                columnName: 'Name',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Name'))),
            GridColumn(
                columnName: 'Designation',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child:
                        Text('Designation', overflow: TextOverflow.ellipsis))),
            GridColumn(
                columnName: 'Salary',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Salary'))),
          ]),
    );
  }

{% endhighlight %}
{% endtabs %}

### GroupCollapsing

The [SfDataGrid.groupCollapsing](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/groupCollapsing.html) callback is invoked when a group is being collapsed. You can return `false` from this callback to restrict the group from being collapsed:

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: SfDataGrid(
          source: employeeDataSource,
          allowExpandCollapseGroup: true,
          groupCollapsing: (group) {
            print('Group expanding: ${group.key}');
            print('Group level: ${group.groupLevel}');
            return true;
          },
          columns: <GridColumn>[
            GridColumn(
                columnName: 'ID',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('ID'))),
            GridColumn(
                columnName: 'Name',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Name'))),
            GridColumn(
                columnName: 'Designation',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child:
                        Text('Designation', overflow: TextOverflow.ellipsis))),
            GridColumn(
                columnName: 'Salary',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Salary'))),
          ]),
    );
  }
        
{% endhighlight %}
{% endtabs %}

### GroupCollapsed

The [SfDataGrid.groupCollapsed](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/groupCollapsed.html) callback is invoked when the group is collapsed.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: SfDataGrid(
          source: employeeDataSource,
          allowExpandCollapseGroup: true,
          groupCollapsed: (group) {
            print('Group expanding: ${group.key}');
            print('Group level: ${group.groupLevel}');
          },
          columns: <GridColumn>[
            GridColumn(
                columnName: 'ID',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('ID'))),
            GridColumn(
                columnName: 'Name',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Name'))),
            GridColumn(
                columnName: 'Designation',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child:
                        Text('Designation', overflow: TextOverflow.ellipsis))),
            GridColumn(
                columnName: 'Salary',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Salary'))),
          ]),
    );
  }
        
{% endhighlight %}
{% endtabs %}

## Custom grouping

Use custom grouping when you need to group data based on derived or transformed values, such as salary ranges, age groups, or custom categories that don't directly correspond to column values. This approach provides more flexibility than standard column-based grouping.

Custom grouping is implemented by overriding the [DataGridSource.performGrouping](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/performGrouping.html) method. This method is invoked when grouping is applied to the `SfDataGrid`, allowing you to implement custom logic and return a `String` representing the group key for each row.

{% tabs %}
{% highlight Dart %}

import 'package:collection/collection.dart';
import 'package:syncfusion_flutter_datagrid/datagrid.dart';
import 'package:flutter/material.dart';

class SfDataGridDemoState extends State<SfDataGridDemo> {
  List<Employee> employees = <Employee>[];
  late EmployeeDataSource employeeDataSource;

  @override
  void initState() {
    super.initState();
    employees = getEmployeeData();
    employeeDataSource = EmployeeDataSource(employeeData: employees);
    employeeDataSource.addColumnGroup(
      ColumnGroup(name: 'Salary', sortGroupRows: true),
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: SfDataGrid(
        source: employeeDataSource,
        allowExpandCollapseGroup: true,
        columns: <GridColumn>[
          GridColumn(
            columnName: 'ID',
            label: Container(
              padding: EdgeInsets.all(8),
              alignment: Alignment.center,
              child: Text('ID'),
            ),
          ),
          GridColumn(
            columnName: 'Name',
            label: Container(
              padding: EdgeInsets.all(8),
              alignment: Alignment.center,
              child: Text('Name'),
            ),
          ),
          GridColumn(
            columnName: 'Designation',
            label: Container(
              padding: EdgeInsets.all(8),
              alignment: Alignment.center,
              child: Text('Designation', overflow: TextOverflow.ellipsis),
            ),
          ),
          GridColumn(
            columnName: 'Salary',
            label: Container(
              padding: EdgeInsets.all(8),
              alignment: Alignment.center,
              child: Text('Salary'),
            ),
          ),
        ],
      ),
    );
  }
}

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource({required List<Employee> employeeData}) {
    dataGridRows = employeeData
        .map<DataGridRow>(
          (e) => DataGridRow(
            cells: [
              DataGridCell<int>(columnName: 'ID', value: e.id),
              DataGridCell<String>(columnName: 'Name', value: e.name),
              DataGridCell<String>(
                columnName: 'Designation',
                value: e.designation,
              ),
              DataGridCell<double>(columnName: 'Salary', value: e.salary),
            ],
          ),
        )
        .toList();
  }

  List<DataGridRow> dataGridRows = [];

  @override
  List<DataGridRow> get rows => dataGridRows;

  @override
  DataGridRowAdapter buildRow(DataGridRow row) {
    return DataGridRowAdapter(
      cells: row.getCells().map<Widget>((e) {
        return Container(
          alignment: Alignment.center,
          padding: EdgeInsets.all(8),
          child: Text(e.value.toString()),
        );
      }).toList(),
    );
  }

  @override
  Widget? buildGroupCaptionCellWidget(
    RowColumnIndex rowColumnIndex,
    String summaryValue,
  ) {
    return Container(
      padding: EdgeInsets.symmetric(horizontal: 12, vertical: 15),
      child: Text(summaryValue),
    );
  }

  @override
  String performGrouping(String columnName, DataGridRow row) {
    if (columnName == 'Salary') {
      final DataGridCell<double>? salaryCell = row
          .getCells()
          .whereType<DataGridCell<double>>()
          .firstWhereOrNull(
            (DataGridCell cell) => cell.columnName == columnName,
          );

      if (salaryCell != null && salaryCell.value != null) {
        final double total = salaryCell.value!;
        if (total > 100000 && total <= 200000) {
          return '> 100 K & <= 200 K';
        } else if (total > 90000 && total <= 100000) {
          return '> 90 K & <= 100 K';
        } else if (total > 50000 && total <= 90000) {
          return '> 50 K & <= 90 K';
        } else if (total > 30000 && total <= 50000) {
          return '> 30 K & <= 50 K';
        } else {
          return '<= 30 K';
        }
      }
    }
    return super.performGrouping(columnName, row);
  }
}
        
{% endhighlight %}
{% endtabs %}

<img alt="Flutter datagrid shows the custom grouping" src="images/grouping/flutter-datagrid-custom-group.png" width="400"/>

## Enable group expand and collapse 

The group expand and collapse functionality can be enabled by setting the [SfDataGrid.allowExpandCollapseGroup](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/allowExpandCollapseGroup.html) property to `true`. The default value of this property is `false`.

When `allowExpandCollapseGroup` is set to `false`, groups are displayed but users cannot expand or collapse them; all groups remain in their default state as determined by the `autoExpandGroups` property.

{% tabs %}
{% highlight Dart %}

  @override
  void initState() {
    super.initState();
    employees = getEmployeeData();
    employeeDataSource = EmployeeDataSource(employeeData: employees);
    employeeDataSource
        .addColumnGroup(ColumnGroup(name: 'Salary', sortGroupRows: true));
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: SfDataGrid(
          source: employeeDataSource,
          allowExpandCollapseGroup: true,
          columns: <GridColumn>[
            GridColumn(
                columnName: 'ID',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('ID'))),
            GridColumn(
                columnName: 'Name',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Name'))),
            GridColumn(
                columnName: 'Designation',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child:
                        Text('Designation', overflow: TextOverflow.ellipsis))),
            GridColumn(
                columnName: 'Salary',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Salary'))),
          ]),
    );
  }
        
{% endhighlight %}
{% endtabs %}

## Disable group expanding on the initial loading

By default, the SfDataGrid always expands all the groups. All the groups can be collapsed intially by setting the [SfDataGrid.autoExpandGroups](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/autoExpandGroups.html) property to false.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: SfDataGrid(
          source: employeeDataSource,
          autoExpandGroups: false,
          allowExpandCollapseGroup: true,
          columns: <GridColumn>[
            GridColumn(
                columnName: 'ID',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('ID'))),
            GridColumn(
                columnName: 'Name',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Name'))),
            GridColumn(
                columnName: 'Designation',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child:
                        Text('Designation', overflow: TextOverflow.ellipsis))),
            GridColumn(
                columnName: 'Salary',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Salary'))),
          ]),
    );
  }
        
{% endhighlight %}
{% endtabs %}

## Programmatically expand and collapse groups

Expanding and collapsing groups programmatically can be achieved using the following [DataGridController](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController-class.html) methods:

<table>
<tr>
<th>Method </th>
<th>Description </th>
</tr>
<tr>
<td><code>expandAllGroup</code></td>
<td>Expands all the groups in the SfDataGrid</td>
</tr>
<tr>
<td><code>collapseAllGroup</code></td>
<td>Collapses all the groups in the SfDataGrid</td>
</tr>
<tr>
<td><code>expandGroupsAtLevel</code></td>
<td>Expands the groups based on the group level</td>
</tr>
<tr>
<td><code>collapseGroupsAtLevel</code></td>
<td>Collapses the groups based on the group level</td>
</tr>
</table>

The following code example demonstrates how to use these methods:

{% tabs %}
{% highlight Dart %}

  List<Employee> _employees = <Employee>[];
  late EmployeeDataSource _employeeDataSource;
  final DataGridController _dataGridController = DataGridController();
  
  @override
  void initState() {
    super.initState();
    _employees = getEmployeeData();
    _employeeDataSource = EmployeeDataSource(employeeData: _employees);
    _employeeDataSource.addColumnGroup(
      ColumnGroup(name: 'Designation', sortGroupRows: true),
    );
    _employeeDataSource.addColumnGroup(
      ColumnGroup(name: 'Salary', sortGroupRows: false),
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: Column(
        children: [
          Row(
            mainAxisAlignment: MainAxisAlignment.spaceEvenly,
            children: [
              ElevatedButton(
                onPressed: () {
                  _dataGridController.expandAllGroup();
                },
                child: const Text('Expand All'),
              ),
              ElevatedButton(
                onPressed: () {
                  _dataGridController.collapseAllGroup();
                },
                child: const Text('Collapse All'),
              ),
            ],
          ),
          Expanded(
            child: SfDataGrid(
              controller: _dataGridController,
              source: _employeeDataSource,
              gridLinesVisibility: GridLinesVisibility.both,
              headerGridLinesVisibility: GridLinesVisibility.both,
              allowExpandCollapseGroup: true,
              columns: <GridColumn>[
                GridColumn(
                  columnName: 'ID',
                  label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('ID'),
                  ),
                ),
                GridColumn(
                  columnName: 'Name',
                  label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Name'),
                  ),
                ),
                GridColumn(
                  columnName: 'Designation',
                  label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Designation', overflow: TextOverflow.ellipsis),
                  ),
                ),
                GridColumn(
                  columnName: 'Salary',
                  label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Salary'),
                  ),
                ),
              ],
            ),
          ),
        ],
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Customize the group caption summary row format

The caption summary value is displayed in a caption summary row by the default format `'{ColumnName} : {Key} - {ItemsCount} Items'`. The available placeholders for customizing the format are:

* `{ColumnName}`: The name of the grouped column
* `{Key}`: The identical cell value of the group
* `{ItemsCount}`: The number of rows in the group

The format can be customized by using the [SfDataGrid.groupCaptionTitleFormat](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/groupCaptionTitleFormat.html) property.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: SfDataGrid(
          source: employeeDataSource,
          allowExpandCollapseGroup: true,
          groupCaptionTitleFormat: '{ColumnName} : {Key} - {ItemsCount}',
          columns: <GridColumn>[
            GridColumn(
                columnName: 'ID',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('ID'))),
            GridColumn(
                columnName: 'Name',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Name'))),
            GridColumn(
                columnName: 'Designation',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child:
                        Text('Designation', overflow: TextOverflow.ellipsis))),
            GridColumn(
                columnName: 'Salary',
                label: Container(
                    padding: EdgeInsets.all(8),
                    alignment: Alignment.center,
                    child: Text('Salary'))),
          ]),
    );
  }
        
{% endhighlight %}
{% endtabs %}

<img alt="Flutter datagrid shows the customized summary format" src="images/grouping/flutter-datagrid-customize-summary-format.png" width="400"/>

## Customize the indent column appearance

The width and color of the indent column can be personalized using the [SfDataGridThemeData.indentColumnWidth](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/indentColumnWidth.html) and [SfDataGridThemeData.indentColumnColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/indentColumnColor.html) properties. The default values for these properties are `40.0` and `null,` respectively.

{% tabs %}
{% highlight Dart %}

 import 'package:syncfusion_flutter_core/theme.dart';
 import 'package:syncfusion_flutter_datagrid/datagrid.dart';

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: SfDataGridTheme(
        data: SfDataGridThemeData(
            indentColumnWidth: 100, indentColumnColor: Colors.amber),
        child: SfDataGrid(
            source: employeeDataSource,
            allowExpandCollapseGroup: true,
            columns: <GridColumn>[
              GridColumn(
                  columnName: 'ID',
                  label: Container(
                      padding: EdgeInsets.all(8),
                      alignment: Alignment.center,
                      child: Text('ID'))),
              GridColumn(
                  columnName: 'Name',
                  label: Container(
                      padding: EdgeInsets.all(8),
                      alignment: Alignment.center,
                      child: Text('Name'))),
              GridColumn(
                  columnName: 'Designation',
                  label: Container(
                      padding: EdgeInsets.all(8),
                      alignment: Alignment.center,
                      child: Text('Designation',
                          overflow: TextOverflow.ellipsis))),
              GridColumn(
                  columnName: 'Salary',
                  label: Container(
                      padding: EdgeInsets.all(8),
                      alignment: Alignment.center,
                      child: Text('Salary'))),
            ]),
      ),
    );
  }
        
{% endhighlight %}
{% endtabs %}

## Customize the group expander icon

The group expander icon is used to indicate the state of a group. It is displayed only when the [SfDataGrid.allowExpandCollapseGroup](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/allowExpandCollapseGroup.html) option is enabled. The icon can be customized by using the [SfDataGridThemeData.groupExpanderIcon](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/groupExpanderIcon.html) property.

The `SfDataGridThemeData` and `SfDataGridTheme` classes are available in the [syncfusion_flutter_core](https://pub.dev/packages/syncfusion_flutter_core) package.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: SfDataGridTheme(
        data: SfDataGridThemeData(
            groupExpanderIcon: Icon(Icons.expand_circle_down_outlined,
                size: 20, color: Colors.pink)),
        child: SfDataGrid(
            source: employeeDataSource,
            allowExpandCollapseGroup: true,
            columns: <GridColumn>[
              GridColumn(
                  columnName: 'ID',
                  label: Container(
                      padding: EdgeInsets.all(8),
                      alignment: Alignment.center,
                      child: Text('ID'))),
              GridColumn(
                  columnName: 'Name',
                  label: Container(
                      padding: EdgeInsets.all(8),
                      alignment: Alignment.center,
                      child: Text('Name'))),
              GridColumn(
                  columnName: 'Designation',
                  label: Container(
                      padding: EdgeInsets.all(8),
                      alignment: Alignment.center,
                      child: Text('Designation',
                          overflow: TextOverflow.ellipsis))),
              GridColumn(
                  columnName: 'Salary',
                  label: Container(
                      padding: EdgeInsets.all(8),
                      alignment: Alignment.center,
                      child: Text('Salary'))),
            ]),
      ),
    );
  }
        
{% endhighlight %}
{% endtabs %}

<img alt="Flutter datagrid shows the custom group expander icon" src="images/grouping/flutter-datagrid-custom-group-expander-icon.png" width="400"/>

## Limitations

* Grouping is refreshed when performing CRUD operations on [DataGridSource.rows](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/rows.html) or [SfDataGrid.columns](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/columns.html). This action resets expand and collapse states of groups based on the [SfDataGrid.autoExpandGroups](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/autoExpandGroups.html) property. To work around this, update the `rows` collection in-place rather than reassigning it completely.
* To prevent unnecessary grouping refresh, ensure that the `SfDataGrid.columns` property is assigned once as a single instance rather than being recreated on each build or state change.
