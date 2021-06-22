---
layout: post
title: Week Number in Flutter Date Range Picker widget | Syncfusion
description: Learn here week number of the month in year of Syncfusion Flutter Date Range Picker (SfDateRangePicker) widget and more.
platform: Flutter
control: SfDateRangePicker
documentation: ug
---

# Week Number in Flutter Date Range Picker (SfDateRangePicker)

You can display the Week Number of the year in MonthView by setting [showWeekNumber]() property of `DateRangePickerMonthViewSettings` as true, by default is false. Will show the week number according to the ISO-8601 standard. 

{% tabs %}
{% highlight Dart %}

@override
  Widget build(BuildContext context) {
    return MaterialApp(
        home: Scaffold(
      body: SfDateRangePicker(
        view: DateRangePickerView.month,
        monthViewSettings: const DateRangePickerMonthViewSettings(
          showWeekNumber: true,
        ),
      ),
    ));
  }

{% endhighlight %}
{% endtabs %}

![week-number](images\week-number\picker-week-number.png)

## Week Number Appearance
You can customize the week number style by using [textStyle]() and [backgroundColor]() properties of [WeekNumberStyle]().

{% tabs %}
{% highlight Dart %}

@override
  Widget build(BuildContext context) {
    return MaterialApp(
        home: Scaffold(
      body: SfDateRangePicker(
        view: DateRangePickerView.month,
        monthViewSettings: const DateRangePickerMonthViewSettings(
          showWeekNumber: true,
          weekNumberStyle: DateRangePickerWeekNumberStyle(
              textStyle: TextStyle(fontStyle: FontStyle.italic),
              backgroundColor: Colors.purple),
        ),
      ),
    ));
  }

{% endhighlight %}
{% endtabs %}

![week-number](images\week-number\picker-week-number-style.png)