---
layout: post
title: Flutter Date Range Picker | Date Picker | Date Selection | Syncfusion
description: The Syncfusion Flutter Date Range Picker widget allows users to easily select dates or a range of dates. It allows us to quickly navigate to the desired date.
platform: Flutter
control: SfDateRangePicker
documentation: ug
---

# Getting Started with Flutter Date Range Picker (SfDateRangePicker)
This section explains the steps required to add the date range picker widget. This section covers only basic features needed to get started with Syncfusion date range picker widget.

## Add Flutter Date Range Picker to an application
Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://flutter.dev/docs/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion Flutter date range picker dependency to your `pubspec.yaml` file.

{% highlight dart %}

dependencies:

syncfusion_flutter_datepicker: ^18.1.36-beta

{% endhighlight %}

**Get packages** 

Run the following command to get the required packages.

{% highlight dart %}

$ flutter pub get

{% endhighlight %}

**Import package**

Import the following package in your Dart code.

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_datepicker/datepicker.dart';

{% endhighlight %}
{% endtabs %}

## Initialize date range picker

After importing the package, initialize the date range picker widget as a child of any widget. Here, the date range picker widget is added as a child of the scaffold widget.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
   return Scaffold(
       body: Container(
       child: SfDateRangePicker(),
));
}
	
{% endhighlight %}
{% endtabs %}

![Initialize Date Range Picker](images/getting-started/initialize.png)

## Multiple picker views

The `SfDateRangePicker` widget provides four different types of views to display. It can be assigned to the widget constructor by using the [view](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/view.html) property. Default view of the widget is month view. By default the current date will be displayed initially for all the date range picker views.

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

![Multiple picker views Date Range Picker](images/getting-started/year-view.png)

## Change first day of week

The DateRangePicker widget will be rendered with Sunday as the first day of the week, but you can customize it to any day by using the [firstDayOfWeek](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthViewSettings/firstDayOfWeek.html) property.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
   return Scaffold(
        body: SfDateRangePicker(
        view: DateRangePickerView.month,
        monthViewSettings: DateRangePickerMonthViewSettings(firstDayOfWeek: 1),
        )
    );
}

![First day of week Date Range Picker](images/getting-started/firstdayofweek.png)

{% endhighlight %}
{% endtabs %}

## Initial display date
You can change the initial display date of date range picker by using the initialDisplayDate[link] property, which displays the `DateRangePicker` based on the given date time. By default, current date will be set as `initialDisplayDate`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDateRangePicker(
        view: DateRangePickerView.month,
        initialDisplayDate: DateTime(2020,3,1,9,0,0),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Initial display date in Date Range Picker](images/getting-started/initialdisplaydate.png)

## Initial selected date
You can programmatically select the specific date of the date range picker by setting corresponding date value to the initialSelectedDate[link] property of `DateRangePicker`. 

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDateRangePicker(
        view: DateRangePickerView.month,
        initialSelectedDate: DateTime.now(),
	),
  );
}

{% endhighlight %}
{% endtabs %}

![Initial selected date in Date Range Picker](images/getting-started/initialselecteddate.png)

## Initial selected dates
You can programmatically set the selected dates for `DateRangePicker` by setting corresponding dates to the initialSelectedDates[link] property. 

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDateRangePicker(
      view: DateRangePickerView.month,
      selectionMode: DateRangePickerSelectionMode.multiple,
      initialSelectedDates: List<DateTime>()
        ..add(DateTime(2020, 04, 20))
        ..add(DateTime(2020, 04, 16))
        ..add(DateTime(2020, 04, 17))
        ..add(DateTime(2020, 04, 30))
        ..add(DateTime(2020, 04, 07))
        ..add(DateTime(2020, 04, 03)),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Initial selected dates in Date Range Picker](images/getting-started/initialselecteddates.png)

## Initial selected range
You can programmatically set the selected range for `DateRangePicker` by setting start end range to the initialSelectedRange[link] property.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDateRangePicker(
        view: DateRangePickerView.month,
        selectionMode: DateRangePickerSelectionMode.range,
        initialSelectedRange: PickerDateRange(
            DateTime.now(), DateTime.now().add(Duration(days: 5)))),
  );
}

{% endhighlight %}
{% endtabs %}

![Initial selected range in Date Range Picker](images/getting-started/initialselectedrange.png)

## Initial selected ranges
You can programmatically set more than one selected range for `DateRangePicker` by setting start and end ranges to the initialSelectedRanges[link] property.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDateRangePicker(
        view: DateRangePickerView.month,
        selectionMode: DateRangePickerSelectionMode.multiRange,
        initialSelectedRanges: List<PickerDateRange>()
          ..add(
            PickerDateRange(
                DateTime.now(), DateTime.now().add(Duration(days: 5))),
          )..add(
            PickerDateRange(DateTime(2020, 4, 21), DateTime(2020, 4, 28)),
          )),
  );
}

{% endhighlight %}
{% endtabs %}

![Initial selected ranges in Date Range Picker](images/getting-started/initialselectedranges.png)

## Background color
You can customize background of the `DateRangePicker` using the backgroundColor[link] property. 

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDateRangePicker(
      view: DateRangePickerView.month,
      backgroundColor: Color(0xFFF6D55C),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Date selection

The DateRangePicker supports selecting single, multiple, and range of dates. It also supports programmatic selection.

The selected date or range details can be obtained using the `onSelectionChanged` callback of date range picker. The callback will return the `DateRangePickerSelectionChangedArgs` which contains the selected date or range details.

{% tabs %}
{% highlight Dart %}

void _onSelectionChanged(DateRangePickerSelectionChangedArgs args) {
// TODO: implement your code here
}

@override
Widget build(BuildContext context) {
    return MaterialApp(
        home: Scaffold(
            body: Container(
                child: SfDateRangePicker(
                    onSelectionChanged: _onSelectionChanged,
                    selectionMode: DateRangePickerSelectionMode.range,
                ),
            ),
        ),
    );
}


{% endhighlight %}
{% endtabs %}

![Date selection Date Range Picker](images/getting-started/range-selection.png)
