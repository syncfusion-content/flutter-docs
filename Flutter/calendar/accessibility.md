---
layout: post
title: Accessibility in Flutter Event Calendar widget | Syncfusion
description: Learn here all about accessibility features of Syncfusion Flutter Calendar (SfCalendar) widget and more.
platform: flutter
control: SfCalendar
documentation: ug
---

# Accessibility in Flutter Event Calendar (SfCalendar)

## Screen reader support

The [SfCalendar](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar-class.html) can easily be accessed by screen readers. Please find the following table to get spoken feedback about the inner element contents of the screen.

### Month view

| View              | Format                       | Example                                       |
|-------------------|------------------------------|-----------------------------------------------|
| Month cell        | EEE, dd/MMMM/yyyy            | Thursday the 2nd of January 2020              |
| No events         | EEE, dd/MMMM/yyyy, No events | Wednesday the 15th of January 2020, No events |
| No selected dates | No selected date             | No selected date                              |
| Week number panel | Week, Week number            | Week 26                                       |        

### TimeSlot view

| View                   | Format                                     | Example                                        |
|------------------------|--------------------------------------------|------------------------------------------------|
| Timeslot view          | hh mm a dd/MMMM/yyyy                       | 11AM the 28th of January 2020                  |
| All day expander icons | Expand all day panelCollapse all day panel | Expand all day sectionCollapse all day section |
| All day expander view  | + appointment Count                        | +3                                             |
| Week number panel      | Week, Week number                          | Week 26                                        |


### Appointments

| View                          | Format                                              | Example                                                                      |
|-------------------------------|-----------------------------------------------------|------------------------------------------------------------------------------|
| Normal appointment            | Subject hh mm a – hh mm a dd/MMMM/yyyy              | Yoga therapy 10AM to 11AM the 29th of January 2020                           |
| Month agenda view appointment | Subject hh mm a – hh mm a dd/MMMM/yyyy              | Plan execution 9AM to 11AM the 23rd January 2020                             |
| All day appointment           | Subject All day                                     | General meeting all day                                                      |
| Spanning appointment          | Subject hh mm a dd/MMMM/yyyy - hh mm a dd/MMMM/yyyy | General meeting 12AM the 23rd of January 2020 – 1AM the 30th of January 2020 |


### Headers

| View                     | Format                  | Example                              |
|--------------------------|-------------------------|--------------------------------------|
| Header                   | MMMM yyyy               | January 2020                         |
| Timeline week header     | dd/MMMM to dd/MMMM/yyyy | 15th of January to 21st January 2020 |
| Timeline workweek header | dd/MMMM to dd/MMMM/yyyy | 16th of January to 20th January 2020 |
| Month view header        | EEE                     | Monday                               |
| TimeSlot view header     | EEE, dd/MMMM/yyyy       | Wednesday the 29th of January 2020   |

## Sufficient contrast

The [SfCalendar](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar-class.html). [theming](https://help.syncfusion.com/flutter/themes) support offers a consistent and standardized look, as well as the ability to set the colors for all UI elements.

The following APIs allow you to customize the colors of the following elements.
* [todayHighlightColor](https://help.syncfusion.com/flutter/calendar/getting-started#today-highlight-color)
* [cellBorderColor](https://help.syncfusion.com/flutter/calendar/getting-started#cell-border-color)
* [backgroundColor](https://help.syncfusion.com/flutter/calendar/getting-started#background-color)
* [selectionDecoration](https://help.syncfusion.com/flutter/calendar/getting-started#selection-decoration)
* [agendasStyle](https://help.syncfusion.com/flutter/calendar/month-view#agenda-view-appearance)
* [monthCellStyle](https://help.syncfusion.com/flutter/calendar/month-view#month-cell-appearance)
* [dayHeaderSettings](https://help.syncfusion.com/flutter/calendar/schedule-view#day-header-customization)
* [weekHeaderSettings](https://help.syncfusion.com/flutter/calendar/schedule-view#week-header-customization)
* [monthHeaderSettings](https://help.syncfusion.com/flutter/calendar/schedule-view#month-header-customization)
* [resourceViewSettings](https://help.syncfusion.com/flutter/calendar/resource-view#customization)

## Large fonts

The [SfCalendar](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar-class.html). font size can be adjusted automatically based on device settings and the font size scaled based on the `MediaQueryData.textScaleFactor`. And also it allows to change the font size of all UI elements in the calendar.
* [appointmentTextStyle](https://help.syncfusion.com/flutter/calendar/appointments#appearance-customization)
* [timeTextStyle](https://help.syncfusion.com/flutter/calendar/timeslot-views#time-text-appearance)
* [dateTextStyle](https://help.syncfusion.com/flutter/calendar/schedule-view#day-header-customization)
* [dayTextStyle](https://help.syncfusion.com/flutter/calendar/schedule-view#day-header-customization)
* [displayNameTextStyle](https://help.syncfusion.com/flutter/calendar/resource-view#customization)

## Keyboard navigation

The following keyboard interactions are supported by the [SfCalendar](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar-class.html).


| Key               | Description                     														                                                                                                             |
|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Up arrow          | Moves selection to the next calendar cell directly above the currently selected time slot                                                                                                          |
| Down arrow        | Moves selection to the next calendar cell directly below the currently selected time slot                                                                                                          |
| Right arrow       | Moves selection to the same time slot on the next day                                                                                                                                              |
| Left arrow        | Moves selection to the same time slot on the previous day                                                                                                                                          |
| Tab               | Focuses the next clickable element, except appointments and cells						                                                                                                             |
| Shift + tab       | Focuses the previous clickable element, except appointment and cells                                                                                                                               |
| Alt + number      | Calendar view changes in the order of day, week, work week, month, timeline and schedule. Also view change will be restricted if it is not mentioned in the allowed views property of the calendar |
| Ctrl + left arrow | To navigate to the previous view                                                                                                                                                                   |
| Ctrl + right arrow| To navigate to the next view                                                                                                                                                                       |
| Page up/down      | Vertically scrolls through the timeslot views                                                                                                                                                      |

### Appointments

| Key               | Description                     														                                                                                                       |
|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tab               | Moves selection to the next appointment from the currently selected appointment. If no appointment is selected, then use the tab traversal and move the focus to the next clickable item     |
| Shift + Tab       | Moves selection to the previous appointment from the currently selected appointment. If no appointment is selected, then use the tab traversal and move the focus to the next clickable item |
