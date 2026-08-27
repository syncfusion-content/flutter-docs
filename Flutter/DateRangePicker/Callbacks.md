---
layout: post
title: Callbacks in Flutter DateRangePicker | Syncfusion®
description: Learn about callback support in Syncfusion® Flutter DateRangePicker (SfDateRangePicker), including date selection, view changes, and navigation events.
platform: flutter
control: SfDateRangePicker
documentation: ug
---

# Callbacks in Flutter Date Range Picker (SfDateRangePicker)

Calendar supports the [ViewChangedCallback](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerViewChangedCallback.html) and [SelectionChangedCallback](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerSelectionChangedCallback.html) to interact with the Flutter Date Range Picker.

## View changed callback

The [onViewChanged](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/onViewChanged.html) callback triggers when the current view swiped to previous or next view, picker view switched to another picker view.

* [visibleDateRange](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerViewChangedArgs/visibleDateRange.html) - returns the start and end dates of the current visible month.

{% tabs %}
{% highlight dart hl_lines="6 7 8" %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SfDateRangePicker(
        view: DateRangePickerView.month,
        onViewChanged: (DateRangePickerViewChangedArgs args) {
          var visibleDates = args.visibleDateRange;
        },
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

>**NOTE** 
* Use [HijriDatePickerViewChangedArgs](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/HijriDatePickerViewChangedArgs-class.html) for the [SfHijriDateRangePicker](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfHijriDateRangePicker-class.html).

## Selection changed callback

The [onSelectionChanged](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/onSelectionChanged.html) callback triggers when selecting the dates from the Flutter Date Range Picker.

* `args.value` - returns the dates based on the selection mode.

{% tabs %}
{% highlight dart hl_lines="7 8 9 10 11 12 13 14 15 16 17 18" %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SfDateRangePicker(
        view: DateRangePickerView.month,
        selectionMode: DateRangePickerSelectionMode.range,
        onSelectionChanged: (DateRangePickerSelectionChangedArgs args) {
          if (args.value is PickerDateRange) {
            final DateTime rangeStartDate = args.value.startDate;
            final DateTime rangeEndDate = args.value.endDate;
          } else if (args.value is DateTime) {
            final DateTime selectedDate = args.value;
          } else if (args.value is List<DateTime>) {
            final List<DateTime> selectedDates = args.value;
          } else {
            final List<PickerDateRange> selectedRanges = args.value;
          }
        },
      ),
    );
  }

{% endhighlight %}
{% endtabs %}
