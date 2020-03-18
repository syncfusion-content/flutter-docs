---
layout: post
title: Date Navigation of Syncfusion Flutter Calendar | Calendar
description: Learn about the complete navigation and gesture support in Syncfusion Flutter Calendar (SfCalendar) widget | Calendar
platform: flutter
control: SfCalendar
documentation: ug
---

# Date Navigation in Flutter Calendar (SfCalendar)

## Range for visible dates
Visible dates can be restricted between certain range of dates, using `MinDisplayDate` and `MaxDisplayDate` properties in `SfCalendar`. It is applicable in all the schedule views.

### Minimum Display Date
`MinDisplayDate` will restrict date navigations features of `Backward`,  also cannot swipe the control using touch gesture beyond the min date range.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
return Scaffold(
body: SfCalendar(
view: CalendarView.month,
minDate: DateTime(DateTime.now().year,DateTime.now().month -  6,DateTime.now().day,10,0,0),
     )
  );
}

{% endhighlight %}
{% endtabs %}

### Maximum Display Date :
`MaxDisplayDate` will restrict date navigations features of `Forward`,  and also cannot swipe the control using touch gesture beyond the max date range.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
return Scaffold(
body: SfCalendar(
view: CalendarView.month,
maxDate: DateTime(DateTime.now().year,DateTime.now().month +  6,DateTime.now().day,10,0,0),));
}

{% endhighlight %}
{% endtabs %}

## Programmatic date navigation and selection
You can programmatically navigate and select the dates in calendar widget by using the `displayDate` and `selectedDate` properties of controller.

{% tabs %}
{% highlight Dart %}

class MyAppState extends State<MyApp>{
CalendarController _calendarController;
@override
initState(){
_calendarController = CalendarController();
_calendarController.selectedDate = DateTime(2022, 02, 05);
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

## Programmatically change to adjacent dates
By default, the date can be navigated to next and previous views using touch gesture, by swiping the control from right to left and left to right direction. The view can be also changed programmatically using the `Forward` and `Backward` methods available in `CalendarController`.

### Forward
You can use the forward method of controller for viewing the next immediate visible dates in the `SfCalendar`. It will move to next month if the calendar view is month, similarly it will move to next week for week view and next day for day view.

{% tabs %}
{% highlight Dart %}

_calendarController.forward();

{% endhighlight %}
{% endtabs %}

### Backward :
You can use the backward method of controller for viewing the previous immediate visible dates in the `SfCalendar`. It will move to previous month if the calendar view is month, similarly it will move to previous week for week view and previous day for day view.

{% tabs %}
{% highlight Dart %}

_calendarController.backward();

{% endhighlight %}
{% endtabs %}
