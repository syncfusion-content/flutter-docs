---
layout: post 
title: Week Number in Flutter Event Calendar widget | Syncfusion
description: Learn here week number of the month in year of Syncfusion Flutter Event Calendar (SfCalendar) widget and more.
platform: flutter
control: SfCalendar
documentation: ug
---

# Week Number in Flutter Event Calendar (SfCalendar)

You can display the Week Number of the year in month, week and work week views of `SfCalendar` by using the [showWeekNumber]() property. Will show the week number according to the ISO-8601 standard. By default is false.

{% tabs %}
{% highlight Dart %}

@override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: SfCalendar(
          view: CalendarView.month,
          showWeekNumber: true,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

![week-number](images\week-number\week-number.png)

## Week Number Appearance

You can customize the Week Number text style of calendar by  using [WeekNumberStyle]() property. Allows to customize the [textStyle]() and [backgroundColor]() in week number of calendar.

{% tabs %}
{% highlight Dart %}

@override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: SfCalendar(
          view: CalendarView.month,
          showWeekNumber: true,
          weekNumberStyle: const WeekNumberStyle(
            backgroundColor: Colors.pink,
            textStyle: TextStyle(color: Colors.white, fontSize: 15),
          ),
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

![week-number](images\week-number\week-number-style.png)