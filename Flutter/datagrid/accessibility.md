---
layout: post
title: Accessibility in Flutter DataGrid | DataTable | Syncfusion
description: Learn here all about the accessibility features of the Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Accessibility in Flutter DataGrid (SfDataGrid)

The [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) widget is designed with comprehensive accessibility features to ensure all users, including those using assistive technologies, can interact with data effectively. This section covers built-in accessibility support and best practices for implementing an accessible data grid experience.

## Screen reader support

The SfDataGrid supports screen readers through the following interactions on Android and iOS platforms:

* Cell contents can be read by tapping the required cell.
* Adjacent cell content can be navigated by swiping left or right.
* Scroll the DataGrid vertically and horizontally by dragging with two fingers.

* Cell contents can be read by tapping the required cell.
* Read adjacent cell content by swiping right or left.
* Scroll the DataGrid vertically and horizontally by dragging with two fingers.

## Sufficient contrast

The [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) provides sufficient color contrast to make cell content more readable and compliant with WCAG 2.1 AA standards. Customize the appearance of DataGrid elements using the following properties:

* [`currentCellStyle`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/currentCellStyle.html) — Styling for the currently selected cell
* [`frozenPaneElevation`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/frozenPaneElevation.html) — Shadow depth for frozen panes
* [`frozenPaneLineColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/frozenPaneLineColor.html) — Border color for frozen pane dividers
* [`gridLineColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/gridLineColor.html) — Color of grid lines between cells
* [`headerColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/headerColor.html) — Background color of column headers
* [`headerHoverColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/headerHoverColor.html) — Header background color on hover
* [`selectionColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/selectionColor.html) — Background color for selected cells
* [`sortIconColor`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/sortIconColor.html) — Color of sort indicator icons

## Large fonts

Since [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) receives widgets from the user for each cell, the font size in those widgets automatically adjusts based on OS text scale settings on Android and iOS platforms. To ensure cell content remains clearly visible, row heights adjust automatically based on the [`MediaQueryData.textScaleFactor`](https://api.flutter.dev/flutter/widgets/MediaQueryData/textScaleFactor.html). 

The following example demonstrates how to apply a custom text scale factor:

{% tabs %}
{% highlight Dart %}

import 'package:flutter/material.dart';
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
            ),
          ),
        ),
        GridColumn(
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
        GridColumn(
          columnName: 'salary',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              'Salary',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridColumn(
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

The [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) supports keyboard navigation for enhanced accessibility and desktop usability. Enable keyboard navigation by configuring the [`selectionMode`](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/selectionMode.html) and [`navigationMode`](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/navigationMode.html) properties.

**Supported keyboard interactions:**
* **Arrow keys** — Navigate between cells (up, down, left, right)
* **Tab/Shift+Tab** — Move focus to the next/previous cell
* **Enter** — Select/activate the current cell
* **Ctrl+Home** — Navigate to the first cell
* **Ctrl+End** — Navigate to the last cell
* **Page Up/Page Down** — Scroll vertically by one page

For detailed keyboard behavior documentation, refer to the [keyboard behavior guide](https://help.syncfusion.com/flutter/datagrid/selection#keyboard-behavior).

The following example enables keyboard navigation:

{% tabs %}
{% highlight Dart %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_datagrid/datagrid.dart';

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SfDataGrid(
        source: _employeeDataSource,
        selectionMode: SelectionMode.single,
        navigationMode: GridNavigationMode.cell,
        columns: <GridColumn>[
          GridColumn(
            columnName: 'id',
            label: Container(
              padding: EdgeInsets.all(16.0),
              alignment: Alignment.center,
              child: Text('ID'),
            ),
          ),
          GridColumn(
            columnName: 'name',
            label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text('Name'),
            ),
          ),
          GridColumn(
            columnName: 'designation',
            label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text('Designation', overflow: TextOverflow.ellipsis),
            ),
          ),
          GridColumn(
            columnName: 'salary',
            label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text('Salary'),
            ),
          ),
        ],
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Visual density

Row heights in [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) automatically adjust based on the [`visualDensity`](https://api.flutter.dev/flutter/material/ThemeData/visualDensity.html) property. This allows you to create compact or spacious layouts that adapt to user preferences and device capabilities.

{% tabs %}
{% highlight Dart %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_datagrid/datagrid.dart';

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Theme(
        data: ThemeData(visualDensity: VisualDensity.compact),
        child: SfDataGrid(
          source: _employeeDataSource,
          columns: <GridColumn>[
            GridColumn(
              columnName: 'id',
              label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text('ID', overflow: TextOverflow.ellipsis),
              ),
            ),
            GridColumn(
              columnName: 'name',
              label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text('Name', overflow: TextOverflow.ellipsis),
              ),
            ),
            GridColumn(
              columnName: 'salary',
              label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text('Salary', overflow: TextOverflow.ellipsis),
              ),
            ),
            GridColumn(
              columnName: 'designation',
              label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text('Designation', overflow: TextOverflow.ellipsis),
              ),
            ),
          ],
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Testing accessibility

To ensure your DataGrid implementation is accessible, follow these testing practices:

* **Screen reader testing:** Use Android TalkBack or iOS VoiceOver to verify that cell content is properly announced.
* **Keyboard navigation:** Test all keyboard interactions on desktop platforms (Windows, macOS, Linux) to ensure proper navigation flow.
* **Color contrast:** Validate that all text meets WCAG 2.1 AA color contrast requirements (4.5:1 for normal text).
* **Text scaling:** Test your grid with text scale factors of 1.0x, 1.25x, 1.5x, and 2.0x to ensure content remains readable.
* **Automated testing:** Use accessibility scanning tools available in Android Studio and Xcode to detect potential accessibility issues.

## Related resources

For comprehensive information on implementing accessible DataGrid functionality, refer to the following resources:

* [DataGrid selection guide](https://help.syncfusion.com/flutter/datagrid/selection)
* [DataGrid API documentation](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/)
* [Flutter accessibility guide](https://flutter.dev/docs/development/accessibility-and-localization/accessibility)
* [WCAG 2.1 accessibility standards](https://www.w3.org/WAI/WCAG21/quickref/)

