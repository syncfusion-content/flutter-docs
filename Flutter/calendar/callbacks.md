---
layout: post
title: Callbacks in Syncfusion Flutter Calendar 
description: Learn about the callbacks in Syncfusion Flutter Calendar and the return values and usage of the callbacks
platform: flutter
control: SfCalendar
documentation: ug
---

# Callbacks
Calendar supports the following two events:

## View changed callback

The [onViewChanged](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/onViewChanged.html) callback triggers when the current view of calendar changed, that is view swiped to previous /next view, calendar view switched to another calendar view.

`visibleDates` - returns the current view visible dates collection.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          onViewChanged: (ViewChangedDetails details) {
            dates = details.visibleDates;
          },
        ),
      ),
    ),
  );
}

{% endhighlight %}

## Calendar tap callback

The [onTapUp](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/onTap.html) callback triggers whenever the calendar tapped.

`date` - returns the selected date.
`appointments` - returns the selected appointments.
‘targetElement` - returns the element tapped.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          onTap: (CalendarTapDetails details) {
            appointment = details.appointments;
            date = details.date;
            element = details.targetElement;
          },
        ),
      ),
    ),
  );
}

{% endhighlight %}

