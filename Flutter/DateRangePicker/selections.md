---
layout: post
title: Selections in Syncfusion Flutter Date Range Picker | Syncfusion
description: This session describes the multiple selections in SfDateRangePicker widget in Flutter | DatePicker | Syncfusion
platform: flutter
control: SfDateRangePicker
documentation: ug
---

# Selections in flutter Date Range Picker (SfDateRangePicker)
Dates can be selected by making a touch on month view cells. The default [selectionMode](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/selectionMode.html) is Single which allows user to select one date at a time. `SfDateRangePicker` provides support to select dates in four modes such as Single,Multiple,Range,MultiRange selection

## Single selection mode
 A `single` date can be selected in a month view by changing [DateRangePickerSelectionMode](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerSelectionMode-class.html) as `single`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
       body: SfDateRangePicker(
       view: DateRangePickerView.month,
       selectionMode: DateRangePickerSelectionMode.single,
       )
   );
}

{% endhighlight %}
{% endtabs %}

## Multiple selection mode
More than one date can be selected in a random manner by using `DateRangePickerSelectionMode` as `multiple`. Clicking again on selected dates can do deselection.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
       body: SfDateRangePicker(
       view: DateRangePickerView.month,
       selectionMode: DateRangePickerSelectionMode.multiple,
       )
   );
}


{% endhighlight %}
{% endtabs %}

## Range selection mode
You can select a single date range in `SfDateRangePicker`  view by using `DateRangePickerSelectionMode` as `range`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
               body: SfDateRangePicker(
               view: DateRangePickerView.month,
               selectionMode: DateRangePickerSelectionMode.range,
              )
      );
}

{% endhighlight %}
{% endtabs %}

## Multi range selection mode
You can select more than one date range in a month view by changing `DateRangePickerSelectionMode` as `multiRange`.

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
