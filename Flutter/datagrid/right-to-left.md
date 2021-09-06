---
layout: post
title: RTL support in Flutter DataGrid | DataTable | Syncfusion 
description: Learn here about the right to left (RTL) support in Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Right to Left (RTL) in Flutter DataGrid (SfDataGrid)

SfDataGrid supports right-to-left rendering. The columns will be rendered based on LTR and RTL direction.

## RTL rendering ways

Right to left rendering can be switched in the following ways:

### Wrapping the SfDataGrid with Directionality widget

To change the rendering direction from right to left, wrap the [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) widget inside the [Directionality](https://api.flutter.dev/flutter/widgets/Directionality-class.html) widget and set the [textDirection](https://api.flutter.dev/flutter/widgets/Directionality/textDirection.html) property as [TextDirection.rtl](https://api.flutter.dev/flutter/dart-ui/TextDirection-class.html).

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

@override
Widget build(BuildContext context) {
  return Directionality(
      textDirection: TextDirection.rtl,
      child: SfDataGrid(
          source: _employeeDataSource,
          columnWidthMode: ColumnWidthMode.fill,
          columns: <GridColumn>[
            GridColumn(
                columnName: 'id',
                label: Container(
                    padding: EdgeInsets.all(16.0),
                    alignment: Alignment.center,
                    child: Text(
                      'ID',
                    ))),
            GridColumn(
                columnName: 'name',
                label: Container(
                    padding: EdgeInsets.all(8.0),
                    alignment: Alignment.center,
                    child: Text('Name'))),
            GridColumn(
                columnName: 'designation',
                label: Container(
                    padding: EdgeInsets.all(8.0),
                    alignment: Alignment.center,
                    child: Text(
                      'Designation',
                      overflow: TextOverflow.ellipsis,
                    ))),
            GridColumn(
                columnName: 'salary',
                label: Container(
                    padding: EdgeInsets.all(8.0),
                    alignment: Alignment.center,
                    child: Text('Salary'))),
          ]));
}

{% endhighlight %}
{% endtabs %}

### Changing the locale to RTL languages

To change the datagrid rendering direction from right to left, change the [locale](https://api.flutter.dev/flutter/material/MaterialApp/locale.html) to any of the RTL languages such as Arabic, Persian, Hebrew, Pashto, and Urdu.

To use `flutter_localizations`, add the package as dependency to `pubspec.yaml` file.

{% highlight dart %}

dependencies:
flutter_localizations:
  sdk: flutter

{% endhighlight %}

Next, import the `flutter_localizations` library and specify [localizationsDelegates](https://api.flutter.dev/flutter/widgets/LocalizationsDelegate-class.html) and `supportedLocales` for `MaterialApp`.

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_datagrid/datagrid.dart';
import 'package:flutter_localizations/flutter_localizations.dart';

@override
Widget build(BuildContext context) {
  return MaterialApp(
      localizationsDelegates: [
        GlobalMaterialLocalizations.delegate,
        GlobalWidgetsLocalizations.delegate,
      ],
      supportedLocales: <Locale>[
        Locale('en'),
        Locale('ar'),
        // ... other locales the app supports
      ],
      locale: Locale('ar'),
      home: SfDataGrid(
          source: _employeeDataSource,
          columnWidthMode: ColumnWidthMode.fill,
          columns: <GridColumn>[
            GridColumn(
                columnName: 'id',
                label: Container(
                    padding: EdgeInsets.all(16.0),
                    alignment: Alignment.center,
                    child: Text(
                      'ID',
                    ))),
            GridColumn(
                columnName: 'name',
                label: Container(
                    padding: EdgeInsets.all(8.0),
                    alignment: Alignment.center,
                    child: Text('Name'))),
            GridColumn(
                columnName: 'designation',
                label: Container(
                    padding: EdgeInsets.all(8.0),
                    alignment: Alignment.center,
                    child: Text(
                      'Designation',
                      overflow: TextOverflow.ellipsis,
                    ))),
            GridColumn(
                columnName: 'salary',
                label: Container(
                    padding: EdgeInsets.all(8.0),
                    alignment: Alignment.center,
                    child: Text('Salary'))),
          ]));
}

{% endhighlight %}
{% endtabs %}