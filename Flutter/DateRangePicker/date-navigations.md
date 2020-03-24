---
layout: post
title: Date Navigations of Syncfusion Flutter Date Range Picker | Syncfusion
description: Learn about the complete navigation and gesture support in Syncfusion SfDateRangePicker widget in Flutter
platform: flutter
control: SfDateRangePicker
documentation: ug
---

# Date Navigations in Flutter Date Range Picker (SfDateRangePicker)

## Programmatic date navigation
You can programmatically navigate dates in date range picker widget by using the [displayDate](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerController/displayDate.html)  property of [DateRangePickerController](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerController-class.html)

{% tabs %}
{% highlight Dart %}

class MyAppState extends State<MyApp>{
         DateRangePickerController _datePickerController;
         @override
         initState(){
            _datePickerController = DateRangePickerController ();
            _datePickerController.displayDate = DateTime(2022, 02, 05);
            super.initState();
        }

@override
    Widget build(BuildContext context) {
       return MaterialApp(
           home: Scaffold(
           body: SfDateRangePicker(
           view: DateRangePickerView.month,
           controller: _datePickerController,
           ),
       ),
   );
}

{% endhighlight %}
{% endtabs %}

## Programmatic view navigation
You can programmatically navigate dates in calendar widget by using the [view](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerController/view.html) property of `DateRangePickerController`.

{% tabs %}
{% highlight Dart %}

class MyAppState extends State<MyApp>{
         DateRangePickerController _datePickerController;
         @override
         initState(){
            _datePickerController = DateRangePickerController ();
            _datePickerController.view =DateRangePickerView.month;
            super.initState();
       }

@override
     Widget build(BuildContext context) {
        return MaterialApp(
           home: Scaffold(
           body: SfDateRangePicker(
           controller: _datePickerController,
           ),
       ),
   );
}

{% endhighlight %}
{% endtabs %}

## Programmatic date selection
You can programmatically select the dates in calendar widget by using  `DateRangePickerController` property.

### Single selection
You can selects the date programmatically at initial or run time by using [selectedDate](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerController/selectedDate.html) of `DateRangePickerController` property. It is only applicable when the [selectionMode](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerSelectionMode-class.html) set as `DateRangePickerSelectionMode.single`.

### Multi selection
You can selects the multiple dates programmatically at initial or run time by using [selectedDates](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerController/selectedDates.html) of `DateRangePickerController` property. It is only applicable when the `selectionMode` set as `DateRangePickerSelectionMode.multiple`.

### Range selection
You can selects the single date range programmatically at initial or run time by using [selectedRange](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerController/selectedRange.html) of `DateRangePickerController` property. It is only applicable when the `selectionMode` set as `DateRangePickerSelectionMode.range`

### Multi Range selection
You can selects more than one date range programmatically at initial or run time by using [selectedRanges](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerController/selectedRanges.html) of `DateRangePickerController` property. It is only applicable when the `selectionMode` set as `DateRangePickerSelectionMode.multiRange`.

{% tabs %}
{% highlight Dart %}

class MyAppState extends State<MyApp>{
    DateRangePickerController _datePickerController;
    @override
    initState(){
      _datePickerController = DateRangePickerController ();
      _datePickerController.selectedRange = PickerDateRange(DateTime(2020,03,01),DateTime(2020,03,05));
      super.initState();
     }

    @override
    Widget build(BuildContext context) {
      return MaterialApp(
        home: Scaffold(
        body: SfDateRangePicker (
        view: DateRangePickerView.month,
        selectionMode: DateRangePickerSelectionMode.range,
        controller: _datePickerController,
        ),
      ),
    );
}

{% endhighlight %}
{% endtabs %}

## Programmatically change to adjacent dates
By default, the date can be navigated to next and previous views using touch gesture, by swiping the control from right to left and left to right direction. The view can be also changed programmatically using the [forward](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerController/forward.html) and [backward](https://pub.dev/documentation/syncfusion_flutter_datepicker/latest/datepicker/DateRangePickerController/backward.html) methods available in ` DateRangePickerController`.

### Forward
You can use the `forward` method of ` DateRangePickerController ` for viewing the next immediate visible dates in the `SfDateRangePicker`. It will move to next month if the calendar view is month, similarly it will move to next week for week view and next day for day view.

{% tabs %}
{% highlight Dart %}

class MyAppState extends State<MyApp> {
   DateRangePickerController _datePickerController;
   @override
   initState() {
      _ datePickerController = DateRangePickerController ();
      super.initState();
   }

   @override
   Widget build(BuildContext context) {
       return MaterialApp(
          home: Scaffold(
          appBar: AppBar(
          title: Text(‘DateRangePicker Demo'),
          actions: <Widget>[
          IconButton(icon: Icon(Icons.arrow_forward),
         onPressed: () {
           _ datePickerController.forward();
         },
      ),
   ],
),
        body: SfDateRangePicker(
        view: DateRangePickerView.month,
        controller: _ datePickerController,
       ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

### Backward
You can use the `backward` method of ` DateRangePickerController` for viewing the previous immediate visible dates in the `SfDateRangePicker`. It will move to previous month if the calendar view is month, similarly it will move to previous week for week view and previous day for day view.

{% tabs %}
{% highlight Dart %}

class MyAppState extends State<MyApp> {
   DateRangePickerController _datePickerController;

   @override
   initState() {
      _datePickerController = DateRangePickerController ();
      super.initState();
   }

   @override
   Widget build(BuildContext context) {
         return MaterialApp(
             home: Scaffold(
             appBar: AppBar(
             title: Text(DateRangePicker Demo'),
             actions: <Widget>[
             IconButton(
             icon: Icon(Icons.arrow_back),
             onPressed: () {
             _datePickerController.backward();
          },
       ),
    ],
),
            body: SfDateRangePicker(
            view: DateRangePickerView.month,
            controller: _ datePickerController,
           ),
       ),
   );
}

{% endhighlight %}
{% endtabs %}

