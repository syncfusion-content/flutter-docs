---
layout: post
title: Grouping in Flutter DataGrid | DataTable | Syncfusion
description: Learn all about how to group the data rows in Syncfusion Flutter DataGrid (SfDataGrid) widget and more here.
platform: flutter
control: SfDataGrid
documentation: ug
--- 

# Grouping in Flutter DataGrid (SfDataGrid)

Grouping in a DataGrid involves organizing and categorizing data based on specific criteria or field values. This feature enables the grouping of related records together, forming a hierarchical structure within the [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html). Each group is represented by its `CaptionSummaryRow`, allowing easy access to the underlying records within the view.

The DataGrid doesn't show group caption summary values by default. To showcase the caption summary value, you will need to override the `buildGroupCaptionCellWidget` method within the `DataGridSource` class. This method receives the caption summary value as a parameter. Consequently, you'll be required to return the necessary widget containing the summary value.

## Programmatic grouping

### Add column group

The SfDataGrid allows for programmatically performing grouping by passing `ColumnGroup` details through the `DataGridSource.addColumnGroup` property. This functionality facilitates data grouping based on the ColumnGroup object added to this property.

The ColumnGroup object consists of the following two required properties:

* `name`: The name of the grouped column.
* `sortGroupRows`: Determines whether to group the column with ascending sorting.

To implement column grouping, please refer to the following code example:

{% tabs %}
{% highlight Dart %} 

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

### Remove column group

You can remove the grouping by passing `ColumnGroup` details to the `DataGridSource.removeColumnGroup` property.

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
      body: Column(children: [
        ElevatedButton(
            onPressed: () {
              setState(() {});
              ColumnGroup? group = employeeDataSource.groupedColumns
                  .firstWhereOrNull((element) => element.name == 'Salary');
              if (group != null) {
                employeeDataSource.removeColumnGroup(group);
              }
            },
            child: Text('Remove Salary Column Group')),
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
            ])),
      ]),
    );
  }

{% endhighlight %}
{% endtabs %}

### Clear all column groups

You can clear all the groups by calling the `DataGridSource.clearColumnGroups` method.

{% tabs %}
{% highlight Dart %} 

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: Column(children: [
        ElevatedButton(
            onPressed: () {
              setState(() {});
              employeeDataSource.clearColumnGroups();
            },
            child: Text('Clear all column groups')),
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
            ])),
      ]),
    );
  }

{% endhighlight %}
{% endtabs %}

## Multi-level grouping

The `SfDataGrid` allows to grouping of data against one or more columns by adding multiple columns to the `DataGridSource.addColumnGroup` property. This feature organizes data into a hierarchical tree structure based on identical values within those columns. The multi-grouping capability functions similarly to the multi-sorting feature.

Initially, data gets grouped according to the first column added in the DataGridSource.addColumnGroup property. Subsequently, when additional columns are included in DataGridSource.addColumnGroup, each new column is grouped in consideration of the existing group(s). This process creates a tree-like hierarchy. To enable MultiGrouping, please refer to the following code snippet:
    
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

## Callbacks

The `SfDataGrid` provides the following callbacks to notify the grouping stages:

### GroupExpanding

The `groupExpanding` callback is invoked when the group is being expanded to a particular column. You can return false from this callback to restrict the group from being expanded.

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

The `groupExpanded` callback invokes when the group expanding is applied to the particular column.

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

The `groupCollapsing` callback is invoked when the group is being collapsed to a particular column. You can return false from this callback to restrict the group from being collapsed.

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

The `groupCollapsed` callback invokes when the group collapsing is applied to the particular column.

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

## Custom Grouping

The `SfDataGrid` provides support to group a column using custom logic when standard grouping techniques aren't sufficient for specific requirements. This can be accomplished by overriding the `DataGridSource.performGrouping` method. 

