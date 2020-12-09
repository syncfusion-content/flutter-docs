---
layout: post
title: Builders in the Flutter Calendar | Scheduler | Syncfusion
description: Learn about the builders in Syncfusion Flutter Calendar and assigning custom widgets to calendar through builders
platform: flutter
control: SfCalendar
documentation: ug
---

# Builders in flutter calendar
The calendar allows you to create a responsive UI with conditions based on a widget’s details, to design and create your custom view to the month cells and month header of schedule view in the calendar.

The calendar has two builders to create and assign your custom view:
* Month cell builder
* Schedule view month header builder

## Month cell builder
The [MonthCellBuilder](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/MonthCellBuilder.html) allows you to design your custom view and assign the view to the month cells of the calendar by returning an appropriate widget in the [monthCellBuilder](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/monthCellBuilder.html) of [SfCalendar](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar-class.html).

[MonthCellDetails](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/MonthCellDetails-class.html) - returns the details of the month cell.

`date` - returns the month cell date.
`appointments` - returns the month cell appointments.
`visibleDates` - returns the current view visible dates.
`bounds` - returns the month cell bounds.


{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
        body: SfCalendar(
            view: CalendarView.month,
            monthCellBuilder:
                (BuildContext buildContext, MonthCellDetails details) {
              final Color backgroundColor =
              _getMonthCellBackgroundColor(details.date);
              final Color defaultColor = model.themeData != null &&
                  model.themeData.brightness == Brightness.dark
                  ? Colors.black54
                  : Colors.white;
              return Container(
                decoration: BoxDecoration(
                    color: backgroundColor,
                    border: Border.all(color: defaultColor, width: 0.5)),
                child: Center(
                  child: Text(
                    details.date.day.toString(),
                    style: TextStyle(
                        color: _getCellTextColor(backgroundColor)),
                  ),
                ),
              );
            },
            showDatePickerButton: true,
            monthViewSettings: MonthViewSettings(
              showTrailingAndLeadingDates: false,
            )),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Month cell builder](images/builder/month_cell_builder.png)

## Schedule view month header builder

You can design your custom view and assign this view to the month header of a schedule view in the calendar by returning an appropriate widget using the [scheduleViewMonthHeaderBuilder](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/scheduleViewMonthHeaderBuilder.html) in the `SfCalendar`.

[ScheduleViewMonthHeaderDetails](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/ScheduleViewMonthHeaderDetails-class.html) - returns the required details of the schedule view month header.

`date` - returns the header date.
`bounds` - returns the header bounds.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: SfCalendar(
          view: CalendarView.schedule,
          dataSource: _calendarDataSource,
          scheduleViewMonthHeaderBuilder: (BuildContext buildContext,
              ScheduleViewMonthHeaderDetails details) {
            final String monthName = _getMonthDate(details.date.month);
            return Stack(
              children: [
                Image(
                    image: ExactAssetImage('images/' + monthName + '.png'),
                    fit: BoxFit.cover,
                    width: details.bounds.width,
                    height: details.bounds.height),
                Positioned(
                  left: 55,
                  right: 0,
                  top: 20,
                  bottom: 0,
                  child: Text(
                    monthName + ' ' + details.date.year.toString(),
                    style: TextStyle(fontSize: 18),
                  ),
                )
              ],
            );
          },
          showDatePickerButton: true),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Schedule view header builder](images/builder/schedule_view_month_header_builder.png)