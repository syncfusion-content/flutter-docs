---
layout: post
title: Right to Left in Flutter Event Calendar widget | Syncfusion
description: Learn here all about Right to Left feature of Syncfusion Flutter Event Calendar (SfCalendar) widget and more.
platform: flutter
control: SfCalendar
documentation: ug
---

# Right to Left (RTL) in Flutter Event Calendar (SfCalendar)
The event calendar supports right-to-left rendering and all the calendar elements rendering direction will be changed.

## RTL rendering ways
Right to Left rendering can be switched in the following ways:

### Wrapping the SfCalendar with Directionality widget
[SfCalendar](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar-class.html) supports changing the layout direction of the widget in the right-to-left direction by using the `Directionality` widget and set the `textDirection` property as [TextDirection.rtl](https://api.flutter.dev/flutter/dart-ui/TextDirection.html).

{% tabs %}
{% highlight dart hl_lines="17 18" %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_calendar/calendar.dart';

void main() {
  runApp(const CalendarApp());
}

class CalendarApp extends StatelessWidget {
  const CalendarApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: const Text('Right to Left'),
        ),
        body: Directionality(
          textDirection: TextDirection.rtl,
          child: SfCalendar(
            view: CalendarView.month,
          ),
        ),
      ),
    );
  }
}
   
{% endhighlight %}
{% endtabs %}

### Changing the locale to RTL languages
To change the event calendar rendering direction from right to left, change the locale to any of the RTL languages such as Arabic, Persian, Hebrew, Pashto, and Urdu.

{% tabs %}
{% highlight dart hl_lines="14 15 16 17 18 19 20 21 22 23" %}

import 'package:flutter/material.dart';
import 'package:flutter_localizations/flutter_localizations.dart';
import 'package:syncfusion_flutter_calendar/calendar.dart';

void main() {
  runApp(const CalendarApp());
}

class CalendarApp extends StatelessWidget {
  const CalendarApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      localizationsDelegates: const [
        GlobalMaterialLocalizations.delegate,
        GlobalWidgetsLocalizations.delegate,
      ],
      supportedLocales: const <Locale>[
        Locale('en'),
        Locale('ar'),
        // ... other locales the app supports
      ],
      locale: const Locale('ar'),
      home: Scaffold(
        body: SfCalendar(
            //...
            ),
      ),
    );
  }
}

	
{% endhighlight %}
{% endtabs %}


## RTL supported calendar element
Right to Left rendering is supported for all the elements in the [SfCalendar](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar-class.html).


{% tabs %}
{% highlight dart hl_lines="17 18" %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_calendar/calendar.dart';

void main() {
  runApp(const CalendarApp());
}

class CalendarApp extends StatelessWidget {
  const CalendarApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: const Text('Right to Left'),
        ),
        body: Directionality(
          textDirection: TextDirection.rtl,
          child: SfCalendar(
            view: CalendarView.month,
            allowedViews: const [
              CalendarView.day,
              CalendarView.week,
              CalendarView.workWeek,
              CalendarView.month,
              CalendarView.schedule,
              CalendarView.timelineDay,
              CalendarView.timelineWeek,
              CalendarView.timelineWorkWeek,
              CalendarView.timelineMonth
            ],
          ),
        ),
      ),
    );
  }
}

   
{% endhighlight %}
{% endtabs %}
