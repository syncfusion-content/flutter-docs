---
layout: post
title: Localization in Flutter Event Calendar widget | Syncfusion
description: Learn here all about Localization feature of Syncfusion Flutter Event Calendar (SfCalendar) widget and more.
platform: flutter
control: SfCalendar
documentation: ug
---

# Localization in Flutter Event Calendar (SfCalendar)

By default, the calendar widget supports US English localizations. You can change the other languages by specifying the `MaterialApp` properties and adding the `flutter_localizations` package to your application.

To use `flutter_localizations`, add the package as dependency to `pubspec.yaml` file.

{% highlight dart %}

dependencies:
flutter_localizations:
  sdk: flutter

{% endhighlight %}

Next, import the `flutter_localizations` library and specify `localizationsDelegates` and `supportedLocales` for `MaterialApp`.

{% tabs %}
{% highlight dart hl_lines="1 6 7 8 9 10 11 12 13 14 15" %}

import 'package:flutter_localizations/flutter_localizations.dart';

@override
Widget build(BuildContext context) {
return MaterialApp(
        localizationsDelegates: [
            GlobalMaterialLocalizations.delegate,
            GlobalWidgetsLocalizations.delegate,
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
   );
}

{% endhighlight %}
{% endtabs %}

## Localize the custom text in Calendar
Calendar custom text can be localized using the `syncfusion_localizations` package and specifying `localizationsDelegates` in `MaterialApp`.

To use `syncfusion_localizations`, add the package as dependency to `pubspec.yaml` file.

{% highlight dart %}

dependencies:
syncfusion_localizations: ^18.1.36

{% endhighlight %}

Next, import the `syncfusion_localizations` library.

{% highlight dart %}

import 'package:syncfusion_localizations/syncfusion_localizations.dart';

{% endhighlight %}

Then, declare the `SfGlobalLocalizations.delegate` in the `localizationsDelegates`, which is used to localize the custom string (No events, No selected date) using in calendar and specify the `supportedLocales` as well.

{% tabs %}
{% highlight dart hl_lines="7" %}

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
     );
}

{% endhighlight %}
{% endtabs %}

![Localization Calendar](images/localization/localization.jpg)

## See also

* [How to override the localization in the Flutter event calendar (SfCalendar)](https://support.syncfusion.com/kb/article/10830/how-to-override-the-localization-in-the-flutter-calendar)
* [How to override the Material app locale and set English language for Flutter Calendar](https://support.syncfusion.com/kb/article/11052/how-to-override-the-material-app-locale-and-set-english-language-for-flutter-calendar)