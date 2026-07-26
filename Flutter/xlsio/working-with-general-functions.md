---
layout: post
title: Working with General Function Formulas | Syncfusion Flutter XlsIO
description: Learn how to apply general function formulas and read calculated values in the cells of an Excel worksheet using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with General Function Formulas

General function formulas are the most common Excel functions used to summarize numeric data. Syncfusion Flutter XlsIO supports the following general functions:

* [SUM](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-general-functions#sum-function) — adds its arguments.
* [AVERAGE](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-general-functions#average-function) — returns the average of its arguments.
* [MAX](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-general-functions#max-function) — returns the largest value in its arguments.
* [MIN](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-general-functions#min-function) — returns the smallest value in its arguments.
* [COUNT](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-general-functions#count-function) — counts how many numbers are in its arguments.

For prerequisites and installation steps, see the [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview). For background on formulas and how to enable calculation, see [Working with Formulas](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-formulas).

N> The code samples in this document use `await workbook.save()`. Always call `workbook.dispose()` after saving to release the XlsIO DOM memory, ideally inside a `try/finally` block. Each function sample calls `enableSheetCalculations()` so the calculated value is available through the `calculatedValue` property of a `Range`.

## Shared sample data

The samples in this page share the following data setup, which writes eight numbers into the worksheet:

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

void populateSampleData(Worksheet sheet) {
  // Column A.
  sheet.getRangeByName('A1').setNumber(10);
  sheet.getRangeByName('A2').setNumber(20);
  sheet.getRangeByName('A3').setNumber(4);
  sheet.getRangeByName('A4').setNumber(12);

  // Column B.
  sheet.getRangeByName('B1').setNumber(2);
  sheet.getRangeByName('B2').setNumber(16);
  sheet.getRangeByName('B3').setNumber(8);
  sheet.getRangeByName('B4').setNumber(11);
}
{% endhighlight %}

## SUM function

The `SUM` function returns the sum of its arguments. Arguments can be individual cells (`SUM(A1, B1)`), ranges (`SUM(A1:A4)`), or a mix of both. Empty cells and text values are ignored.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> sumFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateSampleData(sheet);
  sheet.enableSheetCalculations();

  // Sum of two individual cells.
  sheet.getRangeByName('A6').setFormula('=SUM(A1,B1)');

  // Sum of two ranges.
  sheet.getRangeByName('B6').setFormula('=SUM(A1:A4,B1:B4)');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

`A6` evaluates to `12` (the sum of `A1` and `B1`). `B6` evaluates to `83` (the sum of all eight values).

## AVERAGE function

The `AVERAGE` function returns the arithmetic mean of its arguments. Empty cells and text values are ignored; only numeric values are included in the calculation.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> averageFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateSampleData(sheet);
  sheet.enableSheetCalculations();

  // Average of two individual cells.
  sheet.getRangeByName('A6').setFormula('=AVERAGE(A1,B1)');

  // Average of two ranges.
  sheet.getRangeByName('B6').setFormula('=AVERAGE(A1:A4,B1:B4)');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

`A6` evaluates to `6` (the average of `A1` and `B1`). `B6` evaluates to `10.375` (the average of all eight values).

## MAX function

The `MAX` function returns the largest value in its arguments. Empty cells and text values are ignored.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> maxFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateSampleData(sheet);
  sheet.enableSheetCalculations();

  // Maximum of two individual cells.
  sheet.getRangeByName('A6').setFormula('=MAX(A1,B1)');

  // Maximum of two ranges.
  sheet.getRangeByName('B6').setFormula('=MAX(A1:A4,B1:B4)');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

`A6` evaluates to `10` (the larger of `A1` and `B1`). `B6` evaluates to `20` (the largest of all eight values).

## MIN function

The `MIN` function returns the smallest value in its arguments. Empty cells and text values are ignored.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> minFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateSampleData(sheet);
  sheet.enableSheetCalculations();

  // Minimum of two individual cells.
  sheet.getRangeByName('A6').setFormula('=MIN(A1,B1)');

  // Minimum of two ranges.
  sheet.getRangeByName('B6').setFormula('=MIN(A1:A4,B1:B4)');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

`A6` evaluates to `2` (the smaller of `A1` and `B1`). `B6` evaluates to `2` (the smallest of all eight values).

## COUNT function

The `COUNT` function counts the number of numeric values in its arguments. Empty cells, text values, and logical values are not counted. To count non-empty cells regardless of type, use `COUNTA`; to count cells that meet a condition, use `COUNTIF` or `COUNTIFS`.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> countFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateSampleData(sheet);
  sheet.enableSheetCalculations();

  // Count of two individual cells.
  sheet.getRangeByName('A6').setFormula('=COUNT(A1,B1)');

  // Count of two ranges.
  sheet.getRangeByName('B6').setFormula('=COUNT(A1:A4,B1:B4)');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

`A6` evaluates to `2` (both `A1` and `B1` are numeric). `B6` evaluates to `8` (all eight values are numeric).

## See also

* [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview)
* [Working with Formulas](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-formulas)
* [Working with Cells](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-cells)
* [Range API reference](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Range-class.html)
* [Release notes](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/release-notes)
