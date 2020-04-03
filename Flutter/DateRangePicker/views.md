---
layout: post
title: Views of Syncfusion Flutter Date Range Picker | Syncfusion
description: This session describes the Date Range Picker views in SfDateRangePicker widget in Flutter | Date Picker
platform: Flutter
control: SfDateRangePicker
documentation: ug
---

# Multiple picker Views in Flutter Date Range Picker (SfDateRangePicker)
The `SfDateRangePicker` widget provides four different types of views to display. It can be assigned to the widget constructor by using the [view](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/view.html) property. Default view of the widget is month view. By default the current date will be displayed initially for all the date range picker views.

## Month view
This view displays the entire dates of a particular month. By default , the current month will be displayed on loading. The current date is provided with a separate color different from the rest of the dates color in `month view`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
   return Scaffold(
        body: SfDateRangePicker(
       view: DateRangePickerView.month,
       )
   );
}

{% endhighlight %}
{% endtabs %}

![Month view Date Range Picker](images/views/monthview.png)

## Year view
This displays the entire month of a particular year. By default, the current year will be displayed on loading. You can navigate between months quickly by selecting the particular month in a `year view`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
   return Scaffold(
             body: SfDateRangePicker(
             view: DateRangePickerView.year,
             )
      );
}

{% endhighlight %}
{% endtabs %}

![Year view Date Range Picker](images/views/yearview.png)

## Decade view
This view displays the period of 10 years. By default, the current year range of 10 years will be displayed on loading. You can easily navigate between month/year view to decade view by tapping the calendar header. The year can be navigated quickly by selecting a particular year from a  `decade view`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
               body: SfDateRangePicker(
               view: DateRangePickerView.decade,
              )
      );
}

{% endhighlight %}
{% endtabs %}

![Decade view Date Range Picker](images/views/decadeview.png)

## Century view
This view displays the period of 100 years. By default, the current year range of 100 years will be displayed on loading. You can easily navigate between month/year/decade view to century view by tapping the calendar header. You can easily navigate to a decade view by selecting decade years in `century view`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
               body: SfDateRangePicker(
               view: DateRangePickerView.century,
               )
      );
}

{% endhighlight %}
{% endtabs %}

![Century view Date Range Picker](images/views/centuryview.png)

## See also

[How to switch between the date range picker views in Flutter date range picker (SfDateRangePicker)?](https://www.syncfusion.com/kb/11305/how-to-switch-between-the-date-range-picker-views-in-flutter-date-range-picker)

[How to get the current view dates in Flutter date range picker (SfDateRangePicker)?](https://www.syncfusion.com/kb/11331/how-to-get-the-current-view-dates-in-flutter-date-range-picker-sfdaterangepicker)
