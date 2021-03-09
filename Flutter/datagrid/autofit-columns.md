---
layout: post
title: AutoFit Columns feature in Syncfusion Flutter DataGrid | DataTable
description: Learn how to autofit the columns, set the column width and column width customization in Syncfusion Flutter DataGrid.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Autofit Columns in Flutter DataGrid

[SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) allows to set the column widths based on certain logic using [SfDataGrid.columnWidthMode](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/columnWidthMode.html) or [GridColumn.columnWidthMode](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridColumn/columnWidthMode.html) property. Below are the list of predefined column sizing options available.

| Mode                      | Description                                         |
|---------------------------|-----------------------------------------------------|
| ColumnWidthMode.lastColumnFill | Applies default Column width to all the columns except last column which is visible and the remaining width from total width of SfDataGrid is set to last column. |
| ColumnWidthMode.fill      | Divides the total width equally for columns.         |
| ColumnWidthMode.none      | No sizing. Default column width or defined width set to column. |

> **NOTE**  
    [ColumnWidthMode](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/ColumnWidthMode-class.html) will not work when the column width defined explicitly. `columnWidthMode` calculates column width based on miniumWidth and maximumWidth properties.

The following example shows how to set the width equally for column based on the view port size.

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDataGrid(
      source: _employeeDataSource,
      columnWidthMode: ColumnWidthMode.fill,
      columns: [
        GridTextColumn(columnName: 'id', label: Text('ID')),
        GridTextColumn(columnName: 'name', label: Text('Name')),
        GridTextColumn(columnName: 'designation', label: Text('Designation')),
        GridTextColumn(columnName: 'city', label: Text('City')),
        GridTextColumn(columnName: 'salary', label: Text('Salary')),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

> **NOTE**  
    The `GridColumn.columnWidthMode` takes higher priority than the `SfDataGrid.columnWidthMode`.

![columns filled based on view port size in flutter datagrid](images/autofit-columns/flutter-datagrid-fill-columns.png)

## Fill remaining width for any column

While setting `SfDataGrid.columnWidthMode` as `lastColumnFill` remaining width is applied to last column. The remaining width to specific column can be applied by setting `GridColumn.columnWidthMode` property.

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDataGrid(
      source: _employeeDataSource,
      columnWidthMode: ColumnWidthMode.lastColumnFill,
      columns: [
        GridTextColumn(columnName: 'id', label: Text('ID')),
        GridTextColumn(columnName: 'name', label: Text('Name')),
        GridTextColumn(columnName: 'salary', label: Text('Salary')),
        GridTextColumn(columnName: 'designation', label: Text('Designation')),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![The last column is filled in view in flutter datagrid](images/autofit-columns/flutter-datagrid-fill-lastcolumn.png)

The below example shows Name column is set as `lastColumnFill` mode.

{% tabs %}
{% highlight Dart %} 
 
@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDataGrid(
      source: _employeeDataSource,
      columnWidthMode: ColumnWidthMode.auto,
      columns: [
        GridTextColumn(columnName: 'id', label: Text('ID')),
        GridTextColumn(columnName: 'name', label: Text('Name'), 
                 columnWidthMode: ColumnWidthMode.lastColumnFill),
        GridTextColumn(columnName: 'designation', label: Text('Designation')),
        GridTextColumn(columnName: 'salary', label: Text('Salary')),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Name column is filled with remaining available space in flutter datagrid](images/autofit-columns/flutter-datagrid-fill-anycolumn.png)

## Recalculating column widths when datasource is changed

By default, column widths are calculated based on the `columnWidthMode` property on initial loading of datagrid. When the datasource is changed for same datagrid at run time, datagrid does not recalculate the column widths. To recalculate the column widths at run time when datasource is changed or data is updated, you can override the [shouldRecalculateColumnWidths](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/shouldRecalculateColumnWidths.html) method and return `true`. 
 
Returning true may impact performance as the column widths are recalculated again (whenever the notifyListeners is called). If you are aware that column widths are going to be same whenever underlying data changes, return 'false' from this method.

{% tabs %}
{% highlight Dart %} 

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource(List<Employee> employees) {
    dataGridRows = employees.map<DataGridRow>((employee) {
      return DataGridRow(cells: [
        DataGridCell<int>(value: employee.id, columnName: 'id'),
        DataGridCell<String>(value: employee.name, columnName: 'name'),
        DataGridCell<String>(
            value: employee.designation, columnName: 'designation'),
        DataGridCell<double>(value: employee.salary, columnName: 'salary'),
      ]);
    }).toList();
  }

  List<DataGridRow> dataGridRows;

  @override
  List<DataGridRow> get rows => dataGridRows;

  @override
  DataGridRowAdapter buildRow(DataGridRow row) {
    return DataGridRowAdapter(
        cells: row.getCells().map<Widget>((e) {
      return Container(
        child: Text(e.value.toString()),
      );
    }).toList());
  }

  @override
  bool shouldRecalculateColumnWidths() {
    return true;
  }
}

{% endhighlight %}
{% endtabs %}