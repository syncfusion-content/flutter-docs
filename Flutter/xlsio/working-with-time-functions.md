---
layout: post
title: Excel Time Function Formulas of Syncfusion Flutter XlsIO.
description: Learn how to apply Time function formulas and to calculate value in the cells of Excel worksheet using Syncfusion Flutter XlsIO. 
platform: flutter
control: Excel
documentation: ug
---

# Working with Time Function Formulas

Time Function Formulas includes the following functions:

* NOW
* TODAY

## NOW Function

NOW Function is used to returns the serial number of the current date and time.

The following code snippet illustrates on how to use NOW function formula.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Formula calculation is enabled for the sheet.
sheet.enableSheetCalculations();

// Setting formula in the cell.
final Range range = sheet.getRangeByName('A1');
range.setFormula('=NOW()');
double.parse(range.calculatedValue).toStringAsFixed(2);
range.numberFormat = 'm/d/yyyy h:mm';

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
File('NOWFunction.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

## TODAY Function

TODAY Function is used to returns the serial number of the current date.

The following code snippet illustrates on how to use TODAY function formula.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Formula calculation is enabled for the sheet.
sheet.enableSheetCalculations();

// Setting formula in the cell.
final Range range = sheet.getRangeByName('A1');
range.setFormula('=TODAY()');
range.numberFormat = 'mm/dd/yyyy';

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
File('TODAYFunction.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}




