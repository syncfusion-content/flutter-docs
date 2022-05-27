---
layout: post
title: Schedule view in Flutter Event Calendar widget | Syncfusion
description: Learn here all about Schedule view feature of Syncfusion Flutter Event Calendar (SfCalendar) widget and more.
platform: flutter
control: SfCalendar
documentation: ug
---

# Schedule view in Flutter Event Calendar (SfCalendar)

The `schedule` view of SfCalendar shows a list of scheduled appointments grouped by week, between min, and max dates, by default displaying the appointments from the current date. If the `DataSource` property of `SfCalendar` is null then the schedule view will display the month, week, and date headers alone in the view.

The schedule view display two different UI for mobile and web, for mobile it will display the month header, week header, and date header but for the web, it will display the appointments alone in the view.

![Schedule view in Flutter event calendar](images/scheduleview/Schedule-view.png)

>**NOTE** 
* If the web view width is less than `767` the calendar will render the mobile schedule UI for the web. 

## Appointment item height
You can customize the height of an appointment in a schedule view by using the [appointmentItemHeight](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/ScheduleViewSettings/appointmentItemHeight.html) property of [ScheduleViewSettings](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/ScheduleViewSettings-class.html).

{% tabs %}
{% highlight dart hl_lines="7" %}

@override
  Widget build(BuildContext context) {
    return Container(
      child: SfCalendar(
        view: CalendarView.schedule,
        scheduleViewSettings: ScheduleViewSettings(
          appointmentItemHeight: 70,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

![Schedule view appointment height customization](images/scheduleview/Schedule_view_appointment_height.png)

## Hide empty weeks
You can hide the weeks that do not have an appointment on it in schedule view, by using the [hideEmptyScheduleWeek](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/ScheduleViewSettings/hideEmptyScheduleWeek.html) property of  `scheduleViewSettings`.

{% tabs %}
{% highlight dart hl_lines="7" %}

@override
  Widget build(BuildContext context) {
    return Container(
      child: SfCalendar(
        view: CalendarView.schedule,
        scheduleViewSettings: ScheduleViewSettings(
          hideEmptyScheduleWeek: true,
        ),
      ),
    );
  }
  
{% endhighlight %}
{% endtabs %}

![Schedule view hide empty agenda weeks](images/scheduleview/Schedule_view_hide-empty_week.png)

## Appointment text customization
The appointment text style of schedule view can be customized by using the [appointmentTextStyle](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/ScheduleViewSettings/appointmentTextStyle.html) property of `scheduleViewSettings`.

{% tabs %}
{% highlight dart hl_lines="7 8" %}

@override
  Widget build(BuildContext context) {
    return Container(
      child: SfCalendar(
        view: CalendarView.schedule,
        scheduleViewSettings: ScheduleViewSettings(
            appointmentTextStyle: TextStyle(
                fontSize: 12, fontWeight: FontWeight.w500, color: Colors.lime)),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

![Schedule view appointment customization](images/scheduleview/Schedule_view_appointment.png)

## Day header customization
The day header can be customized by using the [dayHeaderSettings](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/ScheduleViewSettings/dayHeaderSettings.html) property of `scheduleViewSettings`. 

The [DayHeaderSettings](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/DayHeaderSettings-class.html) contains the properties to customize the day format, width, day text style, and date text style of the day header by using the [dayFormat](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/DayHeaderSettings/dayFormat.html), [width](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/DayHeaderSettings/width.html), [dayTextStyle](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/DayHeaderSettings/dayTextStyle.html), and [dateTextStyle](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/DayHeaderSettings/dateTextStyle.html) of `DayHeaderSettings`.

{% tabs %}
{% highlight dart hl_lines=" 7 8 9 10 11 12 13 14 15 16 17 18 19" %}

  @override
  Widget build(BuildContext context) {
    return Container(
      child: SfCalendar(
        view: CalendarView.schedule,
        scheduleViewSettings: ScheduleViewSettings(
            dayHeaderSettings: DayHeaderSettings(
                dayFormat: 'EEEE',
                width: 70,
                dayTextStyle: TextStyle(
                  fontSize: 10,
                  fontWeight: FontWeight.w300,
                  color: Colors.red,
                ),
                dateTextStyle: TextStyle(
                  fontSize: 20,
                  fontWeight: FontWeight.w300,
                  color: Colors.red,
                ))),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

![Schedule view day header customization](images/scheduleview/Schedule_view_day_header.png)

## Week header customization
The week header can be customized by using the [weekHeaderSettings](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/ScheduleViewSettings/weekHeaderSettings.html) property of `scheduleViewSettings`. 

The [WeekHeaderSettings](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/WeekHeaderSettings-class.html) contains the properties to customize the start and end date format, height, Text alignment, background color, and week text style of the week header by using the [startDateFormat](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/WeekHeaderSettings/startDateFormat.html), [endDateFormat](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/WeekHeaderSettings/endDateFormat.html), [height](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/WeekHeaderSettings/height.html), [textAlign](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/WeekHeaderSettings/textAlign.html), [backgroundColor](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/WeekHeaderSettings/backgroundColor.html), and [weekTextStyle](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/WeekHeaderSettings/weekTextStyle.html) of `WeekHeaderSettings`.

{% tabs %}
{% highlight dart hl_lines="7 8 9 10 11 12 13 14 15 16 17" %}

@override
  Widget build(BuildContext context) {
    return Container(
      child: SfCalendar(
        view: CalendarView.schedule,
        scheduleViewSettings: ScheduleViewSettings(
            weekHeaderSettings: WeekHeaderSettings(
                startDateFormat: 'dd MMM ',
                endDateFormat: 'dd MMM, yy',
                height: 50,
                textAlign: TextAlign.center,
                backgroundColor: Colors.red,
                weekTextStyle: TextStyle(
                  color: Colors.white,
                  fontWeight: FontWeight.w400,
                  fontSize: 15,
                ))),
      ),
    );
  }


{% endhighlight %}
{% endtabs %}

![Schedule view week header customization](images/scheduleview/Schedule_view_week_header.png)

## Month header customization
The month header can be customized by using the [monthHeaderSettings](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/ScheduleViewSettings/monthHeaderSettings.html) property of `scheduleViewSettings`. 

The [MonthHeaderSettings](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/MonthHeaderSettings-class.html) contains the properties to customize the month format, height, text alignment, background color, and month text style of the month header by using the [monthFormat](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/MonthHeaderSettings/monthFormat.html), [height](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/MonthHeaderSettings/height.html), [textAlign](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/MonthHeaderSettings/textAlign.html), [backgroundColor](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/MonthHeaderSettings/backgroundColor.html), and [monthTextStyle](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/MonthHeaderSettings/monthTextStyle.html) of `MonthHeaderSettings`.

{% tabs %}
{% highlight dart hl_lines="6 7 8 9 10 11 12  13 14 15" %}

@override
  Widget build(BuildContext context) {
    return Container(
      child: SfCalendar(
        view: CalendarView.schedule,
        scheduleViewSettings: ScheduleViewSettings(
            monthHeaderSettings: MonthHeaderSettings(
                monthFormat: 'MMMM, yyyy',
                height: 100,
                textAlign: TextAlign.left,
                backgroundColor: Colors.green,
                monthTextStyle: TextStyle(
                    color: Colors.red,
                    fontSize: 25,
                    fontWeight: FontWeight.w400))),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

![Schedule view month header customization](images/scheduleview/Schedule_view_month_header.png)

## See also

* [How do I view schedule in Flutter event calendar (SfCalendar)?](https://www.syncfusion.com/kb/11803/how-do-i-view-schedule-in-flutter-event-calendar-sfcalendar)
* [How to customize the day, week, month header of Schedule view in the Flutter event calendar (SfCalendar)](https://www.syncfusion.com/kb/12178/how-to-customize-the-day-week-month-header-of-schedule-view-in-the-flutter-event-calendar)
* [How to customize the schedule view month header using builder in Flutter event calendar (SfCalendar)](https://www.syncfusion.com/kb/12064/how-to-customize-the-schedule-view-month-header-using-builder-in-flutter-event-calendar)
* [How to customize the appointment height in schedule view of the Flutter event calendar (SfCalendar)](https://www.syncfusion.com/kb/12226/how-to-customize-the-appointment-height-in-schedule-view-of-the-flutter-event-calendar)
