---
layout: post
title: Labels features in Syncfusion Flutter Range Selector | Syncfusion
description: This section helps to learn about how to add labels and divisor in the range selector for flutter platform
platform: flutter
control: SfRangeSelector
documentation: ug
---

# Labels and divisors in range selector
This section explains about how to add the labels and divisors in the range selector.

## Show labels

Option to render the labels on given interval. The default value of `showLabels` property is `false`.

N>
* Refer the `numberFormat` and `dateFormat` for formatting the numeric and date labels respectively.
* Refer the `SfRangeSliderThemeData` for customizing the appearance of the labels.

## Show divisors

Option to render the divisors on the track. The default value of `showDivisors` property is `false`. It is a shape which is used to represent the major interval points of the track.

For example, if `min` is 0.0 and `max` is 10.0 and `interval` is 2.0, the range selector will render the divisors at 0.0, 2.0, 4.0 and so on.

## Number format

Formats the numeric labels. The default value of `numberFormat` property is `null`.

## Date format

Formats the date labels. It is mandatory for date `SfRangeSelector`. For date values, the range selector does not have auto interval support. So, it is mandatory to set `interval`, `dateIntervalType`, and `dateFormat` for date values. The default of `dateFormat` property is `null`.

## Label placement

Option to place the labels either between the major ticks or on the major ticks. The default value of `labelPlacement` property is `LabelPlacement.onTicks`.

## Label formatter callback

You can format or change the whole numeric or date label text. Its arguments contains the following parameters:

* actualValue – either `DateTime` or `double` based on given `values`.
* formattedText – If the actual value is `double`, it is formatted by `numberFormat` and if the actual value is `DateTime`, it is formatted by `dateFormat`.
