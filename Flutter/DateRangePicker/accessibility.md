---
layout: post
title:  Accessibility in Flutter Date Range Picker widget | Syncfusion
description: Learn here all about Accessibility feature of Syncfusion Flutter Date Range Picker (SfDateRangePicker) widget and more.
platform: flutter
control: SfDateRangePicker
documentation: ug
---

# Accessibility in Flutter DateRangePicker (SfDateRangePicker)

The `SfDateRangePicker` can easily be accessed by screen readers. Please find the following table  for inner elements.

## Month view

| View                                                              | Format                           | Example                                  |
|-------------------------------------------------------------------|----------------------------------|------------------------------------------|
| Month cell                                                        | EEE, dd/MMMM/yyyy                | Thursday the 2nd of January 2020         |
| Month header                                                      | MMMM yyyy                        | January 2020                             |
| View header                                                       | EEE                              | Monday                                   |
| Disabled cells (Enable dates in past, dates exceed min/max dates) | EEE, dd/MMMM/yyyy, Disabled date | Friday, 31st January 2020, Disabled date |
| Blackout date                                                     | EEE, dd/MMMM/yyyy, blackout date | 6th February 2020, Blackout date         |

## Year view

| View                                                             | Format                   | Example                      |
|------------------------------------------------------------------|--------------------------|------------------------------|
| Year cell                                                        | MMMM yyyy                | January 2020                 |
| Header                                                           | yyyy                     | 2020                         |
| Disabled cell (Enable dates in past, dates exceeds min/max date) | MMMM yyyy, Disabled cell | December 2019, Disabled cell |

## Decade view

| View                                                             | Format              | Example            |
|------------------------------------------------------------------|---------------------|--------------------|
| Header                                                           | yyyy - yyyy         | 2020 to 2029       |
| Decade cell                                                      | yyyy                | 2020               |
| Disabled cell (Enable dates in past, dates exceeds min/max date) | yyyy, Disabled cell | 2019 Disabled cell |

## Century view

| View                                                             | Format      | Example                     |
|------------------------------------------------------------------|-------------|-----------------------------|
| Header                                                           | yyyy - yyyy | 2020 to 2029                |
| Century cell                                                     | yyyy - yyyy | 2020 to 2029                |
| Disabled cell (Enable dates in past, dates exceeds min/max date) | yyyy - yyyy | 2010 to 2019, Disabled cell |

## Navigation arrows

| View                      | Format | Example         |
|---------------------------|--------|-----------------|
| Forward navigation arrow  | >      | Forward button  |
| Backward navigation arrow | <      | Backward button |
