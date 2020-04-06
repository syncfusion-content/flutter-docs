---
layout: post
title: Selections in Syncfusion Flutter Date Range Picker | Syncfusion
description: This session describes the multiple selections in SfDateRangePicker widget in Flutter | DatePicker | Syncfusion
platform: Flutter
control: SfDateRangePicker
documentation: ug
---

# Selections in Flutter Date Range Picker (SfDateRangePicker)
Dates can be selected by touching the on month view cells. The default [selectionMode](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/selectionMode.html) is Single that allows the user to select one date at a time. `SfDateRangePicker` provides support to select dates in four modes such as `Single`, `Multiple`, `Range` and `MultiRange` selection

## Single selection
 A `single` date can be selected in a month view by changing the [DateRangePickerSelectionMode](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerSelectionMode-class.html) to `single`.

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

![SingleSelection Date Range Picker](images/selections/singleselection.png)

## Multiple selection
You can randomly select more than one date by changing the `DateRangePickerSelectionMode` to `multiple`. By Clicking again you can deselect the selected dates.

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

![MultiSelection Date Range Picker](images/selections/multiselection.png)

## Range selection
You can select a single date range in the month view by changing the `DateRangePickerSelectionMode` to the `range`.

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

![RangeSelection Date Range Picker](images/selections/range-selection.png)

## Multi range selection
You can select more than one date range in a month view by changing the `DateRangePickerSelectionMode` to the `multiRange`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
               body: SfDateRangePicker(
               view: DateRangePickerView.month,
               selectionMode: DateRangePickerSelectionMode.multiRange,
               )
      );
}

{% endhighlight %}
{% endtabs %}

![MultiRangeSelection Date Range Picker](images/selections/multirange.png)

## Selection radius
You can customize the radius of the selection using selectionRadius[link] property of the `DateRange PickerMonthViewSettings`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDateRangePicker(
      view: DateRangePickerView.month,
      monthViewSettings: DateRangePickerMonthViewSettings(selectionRadius: 10),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Enable swipe selection
Using enableSwipeSelection[link] property of the `DateRangePicker`, you can’t select the dates by using swiping. By default, `enableSwipeSelection` property as `true`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDateRangePicker(
      view: DateRangePickerView.month,
      selectionMode: DateRangePickerSelectionMode.range,
      monthViewSettings:
          DateRangePickerMonthViewSettings(enableSwipeSelection: false),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Toggle day selection
You can de-select the selected date using the toggleDaySelection[link] property of the `DateRangePicker`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDateRangePicker(
      view: DateRangePickerView.month,
      toggleDaySelection: true,
    ),
  );
}

{% endhighlight %}
{% endtabs %}