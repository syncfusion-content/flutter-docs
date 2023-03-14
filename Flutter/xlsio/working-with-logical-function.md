---
layout: post
title: Excel Logical Function Formulas of Syncfusion Flutter XlsIO.
description: Learn how to apply logical function formulas and to calculate value in the cells of Excel worksheet using Syncfusion Flutter XlsIO. 
platform: flutter
control: Excel
documentation: ug
---

# Working with logical Function Formulas

Logical Function Formulas includes the following functions:

* IF
* AND
* OR
* NOT

## IF Function

IF function is used to make logical comparisons between a value and what you expect.

The following code snippet illustrates on how to use IF function formula.

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
sheet.getRangeByName('A6').setFormula('=IF(A4 > B3, \"Yes\", \"No\")');
sheet.getRangeByName('B6').setFormula('=IF(A4 < B3, A1+B1, A1-B1)');

//Save and dispose a workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();

File('IFFormula.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## AND Function

AND function is a logical function that tests multiple conditions. In these simple examples, the formula will display TRUE if all of the conditions are satisfied, and FALSE if even one condition is not satisfied.

The following code snippet illustrates on how to use AND function formula.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// set the value to the cell.
sheet.getRangeByName('A1').setNumber(75);
sheet.getRangeByName('A2').setNumber(32);
sheet.getRangeByName('A3').setNumber(84);
sheet.getRangeByName('A4').setNumber(57);
sheet.getRangeByName('A5').setNumber(65);

// Formula calculation is enabled for the sheet.
sheet.enableSheetCalculations();

// Setting formula in the cell.
Range range = sheet.getRangeByName('B1');
range.setFormula('=AND(A1>35,A1<75)');
range = sheet.getRangeByName('B5');
range.setFormula('=AND(A5>35,A5<75)');

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
File('ANDFunc.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

## OR Function

OR Function is a logical function to check whether any of arguments are TRUE, and returns TRUE or FALSE. Return FALSE only When all arguments are FALSE. 

The following code snippet illustrates on how to use OR function formula.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// set the value to the cell.
sheet.getRangeByName('A1').setText('Green');
sheet.getRangeByName('A2').setText('Red');
sheet.getRangeByName('A3').setText('Blue');
sheet.getRangeByName('A4').setText('Red');
sheet.getRangeByName('A5').setText('Green');
sheet.getRangeByName('A6').setText('Blue');

// Formula calculation is enabled for the sheet.
sheet.enableSheetCalculations();

// Setting formula in the cell.
Range range = sheet.getRangeByName('B1');
range.setFormula('=OR(A1=\"Green\",A1=\"Red\")');
range = sheet.getRangeByName('B5');
range.setFormula('=OR(A3=\"Green\",A3=\"Red\")');

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
File('ORFunc.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

## NOT Function

NOT Function to changes FALSE to TRUE or TRUE to FALSE.

The following code snippet illustrates on how to use NOT function formula.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// set the value to the cell.
sheet.getRangeByName('A1').setText('Green');
sheet.getRangeByName('A2').setText('Red');
sheet.getRangeByName('A3').setText('Blue');
sheet.getRangeByName('A4').setText('Red');
sheet.getRangeByName('A5').setText('Green');
sheet.getRangeByName('A6').setText('Blue');

// Formula calculation is enabled for the sheet.
sheet.enableSheetCalculations();

// Setting formula in the cell.
Range range = sheet.getRangeByName('B1');
range.setFormula('=NOT(A1=\"Green\")');
range = sheet.getRangeByName('B5');
range.setFormula('=NOT(A3=\"Red\")');

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
File('NOTFunc.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

