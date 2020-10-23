---
layout: post
title: Excel Formula of Syncfusion Flutter XlsIO.
description: Learn how to apply formulas and to calculate value in the cells of Excel worksheet using Syncfusion Flutter XlsIO. 
platform: flutter
control: Excel
documentation: ug
---

# Working with Formulas

Formulas are entries in Excel that have equations, by which values are calculated. A typical formula might contain cell references, constants, and even functions.

## Enable Calculation

To perform calculation in an Excel workbook, it is recommended to invoke **enableSheetCalculations()** method of **Worksheet**. Enabling this method will initialize **CalcEngine** objects and retrieves calculated values of formulas in a worksheet.

The following code sample illustrates on how to enable worksheet formula calculations.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

//Formula calculation is enabled for the sheet
sheet.enableSheetCalculations();

// Save and dispose workbook
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

File('Output.xlsx').writeAsBytes(bytes);

{% endhighlight %}


## Apply Formula

In a worksheet, formulas can be entered by using the **setFormula()** method of the Range instance.
Following code example illustrates on how to write a formula.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

//Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

//set the value to the cell.
sheet.getRangeByName('A1').setNumber(10);
sheet.getRangeByName('A2').setNumber(20);

//Setting formula in the cell.
sheet.getRangeByName('A3').setFormula('=A1+A2');

//Save and dispose a workbook.
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

File('Formula.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Accessing a Calculated value

To evaluate formula, it is must to [enable sheet calculation](enable-sheet-calculation) in prior. After enabling the sheet calculation, the formula can be evaluated using **calculatedValue** of **Range**, which returns a string value.

The following code shows how to access a calculated value.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Formula calculation is enabled for the sheet.
sheet.enableSheetCalculations();

// set the value to the cell.
sheet.getRangeByName('A1').setNumber(10);
sheet.getRangeByName('A2').setNumber(20);

// Setting formula in the cell.
sheet.getRangeByName('A3').setFormula('=A1+A2');

// Returns the calculated value of a formula using the most current inputs
String calculatedValue = sheet.getRangeByName('A3').calculatedValue;

// Save and dispose a workbook.
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

File('Formula.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Supported Formulas

In flutter XlsIO, we have support for Range reference and basic function formula listed below:

<table>
<tr>
<td>

[SUM](https://help.syncfusion.com/flutter/xlsio/working-with-general-functions#sum-function)

</td>
<td>
Adds its arguments
</td>
</tr>
<tr>
<td>

[AVERAGE](https://help.syncfusion.com/flutter/xlsio/working-with-general-functions#average-function)

</td>
<td>
Returns the average of its arguments
</td>
</tr>
<tr>
<td>

[MAX](https://help.syncfusion.com/flutter/xlsio/working-with-general-functions#max-function)

</td>
<td>
Returns the maximum value in a list of arguments
</td>
</tr>
<tr>
<td>

[MIN](https://help.syncfusion.com/flutter/xlsio/working-with-general-functions#min-function)

</td>
<td>
Returns the minimum value in a list of arguments
</td>
</tr>
<tr>
<td>

[COUNT](https://help.syncfusion.com/flutter/xlsio/working-with-general-functions#count-function)

</td>
<td>
Counts how many numbers are in the list of arguments
</td>
</tr>
<tr>
<td>

[IF](https://help.syncfusion.com/flutter/xlsio/working-with-logical-function#if-function)

</td>
<td>
Specifies a logical test to perform
</td>
</tr>
</table>
