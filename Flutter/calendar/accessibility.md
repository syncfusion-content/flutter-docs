---
layout: post
title: Accessibility of Syncfusion Flutter Calendar | Calendar
description: Learn about the accessibility support in Syncfusion Flutter Calendar widget
platform: flutter
control: SfCalendar
documentation: ug
---

# Accessibility
The `SfCalendar` can easily be accessed by screen readers. Please find the following table  for inner elements.

## Month view
| View                       | Format                                              | Example                                                                      |
|--------------------------------|----------------------------------------------|-----------------------------------------------------------------|
| Month cell | EEE, dd/MMMM/yyyy| Thursday the 2nd of January 2020 |
| Month header | MMMM yyyy | January 2020 |
| View header | EEE | Monday |
| Agenda view appointment | Subject hh mm a – hh mm a dd/MMMM/yyyy | Plan execution 9AM to 11AM the 23rd January 2020                            |
| All day appointment| Subject All day| General meeting all day|
| Spanning appointment| Subject hh mm a dd/MMMM/yyyy - hh mm a dd/MMMM/yyyy | General meeting 12AM the 23rd of January 2020 – 1AM the 30th of January 2020 |
| No events| EEE, dd/MMMM/yyyy, No events| Wednesday the 15th of January 2020, No events|
| No selected date| No selected date | No selected date|

## TimeSlot view
| View                   | Format                                              | Example                                                                      |
|------------------------|-----------------------------------------------------|------------------------------------------------------------------------------|
| Timeslotview| hh mm a dd/MMMM/yyyy | 11AM the 28th of January 2020 |
| Appointment | Subject hh mm a – hh mm a dd/MMMM/yyyy  | Yoga therapy 10AM to 11AM the 29th of January 2020                           |
| Header | MMMM yyyy | January 2020|
| View header | EEE, dd/MMMM/yyyy| Wednesday the 29th of January 2020|
| All day appointment | Subject All day| Plan execution all day |
| Spanning appointment | Subject hh mm a dd/MMMM/yyyy - hh mm a dd/MMMM/yyyy | General meeting 12AM the 23rd of January 2020 – 1AM the 30th of January 2020 |
| All day expander icons | Expand all day panelCollapse all day panel| Expand all day sectionCollapse all day section                               |
| All day expander view | + appointment Count | +3 |
