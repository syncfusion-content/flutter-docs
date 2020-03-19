---
layout: post
title: Right to Left of Syncfusion Flutter Calendar | Calendar
description: Describes how Calendar works on right-to-left localization in Flutter Calendar(SfCalendar) | Calendar
platform: flutter
control: SfCalendar
documentation: ug
---

# Right to left (RTL) in Flutter Calendar (SfCalendar)
`SfCalendar` supports changing the layout direction of the widget in the right-to-left direction by using the `Directionality` widget `textDirection` property to rtl.

You can also change the right to left direction by specifying locale, which support RTL language such as (Arabic ,Persian ,Hebrew, Pashto, Urdu) by specifying the `MaterialApp` properties and adding the flutter_localizations package to your application.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
        return Directionality(
            textDirection: TextDirection.rtl,
            child: Scaffold(
                appBar: AppBar(
                title: const Text('RTL in calendar'),
            ),
            body: SfDateRangePicker(
            view: DateRangePickerView.month,
             ),
         ),
      );
   }
}

![Right to Left Calendar](images/right-to-left/rtl.jpg)
