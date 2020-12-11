---
layout: post
title: Flutter Hijri Date Range Picker | Hijri Date Picker | Hijri Date Selection | Syncfusion
description: Hijri date picker to display and handle the lunar calendar.
platform: flutter
control: SfDateRangePicker
documentation: ug
---

# Hijri date range picker
Along with Gregorian calendar, the picker package contains Hijri date picker to display the Islamic calendar. Islamic calendar or Hijri calendar is a lunar calendar consisting of 12 months in a year of 354 or 355 days. To know more about Islamic calendar, kindly refer [Wikipedia](https://en.wikipedia.org/wiki/Islamic_calendar).

Also, It consists of all the Gregorian calendar functionalities like, min and max date, first day of week , different selection modes, RTL and customization for special dates.

To display Hijri date picker, initialize [HijriDateRangePicker]() widget as a child of any widget. Here Hijri date range picker added as a child of the scaffold widget.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(body: SfHijriDateRangePicker()),
  );
}

{% endhighlight %}
{% endtabs %}

>**NOTE** 

* Most of the properties type and classes were same from [SfDateRangePicker]() except the followings [HijriDatePickerController](), [HijriDatePickerMonthCellStyle](), [HijriDatePickerMonthViewSettings](), [HijriDatePickerViewChangedArgs](), [HijriDatePickerYearCellStyle](), [HijriDateRange]() and [HijriDatePickerView]().
* Use [HijriDateTime]() class to define the date for ‘SfHijriDateRangePicker’.

## Multiple picker views
The [SfHijriDateRangePickerView]() widget provides three different types of views to display. It can be assigned to widget constructor by using the [view]() property. Default view of the widget is month view. By default, current date will be displayed initially for all the date range picker views.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
        body: SfHijriDateRangePicker(
      view: HijriDatePickerView.year,
    )),
  );
}

{% endhighlight %}
{% endtabs %}

## Change first day of week
The HijriDateRangePicker widget will be rendered with Sunday as the first day of the week, but you can customize it to any day by using the [firstDayOfWeek]() property [HijriDatePickerMonthViewSettings]().

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
        body: SfHijriDateRangePicker(
      view: HijriDatePickerView.month,
      monthViewSettings: HijriDatePickerMonthViewSettings(firstDayOfWeek: 1),
    )),
  );
}

{% endhighlight %}
{% endtabs %}

## Date selection
The HijriDateRangePicker supports selecting single, multiple, and range of dates. It also supports programmatic selection.

The selected date or range details can be obtained using the [onSelectionChanged ]()callback of hijri date range picker. The callback will return the [DateRangePickerSelectionChangedArgs]() which contains the selected date or range details.

{% tabs %}
{% highlight Dart %}

void _onSelectionChanged(DateRangePickerSelectionChangedArgs args) {
  /// TODO: implement your code here
}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
        body: SfHijriDateRangePicker(
      view: HijriDatePickerView.month,
      selectionMode: DateRangePickerSelectionMode.range,
      onSelectionChanged: _onSelectionChanged,
    )),
  );
}

{% endhighlight %}
{% endtabs %}

## HijriDatePickerController
### Programmatic date navigation
You can programmatically navigate date in hijri date picker widget by using the [displayDate]() property in of [HijriDatePickerController]().


{% tabs %}
{% highlight Dart %}

class MyAppState extends State<MyApp> {
  HijriDatePickerController _controller;

  @override
  void initState() {
    _controller = HijriDatePickerController();
    _controller.displayDate = HijriDateTime(1445, 02, 05);
    super.initState();
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
          body: SfHijriDateRangePicker(
        controller: _controller,
        view: HijriDatePickerView.month,
      )),
    );
  }
}

{% endhighlight %}
{% endtabs %}

### Programmatic view navigation
You can programmatically navigate view in the hijri date picker widget by using the [view]() property of `HijriDtePickerController`.

{% tabs %}
{% highlight Dart %}

class MyAppState extends State<MyApp> {
  HijriDatePickerController _controller;

