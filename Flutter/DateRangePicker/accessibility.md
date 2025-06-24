---
layout: post
title:  Accessibility in Flutter Date Range Picker widget | Syncfusion
description: Learn here all about Accessibility feature of Syncfusion Flutter Date Range Picker (SfDateRangePicker) widget and more.
platform: flutter
control: SfDateRangePicker
documentation: ug
---

# Accessibility in Flutter DateRangePicker (SfDateRangePicker)

## Screen reader support
The `SfDateRangePicker` can easily be accessed by screen readers. Please find the following table to get spoken feedback about the inner element contents of the screen.

### Month view

| View                                                              | Format                           | Example                                  |
|-------------------------------------------------------------------|----------------------------------|------------------------------------------|
| Month cell                                                        | EEE, dd/MMMM/yyyy                | Thursday the 2nd of January 2020         |
| Month header                                                      | MMMM yyyy                        | January 2020                             |
| View header                                                       | EEE                              | Monday                                   |
| Disabled cells (Enable dates in past, dates exceed min/max dates) | EEE, dd/MMMM/yyyy, Disabled date | Friday, 31st January 2020, Disabled date |
| Blackout date                                                     | EEE, dd/MMMM/yyyy, blackout date | 6th February 2020, Blackout date         |
| Week number panel                                                 | Week, Week number                | Week 26                                  |

### Year view

| View                                                             | Format                   | Example                      |
|------------------------------------------------------------------|--------------------------|------------------------------|
| Year cell                                                        | MMMM yyyy                | January 2020                 |
| Header                                                           | yyyy                     | 2020                         |
| Disabled cell (Enable dates in past, dates exceeds min/max date) | MMMM yyyy, Disabled cell | December 2019, Disabled cell |

### Decade view

| View                                                             | Format              | Example            |
|------------------------------------------------------------------|---------------------|--------------------|
| Header                                                           | yyyy - yyyy         | 2020 to 2029       |
| Decade cell                                                      | yyyy                | 2020               |
| Disabled cell (Enable dates in past, dates exceeds min/max date) | yyyy, Disabled cell | 2019 Disabled cell |

### Century view

| View                                                             | Format      | Example                     |
|------------------------------------------------------------------|-------------|-----------------------------|
| Header                                                           | yyyy - yyyy | 2020 to 2029                |
| Century cell                                                     | yyyy - yyyy | 2020 to 2029                |
| Disabled cell (Enable dates in past, dates exceeds min/max date) | yyyy - yyyy | 2010 to 2019, Disabled cell |

### Navigation arrows

| View                      | Format | Example         |
|---------------------------|--------|-----------------|
| Forward navigation arrow  | >      | Forward button  |
| Backward navigation arrow | <      | Backward button |

## Sufficient contrast

The `SfDateRangePicker` [theming](https://help.syncfusion.com/flutter/themes) support offers a consistent and standardized look, as well as the ability to set the colors for all the UI elements.

The following APIs allows you to customize the colors of the following elements.
* [viewHeaderStyle](https://help.syncfusion.com/flutter/daterangepicker/headers#view-header) 
* [headerStyle](https://help.syncfusion.com/flutter/daterangepicker/headers#header-appearance)
* [leadingDatesDecoration](https://help.syncfusion.com/flutter/daterangepicker/customizations#month-cell-customization)
* [trailingDatesDecoration](https://help.syncfusion.com/flutter/daterangepicker/customizations#month-cell-customization)
* [cellDecoration](https://help.syncfusion.com/flutter/daterangepicker/customizations#month-cell-customization)
* [blackoutDatesDecoration](https://help.syncfusion.com/flutter/daterangepicker/customizations#month-cell-customization)
* [specialDatesDecoration](https://help.syncfusion.com/flutter/daterangepicker/customizations#month-cell-customization)
* [weekendDatesDecoration](https://help.syncfusion.com/flutter/daterangepicker/customizations#month-cell-customization)
* [selectionColor](https://help.syncfusion.com/flutter/daterangepicker/customizations#selection-cell-customization)
* [startRangeSelectionColor](https://help.syncfusion.com/flutter/daterangepicker/customizations#selection-cell-customization)
* [endRangeSelectionColor](https://help.syncfusion.com/flutter/daterangepicker/customizations#selection-cell-customization)
* [rangeSelectionColor](https://help.syncfusion.com/flutter/daterangepicker/customizations#selection-cell-customization)
* [yearCellStyle](https://help.syncfusion.com/flutter/daterangepicker/customizations#year-cell-customization)

## Large fonts

The `SfDateRangePicker` font size can be adjusted automatically based on device settings and the font size scaled based on the `MediaQueryData.textScaleFactor`. It also allows you to change the font size of all elements in date range picker.
* [todayTextStyle](https://help.syncfusion.com/flutter/daterangepicker/customizations)
* [leadingDatesTextStyle](https://help.syncfusion.com/flutter/daterangepicker/customizations)
* [trailingDatesTextStyle](https://help.syncfusion.com/flutter/daterangepicker/customizations)
* [disabledDatesTextStyle](https://help.syncfusion.com/flutter/daterangepicker/customizations)
* [textStyle](https://help.syncfusion.com/flutter/daterangepicker/customizations)
* [blackoutDateTextStyle](https://help.syncfusion.com/flutter/daterangepicker/customizations#month-cell-customization)
* [specialDatesTextStyle](https://help.syncfusion.com/flutter/daterangepicker/customizations#month-cell-customization)
* [weekendTextStyle](https://help.syncfusion.com/flutter/daterangepicker/customizations#month-cell-customization)
* [selectionTextStyle](https://help.syncfusion.com/flutter/daterangepicker/customizations#selection-cell-customization)
* [rangeTextStyle](https://help.syncfusion.com/flutter/daterangepicker/customizations#selection-cell-customization)

## Keyboard navigation

The following keyboard interactions are supported by the `SfDateRangePicker`.

| Key                   | Description                     									  					                         |
|-----------------------|----------------------------------------------------------------------------------------------------------------|
| Up arrow              | Selects the same day of the previous week                                                                      |
| Down arrow     		| Selects the same day of the next week                                                                          |
| Right arrow           | Selects the day after                                                                                          |
| Left arrow            | Selects the day before                                                                                         |
| Alt+1                 | Displays month view                                           							                     |
| Alt+2                 | Displays year view                                                                                             |
| Alt+3                 | Displays decade view                                                                                           |
| Alt+4                 | Displays century view                                                                                          |
| Tap                   | Focuses the next clickable element                                                                             |
| Shift + upper arrow   | Selects the same day in previous week to complete the range selection or add the day in the multiple selection |
| Shift + down arrow    | Selects the same day in next week to complete the range selection or add the day in the multiple selection     |
| Shift + left arrow    | Selects the day before to complete the range selection or add the day in the multiple selection                |
| Shift + right arrow   | Selects the day after to complete the range selection or add the day in the multiple selection                 |
| Ctrl  + left arrow    | To navigate to the previous view                                                                               |
| Ctrl  + right arrow   | To navigate to the next view                                                                                   |
