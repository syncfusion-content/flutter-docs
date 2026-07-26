---
layout: post
title: Working with Number Formats | Syncfusion Flutter XlsIO
description: Learn how to apply a number format to a cell or a range of cells in an Excel worksheet using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with Number Formats

Number formats are codes that control the appearance of cell values without changing the underlying data. Syncfusion Flutter XlsIO supports reading and writing both built-in and custom number formats through the `numberFormat` property of a `Range` or `Style`.

The following categories are documented in this page:

| Category | Description |
|----------|-------------|
| Number | General numeric display, including digit placeholders and thousands separators. |
| Currency | Numeric display with a currency symbol and locale-aware formatting. |
| Percentage | Multiplies the value by 100 and appends a `%` sign. |
| Date | Date formats using day, month, and year tokens. |
| Time | Time formats using hour, minute, and second tokens. |
| Accounting | Currency-aligned format that lines up the decimal point and the currency symbol. |
| Scientific | Displays values in scientific notation. |
| Fraction | Displays values as fractions. |
| Text | Displays the value as text exactly as entered. |

N> The decimal and thousands separators used in formatted values are taken from the culture of the application. The format codes in this page use `.` and `,` as separators, but the same code with a different culture will produce different output.

For prerequisites and installation steps, see the [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview). For the complete list of format tokens, see [Working with Cell Formatting](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-cell-formatting#apply-number-formats).

N> The code samples in this document use `await workbook.save()`. Always call `workbook.dispose()` after saving to release the XlsIO DOM memory, ideally inside a `try/finally` block.

## Number

Number formats control the digits, grouping, and sign display of a value. The `getRangeByIndex(row, column)` method used in the samples accepts 1-based row and column arguments.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> numberFormats() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  sheet.getRangeByIndex(1, 1).setNumber(279);
  sheet.getRangeByIndex(1, 1).numberFormat = '0.0';

  sheet.getRangeByIndex(2, 1).setNumber(-2211);
  sheet.getRangeByIndex(2, 1).numberFormat = '#,##0.00';

  sheet.getRangeByIndex(3, 1).setNumber(9032);
  sheet.getRangeByIndex(3, 1).numberFormat = '[Blue](#,##0.000)';

  sheet.getRangeByIndex(4, 1).setNumber(1291);
  sheet.getRangeByIndex(4, 1).numberFormat = '(#,##0.0000)';

  sheet.getRangeByIndex(5, 1).setNumber(-22);
  sheet.getRangeByIndex(5, 1).numberFormat = '#,##0.00000_)';

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

The format codes used above are:

| Code | Description |
|------|-------------|
| `0.0` | One decimal place, padded with zeros if needed. |
| `#,##0.00` | Negative number with a leading minus sign and two decimal places. |
| `[Blue](#,##0.000)` | Three decimal places with blue color and parentheses around the value. |
| `(#,##0.0000)` | Four decimal places wrapped in parentheses. |
| `#,##0.00000_)` | Five decimal places with a trailing space the width of a closing parenthesis. |

## Currency

Currency formats add a currency symbol to a numeric value. The `$` character in a format string is a literal and does not need to be escaped in Dart raw strings.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> currencyFormats() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  sheet.getRangeByIndex(1, 1).setNumber(2955);
  sheet.getRangeByIndex(1, 1).numberFormat = r'$#,##0.0';

  sheet.getRangeByName('A2').setNumber(22.11);
  sheet.getRangeByName('A2').numberFormat = '([Red]$0.00)';

  sheet.getRangeByIndex(3, 1).setNumber(9312);
  sheet.getRangeByIndex(3, 1).numberFormat = '($#,##0.00)';

  sheet.getRangeByName('A4').setNumber(111);
  sheet.getRangeByName('A4').numberFormat = '[BLUE]$0.0000';

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

The format codes used above are:

| Code | Description |
|------|-------------|
| `$#,##0.0` | Currency with one decimal place. |
| `([Red]$0.00)` | Negative currency in red, wrapped in parentheses. |
| `($#,##0.00)` | Negative currency in parentheses. |
| `[BLUE]$0.0000` | Currency in blue with four decimal places. |

## Percentage

Percentage formats multiply the underlying value by 100 and append a `%` sign. For example, a cell that stores `0.25` is displayed as `25%`.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> percentageFormats() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  sheet.getRangeByIndex(1, 1).setNumber(29);
  sheet.getRangeByIndex(1, 1).numberFormat = '0%';

  sheet.getRangeByName('A2').setNumber(22.11);
  sheet.getRangeByName('A2').numberFormat = '0.00%';

  sheet.getRangeByIndex(3, 1).setNumber(0.09312);
  sheet.getRangeByIndex(3, 1).numberFormat = '0.000%';

  sheet.getRangeByName('A4').setNumber(0.111);
  sheet.getRangeByName('A4').numberFormat = '0.0000%';

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Date and time

Date and time formats use the date and time tokens documented in [Working with Cell Formatting](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-cell-formatting#apply-number-formats). The samples below cover common date, named-month, ISO, and mixed date-time patterns.

### Date formats

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> dateFormats() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Short date.
  sheet.getRangeByIndex(1, 1).setDateTime(DateTime(2020, 8, 23));
  sheet.getRangeByIndex(1, 1).numberFormat = 'm/d/yyyy';

  // Long date with named weekday and month.
  sheet.getRangeByName('A2').setDateTime(DateTime(2002, 12, 3));
  sheet.getRangeByName('A2').numberFormat = 'dddd, mmmm dd, yyyy';

  // ISO 8601.
  sheet.getRangeByIndex(3, 1).setDateTime(DateTime(2012, 11, 22));
  sheet.getRangeByIndex(3, 1).numberFormat = 'yyyy-mm-dd';

  // Short day-month.
  sheet.getRangeByName('A4').setDateTime(DateTime(2014, 10, 12));
  sheet.getRangeByName('A4').numberFormat = 'm/d';

  // Two-digit year.
  sheet.getRangeByIndex(5, 1).setDateTime(DateTime(2020, 8, 23));
  sheet.getRangeByIndex(5, 1).numberFormat = 'm/d/yy';

  // Zero-padded short date.
  sheet.getRangeByName('A6').setDateTime(DateTime(1999, 7, 30));
  sheet.getRangeByName('A6').numberFormat = 'mm/dd/yy';

  // Day and abbreviated month.
  sheet.getRangeByIndex(7, 1).setDateTime(DateTime(2012, 11, 22));
  sheet.getRangeByIndex(7, 1).numberFormat = 'd-mmm';

  // Day, abbreviated month, two-digit year.
  sheet.getRangeByName('A8').setDateTime(DateTime(2014, 10, 12));
  sheet.getRangeByName('A8').numberFormat = 'd-mmm-yy';

  // Full month name and two-digit year.
  sheet.getRangeByIndex(9, 1).setDateTime(DateTime(2020, 8, 23));
  sheet.getRangeByIndex(9, 1).numberFormat = 'mmmm-yy';

  // Full month name, day, and four-digit year.
  sheet.getRangeByName('A10').setDateTime(DateTime(2002, 12, 3));
  sheet.getRangeByName('A10').numberFormat = 'mmmm d, yyyy';

  // First letter of the month (five m's).
  sheet.getRangeByIndex(11, 1).setDateTime(DateTime(2012, 11, 22));
  sheet.getRangeByIndex(11, 1).numberFormat = 'mmmmm';

  // First letter of the month plus two-digit year.
  sheet.getRangeByName('A12').setDateTime(DateTime(2014, 10, 12));
  sheet.getRangeByName('A12').numberFormat = 'mmmmm-yy';

  // Day, abbreviated month, four-digit year.
  sheet.getRangeByIndex(13, 1).setDateTime(DateTime(2020, 8, 23));
  sheet.getRangeByIndex(13, 1).numberFormat = 'd-mmm-yyyy';

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Time formats

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> timeFormats() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // 12-hour clock with seconds and AM/PM.
  sheet.getRangeByIndex(1, 1).setDateTime(DateTime(2020, 8, 23, 8, 15, 20));
  sheet.getRangeByIndex(1, 1).numberFormat = 'h:mm:ss AM/PM';

  // 24-hour clock, hour and minutes only.
  sheet.getRangeByName('A2').setDateTime(DateTime(2002, 12, 3, 23, 45, 45));
  sheet.getRangeByName('A2').numberFormat = 'h:mm';

  // 12-hour clock, hour and minutes only.
  sheet.getRangeByIndex(3, 1).setDateTime(DateTime(2012, 11, 22, 5, 45, 45));
  sheet.getRangeByIndex(3, 1).numberFormat = 'h:mm AM/PM';

  // 24-hour clock with seconds.
  sheet.getRangeByName('A4').setDateTime(DateTime(2014, 10, 12, 20, 5, 5));
  sheet.getRangeByName('A4').numberFormat = 'h:mm:ss';

  // Minutes, seconds, and tenths.
  sheet.getRangeByIndex(5, 1).setDateTime(DateTime(2020, 8, 23, 8, 15, 20));
  sheet.getRangeByIndex(5, 1).numberFormat = 'mm:ss.0';

  // Elapsed time (uses the [h] token to allow hours larger than 24).
  sheet.getRangeByName('A6').setDateTime(DateTime(1999, 7, 30, 5, 34, 40));
  sheet.getRangeByName('A6').numberFormat = '[h]:mm:ss';

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Mixed date-time formats

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> dateTimeFormats() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Date and 12-hour time.
  sheet.getRangeByName('A1').setDateTime(DateTime(2002, 12, 3, 23, 45, 45));
  sheet.getRangeByName('A1').numberFormat = 'm/d/yy h:mm AM/PM';

  // Date and 24-hour time.
  sheet.getRangeByIndex(2, 1).setDateTime(DateTime(2012, 11, 22, 5, 45, 45));
  sheet.getRangeByIndex(2, 1).numberFormat = 'm/d/yy h:mm';

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Accounting

Accounting formats align the currency symbol on the left and the decimal point across cells. They use the `_($* …_)` pattern, where the `_` underscore reserves space for the closing parenthesis of negative values and the `*` repeats the next character to fill the column width.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> accountingFormats() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  sheet.getRangeByIndex(1, 1).setNumber(79);
  sheet.getRangeByIndex(1, 1).numberFormat = r'_($* #,##0_)';

  sheet.getRangeByIndex(2, 1).setNumber(2211);
  sheet.getRangeByIndex(2, 1).numberFormat = r'_($* (#,##0.00)';

  sheet.getRangeByIndex(3, 1).setNumber(9.032);
  sheet.getRangeByIndex(3, 1).numberFormat = r'_($* "-"???)';

  sheet.getRangeByIndex(4, 1).setNumber(1.1291);
  sheet.getRangeByIndex(4, 1).numberFormat = r'_($* #,##0.0000_)';

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Scientific

Scientific formats display a value in scientific notation. The `E+00`, `E-00`, `e+00`, and `e-00` tokens control the exponent.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> scientificFormats() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  sheet.getRangeByIndex(1, 1).setNumber(791);
  sheet.getRangeByIndex(1, 1).numberFormat = '0.E+00';

  sheet.getRangeByIndex(2, 1).setNumber(22.11);
  sheet.getRangeByIndex(2, 1).numberFormat = '0.00E+00';

  sheet.getRangeByIndex(3, 1).setNumber(9.1032);
  sheet.getRangeByIndex(3, 1).numberFormat = '0.0000E+00';

  sheet.getRangeByIndex(4, 1).setNumber(11.1);
  sheet.getRangeByIndex(4, 1).numberFormat = '0.0E+00';

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Fraction

Fraction formats display a decimal value as a fraction. The `?` digit placeholder reserves space for digits that are not significant.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> fractionFormats() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  sheet.getRangeByIndex(1, 1).setNumber(29.4);
  sheet.getRangeByIndex(1, 1).numberFormat = '# ?/?';

  sheet.getRangeByName('A2').setNumber(22.11);
  sheet.getRangeByName('A2').numberFormat = '# ??/??';

  sheet.getRangeByIndex(3, 1).setNumber(0.09312);
  sheet.getRangeByIndex(3, 1).numberFormat = '# ???/???';

  sheet.getRangeByName('A4').setNumber(11.4);
  sheet.getRangeByName('A4').numberFormat = '# ?/2';

  sheet.getRangeByIndex(5, 1).setNumber(47.98);
  sheet.getRangeByIndex(5, 1).numberFormat = '# ?/4';

  sheet.getRangeByName('A6').setNumber(7.39);
  sheet.getRangeByName('A6').numberFormat = '# ?/8';

  sheet.getRangeByIndex(7, 1).setNumber(21.5);
  sheet.getRangeByIndex(7, 1).numberFormat = '# ??/16';

  sheet.getRangeByName('A8').setNumber(13.1);
  sheet.getRangeByName('A8').numberFormat = '# ?/10';

  sheet.getRangeByIndex(9, 1).setNumber(49.56);
  sheet.getRangeByIndex(9, 1).numberFormat = '# ??/100';

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Text

A text format displays the cell value as text. The `@` placeholder represents the text in the cell. When applied to a numeric value, the format causes Excel to display the value as text, but the underlying type may still be numeric; to permanently treat a value as text, write it through `setText()`.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> textFormats() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  sheet.getRangeByIndex(1, 1).setNumber(-12.89);
  sheet.getRangeByIndex(1, 1).numberFormat = '@';

  sheet.getRangeByName('A2').setNumber(2311);
  sheet.getRangeByName('A2').numberFormat = '_(@_)';

  sheet.getRangeByIndex(3, 1).setNumber(0.09312);
  sheet.getRangeByIndex(3, 1).numberFormat = '* @';

  sheet.getRangeByName('A4').setNumber(11.4);
  sheet.getRangeByName('A4').numberFormat = '^ @';

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## See also

* [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview)
* [Working with Cell Formatting](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-cell-formatting#apply-number-formats)
* [Working with Cells](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-cells)
* [Working with Conditional Formatting](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-conditional-formatting)
* [Range API reference](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Range-class.html)
* [Release notes](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/release-notes)
