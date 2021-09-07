---
layout: post
title: Accessibility in Flutter DataGrid | DataTable | Syncfusion
description: Learn here all about the accessibility of the Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Accessibility in Flutter DataGrid (SfDataGrid)

## Screen reader support

The `SfDataGrid` can be accessed easily by the screen readers in the following ways in Android and iOS platforms:

* Cell contents can be read by tapping the required cell.
* Read the adjacent cell's content by swiping right or left.
* Scroll the datagrid vertically and horizontally by dragging two fingers.

## Sufficient contrast

The `SfDataGrid` provides the sufficient color contrast to make the cell content easier. Use the following properties to customize the appearance of the datagrid elements.

* [currentCellStyle](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/currentCellStyle.html)
* [frozenPaneElevation](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/frozenPaneElevation.html)
* [frozenPaneLineColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/frozenPaneLineColor.html)
* [gridLineColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/gridLineColor.html)
* [headerColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/headerColor.html)
* [headerHoverColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/headerHoverColor.html)
* [selectionColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/selectionColor.html)
* [sortIconColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/sortIconColor.html)

## Large fonts

As `SfDataGrid` gets the widget from user end for each cell, the font size in that widget will be automatically changed based on OS settings in Android and iOS platforms. To clearly view the cell content, the row heights in the datagrid will be automatically adjusted based on `MediaQueryData.textScaleFactor`.

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

@override
Widget build(BuildContext context) {
  return MediaQuery(
      data: MediaQueryData(textScaleFactor: 1.5),
      child: SfDataGrid(source: _employeeDataSource, columns: <GridColumn>[
        GridColumn(
            columnName: 'id',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'ID',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'name',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Name',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'salary',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'Salary',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'designation',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Designation',
                  overflow: TextOverflow.ellipsis,
                )))
      ]));
}

{% endhighlight %}
{% endtabs %}

## Keyboard navigation

The `SfDataGrid` provides the keyboard navigation support when the [selectionMode](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/selectionMode.html) and [navigationMode](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/navigationMode.html) are enabled. Refer this [link](https://help.syncfusion.com/flutter/datagrid/selection#keyboard-behavior) for supported keys and their purpose.

## Visual density

The row heights in `SfDataGrid` will be automatically adjusted based on the [visualDensity](https://api.flutter.dev/flutter/material/ThemeData/visualDensity.html).

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

@override
Widget build(BuildContext context) {
  return Theme(
      data: ThemeData(visualDensity: VisualDensity.compact),
      child: SfDataGrid(source: _employeeDataSource, columns: <GridColumn>[
        GridColumn(
            columnName: 'id',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'ID',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'name',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Name',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'salary',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'Salary',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'designation',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Designation',
                  overflow: TextOverflow.ellipsis,
                )))
      ]));
}

{% endhighlight %}
{% endtabs %}

