---
layout: post
title: RTL support in Flutter DataGrid | DataTable | Syncfusion 
description: Learn here about the right to left (RTL) support in Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Right to Left (RTL) in Flutter DataGrid (SfDataGrid)

SfDataGrid supports right-to-left (RTL) rendering. When RTL is enabled, columns will be rendered in reverse order, scrollbars will appear on the left side, and text alignment will be mirrored accordingly.

> **Note:** This feature requires Flutter 2.0+ and syncfusion_flutter_datagrid 19.1.0 or later.

## RTL rendering ways

Right-to-left rendering can be switched in the following ways:

### Wrapping the SfDataGrid with the Directionality widget

Wrap the [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) widget inside the [Directionality](https://api.flutter.dev/flutter/widgets/Directionality-class.html) widget and set the [textDirection](https://api.flutter.dev/flutter/widgets/Directionality/textDirection.html) property to [TextDirection.rtl](https://api.flutter.dev/flutter/dart-ui/TextDirection-class.html) to enable RTL rendering.

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

Change the [locale](https://api.flutter.dev/flutter/material/MaterialApp/locale.html) property of [MaterialApp](https://api.flutter.dev/flutter/material/MaterialApp-class.html) to an RTL language such as Arabic (ar), Persian (fa), Hebrew (he), Pashto (ps), or Urdu (ur) to enable RTL rendering.

> **Note:** The `flutter_localizations` package is required. Add it to your `pubspec.yaml` file:
> 
> ```dart
> dependencies:
>   flutter_localizations:
>     sdk: flutter
> ```
> 
> Then run `flutter pub get` to download the package.

Import the `flutter_localizations` library and configure [localizationsDelegates](https://api.flutter.dev/flutter/widgets/LocalizationsDelegate-class.html) and `supportedLocales` in your `MaterialApp`.

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_datagrid/datagrid.dart';
import 'package:flutter_localizations/flutter_localizations.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

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
          Locale('fa'),
          Locale('he'),
          Locale('ps'),
          Locale('ur'),
        ],
        locale: Locale('ar'),
        home: Scaffold(
          appBar: AppBar(
            title: Text('RTL DataGrid'),
          ),
          body: SfDataGrid(
              source: _employeeDataSource,
              columnWidthMode: ColumnWidthMode.fill,
              columns: <GridColumn>[
                GridColumn(
                    columnName: 'id',
                    label: Container(
                        padding: EdgeInsets.all(16.0),
                        alignment: Alignment.center,
                        child: Text('ID'))),
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
              ]),
        ));
  }
}

{% endhighlight %}
{% endtabs %}