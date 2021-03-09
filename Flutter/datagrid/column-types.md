---
layout: post
title: Column types in Syncfusion Flutter DataGrid | DataTable
description: Learn how to use and customize the different types of column and its properties in Syncfusion Flutter DataGrid.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Column Types in Flutter DataGrid

[SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) provides support for load any type of widget in each column.

The following table describes the types of columns and its usage:

| Column Type           | Renderer                        | Description                            |
|-----------------------|---------------------------------|----------------------------------------|
| GridTextColumn        | GridCellTextFieldRenderer       | Use to display the String data         |

## GridColumn

GridColumn is a class that provides base functionalities for all the column types in `SfDataGrid`.

### Mapping column to a property

Column can be bound to a property in data object using [GridColumn.columnName](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridColumn/mappingName.html) property. [label](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridColumn/headerText.html) is used to display the required widget in a column header. 

{% tabs %}
{% highlight Dart %} 
 
@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDataGrid(
      source: _employeeDataSource,
      columns: [
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

### Hiding a column

[GridColumn.visible](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridColumn/visible.html) property can be used to set a column as hidden. The default value of the `visible` property is true.

>**NOTE**  
   Set the `visible` property to `false` instead of setting column width as `0` to hide a column.

{% tabs %}
{% highlight Dart %} 
 
@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDataGrid(
      source: _employeeDataSource,
      columns: [
        GridTextColumn(columnName: 'id', label: Text('ID')),
        GridTextColumn(columnName: 'name', label: Text('Name')),
        GridTextColumn(columnName: 'designation', label: Text('Designation')),
        GridTextColumn(columnName: 'salary', label: Text('Salary'), visible: false),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

### Set manual width for column

`SfDataGrid` allows you to customize the width of each [GridColumn](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridColumn-class.html) in the [SfDataGrid.Columns](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/columns.html) collection. To customize column width, use the [GridColumn.width](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridColumn/width.html) property. By default, this property will not be assigned any value. The GridColumn renders in view based on the value of the [defaultColumnWidth](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/defaultColumnWidth.html) property.

>**NOTE**  
   Set the `visible` property to `false` instead of setting column width as `0` to hide a column.

{% tabs %}
{% highlight Dart %} 
 
@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDataGrid(
      source: _employeeDataSource,
      columns: [
        GridTextColumn(columnName: 'id', label: Text('ID')),
        GridTextColumn(columnName: 'name', label: Text('Name'), width: 100.0)),
        GridTextColumn(columnName: 'designation', label: Text('Designation')),
        GridTextColumn(columnName: 'salary', label: Text('Salary'), visible: false),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## GridTextColumn

[GridTextColumn](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridTextColumn-class.html) inherits all the properties of GridColumn. 

{% tabs %}
{% highlight Dart %} 
 
@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDataGrid(
      source: _employeeDataSource,
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