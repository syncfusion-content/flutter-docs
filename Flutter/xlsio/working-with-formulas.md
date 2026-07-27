---
layout: post
title: Working with Formulas | Syncfusion Flutter XlsIO
description: Learn how to apply formulas and read calculated values in the cells of an Excel worksheet using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with Formulas

A formula is an expression in an Excel cell that calculates a value from cell references, constants, and functions. Syncfusion Flutter XlsIO supports writing formulas, evaluating them, and reading the calculated values.

The typical workflow is:

1. Enable formula calculation for the worksheet through `enableSheetCalculations()`. This initializes the internal `CalcEngine` and makes `calculatedValue` return a result.
2. Write a formula to a `Range` through the `setFormula()` method or the `formula` property. The expression must start with `=` (for example, `=A1+A2`).
3. Read the calculated value through the `calculatedValue` property of `Range` if you need the result in code.

For prerequisites and installation steps, see the [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview). For information on formatting calculated values, see [Working with Cell Formatting](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-cell-formatting).

N> The code samples in this document use `await workbook.save()`. Always call `workbook.dispose()` after saving to release the XlsIO DOM memory, ideally inside a `try/finally` block.

## Enable sheet calculation

The `enableSheetCalculations()` method of the `Worksheet` class initializes the internal `CalcEngine` so that formulas are evaluated. Call this method before reading `calculatedValue` on any range in the worksheet. Enabling sheet calculation may increase the time required to save the workbook because every formula in the worksheet is evaluated.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> enableCalculation() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Enable formula calculation for the worksheet.
  sheet.enableSheetCalculations();

  // Add a formula so the calculation has a visible effect.
  sheet.getRangeByName('A1').setNumber(10);
  sheet.getRangeByName('A2').setNumber(20);
  sheet.getRangeByName('A3').setFormula('=A1+A2');

  // Read the calculated value as a string.
  final String result = sheet.getRangeByName('A3').calculatedValue;

  // ignore: avoid_print
  print(result);

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Apply a formula

A formula can be written to a `Range` through the `setFormula(String)` method or by assigning a `String` to the `formula` property. Both require the expression to start with `=`. Cell references use the A1 reference style.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> applyFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Set numeric values in A1 and A2.
  sheet.getRangeByName('A1').setNumber(10);
  sheet.getRangeByName('A2').setNumber(20);

  // Set a formula in A3.
  sheet.getRangeByName('A3').setFormula('=A1+A2');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Read a calculated value

After `enableSheetCalculations()` has been called, the `calculatedValue` property of a `Range` returns the result of the formula as a `String`. If the formula has not been evaluated, the property returns an empty string.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> readCalculatedValue() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Enable formula calculation.
  sheet.enableSheetCalculations();

  // Set values and a formula.
  sheet.getRangeByName('A1').setNumber(10);
  sheet.getRangeByName('A2').setNumber(20);
  sheet.getRangeByName('A3').setFormula('=A1+A2');

  // Read the calculated value as a string.
  final String result = sheet.getRangeByName('A3').calculatedValue;

  // ignore: avoid_print
  print(result);

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

N> The `calculatedValue` property always returns a `String`. To use the result as a number or a date, parse the string with `int.parse`, `double.parse`, or `DateTime.parse` as appropriate.

## Use nested functions

