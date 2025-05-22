---
layout: post
title: Accessibility in Flutter DataGrid | DataTable | Syncfusion
description: Learn here all about the accessibility features of the Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Accessibility in Flutter DataGrid (SfDataGrid)

## Screen reader support

The [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) can be accessed easily by screen readers in the following ways on Android and iOS platforms:

* Cell contents can be read by tapping the required cell.
* Read adjacent cell content by swiping right or left.
* Scroll the DataGrid vertically and horizontally by dragging with two fingers.

## Sufficient contrast

The [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) provides sufficient color contrast to make cell content more readable. Use the following properties to customize the appearance of the DataGrid elements:

* [currentCellStyle](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridCurrentCellStyle-class.html)
* [frozenPaneElevation](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/frozenPaneElevation.html)
* [frozenPaneLineColor](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/frozenPaneLineColor.html)
* [gridLineColor](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/gridLineColor.html)
* [headerColor](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/headerColor.html)
* [headerHoverColor](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/headerHoverColor.html)
* [selectionColor](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/selectionColor.html)
* [sortIconColor](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/sortIconColor.html)

## Large fonts

Since [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) receives widgets from the user for each cell, the font size in those widgets will automatically adjust based on OS settings in Android and iOS platforms. To ensure cell content remains clearly visible, the row heights in the DataGrid will automatically adjust based on the `MediaQueryData.textScaleFactor`.

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

@override
Widget build(BuildContext context) {
  return MediaQuery(
    data: MediaQueryData(textScaleFactor: 1.5),
    child: SfDataGrid(
      source: _employeeDataSource, 
      columns: <GridColumn>[
        GridColumn(
          columnName: 'id',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              'ID',
              overflow: TextOverflow.ellipsis,
            )
          )
        ),
        GridColumn(
          columnName: 'name',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerLeft,
            child: Text(
              'Name',
              overflow: TextOverflow.ellipsis,
            )
          )
        ),
        GridColumn(
          columnName: 'salary',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              'Salary',
              overflow: TextOverflow.ellipsis,
            )
          )
        ),
        GridColumn(
          columnName: 'designation',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerLeft,
            child: Text(
              'Designation',
              overflow: TextOverflow.ellipsis,
            )
          )
        )
      ]
    )
  );
}

{% endhighlight %}
{% endtabs %}

## Keyboard navigation

The [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) provides keyboard navigation support when the [selectionMode](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/selectionMode.html) and [navigationMode](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/navigationMode.html) are enabled. Refer to this [link](https://help.syncfusion.com/flutter/datagrid/selection#keyboard-behavior) for supported keys and their purpose.

## Visual density

The row heights in [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) will automatically adjust based on the [visualDensity](https://api.flutter.dev/flutter/material/ThemeData/visualDensity.html) property.

{% tabs %}
{% highlight Dart %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_datagrid/datagrid.dart';

@override
Widget build(BuildContext context) {
  return Theme(
    data: ThemeData(visualDensity: VisualDensity.compact),
    child: SfDataGrid(
      source: _employeeDataSource, 
      columns: <GridColumn>[
        GridColumn(
          columnName: 'id',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              'ID',
              overflow: TextOverflow.ellipsis,
            )
          )
        ),
        GridColumn(
          columnName: 'name',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerLeft,
            child: Text(
              'Name',
              overflow: TextOverflow.ellipsis,
            )
          )
        ),
        GridColumn(
          columnName: 'salary',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              'Salary',
              overflow: TextOverflow.ellipsis,
            )
          )
        ),
        GridColumn(
          columnName: 'designation',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerLeft,
            child: Text(
              'Designation',
              overflow: TextOverflow.ellipsis,
            )
          )
        )
      ]
    )
  );
}

{% endhighlight %}
{% endtabs %}