The `DataGridSource.performGrouping` method is invoked when grouping is applied to the `SfDataGrid`. Within this method, you can implement custom logic to return a `String` based on your specific requirements.

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

  @override
  String performGrouping(String columnName, DataGridRow row) {
    if (columnName == 'Salary') {
      final double total = row
          .getCells()
          .firstWhereOrNull(
              (DataGridCell cell) => cell.columnName == columnName)!
          .value;
      if (total > 100000 && total <= 200000) {
        return '> 100 K & <= 150 K';
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
    return super.performGrouping(columnName, row);
  }
}
        
{% endhighlight %}
{% endtabs %}

## Enable group expand and collapse 

The SfDataGrid allows you to enable the group expand and collapse by setting `true` to the `SfDataGrid.allowExpandCollapseGroup` property. The default value of this property is `false`.

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

The SfDataGrid allows you to disable the group expanding on the initial loading by setting `false` to the `SfDataGrid.autoExpandGroups` property. The default value of this property is `true`.

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

## Expand or collapse the groups programmatically

The SfDataGrid provides the following methods to expand or collapse the groups programmatically.

* `DataGridController.expandAllGroup`: Expands all the groups in the SfDataGrid.

{% tabs %}
{% highlight Dart %}

  DataGridController dataGridController = DataGridController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: Column(children: [
        ElevatedButton(
            onPressed: () {
              dataGridController.expandAllGroup();
            },
            child: Text('Expand All Group')),
        Expanded(
            child: SfDataGrid(
                source: employeeDataSource,
                allowExpandCollapseGroup: true,
                autoExpandGroups: false,
                controller: dataGridController,
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
            ])),
      ]),
    );
  }
        
{% endhighlight %}
{% endtabs %}

* `DataGridController.collapseAllGroup`: Collapses all the groups in the SfDataGrid.

{% tabs %}
{% highlight Dart %}

  DataGridController dataGridController = DataGridController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: Column(children: [
        ElevatedButton(
            onPressed: () {
              dataGridController.collapseAllGroup();
            },
            child: Text('Collapse All Group')),
        Expanded(
            child: SfDataGrid(
                source: employeeDataSource,
                allowExpandCollapseGroup: true,
                controller: dataGridController,
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
            ])),
      ]),
    );
  }
        
{% endhighlight %}
{% endtabs %}

* `DataGridController.expandGroupsAtLevel`: Expands the group based on the group level.

{% tabs %}
{% highlight Dart %}

  DataGridController dataGridController = DataGridController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: Column(children: [
        ElevatedButton(
            onPressed: () {
              dataGridController.expandGroupsAtLevel(1);
            },
            child: Text('Expand level 1 groups')),
        Expanded(
            child: SfDataGrid(
                source: employeeDataSource,
                allowExpandCollapseGroup: true,
                autoExpandGroups: false,
                controller: dataGridController,
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
            ])),
      ]),
    );
  }
        
{% endhighlight %}
{% endtabs %}

* `DataGridController.collapseGroupsAtLevel`: Collapses the group based on the group level.

{% tabs %}
{% highlight Dart %}

  DataGridController dataGridController = DataGridController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: Column(children: [
        ElevatedButton(
            onPressed: () {
              dataGridController.collapseGroupsAtLevel(2);
            },
            child: Text('Collapse Level 2 Groups')),
        Expanded(
            child: SfDataGrid(
                source: employeeDataSource,
                allowExpandCollapseGroup: true,
                controller: dataGridController,
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
            ])),
      ]),
    );
  }
        
{% endhighlight %}
{% endtabs %}

## Customize the group caption summary row format

The SfDataGrid allows you to customize the group caption summary row by using the `SfDataGrid.groupCaptionTitleFormat` property. The default value of this property is  `'{ColumnName} : {Key} - {ItemsCount} Items'`.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: SfDataGrid(
          source: employeeDataSource,
          allowExpandCollapseGroup: true,
          groupCaptionTitleFormat: '{ColumnName} : {Key} - {ItemsCount} Items',
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

## Customize indent column

You can customize the indent column width by using the `SfDataGridThemeData.indentColumnWidth` property and customize the indent column background color by using the `SfDataGridThemeData.indentColumnColor` property. The default value of these properties are 40.0 and null respectively.

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

## Customize group expander icon

The SfDataGrid allows you to change the group expander icon by using the `SfDataGridThemeData.groupExpandIconData` property. The DataGrid should be wrapped inside the SfDataGridTheme.

The `SfDataGridThemeData` and `SfDataGridTheme` classes are available in the syncfusion_flutter_core package. So, import the following file.

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

## Limitations

* When conducting CRUD operations on rows through actions like `editing,` `pull to refresh,` `load more,` or directly on the data source, and when CRUD operations are performed on the columns collection, it triggers a refresh in the grouping. Consequently, this action resets the expansion and collapse states based on the `SfDataGrid.autoExpandGroups` property.
* To prevent unnecessary grouping refresh, ensure that the `SfDataGrid.columns` property is set as an instance."
