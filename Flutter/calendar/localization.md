---
layout: post
title: Localization of Syncfusion Flutter Calendar | Calendar
description: Describes how to Localize the contents and custom texts of calendar (SfCalendar) control in Flutter
platform: flutter
control: SfCalendar
documentation: ug
---

# Localization in Flutter Calendar (SfCalendar)

The `SfCalendar control is available with complete localization support. Localization can be specified by setting locale in Material app.

## Change the default control language
Based on the locale specified in the material app, control such as date, time, and days are localized accordingly.

### Add dependency

{% highlight dart %}

dependencies:
flutter_localizations:
sdk: flutter
syncfusion_localizations:^18.1.0.36

{% endhighlight %}

### Import package
Import the following package in your Dart code.

{% highlight dart %}

import 'package:flutter_localizations/flutter_localizations.dart';
import 'package:syncfusion_localizations/syncfusion_localizations.dart';

{% endhighlight %}

Then, declare the SfGlobalLocalizations.delegate in the localizationsDelegates and specify the supported locales and current locale as depicted below. By default, the schedule control is available with en locale, which is English.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
return MaterialApp(
localizationsDelegates: [
GlobalMaterialLocalizations.delegate,
GlobalWidgetsLocalizations.delegate,
SfGlobalLocalizations.delegate
],
supportedLocales: [
const Locale('zh'),
const Locale('ar'),
const Locale('ja'),
],
locale: const Locale('zh'),
title: 'Calendar Localization',
home: Scaffold(
appBar: AppBar(
title: Text('Calendar'),
),
body: SfCalendar(
view: CalendarView.month,
       ),
    ),
)

{% endhighlight %}
{% endtabs %}




