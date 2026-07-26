---
layout: post
title: Excel Data Validation Syncfusion Flutter XlsIO
description: Learn how to use different types of data validations on Excel data using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with Excel Data Validation

Data validation is a list of rules for the data that can be entered into a cell. XlsIO supports the following data validation types.

* Text Length Validation
* Time Validation
* List Validation
* Whole Number Validation
* Decimal Number Validation
* Date Validation
* Custom Validation

N> Before you begin, complete the [Getting Started with Flutter XlsIO](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/getting-started) steps, then import the package in your Dart file:

{% highlight dart %}
import 'dart:io'; // for File
import 'package:syncfusion_flutter_xlsio/xlsio.dart';
{% endhighlight %}

N> In production code, use `await workbook.save()` and wrap workbook usage in a `try/finally` block to guarantee `workbook.dispose()`. The samples below use `saveSync()` for brevity.

The supported values of `ExcelDataValidationType` are `textLength`, `time`, `list`, `integer`, `decimal`, `date`, and `formula`. The supported values of `ExcelDataValidationComparisonOperator` are `between`, `notBetween`, `equal`, `notEqual`, `greaterThan`, `lessThan`, `greaterThanOrEqual`, and `lessThanOrEqual`.

## Text Length Validation

Text length data validation can be applied by setting `allowType` to `textLength`. The following code snippet allows values whose length is between `firstFormula` and `secondFormula` characters.

{% highlight dart %}
// Create a new Excel document and access the first sheet.
final Workbook workbook = Workbook();
final Worksheet sheet = workbook.worksheets[0];

// Data validation for text length.
final DataValidation textLengthValidation = sheet.getRangeByName('A1').dataValidation;
textLengthValidation.allowType = ExcelDataValidationType.textLength;

// Text length should be between 1 and 5 characters.
textLengthValidation.comparisonOperator = ExcelDataValidationComparisonOperator.between;
textLengthValidation.firstFormula = '1';
textLengthValidation.secondFormula = '5';
{% endhighlight %}

## Time Validation

Time data validation can be applied by setting `allowType` to `time`. The following code snippet allows values between the two times given in `firstFormula` and `secondFormula`.

{% highlight dart %}
// Create a new Excel document and access the first sheet.
final Workbook workbook = Workbook();
final Worksheet sheet = workbook.worksheets[0];

// Data validation for time.
final DataValidation timeValidation = sheet.getRangeByName('A3').dataValidation;
timeValidation.allowType = ExcelDataValidationType.time;

// Time between 10:00 and 12:00 o'clock.
timeValidation.comparisonOperator = ExcelDataValidationComparisonOperator.between;
timeValidation.firstFormula = '10:00';
timeValidation.secondFormula = '12:00';
{% endhighlight %}

N> Time values should be entered in 24-hour format using the `HH:MM` pattern, without appending AM or PM.

## List Validation

List data validation can be applied by assigning values to `listOfValues`. When the list is entered manually, the total length of the values (including the separators) is limited to 255 characters. The following code snippet illustrates this.

{% highlight dart %}
// Create a new Excel document and access the first sheet.
final Workbook workbook = Workbook();
final Worksheet sheet = workbook.worksheets[0];

// Data validation for a list.
final DataValidation listValidation = sheet.getRangeByName('A3').dataValidation;
listValidation.listOfValues = <String>['ListItem1', 'ListItem2', 'ListItem3'];
{% endhighlight %}

