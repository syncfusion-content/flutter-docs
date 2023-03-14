---
layout: post
title: Excel Statistical Function Formulas of Syncfusion Flutter XlsIO.
description: Learn how to apply statistical function formulas and to calculate value in the cells of Excel worksheet using Syncfusion Flutter XlsIO. 
platform: flutter
control: Excel
documentation: ug
---

# Working with Statistical Function Formulas

Statistical Function Formulas includes the following functions:

* AVERAGEIFS
* MINIFS
* MAXIFS
* COUNTIFS

## AVERAGEIFS Function

AVERAGEIFS function returns the average (arithmetic mean) of all cells that meet multiple criteria..

The following code snippet illustrates on how to use AVERAGEIFS function formula.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// set the value to the cell.
sheet.getRangeByName('A1').setText('Apple');
sheet.getRangeByName('A2').setText('Grapes');
sheet.getRangeByName('A3').setText('Apple');
sheet.getRangeByName('A4').setText('Grapes');
sheet.getRangeByName('A5').setText('Apple');
sheet.getRangeByName('B1').setNumber(58);
sheet.getRangeByName('B2').setNumber(1200);
sheet.getRangeByName('B3').setNumber(300);
sheet.getRangeByName('B4').setNumber(500);
sheet.getRangeByName('B5').setNumber(1000);
sheet.getRangeByName('C1').setNumber(2);
sheet.getRangeByName('C2').setNumber(3);
sheet.getRangeByName('C3').setNumber(4);
sheet.getRangeByName('C4').setNumber(2);
sheet.getRangeByName('C5').setNumber(1);

// Formula calculation is enabled for the sheet.
sheet.enableSheetCalculations();

// Setting formula in the cell.
Range range = sheet.getRangeByName('C6');
range.setFormula('=AVERAGEIFS(B1:B5,C1:C5,\">2\")');
range = sheet.getRangeByName('C7');
range.setFormula('=AVERAGEIFS(B1:B5,A1:A5,\"Apple\")');

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
File('AVERAGEIFSFunction.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

## MINIFS Function

MINIFS function returns the minimum value among cells specified by a given set of conditions or criteria.

The following code snippet illustrates on how to use MINIFS function formula.

{% highlight dart %}

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// set the value to the cell.
sheet.getRangeByName('A1').setText('Apple');
sheet.getRangeByName('A2').setText('Grapes');
sheet.getRangeByName('A3').setText('Apple');
sheet.getRangeByName('A4').setText('Grapes');
sheet.getRangeByName('A5').setText('Apple');
sheet.getRangeByName('B1').setNumber(58);
sheet.getRangeByName('B2').setNumber(1200);
sheet.getRangeByName('B3').setNumber(300);
sheet.getRangeByName('B4').setNumber(500);
sheet.getRangeByName('B5').setNumber(1000);
sheet.getRangeByName('C1').setNumber(2);
sheet.getRangeByName('C2').setNumber(3);
sheet.getRangeByName('C3').setNumber(4);
sheet.getRangeByName('C4').setNumber(2);
sheet.getRangeByName('C5').setNumber(1);

// Formula calculation is enabled for the sheet.
sheet.enableSheetCalculations();

// Setting formula in the cell.
Range range = sheet.getRangeByName('C6');
range.setFormula('=MINIFS(B1:B5,C1:C5,\">2\")');
range = sheet.getRangeByName('C7');
range.setFormula('=MINIFS(B1:B5,A1:A5,\"Apple\")');

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
File('MINIFSFunction.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

## MAXIFS Function

MAXIFS function returns the maximum value among cells specified by a given set of conditions or criteria.

The following code snippet illustrates on how to use MAXIFS function formula.

{% highlight dart %}

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// set the value to the cell.
sheet.getRangeByName('A1').setText('Apple');
sheet.getRangeByName('A2').setText('Grapes');
sheet.getRangeByName('A3').setText('Apple');
sheet.getRangeByName('A4').setText('Grapes');
sheet.getRangeByName('A5').setText('Apple');
sheet.getRangeByName('B1').setNumber(58);
sheet.getRangeByName('B2').setNumber(1200);
sheet.getRangeByName('B3').setNumber(300);
sheet.getRangeByName('B4').setNumber(500);
sheet.getRangeByName('B5').setNumber(1000);
sheet.getRangeByName('C1').setNumber(2);
sheet.getRangeByName('C2').setNumber(3);
sheet.getRangeByName('C3').setNumber(4);
sheet.getRangeByName('C4').setNumber(2);
sheet.getRangeByName('C5').setNumber(1);

// Formula calculation is enabled for the sheet.
sheet.enableSheetCalculations();

// Setting formula in the cell.
Range range = sheet.getRangeByName('C6');
range.setFormula('=MAXIFS(B1:B5,C1:C5,\">2\")');
range = sheet.getRangeByName('C7');
range.setFormula('=MAXIFS(B1:B5,A1:A5,\"Apple\")');

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
File('MAXIFSFunction.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

## COUNTIFS Function

COUNTIFS function applies criteria to cells across multiple ranges and counts the number of times all criteria are met.

The following code snippet illustrates on how to use COUNTIFS function formula.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// set the value to the cell.
sheet.getRangeByName('A1').setText('Apple');
sheet.getRangeByName('A2').setText('Grapes');
sheet.getRangeByName('A3').setText('Apple');
sheet.getRangeByName('A4').setText('Grapes');
sheet.getRangeByName('A5').setText('Apple');
sheet.getRangeByName('B1').setNumber(58);
sheet.getRangeByName('B2').setNumber(1200);
sheet.getRangeByName('B3').setNumber(300);
sheet.getRangeByName('B4').setNumber(500);
sheet.getRangeByName('B5').setNumber(1000);
sheet.getRangeByName('C1').setNumber(2);
sheet.getRangeByName('C2').setNumber(3);
sheet.getRangeByName('C3').setNumber(4);
sheet.getRangeByName('C4').setNumber(2);
sheet.getRangeByName('C5').setNumber(1);

// Formula calculation is enabled for the sheet.
sheet.enableSheetCalculations();

// Setting formula in the cell.
Range range = sheet.getRangeByName('C8');
range.setFormula('=COUNTIFS(A1:A5,\"Grapes\")');
range = sheet.getRangeByName('C9');
range.setFormula('=COUNTIFS(A1:A5,\"Apple\",C1:C5,\">2\")');

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
File('COUNTIFSFunction.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}
