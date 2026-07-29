---
layout: post
title: Callbacks in Flutter Date Range Picker widget | Syncfusion
description: Learn here all about Callbacks of Syncfusion Flutter Date Range Picker (SfDateRangePicker) widget and more.
platform: flutter
control: SfDateRangePicker
documentation: ug
---

# Callbacks in Flutter Date Range Picker (SfDateRangePicker)

The date range picker supports the [ViewChangedCallback](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerViewChangedCallback.html) and [SelectionChangedCallback](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerSelectionChangedCallback.html) to interact with the Flutter date range picker.

## View changed callback

The [onViewChanged](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/onViewChanged.html) callback is triggered when the current view is swiped to the previous or next view, or when the picker view is switched to another picker view.

* [visibleDateRange](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerViewChangedArgs/visibleDateRange.html) - returns the start and end dates of the current visible month.

{% tabs %}
{% highlight dart hl_lines="15 16 17" %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_datepicker/datepicker.dart';

void main() {
  runApp(const DateRangePickerApp());
}

class DateRangePickerApp extends StatelessWidget {
  const DateRangePickerApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: SfDateRangePicker(
          view: DateRangePickerView.month,
          onViewChanged: (DateRangePickerViewChangedArgs args) {
            final DateTime? visibleDateRange = args.visibleDateRange.startDate;
          },
        ),
      ),
    );
  }
}

{% endhighlight %}
{% endtabs %}

>**NOTE** 
* Use [HijriDatePickerViewChangedArgs](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/HijriDatePickerViewChangedArgs-class.html) for the [SfHijriDateRangePicker](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfHijriDateRangePicker-class.html).

## Selection changed callback

The [onSelectionChanged](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/onSelectionChanged.html) callback is triggered when dates are selected from the date range picker.

* `args.value` - Returns the selected value based on the selection mode: `DateTime` for single selection, `List<DateTime>` for multiple selection, `PickerDateRange` for range selection, and `List<PickerDateRange>` for multi-range selection.

{% tabs %}
{% highlight dart hl_lines="16 17 18 19 20 21 22 23 24 25 26 27" %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_datepicker/datepicker.dart';

void main() {
  runApp(const DateRangePickerApp());
}

class DateRangePickerApp extends StatelessWidget {
  const DateRangePickerApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: SfDateRangePicker(
          view: DateRangePickerView.month,
          selectionMode: DateRangePickerSelectionMode.range,
          onSelectionChanged: (DateRangePickerSelectionChangedArgs args) {
            if (args.value is PickerDateRange) {
              final DateTime? rangeStartDate = args.value.startDate;
              final DateTime? rangeEndDate = args.value.endDate;
              // Use the range values as needed.
            } else if (args.value is DateTime) {
              final DateTime selectedDate = args.value;
              // Use the selected date value as needed.
            } else if (args.value is List<DateTime>) {
              final List<DateTime> selectedDates = args.value;
              // Use the selected dates list as needed.
            } else {
              final List<PickerDateRange> selectedRanges = args.value;
              // Use the selected ranges list as needed.
            }
          },
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}
