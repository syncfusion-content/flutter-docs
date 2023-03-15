---
layout: post
title: Excel NumberFormat of Syncfusion Flutter XlsIO.
description: Learn how to apply number format to cell or range of cells in Excel worksheet using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with Number Formats

Number Formats are codes that helps to control the appearance of cell values especially numbers in an Excel document. Excel recognizes the numbers in various formats like:

* Number
* Currency
* Percentage
* DateTime
* Accounting
* Scientific
* Fraction and
* Text

## Number

The following code snippet illustrates how to set different number formats in a worksheet range.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

final Range range = sheet.getRangeByIndex(1, 1);
range.setNumber(279);
range.numberFormat = '0.0';

final Range range1 = sheet.getRangeByIndex(2, 1);
range1.setNumber(-2211);
range1.numberFormat = '#,##0.00';

final Range range2 = sheet.getRangeByIndex(3, 1);
range2.setNumber(9032);
range2.numberFormat = '[Blue](#,##0.000)';

final Range range3 = sheet.getRangeByIndex(4, 1);
range3.setNumber(1291);
range3.numberFormat = '(#,##0.0000)';

final Range range4 = sheet.getRangeByIndex(5, 1);
range4.setNumber(-22);
range4.numberFormat = '#,##0.00000_)';

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();
File('Number.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Currency 

The following code snippet illustrates how to set different currency number formats in a worksheet range.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

final Range range = sheet.getRangeByIndex(1, 1);
range.setNumber(2955);
range.numberFormat = '\$#,##0.0';

final Range range1 = sheet.getRangeByName('A2');
range1.setNumber(22.11);
range1.numberFormat = '([Red]\$0.00)';

final Range range2 = sheet.getRangeByIndex(3, 1);
range2.setNumber(9312);
range2.numberFormat = '(\$#,##0.00)';

final Range range3 = sheet.getRangeByName('A4');
range3.setNumber(111);
range3.numberFormat = '[BLUE]\$0.0000';

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();
File('Currency.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Percentage

The following code snippet illustrates how to set different percentage number formats in a worksheet range.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

final Range range = sheet.getRangeByIndex(1, 1);
range.setNumber(29);
range.numberFormat = '0%';

final Range range1 = sheet.getRangeByName('A2');
range1.setNumber(22.11);
range1.numberFormat = '0.00%';

final Range range2 = sheet.getRangeByIndex(3, 1);
range2.setNumber(0.09312);
range2.numberFormat = '0.000%';

final Range range3 = sheet.getRangeByName('A4');
range3.setNumber(0.111);
range3.numberFormat = '0.0000%';

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();
File('Percentage.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## DateTime
**Date**
The following code snippet illustrates how to set different date number formats in a worksheet range.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

final Range range = sheet.getRangeByIndex(1, 1);
range.setDateTime(DateTime(2020, 8, 23, 8, 15, 20));
range.numberFormat = 'm/d/yyyy';

final Range range1 = sheet.getRangeByName('A2');
range1.setDateTime(DateTime(2002, 12, 3, 23, 45, 45));
range1.numberFormat = 'dddd, mmmm dd, yyyy';

final Range range2 = sheet.getRangeByIndex(3, 1);
range2.setDateTime(DateTime(2012, 11, 22, 5, 45, 45));
range2.numberFormat = 'yyyy-mm-dd';

final Range range3 = sheet.getRangeByName('A4');
range3.setDateTime(DateTime(2014, 10, 12, 20, 5, 5));
range3.numberFormat = 'm/d';

final Range range4 = sheet.getRangeByIndex(5, 1);
range4.setDateTime(DateTime(2020, 8, 23, 8, 15, 20));
range4.numberFormat = 'm/d/yy';

final Range range5 = sheet.getRangeByName('A6');
range5.setDateTime(DateTime(1999, 7, 30, 5, 34, 40));
range5.numberFormat = 'mm/dd/yy';

final Range range6 = sheet.getRangeByIndex(7, 1);
range6.setDateTime(DateTime(2012, 11, 22, 5, 45, 45));
range6.numberFormat = 'd-mmm';

final Range range7 = sheet.getRangeByName('A8');
range7.setDateTime(DateTime(2014, 10, 12, 20, 5, 5));
range7.numberFormat = 'd-mmm-yy';

final Range range8 = sheet.getRangeByIndex(9, 1);
range8.setDateTime(DateTime(2020, 8, 23, 8, 15, 20));
range8.numberFormat = 'mmmm-yy';

final Range range9 = sheet.getRangeByName('A10');
range9.setDateTime(DateTime(2002, 12, 3, 23, 45, 45));
range9.numberFormat = 'mmmm d, yyyy';

final Range range10 = sheet.getRangeByIndex(11, 1);
range10.setDateTime(DateTime(2012, 11, 22, 5, 45, 45));
range10.numberFormat = 'mmmmm';

final Range range11 = sheet.getRangeByName('A12');
range11.setDateTime(DateTime(2014, 10, 12, 20, 5, 5));
range11.numberFormat = 'mmmmm-yy';

final Range range12 = sheet.getRangeByIndex(13, 1);
range12.setDateTime(DateTime(2020, 8, 23, 8, 15, 20));
range12.numberFormat = 'd-mmm-yyyy';

final Range range13 = sheet.getRangeByName('A14');
range13.setDateTime(DateTime(2002, 12, 3, 23, 45, 45));
range13.numberFormat = 'm/d/yy h:mm AM/PM';

final Range range14 = sheet.getRangeByIndex(15, 1);
range14.setDateTime(DateTime(2012, 11, 22, 5, 45, 45));
range14.numberFormat = 'm/d/yy h:mm';

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();
File('Date.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Time

The following code snippet illustrates how to set different time number formats in a worksheet range.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

final Range range = sheet.getRangeByIndex(1, 1);
range.setDateTime(DateTime(2020, 8, 23, 8, 15, 20));
range.numberFormat = 'h:mm:ss AM/PM';

final Range range1 = sheet.getRangeByName('A2');
range1.setDateTime(DateTime(2002, 12, 3, 23, 45, 45));
range1.numberFormat = 'h:mm';

final Range range2 = sheet.getRangeByIndex(3, 1);
range2.setDateTime(DateTime(2012, 11, 22, 5, 45, 45));
range2.numberFormat = 'h:mm AM/PM';

final Range range3 = sheet.getRangeByName('A4');
range3.setDateTime(DateTime(2014, 10, 12, 20, 5, 5));
range3.numberFormat = 'h:mm:ss';

final Range range4 = sheet.getRangeByIndex(5, 1);
range4.setDateTime(DateTime(2020, 8, 23, 8, 15, 20));
range4.numberFormat = 'mm:ss.0';

final Range range5 = sheet.getRangeByName('A6');
range5.setDateTime(DateTime(1999, 7, 30, 5, 34, 40));
range5.numberFormat = '[h]:mm:ss';

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();
File('Time.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Accounting

The following code snippet illustrates how to set different accounting number formats in a worksheet range.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

final Range range = sheet.getRangeByIndex(1, 1);
range.setNumber(79);
range.numberFormat = '_(\$* #,##0_)';

final Range range1 = sheet.getRangeByIndex(2, 1);
range1.setNumber(2211);
range1.numberFormat = '_(\$* (#,##0.00)';

final Range range2 = sheet.getRangeByIndex(3, 1);
range2.setNumber(9.032);
range2.numberFormat = '_(\$* "-"???_)';

final Range range3 = sheet.getRangeByIndex(4, 1);
range3.setNumber(1.1291);
range3.numberFormat = '_(\$* #,##0.0000_)';

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();
File('Accounting.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Scientific

The following code snippet illustrates how to set different scientific number formats in a worksheet range.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

final Range range = sheet.getRangeByIndex(1, 1);
range.setNumber(791);
range.numberFormat = '0.E+00';

final Range range1 = sheet.getRangeByIndex(2, 1);
range1.setNumber(22.11);
range1.numberFormat = '0.00E+00';

final Range range2 = sheet.getRangeByIndex(3, 1);
range2.setNumber(9.1032);
range2.numberFormat = '0.0000E+00';

final Range range3 = sheet.getRangeByIndex(4, 1);
range3.setNumber(11.1);
range3.numberFormat = '0.0E+00';

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();
File('Scientific.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Fraction

The following code snippet illustrates how to set different fraction formats in a worksheet range.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

final Range range = sheet.getRangeByIndex(1, 1);
range.setNumber(29.4);
range.numberFormat = '# ?/?';

final Range range1 = sheet.getRangeByName('A2');
range1.setNumber(22.11);
range1.numberFormat = '# ??/??';

final Range range2 = sheet.getRangeByIndex(3, 1);
range2.setNumber(0.09312);
range2.numberFormat = '# ???/???';

final Range range3 = sheet.getRangeByName('A4');
range3.setNumber(11.4);
range3.numberFormat = '# ?/2';

final Range range4 = sheet.getRangeByIndex(5, 1);
range4.setNumber(47.98);
range4.numberFormat = '# ?/4';

final Range range5 = sheet.getRangeByName('A6');
range5.setNumber(7.39);
range5.numberFormat = '# ?/8';

final Range range6 = sheet.getRangeByIndex(7, 1);
range6.setNumber(21.5);
range6.numberFormat = '# ??/16';

final Range range7 = sheet.getRangeByName('A8');
range7.setNumber(13.1);
range7.numberFormat = '# ?/10';

final Range range8 = sheet.getRangeByIndex(9, 1);
range8.setNumber(49.56);
range8.numberFormat = '# ??/100';

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();
File('Fraction.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Text 

Text format cells are treated as text even when a number is in the cell. The cell is displayed exactly as entered.

The following code snippet illustrates how to set different text formats in a worksheet range.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

final Range range = sheet.getRangeByIndex(1, 1);
range.setNumber(-12.89);
range.numberFormat = '@';

final Range range1 = sheet.getRangeByName('A2');
range1.setNumber(2311);
range1.numberFormat = '_(@_)';

final Range range2 = sheet.getRangeByIndex(3, 1);
range2.setNumber(0.09312);
range2.numberFormat = '* @';

final Range range3 = sheet.getRangeByName('A4');
range3.setNumber(11.4);
range3.numberFormat = '^ @';

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();
File('Text.xlsx').writeAsBytes(bytes);

{% endhighlight %}