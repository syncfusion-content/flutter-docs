---
layout: post
title: Callbacks in Flutter Event Calendar widget | Syncfusion | Scheduler
description: Learn here all about callbacks feature of Syncfusion Flutter Event Calendar (SfCalendar) widget and more.
platform: flutter
control: SfCalendar
documentation: ug
---

# Callbacks in Flutter Event Calendar (SfCalendar)
Calendar supports the [ViewChangedCallback](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/ViewChangedCallback.html) and [CalendarTapCallback](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarTapCallback.html) to interact with Flutter calendar.

## View changed callback

The [onViewChanged](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/onViewChanged.html) callback triggers when the current view of calendar changed, that is view swiped to previous /next view, calendar view switched to another calendar view.

`visibleDates` - returns the current view visible dates collection.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          onViewChanged: (ViewChangedDetails details) {
            List<DateTime> dates = details.visibleDates;
          },
        ),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

>**NOTE**
* Initially, the `onViewChanged` callback would be triggered to load the appointment data on the basis of visible dates.

## Calendar tap callback

The [onTapUp](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/onTap.html) callback triggers whenever the calendar tapped.

`date` - returns the selected date.
`appointments` - returns the selected appointments.
`targetElement` - returns the element tapped.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          onTap: (CalendarTapDetails details) {
            dynamic appointment = details.appointments;
            DateTime date = details.date!;
            CalendarElement element = details.targetElement;
          },
        ),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

>**NOTE**
* For recurrence appointment, the tap details will always return as `Appointment`, even for the custom business object.
* You can`t get the controller.view by using `onTap` callback for allowedViews.
* `onTap` callback not applicable for date selection of the picker in the calendar header.

## Calendar details callback

Return calendar details based on the given offset passed through argument by using the [getCalendarDetailsAtOffset](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarController/getCalendarDetailsAtOffset.html) method.

`date` - returns the date based on the given offset.
`appointments` - returns the appointments based on the given offset.
`targetElement` - returns the calendar element based on the given offset.
`resource` - returns the resource based on the given offset.

{% tabs %}
{% highlight Dart %}

@override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
          body: MouseRegion(
              onHover: (PointerHoverEvent event) {
                CalendarDetails? details = _calendarController
                    .getCalendarDetailsAtOffset!(event.localPosition);
                if (details!.targetElement == CalendarElement.appointment) {
                  dynamic appointments = details.appointments;
                  final String subject =
                      details.appointments![0].subject.toString();
                  final dynamic startTime = details.appointments![0].startTime;
                  final dynamic endTime = details.appointments![0].endTime;
                }
              },
              child: SfCalendar(
                view: CalendarView.month,
                controller: _calendarController,
                dataSource: _getCalendarDataSource(),
              ))),
    );
  }
}

{% endhighlight %}
{% endtabs %}

## Long press callback
The [onLongPress](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/onLongPress.html) callback is called, whenever the `SfCalendar` elements are long pressed on view.

The long-pressed date, appointments, and element details when the long-press action performed on element available in the [CalendarLongPressDetails](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarLongPressDetails-class.html).

`date` - returns the long-pressed date.
`appointments` - returns the long-pressed appointments.
`targetElement` - returns the long-pressed calendar element.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return MaterialApp(
        home: Scaffold(
            body: Container(
      child: SfCalendar(
        view: CalendarView.week,
        onLongPress: (CalendarLongPressDetails details) {
          DateTime date = details.date!;
          dynamic appointments = details.appointments;
          CalendarElement view = details.targetElement;
        },
      ),
    )));
  }

{% endhighlight %}
{% endtabs %}

>**NOTE**
* For recurrence appointment, the long pressed details will always return as `Appointment`, even for the custom business object.

## See also
* [How to get visible dates details from the flutter event calendar (SfCalendar)](https://www.syncfusion.com/kb/11026/how-to-get-visible-dates-details-from-the-flutter-event-calendar-sfcalendar)
* [How to get Datetime details while tapping the Flutter event calendar elements](https://www.syncfusion.com/kb/10998/how-to-get-datetime-details-while-tapping-the-flutter-event-calendar-elements)
* [How to handle the long press action on date selection in the Flutter event calendar (SfCalendar)?](https://www.syncfusion.com/kb/12121/how-to-handle-the-long-press-action-on-date-selection-in-the-flutter-event-calendar)