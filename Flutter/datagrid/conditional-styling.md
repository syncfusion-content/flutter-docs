---
layout: post
title: Conditional Styling feature in Syncfusion Flutter DataGrid | DataTable
description: Learn how to customize the appearance of rows and cells by using conditional styling feature in Syncfusion Flutter DataGrid.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Conditional Styling in Flutter DataGrid

The [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) allows to customize the style of the individual cells and rows based on the requirements. It can be customized in the following ways:

* Using [onQueryCellStyle](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/onQueryCellStyle.html) Callback
* Using [onQueryRowStyle](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/onQueryRowStyle.html) Callback

All the style classes such as [DataGridCellStyle](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/DataGridCellStyle-class.html), [DataGridHeaderCellStyle](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/DataGridHeaderCellStyle-class.html) related to `SfDataGrid` are available in the [syncfusion_flutter_core](https://pub.dev/packages/syncfusion_flutter_core) package. To access those classes, import the below file in your application,

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_core/theme.dart';

{% endhighlight %}
{% endtabs %}

## Cells

### Styling based on content

The appearance of the cells in `SfDataGrid` can be customized conditionally based on the content by handling the `SfDataGrid.onQueryCellStyle` callback. 
Callback requires [QueryCellStyleArgs](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/QueryCellStyleArgs-class.html) as parameter which provides all the required options to know about the cell.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';
import 'package:syncfusion_flutter_core/theme.dart';

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDataGrid(
        source: _employeeDataSource,
        columns: <GridColumn>[
          GridNumericColumn(mappingName: 'id', headerText: 'Order ID'),
          GridTextColumn(mappingName: 'name', headerText: 'Name'),
          GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
          GridNumericColumn(mappingName: 'salary', headerText: 'Salary')
        ],
        onQueryCellStyle: (QueryCellStyleArgs args) {
          if (args.column.mappingName == 'designation') {
            if (args.cellValue == 'Developer') {
              return DataGridCellStyle(
                  textStyle: TextStyle(fontStyle: FontStyle.italic),
                  backgroundColor: Colors.tealAccent);
            } else if (args.cellValue == 'Manager') {
              return DataGridCellStyle(
                  textStyle: TextStyle(fontStyle: FontStyle.italic),
                  backgroundColor: Colors.blue[200]);
            }
          }
          return null;
        }),
  );
}
    
{% endhighlight %}
{% endtabs %}

![flutter datagrid shows conditional formatting in cells](images/conditional-styling/flutter-datagrid-cells-styling-based-on-content.png)

### Styling alternate cells

The appearance of the alternating cells in a column can be customized conditionally by using the `SfDataGrid.onQueryCellStyle` callback.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';
import 'package:syncfusion_flutter_core/theme.dart';

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDataGrid(
        source: _employeeDataSource,
        columns: <GridColumn>[
          GridNumericColumn(mappingName: 'id', headerText: 'Order ID'),
          GridTextColumn(mappingName: 'name', headerText: 'Name'),
          GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
          GridNumericColumn(mappingName: 'salary', headerText: 'Salary')
        ],
        onQueryCellStyle: (QueryCellStyleArgs args) {
          if (args.column.mappingName == 'id') {
            if (args.rowIndex % 2 != 0) {
              return DataGridCellStyle(
                  textStyle: TextStyle(fontStyle: FontStyle.italic),
                  backgroundColor: Colors.blueAccent);
            }
          }
          return null;
        }),
  );
}
    
{% endhighlight %}
{% endtabs %}

![flutter datagrid shows alternate cells styling](images/conditional-styling/flutter-datagrid-alternate-cells-styling.png)

## Rows

### Styling based on content

The appearance of the rows in `SfDataGrid` can be customized conditionally based on the content by handling the `SfDataGrid.onQueryRowStyle` callback.
Callback requires [QueryRowStyleArgs](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/QueryRowStyleArgs-class.html) as parameter which provides all the required options to know about the cell.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';
import 'package:syncfusion_flutter_core/theme.dart';
      
@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDataGrid(
        source: _employeeDataSource,
        columns: <GridColumn>[
          GridNumericColumn(mappingName: 'id', headerText: 'Order ID'),
          GridTextColumn(mappingName: 'name', headerText: 'Name'),
          GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
          GridNumericColumn(mappingName: 'salary', headerText: 'Salary')
        ],
        onQueryRowStyle: (QueryRowStyleArgs args) {
          Employee employee = _employeeCollection[args.rowIndex];
          if (employee.salary >= 10000 && employee.salary < 15000) {
            return DataGridCellStyle(
                textStyle: TextStyle(color: Colors.white),
                backgroundColor: Colors.blue[300]);
          } else if (employee.salary <= 15000) {
            return DataGridCellStyle(
                textStyle: TextStyle(color: Colors.white),
                backgroundColor: Colors.orange[300]);
          }
          return null;
        }),
  );
}
    
{% endhighlight %}
{% endtabs %}

![flutter datagrid shows styling a row based on content](images/conditional-styling/flutter-datagrid-rows-styling-based-on-content.png)

### Styling alternate rows

The appearance of the alternating rows in `SfDataGrid` can be customized by using the `SfDataGrid.onQueryRowStyle` callback.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';
import 'package:syncfusion_flutter_core/theme.dart';

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDataGrid(
        source: _employeeDataSource,
        columns: <GridColumn>[
          GridNumericColumn(mappingName: 'id', headerText: 'Order ID'),
          GridTextColumn(mappingName: 'name', headerText: 'Name'),
          GridNumericColumn(mappingName: 'salary', headerText: 'Salary'),
          GridTextColumn(mappingName: 'designation', headerText: 'Designation')
        ],
        onQueryRowStyle: (QueryRowStyleArgs args) {
          if (args.rowIndex % 2 != 0) {
            return DataGridCellStyle(backgroundColor: Colors.lightGreen[300]);
          }
          return null;
        }),
  );
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows styling alternate rows](images/conditional-styling/flutter-datagrid-alternate-rows-styling.png)