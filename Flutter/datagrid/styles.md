---
layout: post
title: Styling feature in Syncfusion Flutter DataGrid | DataTable
description: Learn about styles and how to customize the appearance of DataGrid and its elements in Syncfusion Flutter DataGrid.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Styling in Flutter DataGrid

The DataGrid supports to change the appearance of the grid by using the [SfDataGridThemeData](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData-class.html) in [SfDataGridTheme](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridTheme-class.html). The DataGrid should be wrapped inside the `SfDataGridTheme`.

## Styling grid lines

Color and thickness of the grid lines can be changed by using the [SfDataGridThemeData.gridLineColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/gridLineColor.html) and [SfDataGridThemeData.gridLineStrokeWidth](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/gridLineStrokeWidth.html) properties.

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return Scaffold(
     body: SfDataGridTheme(
      data: SfDataGridThemeData(
          gridLineColor: Colors.amber, gridLineStrokeWidth: 3.0),
        child: SfDataGrid(
        source: _employeeDataSource,
        columns: <GridColumn>[
          GridTextColumn(columnName: 'id', label: Text('ID')),
          GridTextColumn(columnName: 'name', label: Text('Name')),
          GridTextColumn(columnName: 'designation', label: Text('Designation')),
          GridTextColumn(columnName: 'salary', label: Text('Salary')),
        ],
      ),
    ),
  );
}
    
{% endhighlight %}
{% endtabs %}

![flutter datagrid shows customizing the grid lines](images/styles/flutter-datagrid-gridline-customization.png)

## Show vertical and horizontal grid lines

To show the vertical and horizontal gridlines, use the following properties. 

* [SfDataGrid.gridLinesVisibility](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/gridLinesVisibility.html): To set the border lines for the cells other than header and stacked header cells. 
* [SfDataGrid.headerGridLinesVisibility](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/headerGridLinesVisibility.html): To set the border lines only for header and stacked header cells.

The following are the list of options available to customize gridlines,

* Vertical
* Horizontal
* Both
* None

The following code describes how to show vertical and horizontal grid lines for the `SfDataGrid`.

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDataGrid(
        source: _employeeDataSource,
        columns: <GridColumn>[
          GridTextColumn(columnName: 'id', label: Text('ID')),
          GridTextColumn(columnName: 'name', label: Text('Name')),
          GridTextColumn(columnName: 'designation', label: Text('Designation')),
          GridTextColumn(columnName: 'salary', label: Text('Salary')),
        ],
        gridLinesVisibility: GridLinesVisibility.both,
        headerGridLinesVisibility: GridLinesVisibility.both),
  );
}
    
{% endhighlight %}
{% endtabs %}

![flutter datagrid shows both grid lines](images/styles/flutter-datagrid-gridlines.png)