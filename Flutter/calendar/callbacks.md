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

The [onViewChanged](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/onViewChanged.html) callback triggers when the current view of calendar changed, that is view swiped to previous/next view, calendar view switched to another calendar view.

* [visibleDates](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/ViewChangedDetails/visibleDates.html) - returns the current view visible dates collection.

{% tabs %}
{% highlight dart hl_lines="8 9 10" %}

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

The [onTap](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/onTap.html) callback triggers whenever the calendar is tapped.

* [date](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarTouchDetails/date.html) - returns the selected date.
* [appointments](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarTouchDetails/appointments.html) - returns the selected appointments.
* [targetElement](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarTouchDetails/targetElement.html) - returns the element tapped.
* [resource](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarTouchDetails/resource.html) - returns the tapped resource.

{% tabs %}
{% highlight dart hl_lines="8 9 10 11 12" %}

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
* The [onTap](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/onTap.html) and [onLongPress](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/onLongPress.html) callbacks are not applicable for pop-ups like allowedViews and date picker in the calendar header.

## Calendar details callback

Return calendar details based on the given offset passed through argument by using the [getCalendarDetailsAtOffset](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarController/getCalendarDetailsAtOffset.html) method.

* [date](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarTouchDetails/date.html) - returns the date based on the given offset.
* [appointments](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarTouchDetails/appointments.html) - returns the appointments based on the given offset.
* [targetElement](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarTouchDetails/targetElement.html) - returns the calendar element based on the given offset.
* [resource](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarTouchDetails/resource.html) - returns the resource based on the given offset.

{% tabs %}
{% highlight dart hl_lines="6 7 8 9 10 11 12 13 14 15 16" %}

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
            ),
          ),
        ),
  );
}

{% endhighlight %}
{% endtabs %}

## Long press callback
The [onLongPress](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/onLongPress.html) callback is called, whenever the [SfCalendar](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar-class.html). elements are long pressed on view.

The long-pressed date, appointments, and element details when the long-press action performed on element available in the [CalendarLongPressDetails](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarLongPressDetails-class.html).

* [date](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarTouchDetails/date.html) - returns the long-pressed date.
* [appointments](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarTouchDetails/appointments.html) - returns the long-pressed appointments.
* [targetElement](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarTouchDetails/targetElement.html) - returns the long-pressed calendar element.
* [resource](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarTouchDetails/resource.html) - returns the long-pressed calendar resource.

{% tabs %}
{% highlight dart hl_lines="8 9 10 11 12" %}

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
* [How to get visible dates details from the flutter event calendar (SfCalendar)](https://support.syncfusion.com/kb/article/9574/how-to-get-visible-dates-details-from-the-flutter-calendar)
* [How to get Datetime details while tapping the Flutter event calendar elements](https://support.syncfusion.com/kb/article/9611/how-to-get-datetime-details-while-tapping-the-flutter-calendar)
* [How to handle the long press action on date selection in the Flutter event calendar (SfCalendar)?](https://support.syncfusion.com/kb/article/10497/how-to-handle-the-long-press-action-on-date-selection-in-the-flutter-calendar)