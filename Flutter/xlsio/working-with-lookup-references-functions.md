---
layout: post
title: Working with Lookup and References Function Formulas | Syncfusion Flutter XlsIO
description: Learn how to apply lookup and references function formulas and read calculated values in the cells of an Excel worksheet using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with Lookup and References Function Formulas

Lookup and references function formulas search a range for a value and return a related value from the same row or column. Syncfusion Flutter XlsIO supports the following lookup and references functions:

* [INDEX](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-lookup-references-functions#index-function) — returns a value or a reference from within a table or range.
* [MATCH](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-lookup-references-functions#match-function) — returns the relative position of an item in a range.
* [VLOOKUP](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-lookup-references-functions#vlookup-function) — searches the first column of a range and returns a value from the same row in a specified column.

For prerequisites and installation steps, see the [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview). For background on formulas and how to enable calculation, see [Working with Formulas](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-formulas).

N> The code samples in this document use `await workbook.save()`. Always call `workbook.dispose()` after saving to release the XlsIO DOM memory, ideally inside a `try/finally` block. Each function sample calls `enableSheetCalculations()` so the calculated value is available through the `calculatedValue` property of a `Range`.

## INDEX function

The `INDEX` function returns a value or a reference from within a table or range. It has two forms:

| Form | Signature | Description |
|------|-----------|-------------|
| Array form | `INDEX(array, rowNum, [columnNum])` | Returns the value at the intersection of the specified row and column in a single range. |
| Reference form | `INDEX(reference, rowNum, [columnNum], [areaNum])` | Returns a reference to a cell in a multi-area reference. The `areaNum` selects which area to use. |

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> indexFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Sample data in A1:B2.
  sheet.getRangeByName('A1').setNumber(10);
  sheet.getRangeByName('A2').setNumber(5);
  sheet.getRangeByName('B1').setNumber(4);
  sheet.getRangeByName('B2').setNumber(8);

  sheet.enableSheetCalculations();

  // Array form: row 2, column 1 of A1:A2 -> 5.
  sheet.getRangeByName('A3').setFormula('=INDEX(A1:A2,2,1)');

  // Reference form: row 1, column 1, area 1 of A1:B2 -> 10.
  sheet.getRangeByName('B3').setFormula('=INDEX(A1:B2,1,1,1)');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

`A3` evaluates to `5`. `B3` evaluates to `10`.

## MATCH function

The `MATCH` function searches for a specified item in a range and returns the relative position of the first match. Its signature is `MATCH(lookupValue, lookupArray, [matchType])`.

| `matchType` | Behavior |
|-------------|----------|
| `1` (default) | Finds the largest value less than or equal to `lookupValue`. The `lookupArray` must be sorted in ascending order. |
| `0` | Finds the first value exactly equal to `lookupValue`. The `lookupArray` can be in any order. |
| `-1` | Finds the smallest value greater than or equal to `lookupValue`. The `lookupArray` must be sorted in descending order. |

If no match is found, `MATCH` returns the `#N/A` error.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> matchFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Sample data in A1:A4.
  sheet.getRangeByName('A1').setNumber(10);
  sheet.getRangeByName('A2').setNumber(8);
  sheet.getRangeByName('A3').setNumber(6);
  sheet.getRangeByName('A4').setNumber(4);

  sheet.enableSheetCalculations();

  // Exact match: the value 8 is at position 2.
  sheet.getRangeByName('A3').setFormula('=MATCH(8,A1:A4,0)');

  // Exact match: the value 4 is at position 4.
  sheet.getRangeByName('B3').setFormula('=MATCH(4,A1:A4,0)');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

`A3` evaluates to `2` (the value `8` is at position 2 in the range). `B3` evaluates to `4` (the value `4` is at position 4).

N> The original sample used `=MATCH(6,A1:A4,-1)`, which would return `#N/A` because the data is not sorted in descending order. The revised sample above uses `matchType = 0` (exact match) so the example produces a result without an unsorted-range requirement.

## VLOOKUP function

The `VLOOKUP` function searches the first column of a range for a value and returns a value from the same row in a specified column. Its signature is `VLOOKUP(lookupValue, tableArray, colIndexNum, [rangeLookup])`.

| `rangeLookup` | Behavior |
|---------------|----------|
| `FALSE` | Exact match. The first column can be in any order. |
| `TRUE` (default) | Approximate match. The first column must be sorted in ascending order. |

If `colIndexNum` is less than `1` or greater than the number of columns in `tableArray`, `VLOOKUP` returns the `#REF!` error. If no match is found, `VLOOKUP` returns the `#N/A` error.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> vlookupFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Sample data: A1:A4 holds names (sorted ascending), B1:B4 holds numbers.
  sheet.getRangeByName('A1').setText('John');
  sheet.getRangeByName('A2').setText('Mark');
  sheet.getRangeByName('A3').setText('Park');
  sheet.getRangeByName('A4').setText('Zuck');
  sheet.getRangeByName('B1').setNumber(10);
  sheet.getRangeByName('B2').setNumber(8);
  sheet.getRangeByName('B3').setNumber(6);
  sheet.getRangeByName('B4').setNumber(4);

  sheet.enableSheetCalculations();

  // Exact match: look up "Park" in A1:A4 and return the value from column 2 (6).
  sheet.getRangeByName('A5').setFormula(r'=VLOOKUP("Park",A1:B4,2,FALSE)');

  // Approximate match: "John" is the first row, so the result is 10.
  sheet.getRangeByName('B5').setFormula(r'=VLOOKUP("John",A1:B4,2,TRUE)');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

`A5` evaluates to `6` (the value paired with `"Park"` in column 2). `B5` evaluates to `10` (the value paired with `"John"` in column 2).

N> The horizontal counterpart of `VLOOKUP` is `HLOOKUP`, which searches the first row of a range and returns a value from a specified column. The modern replacement is `XLOOKUP`, available in Excel 2021 and later, which combines the capabilities of `VLOOKUP`, `HLOOKUP`, and `INDEX`/`MATCH` and does not require a sorted lookup column.

## See also

* [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview)
* [Working with Formulas](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-formulas)
* [Working with Cells](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-cells)
* [Range API reference](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Range-class.html)
* [Release notes](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/release-notes)
