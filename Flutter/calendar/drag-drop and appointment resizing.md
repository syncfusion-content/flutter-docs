---
layout: post 
title: Drag and drop, resizing in Flutter Event Calendar widget | Syncfusion
description: Learn here all about Drag and drop and appointment resizing feature of Syncfusion Flutter Event Calendar (SfCalendar) widget and more.
platform: flutter
control: SfCalendar
documentation: ug
---

# Appointment Drag and Drop in Flutter Event Calendar (SfCalendar)

Appointments can be rescheduled using the drag and drop operation. To perform drag-and-drop operations within the calendar, enable the [allowDragAndDrop]() property of SfCalendar.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
            view: CalendarView.week,
            dataSource: _getCalendarDataSource(),
            allowDragAndDrop: true
        ),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![drag_and_drop](images/appointments/dragdrop.gif)

>**NOTE**
* It is not applicable for month view in mobile platform.

## onDragStart

[onDragStart]() callback was called whenever the appointment starts to drag in the SfCalendar. The [AppointmentDragStartDetails]() arguments contains the dragging appointment and associated resource details. 

[Appointment]() - Get the dragged appointment details. 
[Resource]() - Get the resource details.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          dataSource: _getCalendarDataSource(),
		  allowDragAndDrop: true,
		  onDragStart: dragStart,
        ),
      ),
    ),
  );
}

void dragStart(AppointmentDragStartDetails appointmentDragStartDetails) {
  dynamic appointment = appointmentDragStartDetails.appointment;
  CalendarResource? resource = appointmentDragStartDetails.resource;
}

{% endhighlight %}
{% endtabs %}

## onDragUpdate

[onDragUpdate]() callback was called whenever the appointment is dragging in the SfCalendar. The [AppointmentDragUpdateDetails]() arguments contains the dragging appointment, dragging time, dragging offset, source resource and target resource details. 

[Appointment]() - Get the dragged appointment details. 
[Dragging time]() - Get the resource details.
[Dragging offset]() - Get the drag position.
[SourceResource]() - Get the source resource details.
[Target resource]() - Get the resource details.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          dataSource: _getCalendarDataSource(),
		  allowDragAndDrop: true,
		  onDragUpdate: dragUpdate,
        ),
      ),
    ),
  );
}

void dragUpdate(AppointmentDragUpdateDetails appointmentDragUpdateDetails) {
  dynamic appointment = appointmentDragUpdateDetails.appointment;
  DateTime? draggingTime = appointmentDragUpdateDetails.draggingTime;
  Offset> draggingOffset = appointmentDragUpdateDetails.draggingPosition;
  CalendarResource? sourceResource = appointmentDragUpdateDetails.sourceResource;
  CalendarResource? targetResource = appointmentDragUpdateDetails.targetResource;
}

{% endhighlight %}
{% endtabs %}

## onDragEnd

[onDragEnd]() callback called when the dragging appointment is dropped in the SfCalendar. The [AppointmentDragEndDetails]() arguments contains the dropped appointment, dropping time, source and target resource details. 

[Appointment]() - Get the dragged appointment details. 
[Drapping time]() - Get the resource details.
[Resource]() - Get the resource details.
[Target resource]() - Get the target resource details.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          dataSource: _getCalendarDataSource(),
		  allowDragAndDrop: true,
		  onDragEnd: dragEnd,
        ),
      ),
    ),
  );
}

void dragEnd(AppointmentDragEndDetails appointmentDragEndDetails) {
  dynamic appointment = appointmentDragEndDetails.appointment!;
  CalendarResource? sourceResource = appointmentDragEndDetails.sourceResource;
  CalendarResource? targetResource = appointmentDragEndDetails.targetResource;
  DateTime? draggingTime = appointmentDragEndDetails.droppingTime;
}

{% endhighlight %}
{% endtabs %}

## Disabling navigation when dragging appointment

You can restrict the dragging appointment navigation to the next/previous view when the appointment reaches the start/end point of the current view in calendar by using the [allowNavigation]() property of `DragDropSettings`. Default value of `allowNavigation` property is true.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          dataSource: _getCalendarDataSource(),
          allowDragAndDrop: true,
          dragAndDropSettings: DragAndDropSettings(
              allowNavigation: true),
        ),
      ),
    ),
  );
}
	
{% endhighlight %}
{% endtabs %}

## Disabling scroll when dragging appointment

You can restrict the timeslot views auto scroll when the appointment reaches the start/end point of the view port in the timeslot views of calendar by using the [allowScroll]() property of [DragDropSettings]().

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          dataSource: _getCalendarDataSource(),
          allowDragAndDrop: true,
          dragAndDropSettings: DragAndDropSettings(
              allowScroll: true),
        ),
      ),
    ),
  );
}
	
{% endhighlight %}
{% endtabs %}

## Disabling dragging time indicator
[showTimeIndicator]() - Using this property can handle the time indicator whether it should visible or not, which shows the dragged appointment current position time in time text slots. Default value of the [ShowTimeIndicator]() property is true. Also you can set the time indicator style and format by using [indicatorTimeFormat]() and [timeIndicatorStyle]().

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          dataSource: _getCalendarDataSource(),
          allowDragAndDrop: true,
          dragAndDropSettings: DragAndDropSettings(
              indicatorTimeFormat: 'hh:mm',
              showTimeIndicator: true,
              timeIndicatorStyle: TextStyle(backgroundColor: Colors.red),
              autoNavigateDelay: Duration(seconds: 1)),
        ),
      ),
    ),
  );
}
	
{% endhighlight %}
{% endtabs %}

## Appointment resize
[allowAppointmentResize]() property allows to reschedule the appointment by resizing the appointment in desktop platforms.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          dataSource: _getCalendarDataSource(),
		  allowAppointmentResize: true
        ),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![appointment_resizing](images/appointments/appointment_resize.gif)

>**NOTE**
* It is not applicable for mobile platforms.

### onAppointmentResizeStart
[onAppointmentResizeStart]() callback was called whenever the appointment starts to resizing in SfCalendar. The [AppointmentResizeStartDetails]() arguments contains the resizing appointment, and resource details. 
[Resizing appointment]() - Get the resizing appointment details.
[Resource]() - Get the resource details.

{% tabs %}
{% highlight Dart %}

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
  dynamic appointment=appointmentResizeStartDetails.appointment;
  CalendarResource? resource = appointmentResizeStartDetails.resource;
}

{% endhighlight %}
{% endtabs %}

### onAppointmentResizeUpdate
[onAppointmentResizeUpdate]() callback was called whenever the appointment resizing in SfCalendar. The [onAppointmentResizeUpdate]() arguments contains the resizing appointment, resizing time, resizing offset and resource details. 

[Resizing appointment]() - Get the resize appointment.
[Resizing time]() - Get the resize appointment time.
[Resizing offset]() - Get the offset value.
[Resource details]() - Get the resource details.

{% tabs %}
{% highlight Dart %}

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

### onAppointmentResizeEnd
[onAppointmentResizeEnd]() callback was called whenever the appointment resizing end in the SfCalendar. The [onAppointmentResizeEnd]()  arguments contains the resized appointment, start time, end time and resource details. 

[Resized appointment]() - Get the resized appointment details.
[Start time]() -  Get the start time.
[End time]() - Get the end time.
[Resource details]() - Get the resource details.

{% tabs %}
{% highlight Dart %}

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