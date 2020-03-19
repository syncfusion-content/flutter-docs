---
layout: post
title: Date Navigations of Syncfusion Flutter Calendar | Scheduler
description: Learn about the complete navigation and gesture support in Syncfusion Flutter Calendar (SfCalendar) widget | Scheduler
platform: flutter
control: SfCalendar
documentation: ug
---

# Date Navigations in Flutter Calendar (SfCalendar)

## Range for visible dates
Visible dates can be restricted between certain range of dates, using  [minDate](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/minDate.html) and [maxDate](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/maxDate.html)  properties in `SfCalendar`. It is applicable in all the schedule views.

### Minimum display date
`minDate` will restrict date navigations features of  backward, also cannot swipe the control using touch gesture beyond the min date range.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
        return Scaffold(
            body: SfCalendar(
                view: CalendarView.month,
                minDate: DateTime(2020, 03, 05, 10 , 0, 0),
                )
        );
}

{% endhighlight %}
{% endtabs %}

### Maximum display date
`maxDate` will restrict date navigations features of forward, and also cannot swipe the control using touch gesture beyond the max date range.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
        return Scaffold(
            body: SfCalendar(
            view: CalendarView.month,
            maxDate: DateTime(2020, 03, 25, 10 , 0, 0),
            )
        );
}

{% endhighlight %}
{% endtabs %}

![MinMaxDate Calendar](images/date-navigation/minmaxdate.png)

## Programmatic date navigation
You can programmatically navigate dates in calendar widget by using the [displayDate](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/controller/displayDate.html) properties of `controller`.

{% tabs %}
{% highlight Dart %}

class MyAppState extends State<MyApp>{
        CalendarController _calendarController;
        @override
        initState(){
            _calendarController = CalendarController();
            _calendarController.displayDate = DateTime(2022, 02, 05);
            super.initState();
      }

  @override
     Widget build(BuildContext context) {
         return MaterialApp(
             home: Scaffold(
             body: SfCalendar(
             view: CalendarView.month,
             controller: _calendarController,
            ),
        ),
    );
 }
 
{% endhighlight %}
{% endtabs %}

## Programmatic date selection
You can programmatically select the dates in calendar widget by [selectedDate](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/controller/selectedDate.html) properties of `controller`.

{% tabs %}
{% highlight Dart %}

class MyAppState extends State<MyApp>{
        CalendarController _calendarController;
        @override
        initState(){
            _calendarController = CalendarController();
            _calendarController.selectedDate = DateTime(2022, 02, 05);
            super.initState();
 }

    @override
    Widget build(BuildContext context) {
        return MaterialApp(
            home: Scaffold(
            body: SfCalendar(
            view: CalendarView.month,
            controller: _calendarController,
        ),
      ),
   );
}

{% endhighlight %}
{% endtabs %}

## Programmatically change to adjacent dates
By default, the date can be navigated to next and previous views using touch gesture, by swiping the control from right to left and left to right direction. The view can be also changed programmatically using the [forward](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/controller/forward.html) and [backward](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/controller/backward.html) methods available in `CalendarController`.

### Forward
You can use the `forward` method of `controller` for viewing the next immediate visible dates in the `SfCalendar`. It will move to next month if the calendar view is month, similarly it will move to next week for week view and next day for day view.

{% tabs %}
{% highlight Dart %}

class MyAppState extends State<MyApp> {
    CalendarController _calendarController;

  @override
        initState() {
            _calendarController = CalendarController();
            super.initState();
  }

 @override
 Widget build(BuildContext context) {
     return MaterialApp(
         home: Scaffold(
         appBar: AppBar(
             title: Text('Calendar Demo'),
             actions: <Widget>[
             IconButton(icon: Icon(Icons.arrow_forward),
             onPressed: () {
             _calendarController.forward();
         },
     ),
  ],
),
         body: SfCalendar(
             view: CalendarView.month,
             controller: _calendarController,
        ),
     ),
  );
}

{% endhighlight %}
{% endtabs %}

### Backward
You can use the `backward` method of `controller` for viewing the previous immediate visible dates in the `SfCalendar`. It will move to previous month if the calendar view is month, similarly it will move to previous week for week view and previous day for day view.

{% tabs %}
{% highlight Dart %}

class MyAppState extends State<MyApp> {
  CalendarController _calendarController;

  @override
  initState() {
    _calendarController = CalendarController();
    super.initState();
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('Calendar Demo'),
          actions: <Widget>[
              IconButton(
                  icon: Icon(Icons.arrow_back),
                  onPressed: () {
                      _calendarController.backward();
                      },
              ),
           ],
        ),
        body: SfCalendar(
          view: CalendarView.month,
          controller: _calendarController,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}