  @override
  void initState() {
    _controller = HijriDatePickerController();
    _controller.view = HijriDatePickerView.month;
    super.initState();
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
          body: SfHijriDateRangePicker(
        controller: _controller,
      )),
    );
  }
}

{% endhighlight %}
{% endtabs %}

### Programmatic date selection
You can select dates programmatically on hijri date picker widget by using the ‘HijriDatePickerController’.

#### Single selection
Initially or during the run time, you can select the date programmatically by using the selectedDate property of `HijriDatePickerController`. It is only applicable when the selectionMode is set to `DateRangePickerSelectionMode.single`.

{% tabs %}
{% highlight Dart %}

class MyAppState extends State<MyApp> {
  HijriDatePickerController _controller;

  @override
  void initState() {
    _controller = HijriDatePickerController();
    _controller.view = HijriDatePickerView.month;
    _controller.selectedDate = HijriDateTime.now().add(Duration(days: 2));
    super.initState();
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
          body: SfHijriDateRangePicker(
        selectionMode: DateRangePickerSelectionMode.single,
        controller: _controller,
      )),
    );
  }
}

{% endhighlight %}
{% endtabs %}

#### Multi selection
Initially or during the run time, you can selects the multiple dates programmatically by using the selectedDates property of `HijriDatePickerController`. It is only applicable when the selectionMode is set to `DateRangePickerSelectionMode.multiple`.

{% tabs %}
{% highlight Dart %}

class MyAppState extends State<MyApp> {
  HijriDatePickerController _controller;

  @override
  void initState() {
    _controller = HijriDatePickerController();
    _controller.view = HijriDatePickerView.month;
    _controller.selectedDates = <HijriDateTime>[
      HijriDateTime.now().add(Duration(days: 2)),
      HijriDateTime.now().add(Duration(days: 4)),
      HijriDateTime.now().add(Duration(days: 7)),
      HijriDateTime.now().add(Duration(days: 11))
    ];
    super.initState();
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
          body: SfHijriDateRangePicker(
        selectionMode: DateRangePickerSelectionMode.multiple,
        controller: _controller,
      )),
    );
  }
}

{% endhighlight %}
{% endtabs %}

#### Range selection
Initially or during run time, you can selects the single date range programmatically by using the selectedRange property of `HijriDatePickerController`. It is only applicable when the selectionMode is set to `DateRangePickerSelectionMode.range`.

Use [HijriDtaeRange]() to define the date range for hijir date picker.

{% tabs %}
{% highlight Dart %}

class MyAppState extends State<MyApp> {
  HijriDatePickerController _controller;

  @override
  void initState() {
    _controller = HijriDatePickerController();
    _controller.view = HijriDatePickerView.month;
    _controller.selectedRange = HijriDateRange(
        HijriDateTime(1442, 03, 01), HijriDateTime(1442, 03, 05));
    super.initState();
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
          body: SfHijriDateRangePicker(
        selectionMode: DateRangePickerSelectionMode.range,
        controller: _controller,
      )),
    );
  }
}

{% endhighlight %}
{% endtabs %}

#### Multi-range selection
Initially or during run time, you can selects more than one date range programmatically by using the selectedRanges  property of `HijriDatePickerController`. It is only applicable when the selectionMode is set to `DateRangePickerSelectionMode.multiRange`.

{% tabs %}
{% highlight Dart %}

class MyAppState extends State<MyApp> {
  HijriDatePickerController _controller;

  @override
  void initState() {
    _controller = HijriDatePickerController();
    _controller.view = HijriDatePickerView.month;
    _controller.selectedRanges = <HijriDateRange>[
      HijriDateRange(HijriDateTime.now().subtract(Duration(days: 4)),
          HijriDateTime.now().add(Duration(days: 4))),
      HijriDateRange(HijriDateTime.now().add(Duration(days: 11)),
          HijriDateTime.now().add(Duration(days: 16)))
    ];
    super.initState();
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
          body: SfHijriDateRangePicker(
        selectionMode: DateRangePickerSelectionMode.multiRange,
        controller: _controller,
      )),
    );
  }
}


{% endhighlight %}
{% endtabs %}

