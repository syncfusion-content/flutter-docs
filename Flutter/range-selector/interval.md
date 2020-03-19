---
layout: post
title: Interval in Syncfusion Flutter Range Selector | Syncfusion
description: This section explains about how to add the interval for numeric and date range selector for flutter platform
platform: flutter
control: SfRangeSelector
documentation: ug
---

# Range selector interval
This section explains about how to add the interval for numeric and date range selector.

## Numeric interval

Splits the range selector into given interval. It is mandatory if labels, major ticks and divisions are needed. The default value of `interval` property is `null`. Must be greater than 0.

For example, if `min` is 0.0 and `max` is 10.0 and `interval` is 2.0, the range selector will render the labels,  major ticks, and divisors at 0.0, 2.0, 4.0 and so on.

N>
* Refer the `showDivisions` to know about the rendering of divisors at given interval.
* Refer the `showTicks` to know about the rendering of major ticks at given interval.
* Refer the `showLabels` to know about the rendering of labels at given interval.

## Date interval

The type of date interval. It can be years to seconds. It is mandatory for date `SfRangeSelector`. The default value of `dateIntervalType` property is `null`.

For date values, the range selector does not have auto interval support. So, it is mandatory to set `interval`, `dateIntervalType`, and `dateFormat` for date values.

For example, if `min` is `DateTime(2000, 01, 01)` and `max` is `DateTime(2005, 01, 01)` and `interval` is `1`, `dateIntervalType` is `DateIntervalType.years`, `dateFormat` is `DateFormat.y()` then the range selector will render the labels,  major ticks, and divisors at 2000, 2001, 2002 and so on.
