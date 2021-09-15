---
layout: post 
title: Appointments in Flutter Event Calendar widget | Syncfusion
description: Learn here all about Appointments feature of Syncfusion Flutter Event Calendar (SfCalendar) widget and more.
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

class _AppointmentDataSource extends CalendarDataSource {
  _AppointmentDataSource(List<Appointment> source){
   appointments = source; 
  }
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
[Dragging offset]() - 
[Resource]() -
[Target resource]() -

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

Called when the dragging appointment is dropped in the SfCalendar. The [AppointmentDragEndDetails]() arguments contains the dropped appointment, dropping time, source and target resource details. 

[Appointment] - Get the dragged appointment details. 
[Drapping time] - Get the resource details.
[Resource] -
[Target resource] -

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

## Customize the drag and drop settings

Using [dropAndDropSettings]() property of calendar, you can handle the behavior of drag and drop in calendar.

{% tabs %}
{% highlight Dart %}

dragAndDropSettings: DragAndDropSettings(
    allowNavigation: true,
    allowScroll: true,
    indicatorTimeFormat: 'hh:mm',
    showTimeIndicator: true,
    timeIndicatorStyle: TextStyle(backgroundColor: Colors.red)),
	
{% endhighlight %}
{% endtabs %}