---
layout: post
title: Tick features in Syncfusion Flutter Range Selector | Syncfusion
description: This section helps to learn about how to add major and minor ticks in the range selector for flutter platform
platform: flutter
control: SfRangeSelector
documentation: ug
---

# Ticks features in range selector

This section helps to learn about how to add major and minor ticks in the range selector.

## Show major ticks

You can enable the major ticks on the track. It is a shape which is used to represent the major interval points of the track. The default value of `showTicks` property is `false`.

For example, if `min` is 0.0 and `max` is 10.0 and `interval` is 2.0, the range selector will render the major ticks at 0.0, 2.0, 4.0 and so on.

N> Refer the `tickShape` and `SfRangeSliderThemeData` for customizing the major tick’s visual appearance.

## Show minor ticks

Represents the number of smaller ticks between two major ticks. For example, if `min` is 0.0 and `max` is 10.0 and `interval` is 2.0, the range selector will render the major ticks at 0.0, 2.0, 4.0 and so on. If `minorTicksPerInterval` is 1, then smaller ticks will be rendered on 1.0 and 3.0 and so on.

I> The default value of `minorTicksPerInterval` property is null. Must be greater than 0.

N>
* Refer the `showTicks` to know about the rendering of major ticks at given interval.
* Refer the `minorTickShape` and `SfRangeSliderThemeData` for customizing the minor tick’s visual appearance.
