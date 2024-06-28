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
final List<int> bytes = workbook.saveSync();
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
final List<int> bytes = workbook.saveSync();
workbook.dispose();

File('Formula.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Accessing a Calculated value

To evaluate formula, it is must to [enable sheet calculation](https://help.syncfusion.com/flutter/xlsio/working-with-formulas#enable-calculation) in prior. After enabling the sheet calculation, the formula can be evaluated using **calculatedValue** of **Range**, which returns a string value.

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
final List<int> bytes = workbook.saveSync();
workbook.dispose();

File('Formula.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Formula with Nested Functions

Using a function as one of the arguments in a formula is known as Nested Function.

The following code shows how to use nested functions.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// set the value to the cell.
sheet.getRangeByName('B3').setText('Team A');
sheet.getRangeByName('B4').setNumber(47);
sheet.getRangeByName('B5').setNumber(43);
sheet.getRangeByName('B6').setNumber(40);
sheet.getRangeByName('B7').setNumber(51);
sheet.getRangeByName('B8').setNumber(53);
sheet.getRangeByName('B9').setNumber(50);

sheet.getRangeByName('D3').setText('Team B');
sheet.getRangeByName('D4').setNumber(72);
sheet.getRangeByName('D5').setNumber(43);
sheet.getRangeByName('D6').setNumber(84);
sheet.getRangeByName('D7').setNumber(90);
sheet.getRangeByName('D8').setNumber(42);
sheet.getRangeByName('D9').setNumber(56);

// Formula calculation is enabled for the sheet.
sheet.enableSheetCalculations();

// Setting formula in the cell.
final Range range = sheet.getRangeByName('B11');
range.setFormula(
  '=IF(SUM(AVERAGE(B4:B9), MAX(COUNT(B4,D4), MIN(B5,D5))) > 50, \"PASS\", \"FAIL\")');

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
File('NestedFunction.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

## Supported Formulas

In flutter XlsIO, we have support for Range reference and basic function formula listed below:

<table>
<tr>
<td>
<a href="https://help.syncfusion.com/flutter/xlsio/working-with-general-functions#sum-function">SUM</a>
</td>
<td>
Adds its arguments
</td>
</tr>
<tr>
<td>
<a href="https://help.syncfusion.com/flutter/xlsio/working-with-general-functions#average-function
">AVERAGE</a>
</td>
<td>
Returns the average of its arguments
</td>
</tr>
<tr>
<td>
<a href="https://help.syncfusion.com/flutter/xlsio/working-with-general-functions#max-function">MAX</a>
</td>
<td>
Returns the maximum value in a list of arguments
</td>
</tr>
<tr>
<td>
<a href="https://help.syncfusion.com/flutter/xlsio/working-with-general-functions#min-function">MIN</a>
</td>
<td>
Returns the minimum value in a list of arguments
</td>
</tr>
<tr>
<td>
<a href="https://help.syncfusion.com/flutter/xlsio/working-with-general-functions#count-function
">COUNT</a>
</td>
<td>
Counts how many numbers are in the list of arguments
</td>
</tr>
<tr>
<td>
<a href="https://help.syncfusion.com/flutter/xlsio/working-with-logical-function#if-function">IF</a>
</td>
<td>
Specifies a logical test to perform
</td>
</tr>
<tr>
<td>
<a href="https://help.syncfusion.com/flutter/xlsio/working-with-logical-function#and-function">AND</a>
</td>
<td>
Returns TRUE if all of its arguments are TRUE
</td>
</tr>
<tr>
<td>
<a href="https://help.syncfusion.com/flutter/xlsio/working-with-logical-function#or-function">OR</a>
</td>
<td>
Returns TRUE if any argument is TRUE
</td>
</tr>
<tr>
<td>
<a href="https://help.syncfusion.com/flutter/xlsio/working-with-logical-function#not-function">NOT</a>
</td>
<td>
Reverses the logic of its argument
</td>
</tr>
<tr>
<td>
<a href="https://help.syncfusion.com/flutter/xlsio/working-with-text-functions#concatenate-function">CONCATENATE</a>
</td>
<td>
Joins several text items into one text item
</td>
</tr>
<tr>
<td>
<a href="https://help.syncfusion.com/flutter/xlsio/working-with-text-functions#trim-function">TRIM</a>
</td>
<td>
Removes spaces from text
</td>
</tr>
<tr>
<td>
<a href="https://help.syncfusion.com/flutter/xlsio/working-with-text-functions#lower-function">LOWER</a>
</td>
<td>
Converts text to lowercase
</td>
</tr>
<tr>
<td>
<a href="https://help.syncfusion.com/flutter/xlsio/working-with-text-functions#upper-function">UPPER</a>
</td>
<td>
Converts text to uppercase
</td>
</tr>
<tr>
<td>
<a href="https://help.syncfusion.com/flutter/xlsio/working-with-time-functions#now-function">NOW</a>
</td>
<td>
Returns the serial number of the current date and time
</td>
</tr>
<tr>
<td>
<a href="https://help.syncfusion.com/flutter/xlsio/working-with-time-functions#today-function">TODAY</a>
</td>
<td>
Returns the serial number of today's date
</td>
</tr>
<tr>
<td>
<a href="https://help.syncfusion.com/flutter/xlsio/working-with-lookup-references-functions#index-function">INDEX</a>
</td>
<td>
Uses an index to choose a value from a reference or array
</td>
</tr>
<tr>
<td>
<a href="https://help.syncfusion.com/flutter/xlsio/working-with-lookup-references-functions#match-function">MATCH</a>
</td>
<td>
Looks up values in a reference or array
</td>
</tr>
<tr>
<td>
<a href="">PRODUCT</a>
</td>
<td>
Multiplies its arguments
</td>
</tr>
<tr>
<td>
<a href="">SUMPRODUCT</a>
</td>
<td>
Returns the sum of the products of corresponding array components
</td>
</tr>
<tr>
<td>
<a href="">SUMIF</a>
</td>
<td>
Adds the cells specified by a given criteria
</td>
</tr>
<tr>
<td>
<a href="">VLOOKUP</a>
</td>
<td>
Looks in the first column of an array and moves across the row to return the value of a cell
</td>
</tr>
<tr>
<td>
<a href="">COUNTIFS</a>
</td>
<td>
Counts the number of times all criteria are met.
</td>
</tr>
<tr>
<td>
<a href="">MAXIFS</a>
</td>
<td>
Returns the maximum value among cells specified by a given set of conditions or criteria
</td>
</tr>
<tr>
<td>
<a href="">MINIFS</a>
</td>
<td>
Returns the minimum value among cells specified by a given set of conditions or criteria
</td>
</tr>
<tr>
<td>
<a href="">SUMIF</a>
</td>
<td>
Adds the cells specified by a given criteria
</td>
</tr>
<tr>
<td>
<a href="">SUMIFS</a>
</td>
<td>
Adds all of its arguments that meet multiple criteria
</td>
</tr>
</table>