## Month cell customization
You can customize the hijri date picker month view by using the [monthCellStyle]() property of `SfHijriDateRangePicker`.

•    **Current month dates** – You can customize the current month date’s text style and background of the HijriDateRangePicker by using the [textStyle]() and [cellDecoration]() properties of [HijriDatePickerMonthCellStyle]().
•    **Today date** – You can customize the today date text style and background of the HijriDateRangePicker by using the [todayTextStyle]() and [todayCellDecoration]().
•    **Blackout Dates** - You can customize the blackout dates text style and background of the HijriDateRangePicker by using the [blackoutDateTextStyle]() and [blackoutDatesDecoration]().
•    **Disabled dates** – Disable dates text style and background beyond of the [minDate]() and [maxDate]() in HijriDateRangePicker by using [disableDatesTextStyle]() and [disableDatesDecoration]().
•    **Special Dates** – You can add special dates to the HijriDateRangePicker by using [specialDates]() property, and you can also customize the special dates text style and background by using the [specialDatesTextStyle]() and [specialDatesDecoration]().
•    **Weekend Dates** – You can change weekend dates to HijriDateRangePicker by using the [weekendDays]() property, and you can also customize the weekend dates text style and background by using the [weekendDatesTextStyle]() and [weekendDatesDecoration]().

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
        body: SfHijriDateRangePicker(
      view: HijriDatePickerView.month,
      monthViewSettings: HijriDatePickerMonthViewSettings(
        blackoutDates: <HijriDateTime>[HijriDateTime(1442, 02, 05)],
        weekendDays: <int>[6, 7],
        specialDates: <HijriDateTime>[
          HijriDateTime(1442, 02, 10),
          HijriDateTime(1442, 02, 15)
        ],
      ),
      monthCellStyle: HijriDatePickerMonthCellStyle(
        blackoutDatesDecoration: BoxDecoration(
            color: Colors.red,
            border: Border.all(color: const Color(0xFFF44436), width: 1),
            shape: BoxShape.circle),
        weekendDatesDecoration: BoxDecoration(
            color: const Color(0xFFDFDFDF),
            border: Border.all(color: const Color(0xFFB6B6B6), width: 1),
            shape: BoxShape.circle),
        specialDatesDecoration: BoxDecoration(
            color: Colors.green,
            border: Border.all(color: const Color(0xFF2B732F), width: 1),
            shape: BoxShape.circle),
        blackoutDateTextStyle: TextStyle(
            color: Colors.white, decoration: TextDecoration.lineThrough),
        specialDatesTextStyle: const TextStyle(color: Colors.white),
      ),
    )),
  );
}

{% endhighlight %}
{% endtabs %}

## Year cell customization
You can customize the calendar year, and decde view by using the [yearCellStyle]() of `SfHijriDateRangePicker`.

•    **Current year** – You can customize current month dates text style and background of the DateRangePicker by using the [textStyle]() and [cellDecoration]() properties of [HijriDatePickerYearCellStyle]().
•    **Disabled dates** – Disable dates text style and background beyond of the HijriDateRangePicker by using the [disableDatesTextStyle]() and [disableDatesDecoration]().
•    **Today date** – You can customize the today date text style and background of the HijriDateRangePicker by using the [todayTextStyle]() and [todayCellDecoration]().

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
        body: SfHijriDateRangePicker(
      view: HijriDatePickerView.year,
      yearCellStyle: HijriDatePickerYearCellStyle(
        disabledDatesDecoration: BoxDecoration(
            color: const Color(0xFFDFDFDF),
            border: Border.all(color: const Color(0xFFB6B6B6), width: 1),
            shape: BoxShape.circle),
        disabledDatesTextStyle: const TextStyle(color: Colors.black),
        textStyle: const TextStyle(color: Colors.blue),
        todayCellDecoration: BoxDecoration(
            color: const Color(0xFFDFDFDF),
            border: Border.all(color: const Color(0xFFB6B6B6), width: 1),
            shape: BoxShape.circle),
        todayTextStyle: const TextStyle(color: Colors.purple),
      ),
    )),
  );
}

{% endhighlight %}
{% endtabs %}


