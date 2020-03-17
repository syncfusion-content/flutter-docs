---
layout: post
title: Flutter date range picker widget | Syncfusion
description: Getting started with the Syncfusion flutter date range picker with four built-in configurable views modes.
platform: flutter
control: SfDateRangePicker
documentation: ug
---

# Getting Started with Flutter Date Range Picker (SfDateRangePicker)
This section explains the steps required to add the date range picker widget. This section covers only basic features needed to get started with Syncfusion date range picker widget.

## Add flutter date range picker to an application
Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://flutter.dev/docs/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion flutter date range picker dependency to your pubspec.yaml file.

{% highlight dart %}

dependencies:

syncfusion_flutter_datepicker: ^18.1.0.36-beta

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


## Multiple picker views

The `SfDateRangePicker` widget provides four different types of views to display. It can be assigned to the widget constructor by using the [view](https://pub.dev/documentation/syncfusion_flutter_daterangepicker/latest/daterangepicker/SfDateRangePicker/view.html) property. Default view of the widget is month view. By default the current date will be displayed initially for all the date range picker views.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
   return Scaffold(
       body: SfDateRangePicker(
     view: DateRangePickerView.year,
));
}

{% endhighlight %}
{% endtabs %}

## Change first day of week

The DateRangePicker widget will be rendered with Sunday as the first day of the week, but you can customize it to any day by using the [firstDayOfWeek](https://pub.dev/documentation/syncfusion_flutter_daterangepicker/latest/daterangepicker/SfDateRangePicker/firstDayOfWeek.html) property.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
   return Scaffold(
       body: SfDateRangePicker(
     view: DateRangePickerView.month,
     firstDayOfWeek: 1,
));
}

{% endhighlight %}
{% endtabs %}


## Date selection

The DateRangePicker supports selecting single, multiple, and range of dates. It also supports programmatic selection.

The selected date or range details can be obtained using the `onSelectionChanged` callback of datepicker. The callback will return the `DateRangePickerSelectionChangedArgs` which contains the selected date or range details.

{% tabs %}
{% highlight Dart %}

void _onSelectionChanged(DateRangePickerSelectionChangedArgs args) {
 final dynamic value = args;
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
