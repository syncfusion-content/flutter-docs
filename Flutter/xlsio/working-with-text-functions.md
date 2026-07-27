---
layout: post
title: Working with Text Function Formulas | Syncfusion Flutter XlsIO
description: Learn how to apply text function formulas and read calculated values in the cells of an Excel worksheet using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with Text Function Formulas

Text function formulas manipulate text values: joining strings, trimming whitespace, and changing letter case. Syncfusion Flutter XlsIO supports the following text functions:

* [CONCATENATE](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-text-functions#concatenate-function) — joins two or more text strings into one string.
* [TRIM](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-text-functions#trim-function) — removes leading and trailing spaces and collapses internal multiple spaces to a single space.
* [LOWER](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-text-functions#lower-function) — converts all uppercase letters in a text string to lowercase.
* [UPPER](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-text-functions#upper-function) — converts all lowercase letters in a text string to uppercase.

For prerequisites and installation steps, see the [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview). For background on formulas and how to enable calculation, see [Working with Formulas](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-formulas).

N> The code samples in this document use `await workbook.save()`. Always call `workbook.dispose()` after saving to release the XlsIO DOM memory, ideally inside a `try/finally` block. Each function sample calls `enableSheetCalculations()` so the calculated value is available through the `calculatedValue` property of a `Range`.

## CONCATENATE function

The `CONCATENATE` function joins two or more text strings into one string. Its signature is `CONCATENATE(text1, text2, ...)`. To insert a separator between the joined parts, include a literal text argument, for example `CONCATENATE(text1, " ", text2)`. The modern Excel functions `CONCAT` and `TEXTJOIN` provide more flexible joining options and may be preferred for new code.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> concatenateFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // First pair: A1 already has a trailing space so the result reads naturally.
  sheet.getRangeByName('A1').setText('Syncfusion ');
  sheet.getRangeByName('A2').setText('Software');

  // Second pair: no trailing space, so the result is "HelloWorld".
  sheet.getRangeByName('B1').setText('Hello');
  sheet.getRangeByName('B2').setText('World');

  sheet.enableSheetCalculations();

  // Joins "Syncfusion " and "Software" -> "Syncfusion Software".
  sheet.getRangeByName('A3').setFormula('=CONCATENATE(A1,A2)');

  // Joins "Hello" and "World" -> "HelloWorld".
  sheet.getRangeByName('B3').setFormula('=CONCATENATE(B1,B2)');

  // Example with a separator: "Hello World".
  sheet.getRangeByName('C3').setFormula(r'=CONCATENATE(B1, " ", B2)');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

`A3` evaluates to `"Syncfusion Software"`. `B3` evaluates to `"HelloWorld"`. `C3` evaluates to `"Hello World"`.

## TRIM function

The `TRIM` function removes leading and trailing spaces from a text string and collapses internal sequences of multiple spaces into a single space. Its signature is `TRIM(text)`. Numbers and punctuation are unaffected.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> trimFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  sheet.getRangeByName('A1').setText('   Hello  ');
  sheet.getRangeByName('A2').setText('     World  Hi');

  sheet.enableSheetCalculations();

  // Trims the leading and trailing spaces and collapses the internal double space.
  sheet.getRangeByName('A3').setFormula('=TRIM(A1)');

  // Trims the leading spaces and collapses the internal double space.
  sheet.getRangeByName('B3').setFormula('=TRIM(A2)');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

`A3` evaluates to `"Hello"`. `B3` evaluates to `"World Hi"`.

## LOWER function

The `LOWER` function converts every uppercase letter in a text string to lowercase. Its signature is `LOWER(text)`. Numbers, punctuation, and existing lowercase letters are unaffected.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> lowerFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  sheet.getRangeByName('A1').setText('HELLO');
  sheet.getRangeByName('A2').setText('World HI');

  sheet.enableSheetCalculations();

  sheet.getRangeByName('A3').setFormula('=LOWER(A1)');
  sheet.getRangeByName('B3').setFormula('=LOWER(A2)');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

`A3` evaluates to `"hello"`. `B3` evaluates to `"world hi"`.

## UPPER function

The `UPPER` function converts every lowercase letter in a text string to uppercase. Its signature is `UPPER(text)`. Numbers, punctuation, and existing uppercase letters are unaffected.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> upperFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  sheet.getRangeByName('A1').setText('hello');
  sheet.getRangeByName('A2').setText('World hi');

  sheet.enableSheetCalculations();

  sheet.getRangeByName('A3').setFormula('=UPPER(A1)');
  sheet.getRangeByName('B3').setFormula('=UPPER(A2)');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

`A3` evaluates to `"HELLO"`. `B3` evaluates to `"WORLD HI"`.

## See also

* [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview)
* [Working with Formulas](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-formulas)
* [Working with Cells](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-cells)
* [Range API reference](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Range-class.html)
