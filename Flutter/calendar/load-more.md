---
layout: post 
title: Load more support in Syncfusion Flutter Calendar
description: Learn about loading more appointments on-demand lazily with an intuitive UI with Syncfusion Flutter Calendar.
platform: flutter
control: SfCalendar
documentation: ug
---

# Load more in flutter calendar

SfCalendar provides the support to display an interactive view when the calendar view changed, or the schedule view reaches its start/end offset. You can use the [loadMoreWidgetBuilder](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/loadMoreWidgetBuilder.html) builder to display the view while loading appointments in the calendar.

## Building load more widget

Build your own custom widget, that will be displayed as a loading indicator in calendar when the calendar view changes and in Calendar schedule view, the loading indicator will be displayed when it reaches the start or bottom position to load more appointments.

{% tabs %}
{% highlight Dart %}

return SfCalendar(
        controller: calendarController,
        dataSource: calendarDataSource,
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
                  child: CircularProgressIndicator(
                      valueColor: AlwaysStoppedAnimation(Colors.blue)));
            },
          );
        },
        monthViewSettings: MonthViewSettings(
            appointmentDisplayMode: MonthAppointmentDisplayMode.appointment,
            appointmentDisplayCount: 4),
        timeSlotViewSettings: TimeSlotViewSettings(
            minimumAppointmentDuration: const Duration(minutes: 60)));

{% endhighlight %}
{% endtabs %}

## Load appointments

Update the appointments on demand, when the loading indicator displaying in calendar by using the `handleLoadMore` method in the `CalendarDataSource`, which allows to add the appointments to the data source, update the data source and notify the listener to update the appointment on view.

{% tabs %}
{% highlight Dart %}

class _MeetingDataSource extends CalendarDataSource {
  _MeetingDataSource(List<Appointment> source) {
    appointments = source;
  }

  @override
  Future<void> handleLoadMore(DateTime startDate, DateTime endDate) async {
    await Future.delayed(Duration(seconds: 1));
    final List<Appointment> meetings = <Appointment>[];
    DateTime date = DateTime(startDate.year, startDate.month, startDate.day);
    final DateTime appEndDate =
        DateTime(endDate.year, endDate.month, endDate.day, 23, 59, 59);
    while (date.isBefore(appEndDate)) {
      final List<Appointment>? data = _dataCollection[date];
      if (data == null) {
        date = date.add(Duration(days: 1));
        continue;
      }

      for (final Appointment meeting in data) {
        if (appointments!.contains(meeting)) {
          continue;
        }

        meetings.add(meeting);
      }
      date = date.add(Duration(days: 1));
    }

    appointments!.addAll(meetings);
    notifyListeners(CalendarDataSourceAction.add, meetings);
  }
}

{% endhighlight %}
{% endtabs %}

![loadMoreWidgetBuilder](images/load-more/loadmore.gif)

You can get the complete load more sample from [here](https://github.com/SyncfusionExamples/lazily-loading-events-flutter-calendar).

>**NOTE**
* This callback will be called after the `onViewChanged` callback.
* The widget returned from this builder will be removed from the SfCalendar when the `CalendarDataSource.notifyListeners` is called.
