---
layout: post
title: Working with Logical Function Formulas | Syncfusion Flutter XlsIO
description: Learn how to apply logical function formulas and read calculated values in the cells of an Excel worksheet using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with Logical Function Formulas

Logical function formulas evaluate one or more conditions and return a logical value (`TRUE` or `FALSE`) or a value selected by a condition. Syncfusion Flutter XlsIO supports the following logical functions:

* [IF](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-logical-function#if-function) — returns one of two values based on a condition.
* [AND](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-logical-function#and-function) — returns `TRUE` if every argument is `TRUE`.
* [OR](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-logical-function#or-function) — returns `TRUE` if any argument is `TRUE`.
* [NOT](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-logical-function#not-function) — reverses the logical value of its argument.

For prerequisites and installation steps, see the [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview). For background on formulas and how to enable calculation, see [Working with Formulas](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-formulas).

N> The code samples in this document use `await workbook.save()`. Always call `workbook.dispose()` after saving to release the XlsIO DOM memory, ideally inside a `try/finally` block. Each function sample calls `enableSheetCalculations()` so the calculated value is available through the `calculatedValue` property of a `Range`.

## IF function

The `IF` function performs a logical comparison and returns one of two values based on the result. Its signature is `IF(condition, valueIfTrue, valueIfFalse)`. The `valueIfTrue` and `valueIfFalse` arguments can be any expression, including numbers, text, formulas, or even another `IF` for chained conditions.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> ifFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Set values in A1:A4 and B1:B4.
  for (final cell in <String>['A1', 'A2', 'A3', 'A4']) {
    sheet.getRangeByName(cell).setNumber(10);
  }
  sheet.getRangeByName('A2').setNumber(20);
  sheet.getRangeByName('A3').setNumber(4);
  sheet.getRangeByName('A4').setNumber(12);
  sheet.getRangeByName('B1').setNumber(2);
  sheet.getRangeByName('B2').setNumber(16);
  sheet.getRangeByName('B3').setNumber(8);
  sheet.getRangeByName('B4').setNumber(11);

  sheet.enableSheetCalculations();

  // IF that returns a text value.
  sheet.getRangeByName('A6').setFormula(r'=IF(A4 > B3, "Yes", "No")');

  // IF that returns a numeric value.
  sheet.getRangeByName('B6').setFormula(r'=IF(A4 < B3, A1+B1, A1-B1)');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

`A6` evaluates to `"Yes"` (`A4` = 12 is greater than `B3` = 8). `B6` evaluates to `8` (`A4` = 12 is not less than `B3` = 8, so the formula returns `A1-B1` = 10 − 2 = 8).

## AND function

The `AND` function returns `TRUE` only if every argument is `TRUE`; otherwise it returns `FALSE`. Its signature is `AND(condition1, condition2, ...)`. The supported comparison operators are `=`, `<>`, `<`, `<=`, `>`, and `>=`.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> andFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Set values in A1:A5.
  sheet.getRangeByName('A1').setNumber(75);
  sheet.getRangeByName('A2').setNumber(32);
  sheet.getRangeByName('A3').setNumber(84);
  sheet.getRangeByName('A4').setNumber(57);
  sheet.getRangeByName('A5').setNumber(65);

  sheet.enableSheetCalculations();

  // 75 is not less than 75, so B1 is FALSE.
  sheet.getRangeByName('B1').setFormula('=AND(A1>35,A1<75)');

  // 65 is between 35 and 75, so B2 is TRUE.
  sheet.getRangeByName('B2').setFormula('=AND(A5>35,A5<75)');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

`B1` evaluates to `FALSE` (`A1` = 75 is not strictly less than 75). `B2` evaluates to `TRUE` (`A5` = 65 is between 35 and 75).

## OR function

The `OR` function returns `TRUE` if any of its arguments is `TRUE`; it returns `FALSE` only when all arguments are `FALSE`. Its signature is `OR(condition1, condition2, ...)`.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> orFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Set text values in A1:A6.
  sheet.getRangeByName('A1').setText('Green');
  sheet.getRangeByName('A2').setText('Red');
  sheet.getRangeByName('A3').setText('Blue');
  sheet.getRangeByName('A4').setText('Red');
  sheet.getRangeByName('A5').setText('Green');
  sheet.getRangeByName('A6').setText('Blue');

  sheet.enableSheetCalculations();

  // "Green" matches the first condition, so B1 is TRUE.
  sheet.getRangeByName('B1').setFormula(r'=OR(A1="Green",A1="Red")');

  // "Blue" matches neither condition, so B2 is FALSE.
  sheet.getRangeByName('B2').setFormula(r'=OR(A3="Green",A3="Red")');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

`B1` evaluates to `TRUE` (`A1` = "Green" matches the first condition). `B2` evaluates to `FALSE` (`A3` = "Blue" matches neither condition).

## NOT function

The `NOT` function reverses a logical value: `TRUE` becomes `FALSE` and `FALSE` becomes `TRUE`. Its signature is `NOT(condition)`.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> notFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Set text values in A1:A6.
  sheet.getRangeByName('A1').setText('Green');
  sheet.getRangeByName('A2').setText('Red');
  sheet.getRangeByName('A3').setText('Blue');
  sheet.getRangeByName('A4').setText('Red');
  sheet.getRangeByName('A5').setText('Green');
  sheet.getRangeByName('A6').setText('Blue');

  sheet.enableSheetCalculations();

  // A1 is "Green", so the inner comparison is TRUE and NOT inverts it to FALSE.
  sheet.getRangeByName('B1').setFormula(r'=NOT(A1="Green")');

  // A3 is "Blue" (not "Red"), so the inner comparison is FALSE and NOT inverts it to TRUE.
  sheet.getRangeByName('B2').setFormula(r'=NOT(A3="Red")');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

`B1` evaluates to `FALSE`. `B2` evaluates to `TRUE`.

## See also

* [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview)
* [Working with Formulas](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-formulas)
* [Working with Cells](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-cells)
* [Range API reference](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Range-class.html)
* [Release notes](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/release-notes)
