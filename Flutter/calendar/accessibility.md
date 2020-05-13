---
layout: post
title: Accessibility of Syncfusion Flutter Calendar | Scheduler
description: Learn about the accessibility support in Syncfusion Flutter Calendar (SfCalendar) widget  | Scheduler
platform: flutter
control: SfCalendar
documentation: ug
---

# Accessibility with Flutter Calendar (SfCalendar)
The `SfCalendar` can easily be accessed by screen readers. Please find the following table  for inner elements.

## Month view

| View              | Format                       | Example                                       |
|-------------------|------------------------------|-----------------------------------------------|
| Month cell        | EEE, dd/MMMM/yyyy            | Thursday the 2nd of January 2020              |
| No events         | EEE, dd/MMMM/yyyy, No events | Wednesday the 15th of January 2020, No events |
| No selected dates | No selected date             | No selected date                              |                                               

## TimeSlot view

| View                   | Format                                     | Example                                        |
|------------------------|--------------------------------------------|------------------------------------------------|
| Timeslot view          | hh mm a dd/MMMM/yyyy                       | 11AM the 28th of January 2020                  |
| All day expander icons | Expand all day panelCollapse all day panel | Expand all day sectionCollapse all day section |
| All day expander view  | + appointment Count                        | +3                                             |


## Appointments

| View                          | Format                                              | Example                                                                      |
|-------------------------------|-----------------------------------------------------|------------------------------------------------------------------------------|
| Normal appointment            | Subject hh mm a – hh mm a dd/MMMM/yyyy              | Yoga therapy 10AM to 11AM the 29th of January 2020                           |
| Month agenda view appointment | Subject hh mm a – hh mm a dd/MMMM/yyyy              | Plan execution 9AM to 11AM the 23rd January 2020                             |
| All day appointment           | Subject All day                                     | General meeting all day                                                      |
| Spanning appointment          | Subject hh mm a dd/MMMM/yyyy - hh mm a dd/MMMM/yyyy | General meeting 12AM the 23rd of January 2020 – 1AM the 30th of January 2020 |


## Headers

| View                     | Format                  | Example                              |
|--------------------------|-------------------------|--------------------------------------|
| Header                   | MMMM yyyy               | January 2020                         |
| Timeline week header     | dd/MMMM to dd/MMMM/yyyy | 15th of January to 21th January 2020 |
| Timeline workweek header | dd/MMMM to dd/MMMM/yyyy | 16th of January to 20th January 2020 |
| Month view header        | EEE                     | Monday                               |
| TimeSlot view header     | EEE, dd/MMMM/yyyy       | Wednesday the 29th of January 2020   |
