---
layout: post
title: Views of Syncfusion Flutter Date Range Picker | Syncfusion
description: This session describes the Date Range Picker headers in SfDateRangePicker widget in Flutter | Date Picker
platform: Flutter
control: SfDateRangePicker
documentation: ug
---
## Header
You can customize the header of the data range picker using the [headerStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/headerStyle.html) and [headerHeight](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/headerHeight.html) properties in date range picker.

### Customize the header height in date range picker
You can customize the height of the header of `DateRangePicker` by using [headerHeight](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/SfDateRangePicker/headerHeight.html) property.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDateRangePicker(
      view: DateRangePickerView.month,
      headerHeight: 100,
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Header height Date Range Picker](images/headers/headerheight.png)

### Header appearance
You can customize the header style of the `DataRangePicker` by using [backgroundColor](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerHeaderStyle/backgroundColor.html), [textStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerHeaderStyle/textStyle.html), and [textAlign](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerHeaderStyle/textAlign.html) properties of `DateRangePickerHeaderStyle`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDateRangePicker(
      view: DateRangePickerView.month,
      headerStyle: DateRangePickerHeaderStyle(
          backgroundColor: Color(0xFF7fcd91),
          textAlign: TextAlign.center,
          textStyle: TextStyle(
            fontStyle: FontStyle.normal,
            fontSize: 25,
            letterSpacing: 5,
            color: Color(0xFFff5eaea),
          )),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Header appearance Date Range Picker](images/headers/headerappearance.png)

## View header
You can customize the view header of the `DateRangePicker` using the [viewHeaderHeight](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthViewSettings/viewHeaderHeight.html) and [viewHeaderStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthViewSettings/viewHeaderStyle.html) properties of `DateRangePickerMonthViewSettings`.

### View header height
You can customize the view header height of `DateRangePicker` using [viewHeaderHeight](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerMonthViewSettings/viewHeaderHeight.html) property of `DateRangePickerMonthViewSettings`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDateRangePicker(
      view: DateRangePickerView.month,
      monthViewSettings:
          DateRangePickerMonthViewSettings(viewHeaderHeight: 100),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![View Header height Date Range Picker](images/headers/viewheaderheight.png)

### View header appearance
You can customize the view header style of `DateRangePicker` by using [backgroundColor](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerViewHeaderStyle/backgroundColor.html), [textStyle](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerViewHeaderStyle/textStyle.html) properties of `DateRangePickerViewHeaderStyle`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDateRangePicker(
      view: DateRangePickerView.month,
      monthViewSettings: DateRangePickerMonthViewSettings(
          viewHeaderStyle: DateRangePickerViewHeaderStyle(
              backgroundColor: Color(0xFF7fcd91),
              textStyle: TextStyle(fontSize: 20, letterSpacing: 5))),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![View Header appearance Date Range Picker](images/headers/viewheaderappearance.png)

### View header day format
You can customize the view header of `DateRangePicker` by using dayFormat[link] property of `DateRangePickerMonthViewSettings`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDateRangePicker(
        view: DateRangePickerView.month,
        monthViewSettings: DateRangePickerMonthViewSettings(dayFormat: 'EEE')),
  );
}

{% endhighlight %}
{% endtabs %}

![View Header format Date Range Picker](images/headers/viewheaderformat.png)