For longer lists, point the validation at a cell range by using the `dataRange` property — see the [Complete code snippet](#complete-code-snippet) below for a worked example.

## Whole Number Validation

Whole-number data validation can be applied by setting `allowType` to `integer`. The following code snippet allows integer values between `firstFormula` and `secondFormula`.

{% highlight dart %}
// Create a new Excel document and access the first sheet.
final Workbook workbook = Workbook();
final Worksheet sheet = workbook.worksheets[0];

// Data validation for whole numbers.
final DataValidation integerValidation = sheet.getRangeByName('A3').dataValidation;
integerValidation.allowType = ExcelDataValidationType.integer;

// Value between 0 and 10.
integerValidation.comparisonOperator = ExcelDataValidationComparisonOperator.between;
integerValidation.firstFormula = '0';
integerValidation.secondFormula = '10';
{% endhighlight %}

## Decimal Number Validation

Decimal-number data validation can be applied by setting `allowType` to `decimal`. The following code snippet allows decimal values between `firstFormula` and `secondFormula`.

{% highlight dart %}
// Create a new Excel document and access the first sheet.
final Workbook workbook = Workbook();
final Worksheet sheet = workbook.worksheets[0];

// Use G1 as a label describing what G3 should contain.
sheet.getRangeByName('G1').setText('Enter the Decimal Number in G3');

// Data validation for decimals.
final DataValidation decimalValidation = sheet.getRangeByName('G3').dataValidation;
decimalValidation.allowType = ExcelDataValidationType.decimal;
decimalValidation.comparisonOperator = ExcelDataValidationComparisonOperator.between;
decimalValidation.firstFormula = '1.0';
decimalValidation.secondFormula = '10.0';
{% endhighlight %}

## Date Validation

Date data validation can be applied by setting `allowType` to `date`. For date values, use the typed properties `firstDateTime` and `secondDateTime` instead of `firstFormula` and `secondFormula`. The following code snippet allows dates between `firstDateTime` and `secondDateTime`.

{% highlight dart %}
// Create a new Excel document and access the first sheet.
final Workbook workbook = Workbook();
final Worksheet sheet = workbook.worksheets[0];

// Data validation for dates.
final DataValidation dateValidation = sheet.getRangeByName('A3').dataValidation;
dateValidation.allowType = ExcelDataValidationType.date;

// Date between 10/5/2003 and 10/5/2004.
dateValidation.comparisonOperator = ExcelDataValidationComparisonOperator.between;
dateValidation.firstDateTime = DateTime(2003, 5, 10);
dateValidation.secondDateTime = DateTime(2004, 5, 10);
{% endhighlight %}

## Custom Validation

Custom validation can be applied by setting `allowType` to `formula` and providing an Excel formula via `firstFormula`. The validation rule is evaluated against the cell that references the formula.

{% highlight dart %}
// Create a new Excel document and access the first sheet.
final Workbook workbook = Workbook();
final Worksheet sheet = workbook.worksheets[0];

// Data validation using a custom formula: target cell must be greater than 10
// relative to A1 on the same sheet.
final DataValidation customValidation = sheet.getRangeByName('A3').dataValidation;
customValidation.allowType = ExcelDataValidationType.formula;
customValidation.firstFormula = '=A1>10';
{% endhighlight %}

N> The custom formula is interpreted by Excel using absolute references as written. If you want the rule to depend on the same cell that holds the validation, use a relative reference (for example `=A3>10`) or reference the active cell directly.

## Complete code snippet

The following complete code snippet demonstrates all the data validation types above, along with error/prompt tooltip styling and a `dataRange`-based list validation. Copying the snippet into a Flutter project produces a workbook that displays one validation rule per column from A3 to H3.

{% highlight dart %}
// Create a new Excel document and access the first sheet.
final Workbook workbook = Workbook();
final Worksheet sheet = workbook.worksheets[0];

// Data validation for text length.
final DataValidation textLengthValidation = sheet.getRangeByName('A3').dataValidation;
sheet.getRangeByName('A1').setText('Enter the text in A3');
textLengthValidation.allowType = ExcelDataValidationType.textLength;
textLengthValidation.comparisonOperator = ExcelDataValidationComparisonOperator.between;
textLengthValidation.firstFormula = '0';
textLengthValidation.secondFormula = '5';

// Show the error message.
textLengthValidation.showErrorBox = true;
textLengthValidation.errorBoxText = 'Text length should be less than 5 characters';
textLengthValidation.errorBoxTitle = 'ERROR';
textLengthValidation.promptBoxText = 'Data validation for text length';
textLengthValidation.showPromptBox = true;

// Data validation for time.
final DataValidation timeDataValidation = sheet.getRangeByName('B3').dataValidation;
sheet.getRangeByName('B1').setText('Enter the time between 10:00 and 12:00 o\'clock in B3');
timeDataValidation.allowType = ExcelDataValidationType.time;
timeDataValidation.comparisonOperator = ExcelDataValidationComparisonOperator.between;
timeDataValidation.firstFormula = '10:00';
timeDataValidation.secondFormula = '12:00';

// Show the error message.
timeDataValidation.showErrorBox = true;
timeDataValidation.errorBoxText = 'Enter a correct time';
timeDataValidation.errorBoxTitle = 'ERROR';
timeDataValidation.promptBoxText = 'Data validation for time';
timeDataValidation.showPromptBox = true;

// Data validation for list.
final DataValidation listValidation = sheet.getRangeByName('C3').dataValidation;
sheet.getRangeByName('C1').setText('Data Validation List in C3');
listValidation.listOfValues = <String>['ListItem1', 'ListItem2', 'ListItem3'];

// Show the error message.
listValidation.errorBoxText = 'Choose the value from the list';
listValidation.errorBoxTitle = 'ERROR';
listValidation.promptBoxText = 'Data validation for list';
listValidation.showPromptBox = true;

// Data validation for numbers.
final DataValidation numberValidation = sheet.getRangeByName('D3').dataValidation;
sheet.getRangeByName('D1').setText('Enter the Number in D3');
numberValidation.allowType = ExcelDataValidationType.integer;
numberValidation.comparisonOperator = ExcelDataValidationComparisonOperator.between;
numberValidation.firstFormula = '0';
numberValidation.secondFormula = '10';

// Show the error message.
numberValidation.showErrorBox = true;
numberValidation.errorBoxText = 'Enter Value between 0 and 10';
numberValidation.errorBoxTitle = 'ERROR';
numberValidation.promptBoxText = 'Data validation for numbers';
numberValidation.showPromptBox = true;

// Data validation for date.
final DataValidation dateValidation = sheet.getRangeByName('E3').dataValidation;
sheet.getRangeByName('E1').setText('Enter the Date in E3');
dateValidation.allowType = ExcelDataValidationType.date;
dateValidation.comparisonOperator = ExcelDataValidationComparisonOperator.between;
dateValidation.firstDateTime = DateTime(2003, 5, 10);
dateValidation.secondDateTime = DateTime(2004, 5, 10);

// Show the error message.
dateValidation.showErrorBox = true;
dateValidation.errorBoxText = 'Enter Value between 10/5/2003 and 10/5/2004';
dateValidation.errorBoxTitle = 'ERROR';
dateValidation.promptBoxText = 'Data validation for date';
dateValidation.showPromptBox = true;

// Data validation for custom data.
final DataValidation customValidation = sheet.getRangeByName('F3').dataValidation;
customValidation.allowType = ExcelDataValidationType.formula;
customValidation.firstFormula = '=F1>10';

// Show the error message.
customValidation.errorBoxText = 'Enter the value in F1 greater than 10';
customValidation.errorBoxTitle = 'ERROR';
customValidation.promptBoxText = 'Custom data validation';
customValidation.showPromptBox = true;

// Data validation for decimals.
final DataValidation decimalValidation = sheet.getRangeByName('G3').dataValidation;
sheet.getRangeByName('G1').setText('Enter the Decimal Number in G3');
decimalValidation.allowType = ExcelDataValidationType.decimal;
decimalValidation.comparisonOperator = ExcelDataValidationComparisonOperator.between;
decimalValidation.firstFormula = '1.0';
decimalValidation.secondFormula = '10.0';

// Show the error message.
decimalValidation.showErrorBox = true;
decimalValidation.errorBoxText = 'Enter Value between 1.0 and 10.0';
decimalValidation.errorBoxTitle = 'ERROR';
decimalValidation.promptBoxText = 'Data validation for decimal';
decimalValidation.showPromptBox = true;

// Data validation as a list whose values come from a cell range.
final DataValidation dataRangeValidation = sheet.getRangeByName('H3').dataValidation;
sheet.getRangeByName('H1').setText('Select the value provided in the list');
sheet.getRangeByName('H4').setText('ListItem1');
sheet.getRangeByName('H5').setText('ListItem2');
dataRangeValidation.dataRange = sheet.getRangeByName('H4:H5');

// Auto-fit the cells that contain text so the columns are readable.
sheet.getRangeByName('A1:H5').autoFit();

// Save and dispose the workbook.
final List<int> bytes = workbook.saveSync();
File('DataValidation.xlsx').writeAsBytes(bytes);
workbook.dispose();
{% endhighlight %}

N> The `errorBoxType` property accepts `ExcelDataValidationErrorBoxStyle.stop`, `warning`, or `information` to control how Excel reacts to invalid entries. It defaults to `stop`, which rejects the entry.

## See also

* [Getting Started with Flutter XlsIO](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/getting-started)
* [Working with Workbook](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-workbook)
* [Working with Cells](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-cells)

