---
layout: post 
title: Load more in Flutter Event Calendar widget | Syncfusion
description: Learn here all about load more feature of Syncfusion Flutter Event Calendar (SfCalendar) widget and more.
platform: flutter
control: SfCalendar
documentation: ug
---

# Load more in Flutter Event Calendar (SfCalendar)

The Calendar provides the support to display an interactive view when the calendar view is changed, or the schedule view reaches its start or end offset. You can use the [loadMoreWidgetBuilder](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/loadMoreWidgetBuilder.html) builder to display the view while loading appointments in the calendar.

## Building load more widget

Build your own custom widget by using the [loadMoreWidgetBuilder](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/loadMoreWidgetBuilder.html) that will be displayed as a loading indicator in the calendar when the calendar view changes, and in the calendar schedule view, the loading indicator will be displayed when it reaches the start or end position to load more appointments.

{% tabs %}
{% highlight dart hl_lines="20 21 22 23 24 25 26 27 28 29 30 31 32 33" %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_calendar/calendar.dart';

void main() {
  runApp(const CalendarApp());
}

class CalendarApp extends StatefulWidget {
  const CalendarApp({super.key});

  @override
  State<CalendarApp> createState() => _CalendarAppState();
}

class _CalendarAppState extends State<CalendarApp> {
  final CalendarController _calendarController = CalendarController();
  late CalendarDataSource _calendarDataSource;
  final List<CalendarView> _allowedViews = <CalendarView>[
    CalendarView.day,
    CalendarView.week,
    CalendarView.workWeek,
    CalendarView.month,
    CalendarView.schedule
  ];

  @override
  void initState() {
    super.initState();
    _calendarDataSource = _getCalendarDataSource();
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: SfCalendar(
          controller: _calendarController,
          dataSource: _calendarDataSource,
          allowedViews: _allowedViews,
          loadMoreWidgetBuilder:
              (BuildContext context, LoadMoreCallback loadMoreAppointments) {
            return FutureBuilder<void>(
              future: loadMoreAppointments(),
              builder: (context, snapShot) {
                return Container(
                    height: _calendarController.view == CalendarView.schedule
                        ? 50
                        : double.infinity,
                    width: double.infinity,
                    alignment: Alignment.center,
                    child: const CircularProgressIndicator(
                        valueColor: AlwaysStoppedAnimation(Colors.blue)));
              },
            );
          },
          monthViewSettings: const MonthViewSettings(
              appointmentDisplayMode: MonthAppointmentDisplayMode.appointment,
              appointmentDisplayCount: 4),
          timeSlotViewSettings: const TimeSlotViewSettings(
              minimumAppointmentDuration: Duration(minutes: 60))),
        ),
      ),
    );
  }
}

{% endhighlight %}
{% endtabs %}

>**NOTE**
* This callback will be called after the [onViewChanged](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/onViewChanged.html) callback.
* The widget returned from this builder will be removed from the SfCalendar when the [CalendarDataSource.notifyListeners](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarDataSourceChangeNotifier/notifyListeners.html) is called.

You can get the complete load more sample from this [link](https://github.com/SyncfusionExamples/lazily-loading-events-flutter-calendar).

## Load appointments

Update the appointments on-demand, when the loading indicator is displaying in the calendar by using the [handleLoadMore](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarDataSource/handleLoadMore.html) method in the [CalendarDataSource](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/CalendarDataSource-class.html), which allows adding the appointments to the data source, update the data source, and notify the listener to update the appointment on view.

{% tabs %}
{% highlight dart hl_lines="3 9 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34" %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_calendar/calendar.dart';

class _MeetingDataSource extends CalendarDataSource {
  _MeetingDataSource(List<Appointment> source) {
    appointments = source;
  }

  @override
  Future<void> handleLoadMore(DateTime startDate, DateTime endDate) async {
    await Future.delayed(const Duration(seconds: 1));
    final List<Appointment> meetings = <Appointment>[];
    DateTime date = DateTime(startDate.year, startDate.month, startDate.day);
    final DateTime appEndDate =
        DateTime(endDate.year, endDate.month, endDate.day, 23, 59, 59);
    while (date.isBefore(appEndDate)) {
      final List<Appointment>? data = _dataCollection[date];
      if (data == null) {
        date = date.add(const Duration(days: 1));
        continue;
      }

      for (final Appointment meeting in data) {
        if (appointments!.contains(meeting)) {
          continue;
        }

        meetings.add(meeting);
      }
      date = date.add(const Duration(days: 1));
    }

    appointments!.addAll(meetings);
    notifyListeners(CalendarDataSourceAction.add, meetings);
  }
}

{% endhighlight %}
{% endtabs %}

![loadMoreWidgetBuilder](images/load-more/loadmore.gif)
