---
layout: post
title: Localization in Flutter Date Range Picker | Syncfusion
description: Step-by-step guide to configure localization in Syncfusion Flutter Date Range Picker—add flutter_localizations, set localizationsDelegates, and define locales.
platform: flutter
control: SfDateRangePicker
documentation: ug
---

# Flutter Date Range Picker Localization (SfDateRangePicker)

By default, the [SfDateRangePicker](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker-class.html) widget supports US English localizations. You can change to other languages by specifying the [MaterialApp](https://api.flutter.dev/flutter/material/MaterialApp-class.html) properties and adding the `flutter_localizations` package to your application.

To use `flutter_localizations`, add the package as a dependency to your `pubspec.yaml` file.

{% tabs %}
{% highlight yaml %}

dependencies:
  flutter_localizations:
    sdk: flutter

{% endhighlight %}
{% endtabs %}

Next, import the `flutter_localizations` library and specify [localizationsDelegates](https://api.flutter.dev/flutter/material/MaterialApp/localizationsDelegates.html) and [supportedLocales](https://api.flutter.dev/flutter/material/MaterialApp/supportedLocales.html) for [MaterialApp](https://api.flutter.dev/flutter/material/MaterialApp-class.html).

{% tabs %}
{% highlight dart hl_lines="16 17 18 19 20 21 22" %}

import 'package:flutter/material.dart';
import 'package:flutter_localizations/flutter_localizations.dart';
import 'package:syncfusion_flutter_datepicker/datepicker.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      localizationsDelegates: const [
        GlobalMaterialLocalizations.delegate,
        GlobalWidgetsLocalizations.delegate,
      ],
      supportedLocales: const [
        Locale('zh'),
        Locale('ar'),
        Locale('ja'),
      ],
      locale: const Locale('zh'),
      title: 'DateRangePicker Localization',
      home: Scaffold(
        appBar: AppBar(title: const Text('Calendar')),
        body: SfDateRangePicker(view: DateRangePickerView.month),
      ),
    );
  }
}

{% endhighlight %}
{% endtabs %}

![Localization Date Range Picker](images/localization/localization.png)

## See also

* [Globalization in Flutter Date Range Picker](https://help.syncfusion.com/flutter/globalization)
* [Right to left in Flutter Date Range Picker](https://help.syncfusion.com/flutter/daterangepicker/right-to-left)
