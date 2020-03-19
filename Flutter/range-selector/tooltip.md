---
layout: post
title: Tooltip features in Syncfusion Flutter Range Selector | Syncfusion
description: This section helps to learn about how to add tooltip and its features in range selector for flutter platform
platform: flutter
control: SfRangeSelector
documentation: ug
---

# Tooltip features in range selector

This section helps to learn about how to add tooltip in the range selector.

## Show tooltips

You can enable tooltips for both thumbs. It is used to clearly indicate the current selection of the ranges during interaction. By default, tooltip text is formatted with either `numberFormat` or `dateFormat`.

N>
* Refer the `tooltipTextFormatterCallback` for changing the default tooltip text.
* Refer the `SfRangeSliderThemeData` for customizing the appearance of the tooltip text.

## Tooltip text format

You can format or change the whole tooltip label text. Its arguments contains the following parameters:

* actualValue – either `DateTime` or `double` based on given `values`.
* formattedText – If the actual value is `double`, it is formatted by `numberFormat` and if the actual value is `DateTime`, it is formatted by `dateFormat`.
