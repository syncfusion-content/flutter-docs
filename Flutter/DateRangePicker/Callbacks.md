---
layout: post
title: Views of Syncfusion Flutter Date Range Picker | Syncfusion
description: This session describes the Date Range Picker callbacks in SfDateRangePicker widget in Flutter | Date Picker
platform: Flutter
control: SfDateRangePicker
documentation: ug
---

# Callbacks in Flutter date range picker

## View changed callback
The onViewChanged[link] callback triggers when the current view of picker changed that is view swiped to previous /next view, picker view switched to another picker view.

`visibleDateRange` - returns the start and end dates of the current visible month.

{% tabs %}
{% highlight Dart %}

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
