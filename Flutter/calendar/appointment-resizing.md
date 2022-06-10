---
layout: post 
title: Appointment resizing in Flutter Event Calendar widget | Syncfusion
description: Learn here all about appointment resizing feature of Syncfusion Flutter Event Calendar (SfCalendar) widget and more.
platform: flutter
control: SfCalendar
documentation: ug
---

# Appointment Resize in Flutter Event Calendar (SfCalendar)

You can quickly change an appointment’s start and end times by resizing the appointment.

## Allow Appointment resize

[allowAppointmentResize](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/allowAppointmentResize.html) property allows to reschedule the appointment by resizing the appointment in desktop platforms.

{% tabs %}
{% highlight dart hl_lines="9" %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
            view: CalendarView.week,
            dataSource: _getCalendarDataSource(),
            allowAppointmentResize: true),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![appointment_resizing](images/appointments/appointment_resize.gif)

>**NOTE**
* It is not applicable for mobile platforms.

## onAppointmentResizeStart

[onAppointmentResizeStart](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/onAppointmentResizeStart.html) callback was called whenever the appointment starts to resizing in SfCalendar. The [AppointmentResizeStartDetails]() arguments contains the resizing appointment, and resource details. 

[appointment](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/AppointmentResizeStartDetails/appointment.html) - Get the resizing appointment details.
[resource](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/AppointmentResizeStartDetails/resource.html) - Get the resource details.

{% tabs %}
{% highlight dart hl_lines="10 17 18 19 20" %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          dataSource: _getCalendarDataSource(),
          allowAppointmentResize: true,
          onAppointmentResizeStart: resizeStart,
        ),
      ),
    ),
  );
}

void resizeStart(AppointmentResizeStartDetails appointmentResizeStartDetails) {
  dynamic appointment = appointmentResizeStartDetails.appointment;
  CalendarResource? resource = appointmentResizeStartDetails.resource;
}

{% endhighlight %}
{% endtabs %}

## onAppointmentResizeUpdate
[onAppointmentResizeUpdate](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/onAppointmentResizeUpdate.html) callback was called whenever the appointment resizing in SfCalendar. The [AppointmentResizeUpdateDetails](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/AppointmentResizeUpdateDetails-class.html) arguments contains the resizing appointment, resizing time, resizing offset and resource details. 

[appointment](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/AppointmentResizeUpdateDetails/appointment.html) - Get the resize appointment.
[resizingTime](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/AppointmentResizeUpdateDetails/resizingTime.html) - Get the resize appointment time.
[resizingOffset](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/AppointmentResizeUpdateDetails/resizingOffset.html) - Get the offset value.
[resource](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/AppointmentResizeUpdateDetails/resource.html) - Get the resource details.

{% tabs %}
{% highlight dart hl_lines="10 17 18 19 20 21 22" %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          dataSource: _getCalendarDataSource(),
          allowAppointmentResize: true,
          onAppointmentResizeUpdate: resizeUpdate,
        ),
      ),
    ),
  );
}

void resizeUpdate(AppointmentResizeUpdateDetails appointmentResizeUpdateDetails) {
  dynamic appointment = appointmentResizeUpdateDetails.appointment;
  DateTime? resizingTime = appointmentResizeUpdateDetails.resizingTime;
  Offset? resizingOffset = appointmentResizeUpdateDetails.resizingOffset;
  CalendarResource? resourceDetails = appointmentResizeUpdateDetails.resource;
}

{% endhighlight %}
{% endtabs %}

## onAppointmentResizeEnd
[onAppointmentResizeEnd](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/onAppointmentResizeEnd.html) callback was called whenever the appointment resizing end in the SfCalendar. The [AppointmentResizeEndDetails](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/AppointmentResizeEndDetails-class.html) arguments contains the resized appointment, start time, end time and resource details. 

[appointment](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/AppointmentResizeEndDetails/appointment.html) - Get the resized appointment details.
[startTime](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/AppointmentResizeEndDetails/startTime.html) -  Get the start time.
[endTime](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/AppointmentResizeEndDetails/endTime.html) - Get the end time.
[resource](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/AppointmentResizeEndDetails/resource.html) - Get the resource details.

{% tabs %}
{% highlight dart hl_lines="10 17 18 19 20 21 22" %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          dataSource: _getCalendarDataSource(),
          allowAppointmentResize: true,
          onAppointmentResizeEnd: resizeEnd,
        ),
      ),
    ),
  );
}

void resizeEnd(AppointmentResizeEndDetails appointmentResizeEndDetails) {
  dynamic appointment = appointmentResizeEndDetails.appointment;
  DateTime? startTime = appointmentResizeEndDetails.startTime;
  DateTime? endTime = appointmentResizeEndDetails.endTime;
  CalendarResource? resourceDetails = appointmentResizeEndDetails.resource;
}

{% endhighlight %}
{% endtabs %}