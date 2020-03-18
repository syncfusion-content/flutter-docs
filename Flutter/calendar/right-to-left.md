---
layout: post
title: Right to Left of Syncfusion Flutter Calendar | Calendar
description: Describes how Calendar works on right-to-left localization in Flutter Calendar(SfCalendar) | Calendar
platform: flutter
control: SfCalendar
documentation: ug
---

# Right to left (RTL) in Flutter Calendar (SfCalendar)
`SfCalendar` supports changing the layout direction of the control in the right-to-left direction by giving the Directionality textDirection to RightToLeft.

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

![Right to Left](images/right-to-left/rtl.png)
