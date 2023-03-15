---
layout: post
title: Excel General Function Formulas of Syncfusion Flutter XlsIO.
description: Learn how to apply general function formulas and to calculate value in the cells of Excel worksheet using Syncfusion Flutter XlsIO. 
platform: flutter
control: Excel
documentation: ug
---

# Working with General Function Formulas

General Function Formulas includes the following functions:

* SUM
* AVERAGE
* MAX
* MIN
* COUNT

## SUM Function

SUM function is used to add the arguments in the cells and returns the sum value.

The following code snippet illustrates on how to use SUM function formula.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

//Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

//set the value to the cell.
sheet.getRangeByName('A1').setNumber(10);
sheet.getRangeByName('A2').setNumber(20);
sheet.getRangeByName('A3').setNumber(4);
sheet.getRangeByName('A4').setNumber(12);
sheet.getRangeByName('B1').setNumber(2);
sheet.getRangeByName('B2').setNumber(16);
sheet.getRangeByName('B3').setNumber(8);
sheet.getRangeByName('B4').setNumber(11);

//Formula calculation is enabled for the sheet.
sheet.enableSheetCalculations();

//Setting formula in the cell.
sheet.getRangeByName('A6').setFormula('=SUM(A1,A2)');
sheet.getRangeByName('B6').setFormula('=SUM(A1:A4,B1:B4)');

//Save and dispose a workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();

File('SumFormula.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## AVERAGE Function

AVERAGE function is used to returns the average of the arguments in the cells.

The following code snippet illustrates on how to use AVERAGE function formula.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

//Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

//set the value to the cell.
sheet.getRangeByName('A1').setNumber(10);
sheet.getRangeByName('A2').setNumber(20);
sheet.getRangeByName('A3').setNumber(4);
sheet.getRangeByName('A4').setNumber(12);
sheet.getRangeByName('B1').setNumber(2);
sheet.getRangeByName('B2').setNumber(16);
sheet.getRangeByName('B3').setNumber(8);
sheet.getRangeByName('B4').setNumber(11);

//Formula calculation is enabled for the sheet.
sheet.enableSheetCalculations();

//Setting formula in the cell.
sheet.getRangeByName('A6').setFormula('=AVERAGE(A1,B1)');
sheet.getRangeByName('B6').setFormula('=AVERAGE(A1:A4,B1:B4)');

//Save and dispose a workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();

File('AverageFormula.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## MAX Function

MAX function is used to returns maximum value from a list of arguments in the Cells.

The following code snippet illustrates on how to use MAX function formula.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

//Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

//set the value to the cell.
sheet.getRangeByName('A1').setNumber(10);
sheet.getRangeByName('A2').setNumber(20);
sheet.getRangeByName('A3').setNumber(4);
sheet.getRangeByName('A4').setNumber(12);
sheet.getRangeByName('B1').setNumber(2);
sheet.getRangeByName('B2').setNumber(16);
sheet.getRangeByName('B3').setNumber(8);
sheet.getRangeByName('B4').setNumber(11);

//Formula calculation is enabled for the sheet.
sheet.enableSheetCalculations();

//Setting formula in the cell.
sheet.getRangeByName('A6').setFormula('=MAX(A1,B1)');
sheet.getRangeByName('B6').setFormula('=MAX(A1:A4,B1:B4)');

//Save and dispose a workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();

File('MaxFormula.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## MIN Function

MIN function is used to returns minimum value from a list of arguments in the Cells.

The following code snippet illustrates on how to use MIN function formula.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

//Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

//set the value to the cell.
sheet.getRangeByName('A1').setNumber(10);
sheet.getRangeByName('A2').setNumber(20);
sheet.getRangeByName('A3').setNumber(4);
sheet.getRangeByName('A4').setNumber(12);
sheet.getRangeByName('B1').setNumber(2);
sheet.getRangeByName('B2').setNumber(16);
sheet.getRangeByName('B3').setNumber(8);
sheet.getRangeByName('B4').setNumber(11);

//Formula calculation is enabled for the sheet.
sheet.enableSheetCalculations();

//Setting formula in the cell.
sheet.getRangeByName('A6').setFormula('=MIN(A1,B1)');
sheet.getRangeByName('B6').setFormula('=MIN(A1:A4,B1:B4)');

//Save and dispose a workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();

File('MinFormula.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## COUNT Function

COUNT function is used to count how many numbers are in the list of arguments.

The following code snippet illustrates on how to use COUNT function formula.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

//Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

//set the value to the cell.
sheet.getRangeByName('A1').setNumber(10);
sheet.getRangeByName('A2').setNumber(20);
sheet.getRangeByName('A3').setNumber(4);
sheet.getRangeByName('A4').setNumber(12);
sheet.getRangeByName('B1').setNumber(2);
sheet.getRangeByName('B2').setNumber(16);
sheet.getRangeByName('B3').setNumber(8);
sheet.getRangeByName('B4').setNumber(11);

//Formula calculation is enabled for the sheet.
sheet.enableSheetCalculations();

//Setting formula in the cell.
sheet.getRangeByName('A6').setFormula('=COUNT(A1,B1)');
sheet.getRangeByName('B6').setFormula('=COUNT(A1:A4,B1:B4)');

//Save and dispose a workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();

File('CountFormula.xlsx').writeAsBytes(bytes);

{% endhighlight %}



