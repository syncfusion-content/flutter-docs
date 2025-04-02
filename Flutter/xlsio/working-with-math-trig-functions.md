---
layout: post
title: Excel Math and Trig Function Formulas of Syncfusion Flutter XlsIO.
description: Learn how to apply Math and Trig function formulas and to calculate value in the cells of Excel worksheet using Syncfusion Flutter XlsIO. 
platform: flutter
control: Excel
documentation: ug
---

# Working with Math and Trig Function Formulas

Math and Trig Function Formulas includes the following functions:

* SUMIF
* SUMIFS
* SUMPRODUCT
* PRODUCT

## SUMIF Function

SUMIF function to sum the values in a range that meet criteria that specify

The following code snippet illustrates on how to use SUMIF function formula.

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
range.setFormula('=SUMIF(A1:A5,A2,B1:B5)');
range = sheet.getRangeByName('C9');
range.setFormula('=SUMIF(C1:C5,C4,B1:B5)');

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
File('SUMIFFunction.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

## SUMIFS Function

SUMIFS function used to adds all of its arguments that meet multiple criteria.

The following code snippet illustrates on how to use SUMIFS function formula.

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
range.setFormula('=SUMIFS(B1:B5,C1:C5,\">=2\")');
range = sheet.getRangeByName('C9');
range.setFormula('=SUMIFS(B1:B5,A1:A5,\"Apple\")');

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
File('SUMIFSFunction.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

## SUMPRODUCT Function

SUMPRODUCT function returns the sum of the products of corresponding ranges or arrays.

The following code snippet illustrates on how to use SUMPRODUCT function formula.

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
range.setFormula('=SUMPRODUCT(B1:B5,C1:C5)');
range = sheet.getRangeByName('C9');
range.setFormula('=SUMPRODUCT(--(A1:A5=\"Apple\"), B1:B5, C1:C5)');

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
File('SUMPRODUCTFunction.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

## PRODUCT Function

PRODUCT function multiplies all the numbers given as arguments and returns the product.

The following code snippet illustrates on how to use PRODUCT function formula.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// set the value to the cell.
sheet.getRangeByName('A1').setNumber(2);
sheet.getRangeByName('B1').setNumber(3);
sheet.getRangeByName('A2').setNumber(5);
sheet.getRangeByName('B2').setNumber(4);
sheet.getRangeByName('A3').setNumber(6);
sheet.getRangeByName('B3').setNumber(7);
sheet.getRangeByName('A4').setNumber(9);
sheet.getRangeByName('B4').setNumber(8);

// Formula calculation is enabled for the sheet.
sheet.enableSheetCalculations();

// Setting formula in the cell.
Range range = sheet.getRangeByName('C8');
range.setFormula('=PRODUCT(A1:A4,B1:B4)');
range = sheet.getRangeByName('C9');
range.setFormula('=PRODUCT(A1,B1)');

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
File('PRODUCTFunction.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}


