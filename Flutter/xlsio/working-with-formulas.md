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

## Formula with Nested Functions

Using a function as one of the arguments in a formula is known as Nested Function.

The following code shows how to access a Nested Function.

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
  '=IF(SUM(AVERAGE(B4:B9), MAX(COUNT(B4,D4), MIN(B5,D5))) > 50, \'PASS\', \'FAIL\')');
range.calculatedValue;

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('NestedFunction.xlsx').writeAsBytes(bytes);
workbook.dispose();

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
<tr>
<td>

[AND]()

</td>
<td>
Returns TRUE if all of its arguments are TRUE
</td>
</tr>
<tr>
<td>

[OR]()

</td>
<td>
Returns TRUE if any argument is TRUE
</td>
</tr>
<tr>
<td>

[NOT]()

</td>
<td>
Reverses the logic of its argument
</td>
</tr>
<tr>
<td>

[CONCATENATE]()

</td>
<td>
Joins several text items into one text item
</td>
</tr>
<tr>
<td>

[TRIM]()

</td>
<td>
Removes spaces from text
</td>
</tr>
<tr>
<td>

[LOWER]()

</td>
<td>
Converts text to lowercase
</td>
</tr>
<tr>
<td>

[UPPER]()

</td>
<td>
Converts text to uppercase
</td>
</tr>
<tr>
<td>

[NOW]()

</td>
<td>
Returns the serial number of the current date and time
</td>
</tr>
<tr>
<td>

[TODAY]()

</td>
<td>
Returns the serial number of today's date
</td>
</tr>
<tr>
<td>

[INDEX]()

</td>
<td>
Uses an index to choose a value from a reference or array
</td>
</tr>
<tr>
<td>

[MATCH]()

</td>
<td>
Looks up values in a reference or array
</td>
</tr>
</table>
