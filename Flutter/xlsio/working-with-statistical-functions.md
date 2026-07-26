---
layout: post
title: Working with Statistical Function Formulas | Syncfusion Flutter XlsIO
description: Learn how to apply statistical function formulas and read calculated values in the cells of an Excel worksheet using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with Statistical Function Formulas

Statistical function formulas aggregate a range of values that satisfy one or more criteria. Syncfusion Flutter XlsIO supports the following statistical functions:

* [AVERAGEIFS](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-statistical-functions#averageifs-function) — returns the average of all cells that meet multiple criteria.
* [MINIFS](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-statistical-functions#minifs-function) — returns the minimum value among cells that meet multiple criteria.
* [MAXIFS](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-statistical-functions#maxifs-function) — returns the maximum value among cells that meet multiple criteria.
* [COUNTIFS](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-statistical-functions#countifs-function) — counts the number of cells that meet multiple criteria.

N> All `*IFS` functions compare the criteria range and the value range position by position. Every range passed to the function must have the same number of rows and columns; otherwise the function returns a `#VALUE!` error. Text comparisons are case-insensitive.

For prerequisites and installation steps, see the [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview). For background on formulas and how to enable calculation, see [Working with Formulas](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-formulas).

N> The code samples in this document use `await workbook.save()`. Always call `workbook.dispose()` after saving to release the XlsIO DOM memory, ideally inside a `try/finally` block. Each function sample calls `enableSheetCalculations()` so the calculated value is available through the `calculatedValue` property of a `Range`.

## Shared sample data

The samples in this page share the following data setup:

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

void populateSampleData(Worksheet sheet) {
  // Column A: category.
  sheet.getRangeByName('A1').setText('Apple');
  sheet.getRangeByName('A2').setText('Grapes');
  sheet.getRangeByName('A3').setText('Apple');
  sheet.getRangeByName('A4').setText('Grapes');
  sheet.getRangeByName('A5').setText('Apple');

  // Column B: amount.
  sheet.getRangeByName('B1').setNumber(58);
  sheet.getRangeByName('B2').setNumber(1200);
  sheet.getRangeByName('B3').setNumber(300);
  sheet.getRangeByName('B4').setNumber(500);
  sheet.getRangeByName('B5').setNumber(1000);

  // Column C: count.
  sheet.getRangeByName('C1').setNumber(2);
  sheet.getRangeByName('C2').setNumber(3);
  sheet.getRangeByName('C3').setNumber(4);
  sheet.getRangeByName('C4').setNumber(2);
  sheet.getRangeByName('C5').setNumber(1);
}
{% endhighlight %}

## AVERAGEIFS function

The `AVERAGEIFS` function returns the average (arithmetic mean) of all cells in a range that meet one or more criteria. Its signature is `AVERAGEIFS(averageRange, criteriaRange1, criteria1, [criteriaRange2, criteria2, ...])`.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> averageIfsFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateSampleData(sheet);
  sheet.enableSheetCalculations();

  // Average of B values where C is greater than 2: (1200 + 300) / 2 = 750.
  sheet.getRangeByName('C6').setFormula(r'=AVERAGEIFS(B1:B5,C1:C5,">2")');

  // Average of B values where A is "Apple": (58 + 300 + 1000) / 3 = 452.67.
  sheet.getRangeByName('C7').setFormula(r'=AVERAGEIFS(B1:B5,A1:A5,"Apple")');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## MINIFS function

The `MINIFS` function returns the minimum value among cells in a range that meet one or more criteria. Its signature is `MINIFS(minRange, criteriaRange1, criteria1, [criteriaRange2, criteria2, ...])`. If no cells match the criteria, the function returns `0`.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> minIfsFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateSampleData(sheet);
  sheet.enableSheetCalculations();

  // Minimum B value where C is greater than 2: min(1200, 300) = 300.
  sheet.getRangeByName('C6').setFormula(r'=MINIFS(B1:B5,C1:C5,">2")');

  // Minimum B value where A is "Apple": min(58, 300, 1000) = 58.
  sheet.getRangeByName('C7').setFormula(r'=MINIFS(B1:B5,A1:A5,"Apple")');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## MAXIFS function

The `MAXIFS` function returns the maximum value among cells in a range that meet one or more criteria. Its signature is `MAXIFS(maxRange, criteriaRange1, criteria1, [criteriaRange2, criteria2, ...])`. If no cells match the criteria, the function returns `0`.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> maxIfsFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateSampleData(sheet);
  sheet.enableSheetCalculations();

  // Maximum B value where C is greater than 2: max(1200, 300) = 1200.
  sheet.getRangeByName('C6').setFormula(r'=MAXIFS(B1:B5,C1:C5,">2")');

  // Maximum B value where A is "Apple": max(58, 300, 1000) = 1000.
  sheet.getRangeByName('C7').setFormula(r'=MAXIFS(B1:B5,A1:A5,"Apple")');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## COUNTIFS function

The `COUNTIFS` function applies criteria to cells across multiple ranges and counts the cells that meet all of the criteria. Its signature is `COUNTIFS(criteriaRange1, criteria1, [criteriaRange2, criteria2, ...])`. Unlike the other `*IFS` functions, `COUNTIFS` does not take a separate value range — it counts the cells in each criteria range that match the corresponding criteria.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> countIfsFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateSampleData(sheet);
  sheet.enableSheetCalculations();

  // Count cells in A1:A5 that contain "Grapes" -> 2.
  sheet.getRangeByName('C8').setFormula(r'=COUNTIFS(A1:A5,"Grapes")');

  // Count cells where A is "Apple" AND C is greater than 2 -> 1 (only A3/C3).
  sheet.getRangeByName('C9').setFormula(
        r'=COUNTIFS(A1:A5,"Apple",C1:C5,">2")',
      );

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Related functions

The single-criterion counterparts of these functions are also supported by Syncfusion Flutter XlsIO:

| Single-criterion | Multi-criterion | Description |
|-------------------|-----------------|-------------|
| `AVERAGEIF` | `AVERAGEIFS` | Average of values that match one or more criteria. |
| `MINIF` | `MINIFS` | Minimum value that matches one or more criteria. |
| `MAXIF` | `MAXIFS` | Maximum value that matches one or more criteria. |
| `COUNTIF` | `COUNTIFS` | Count of values that match one or more criteria. |
| `SUMIF` | `SUMIFS` | Sum of values that match one or more criteria. |

The supported comparison operators in criteria are `=`, `<>`, `<`, `<=`, `>`, and `>=`. Wildcard characters `*` and `?` are supported in text criteria.

## See also

* [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview)
* [Working with Formulas](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-formulas)
* [Working with General Function Formulas](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-general-functions)
* [Working with Cells](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-cells)
* [Range API reference](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Range-class.html)
* [Release notes](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/release-notes)