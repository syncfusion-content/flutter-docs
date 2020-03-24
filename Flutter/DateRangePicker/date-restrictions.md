---
layout: post
title: Date restrcitions in Syncfusion Flutter Date Range Picker | Date Picker | Date Selection | Syncfusion
description: Learn about the complete date restriction in Syncfusion SfDateRangePicker widget in Flutter
platform: flutter
control: SfDateRangePicker
documentation: ug
---

# Date Restrictions in Flutter Date Range Picker (SfDateRangePicker)

## Minimum display date
[minDate](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/minDate.html) will restrict date navigations features of backward, also cannot swipe the control using touch gesture beyond the min date range.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
       body: SfDateRangePicker(
      view: DateRangePickerView.month,
      minDate: DateTime(2020, 03, 05, 10 , 0, 0),
     )
  );
}

{% endhighlight %}
{% endtabs %}

## Maximum display date
[maxDate](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/maxDate.html) will restrict date navigations features of forward, and also cannot swipe the control using touch gesture beyond the max date range.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
       body: SfDateRangePicker(
       view: DateRangePickerView.month,
       maxDate: DateTime(2020, 03, 25, 10 , 0, 0),
       )
   );
}

{% endhighlight %}
{% endtabs %}

## Enable and disable Past dates

The DateRangePicker allows you to enable/disable the past dates from today dates in `MonthView`. This can be achieved by changing the [enablePastDates](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/enablePastDates.html) property. By default, value of this property is set to true.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
       body: SfDateRangePicker(
       view: DateRangePickerView.month,
       enablePastDates : false,
     )
   );
}

{% endhighlight %}
{% endtabs %}

## Blackout Dates
In DateRangePicker, [blackoutDates](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthViewSettings/blackoutDates.html) refers the disabled dates that restrict the user from selecting it. These dates will be marked with Strikethrough.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
       body: SfDateRangePicker(
       view: DateRangePickerView.year,
       monthViewSettings: DateRangePickerMonthViewSettings(blackoutDates:List<DateTime>()
                ..add(DateTime(2020, 03, 18))..add(DateTime(2020, 03, 19))),
       )
   );
}

{% endhighlight %}
{% endtabs %}