Using a function as one of the arguments of another function is known as a nested function. The arguments of each function are evaluated from the inside out. The following example uses `IF`, `SUM`, `AVERAGE`, `MAX`, `COUNT`, and `MIN` in a single formula.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> nestedFunctions() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Team A data in column B.
  sheet.getRangeByName('B3').setText('Team A');
  sheet.getRangeByName('B4').setNumber(47);
  sheet.getRangeByName('B5').setNumber(43);
  sheet.getRangeByName('B6').setNumber(40);
  sheet.getRangeByName('B7').setNumber(51);
  sheet.getRangeByName('B8').setNumber(53);
  sheet.getRangeByName('B9').setNumber(50);

  // Team B data in column D.
  sheet.getRangeByName('D3').setText('Team B');
  sheet.getRangeByName('D4').setNumber(72);
  sheet.getRangeByName('D5').setNumber(43);
  sheet.getRangeByName('D6').setNumber(84);
  sheet.getRangeByName('D7').setNumber(90);
  sheet.getRangeByName('D8').setNumber(42);
  sheet.getRangeByName('D9').setNumber(56);

  // Enable formula calculation.
  sheet.enableSheetCalculations();

  // Average team A's scores, then add the larger of COUNT(B4,D4) and MIN(B5,D5).
  // If the total exceeds 50, the formula returns "PASS"; otherwise "FAIL".
  sheet
      .getRangeByName('B11')
      .setFormula(
        '=IF(SUM(AVERAGE(B4:B9), MAX(COUNT(B4,D4), MIN(B5,D5))) > 50, "PASS", "FAIL")',
      );

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Supported functions

Syncfusion Flutter XlsIO supports range references and the functions listed below, grouped by category.

### General functions

| Function | Description |
|----------|-------------|
| [SUM](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-general-functions#sum-function) | Adds its arguments. |
| [AVERAGE](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-general-functions#average-function) | Returns the average of its arguments. |
| [MAX](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-general-functions#max-function) | Returns the maximum value in a list of arguments. |
| [MIN](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-general-functions#min-function) | Returns the minimum value in a list of arguments. |
| [COUNT](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-general-functions#count-function) | Counts how many numbers are in the list of arguments. |
| [PRODUCT](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-general-functions#product-function) | Multiplies its arguments. |
| [SUMPRODUCT](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-general-functions#sumproduct-function) | Returns the sum of the products of corresponding array components. |

### Logical functions

| Function | Description |
|----------|-------------|
| [IF](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-logical-function#if-function) | Specifies a logical test to perform. |
| [AND](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-logical-function#and-function) | Returns `TRUE` if all of its arguments are `TRUE`. |
| [OR](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-logical-function#or-function) | Returns `TRUE` if any argument is `TRUE`. |
| [NOT](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-logical-function#not-function) | Reverses the logic of its argument. |

### Text functions

| Function | Description |
|----------|-------------|
| [CONCATENATE](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-text-functions#concatenate-function) | Joins several text items into one text item. |
| [TRIM](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-text-functions#trim-function) | Removes spaces from text. |
| [LOWER](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-text-functions#lower-function) | Converts text to lowercase. |
| [UPPER](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-text-functions#upper-function) | Converts text to uppercase. |

### Time functions

| Function | Description |
|----------|-------------|
| [NOW](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-time-functions#now-function) | Returns the serial number of the current date and time. |
| [TODAY](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-time-functions#today-function) | Returns the serial number of today's date. |

### Lookup and reference functions

| Function | Description |
|----------|-------------|
| [INDEX](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-lookup-references-functions#index-function) | Uses an index to choose a value from a reference or array. |
| [MATCH](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-lookup-references-functions#match-function) | Looks up values in a reference or array. |
| [VLOOKUP](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-lookup-references-functions#vlookup-function) | Looks in the first column of an array and moves across the row to return the value of a cell. |

### Conditional functions

| Function | Description |
|----------|-------------|
| [SUMIF](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-math-trig-functions#sumif-function) | Adds the cells specified by a given criteria. |
| [SUMIFS](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-math-trig-functions#sumifs-function) | Adds all of its arguments that meet multiple criteria. |
| [COUNTIFS](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-statistical-functions#countifs-function) | Counts the number of times all criteria are met. |
| [MAXIFS](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-statistical-functions#maxifs-function) | Returns the maximum value among cells specified by a given set of conditions. |
| [MINIFS](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-statistical-functions#minifs-function) | Returns the minimum value among cells specified by a given set of conditions. |

## See also

* [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview)
* [Working with Cell Formatting](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-cell-formatting)
* [Working with Cells](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-cells)
* [Range API reference](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Range-class.html)
* [Worksheet API reference](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Worksheet-class.html)
