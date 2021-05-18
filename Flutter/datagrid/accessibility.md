---
layout: post
title: Accessibility in Flutter DataGrid | DataTable | Syncfusion
description: Learn here all about the accessibility feature of the Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Accessibility in Flutter DataGrid (SfDataGrid)

## Screen reader support

The `SfDataGrid` can easily be accessed by screen readers. Please find the following ways to navigate cells in the datagrid by using Talk back.

* Swipe right or left move between cells.
* Tap to read cell content.
* Drag two fingers to scroll vertically and horizontally.

## Sufficient contrast

The `SfDataGrid` [theming](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData-class.html) support offers a consistent and standardized look, as well as the ability to set the colors for all the UI elements.

The following APIs allow you to customize the colors of the following elements.

* [currentCellStyle](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/currentCellStyle.html)
* [frozenPaneElevation](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/frozenPaneElevation.html)
* [frozenPaneLineColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/frozenPaneLineColor.html)
* [gridLineColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/gridLineColor.html)
* [headerColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/headerColor.html)
* [headerHoverColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/headerHoverColor.html)
* [selectionColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/selectionColor.html)
* [sortIconColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/sortIconColor.html)

## Large fonts

The `SfDataGrid` font size can be adjusted automatically based on device settings and the font size scaled based on the `MediaQueryData.textScaleFactor`.

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

@override
Widget build(BuildContext context) {
  return MediaQuery(
    data: MediaQueryData(textScaleFactor: 1.5),
    child: SfDataGrid(
      source: employeeDataSource,
      columns: <GridColumn>[
        GridTextColumn(
          columnName: 'id',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              'ID',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridTextColumn(
          columnName: 'name',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerLeft,
            child: Text(
              'Name',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridTextColumn(
          columnName: 'salary',
          visible: false,
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              'Salary',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridTextColumn(
          columnName: 'designation',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerLeft,
            child: Text(
              'Designation',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Keyboard navigation

The `SfDataGrid` provides the keyboard navigation support when the [selectionMode](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/selectionMode.html) or [navigationMode](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/navigationMode.html) is enabled.

* [Keyboard navigation keys](selection.md#Keyboard-behavior)

## Visual density

The `SfDataGrid` provides visual density support. The row heights will be changed based on the visual density properties.

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

@override
Widget build(BuildContext context) {
  return Theme(
    data: ThemeData(visualDensity: VisualDensity.compact),
    child: SfDataGrid(
      source: employeeDataSource,
      columns: <GridColumn>[
        GridTextColumn(
          columnName: 'id',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              'ID',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridTextColumn(
          columnName: 'name',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerLeft,
            child: Text(
              'Name',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridTextColumn(
          columnName: 'salary',
          visible: false,
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              'Salary',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridTextColumn(
          columnName: 'designation',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerLeft,
            child: Text(
              'Designation',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

