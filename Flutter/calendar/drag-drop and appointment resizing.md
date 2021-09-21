---
layout: post 
title: Drag and drop, appointment resizing in Flutter Event Calendar widget | Syncfusion
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

_AppointmentDataSource _getCalendarDataSource() {
  List<Appointment> appointments = <Appointment>[];
  appointments.add(Appointment(
    startTime: DateTime.now(),
    endTime: DateTime.now().add(Duration(minutes: 10)),
    subject: 'Meeting',
    color: Colors.blue,
    startTimeZone: '',
    endTimeZone: '',
  ));

  return _AppointmentDataSource(appointments);
}

{% endhighlight %}
{% endtabs %}

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
  var appointment = appointmentDragStartDetails.appointment;
  var resource = appointmentDragStartDetails.resource;
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
  var appointment = appointmentDragUpdateDetails.appointment;
  var draggingTime = appointmentDragUpdateDetails.draggingTime;
  var draggingOffset = appointmentDragUpdateDetails.draggingPosition;
  var resource = appointmentDragUpdateDetails.sourceResource;
  var targetResource = appointmentDragUpdateDetails.targetResource;
}

{% endhighlight %}
{% endtabs %}

## onDragEnd

[onDragEnd]() callback called when the dragging appointment is dropped in the SfCalendar. The [AppointmentDragEndDetails]() arguments contains the dropped appointment, dropping time, source and target resource details. 

[Appointment] - Get the dragged appointment details. 
[Drapping time] - Get the resource details.
[Resource] - Get the resource details.
[Target resource] - Get the target resource details.

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
  var appointment = appointmentDragUpdateDetails.appointment;
  var draggingTime = appointmentDragUpdateDetails.draggingTime;
  var draggingOffset = appointmentDragUpdateDetails.draggingPosition;
  var resource = appointmentDragUpdateDetails.sourceResource;
  var targetResource = appointmentDragUpdateDetails.targetResource;
}

{% endhighlight %}
{% endtabs %}

## Disabling navigation when dragging appointment
Using [allowNavigation]() property can handle the appointment dragging, whether navigate to next/previous view or not while dragging the appointment to the endpoint of the current view in calendar. Default value of the [allowNavigation]() property is true and calendar will navigate to next/previous view when dragging the appointment to the endpoint of the current view.

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
Using [allowScroll]() property you can handle the appointment dragging, whether scrolling (below/above) the calendar or not while dragging the appointment to the endpoint of the current view in Calendar. Default value of the [allowScroll]() property is true.

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
              timeIndicatorStyle: TextStyle(backgroundColor: Colors.red)),
        ),
      ),
    ),
  );
}
	
{% endhighlight %}
{% endtabs %}

## Appointment resize
[allowAppointmentResize]() property allows to reschedule the appointment by resizing the appointment in web view.

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
		  allowAppointmentResize: true
        ),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

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
  var appointment=appointmentResizeStartDetails.appointment;
  var resource = appointmentResizeStartDetails.resource;
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
  var appointment = appointmentResizeUpdateDetails.appointment;
  var resizingTime = appointmentResizeUpdateDetails.resizingTime;
  var resizingOffset = appointmentResizeUpdateDetails.resizingOffset;
  var resourceDetails = appointmentResizeUpdateDetails.resource;
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
  var appointment = appointmentResizeEndDetails.appointment;
  var startTime = appointmentResizeEndDetails.startTime;
  var endTime = appointmentResizeEndDetails.endTime;
  var resourceDetails = appointmentResizeEndDetails.resource;
}

{% endhighlight %}
{% endtabs %}