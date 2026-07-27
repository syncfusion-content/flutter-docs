---
layout: post
title: Math and Trig Function Formulas | Syncfusion Flutter XlsIO
description: Learn how to apply math and trig function formulas and read calculated values in the cells of an Excel worksheet using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with Math and Trig Function Formulas

Math and trig function formulas perform numeric calculations such as summing, multiplying, and aggregating values that match one or more criteria. Syncfusion Flutter XlsIO supports the following math and trig functions:

* [SUMIF](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-math-trig-functions#sumif-function) — sums the values in a range that meet a single criterion.
* [SUMIFS](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-math-trig-functions#sumifs-function) — sums the values in a range that meet multiple criteria.
* [SUMPRODUCT](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-math-trig-functions#sumproduct-function) — returns the sum of the products of corresponding ranges or arrays.
* [PRODUCT](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-math-trig-functions#product-function) — multiplies all the numbers given as arguments and returns the product.

N> The supported comparison operators in criteria are `=`, `<>`, `<`, `<=`, `>`, and `>=`. Wildcard characters `*` and `?` are supported in text criteria. Text comparisons are case-insensitive.

For prerequisites and installation steps, see the [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview). For background on formulas and how to enable calculation, see [Working with Formulas](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-formulas).

N> The code samples in this document use `await workbook.save()`. Always call `workbook.dispose()` after saving to release the XlsIO DOM memory, ideally inside a `try/finally` block. Each function sample calls `enableSheetCalculations()` so the calculated value is available through the `calculatedValue` property of a `Range`.

## Shared sample data

The samples for `SUMIF`, `SUMIFS`, and `SUMPRODUCT` share the following data setup:

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

## SUMIF function

The `SUMIF` function sums the values in a range that meet a single criterion. Its signature is `SUMIF(range, criteria, [sumRange])`. If `sumRange` is omitted, the values in `range` are summed directly. The `range` and `sumRange` must have the same dimensions when `sumRange` is supplied.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> sumIfFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateSampleData(sheet);
  sheet.enableSheetCalculations();

  // Sum B values where A equals A2 ("Grapes"): 1200 + 500 = 1700.
  sheet.getRangeByName('C8').setFormula('=SUMIF(A1:A5,A2,B1:B5)');

  // Sum B values where C equals C4 (2): 58 + 500 = 558.
  sheet.getRangeByName('C9').setFormula('=SUMIF(C1:C5,C4,B1:B5)');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## SUMIFS function

The `SUMIFS` function sums the values in a range that meet one or more criteria. Its signature is `SUMIFS(sumRange, criteriaRange1, criteria1, [criteriaRange2, criteria2, ...])`. Note that the order of arguments is the opposite of `SUMIF`: the sum range is the first argument, and the criteria ranges and criteria values follow.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> sumIfsFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateSampleData(sheet);
  sheet.enableSheetCalculations();

  // Sum B where C is greater than or equal to 2: 58 + 1200 + 300 + 500 = 2058.
  sheet.getRangeByName('C8').setFormula(r'=SUMIFS(B1:B5,C1:C5,">=2")');

  // Sum B where A is "Apple": 58 + 300 + 1000 = 1358.
  sheet.getRangeByName('C9').setFormula(r'=SUMIFS(B1:B5,A1:A5,"Apple")');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## SUMPRODUCT function

The `SUMPRODUCT` function returns the sum of the products of corresponding ranges or arrays. Its signature is `SUMPRODUCT(array1, [array2, ...])`. All arrays must have the same dimensions; otherwise the function returns a `#VALUE!` error.

The double-unary operator `--` in the second example converts a boolean array into a numeric array (`TRUE` becomes `1` and `FALSE` becomes `0`) so the result can be used as a multiplier.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> sumProductFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateSampleData(sheet);
  sheet.enableSheetCalculations();

  // Sum of B × C: (58×2) + (1200×3) + (300×4) + (500×2) + (1000×1) = 6916.
  sheet.getRangeByName('C8').setFormula('=SUMPRODUCT(B1:B5,C1:C5)');

  // Sum of B × C where A is "Apple": (58×2) + (300×4) + (1000×1) = 2316.
  sheet.getRangeByName('C9').setFormula(
        r'=SUMPRODUCT(--(A1:A5="Apple"), B1:B5, C1:C5)',
      );

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## PRODUCT function

The `PRODUCT` function multiplies all the numbers given as arguments and returns the product. Its signature is `PRODUCT(number1, [number2, ...])`. Arguments can be individual numbers, cell references, or ranges. Empty cells and text values are ignored.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> productFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Two columns of numbers to multiply.
  sheet.getRangeByName('A1').setNumber(2);
  sheet.getRangeByName('B1').setNumber(3);
  sheet.getRangeByName('A2').setNumber(5);
  sheet.getRangeByName('B2').setNumber(4);
  sheet.getRangeByName('A3').setNumber(6);
  sheet.getRangeByName('B3').setNumber(7);
  sheet.getRangeByName('A4').setNumber(9);
  sheet.getRangeByName('B4').setNumber(8);

  sheet.enableSheetCalculations();

  // Product of every cell in A1:A4 and B1:B4: (2×5×6×9) × (3×4×7×8) = 540 × 672 = 362880.
  sheet.getRangeByName('C8').setFormula('=PRODUCT(A1:A4,B1:B4)');

  // Product of A1 and B1: 2 × 3 = 6.
  sheet.getRangeByName('C9').setFormula('=PRODUCT(A1,B1)');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Related functions

The following math and trig functions are also supported by Syncfusion Flutter XlsIO:

| Function | Description |
|----------|-------------|
| `ABS` | Returns the absolute value of a number. |
| `ROUND`, `ROUNDUP`, `ROUNDDOWN` | Round a number to a specified number of decimal places. |
| `CEILING`, `FLOOR` | Round a number up or down to the nearest multiple of significance. |
| `MOD` | Returns the remainder after division. |
| `POWER` | Returns a number raised to a power. |
| `SQRT` | Returns the square root of a number. |
| `SIN`, `COS`, `TAN` | Trigonometric functions (radians). |
| `PI` | Returns the value of π. |
| `RAND`, `RANDBETWEEN` | Random number generators. |

## See also

* [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview)
* [Working with Formulas](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-formulas)
* [Working with Statistical Function Formulas](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-statistical-functions)
* [Working with Cells](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-cells)
* [Range API reference](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Range-class.html)
