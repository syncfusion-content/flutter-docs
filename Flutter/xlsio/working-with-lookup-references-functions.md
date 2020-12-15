---
layout: post
title: Excel Lookup and References Function Syncfusion Flutter XlsIO.
description: Learn how to apply Lookup and References function formulas and to calculate value in the cells of Excel worksheet using Syncfusion Flutter XlsIO. 
platform: flutter
control: Excel
documentation: ug
---

# Working with Lookup and References Function Formulas

Lookup and References Function Formulas includes the following functions:

* INDEX
* MATCH

## INDEX Function

INDEX function returns a value or the reference to a value from within a table or range.

The following code snippet illustrates on how to use INDEX function formula.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// set the value to the cell.
sheet.getRangeByName('A1').number = 10;
sheet.getRangeByName('A2').number = 5;
sheet.getRangeByName('B1').number = 4;
sheet.getRangeByName('B2').number = 8;

// Formula calculation is enabled for the sheet.
sheet.enableSheetCalculations();

// Setting formula in the cell.
Range range = sheet.getRangeByName('A4');
range.setFormula('=INDEX(A1:A2,2,1)');
range = sheet.getRangeByName('A6');
range.setFormula('=INDEX(A1:B2,1,1,1)');

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('INDEXFunction.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

## MATCH Function

MATCH function searches for a specified item in a range of cells, and then returns the relative position of that item in the range.

The following code snippet illustrates on how to use MATCH function formula.

{% highlight dart %}


// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// set the value to the cell.
sheet.getRangeByName('A1').number = 10;
sheet.getRangeByName('A2').number = 8;
sheet.getRangeByName('A3').number = 6;
sheet.getRangeByName('A4').number = 4;

// Formula calculation is enabled for the sheet.
sheet.enableSheetCalculations();

// Setting formula in the cell.
Range range = sheet.getRangeByName('A6');
range.setFormula('=MATCH(8,A1:A4,0)');
range = sheet.getRangeByName('A8');
range.setFormula('=MATCH(6,A1:A4,-1)');

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('MATCHFunction.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}



