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
sheet.getRangeByName('A6').setFormula('=IF(A4 > B3, \'Yes\', \'No\')');
sheet.getRangeByName('B6').setFormula('=IF(A4 < B3, A1+B1, A1-B1)');

sheet.getRangeByName('A6').calculatedValue;
sheet.getRangeByName('A6').calculatedValue;

//Save and dispose a workbook.
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

File('IFFormula.xlsx').writeAsBytes(bytes);

{% endhighlight %}