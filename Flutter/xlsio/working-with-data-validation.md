---
layout: post
title: Excel Data Validation Syncfusion Flutter XlsIO
description: In this section, learn how to use different types of data validations on Excel data using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with Excel Data Validation

Data Validation is a list of rules for the data that can be entered into a cell. XlsIO supports the following data validation types.

* Text Length Validation
* Time Validation
* List Validation
* Whole Number Validation
* Decimal Number Validation
* Date Validation
* Custom Validation

## Text Length Validation

Text length data validation can be applied by selecting the **allowType** as **textLength**. The following code snippet illustrates this.

{% highlight dart %}
//Data Validation for text Length.
final DataValidation textLengthValidation = sheet.getRangeByName(‘A1’).dataValidation;
textLengthValidation.allowType = ExcelDataValidationType.textLength;

//Text Length should be less than 5 characters.
textLengthValidation.comparisonOperator = ExcelDataValidationComparisonOperator.between; 
textLengthValidation.firstFormula = '1';
textLengthValidation.secondFormula = '5';
{% endhighlight %}

## Time Validation

Time data validation can be applied by selecting the **allowType** as **time**. The following code snippet illustrates this.

{% highlight dart %}
//Data validation for time.
final DataValidation timeValidation = sheet.getRangeByName(‘A3’).dataValidation;
timeValidation.allowType = ExcelDataValidationType.time;

//Time between 10:00 and 12:00 ‘o Clock.
timeValidation.comparisonOperator = ExcelDataValidationComparisonOperator.between;
timeValidation.firstFormula = ’10:00’;
timeValidation.secondFormula = ’12:00’;
{% endhighlight %}

N> Time value should be entered in 24-hour format without appending AM or PM at the end of the code.

## List Validation

List data validation can be applied by assigning values to **listOfValues**. The following code snippet illustrates this.

{% highlight dart %}
//DataValidation for list.
final DataValidation listValidation = sheet.getRangeByName(‘A3’).dataValidation;
listValidation.listOfValues = <String>[‘ListItem1’,’ListItem2’,’ListItem3’];
{% endhighlight %}

N> The ListOfValues property should be used when the values in the Data Validation list are entered manually, whose limit is only 255 characters including separators.

## Whole Number Validation

Whole number data validation can be applied by selecting the **allowType** as **integer**. The following code snippet illustrates this.

{% highlight dart %}
//Data validation for number.
final DataValidation integerValidation = sheet.getRangeByName(‘A3’).dataValidation;
integerValidation.allowType = ExcelDataValidationType.integer;

//Value between 0 to 10.
integerValidation.comparisonOperator = ExcelDataValidationComparisonOperator.between;
integerValidation.firstFormula = ‘0’;
integerValidation.secondFormula = ‘10’;
{% endhighlight %}

## Decimal Number Validation

Decimal number data validation can be applied by selecting the **allowType** as **decimal**. The following code snippet illustrates this.

{% highlight dart %}
//Data Validation for decimal.
final DataValidation decimalValidation = sheet.getRangeByName(‘G3’).dataValidation;
sheet.getRangeByName(‘G1’).text =’Enter the Decimal Number in G3’;
decimalValidation.allowType = ExcelDataValidationType.decimal;
decimalValidation.comparisonOperator = ExcelDataValidationComparisonOperator.between;
decimalValidation.firstFormula = ‘1.0’;
decimalValidation.secondFormula = ’10.0’;
{% endhighlight %}

## Date Validation

Date data validation can be applied by selecting the **allowType** as **Date**. The following code snippet illustrates this.

{% highlight dart %}
//Data validation for date.
final DataValidation dateValidation = sheet.getRangeByName(‘A3’).dataValidation;
dateValidation.allowType = ExcelDataValidationType.Date;

//Date between 10/5/2003 to 10/5/2004
dateValidation.comparisonOperator = ExcelDataValidationComparisonOperator.between;
dateValidation.firstFormula = DateTime(2003, 5, 10);
dateValidation.secondFormula = DateTime(2004, 5, 10);
{% endhighlight %}

## Custom Validation

Custom validation can be applied by selecting the **allowType** as **Formula**. The following code snippet illustrates this.

{% highlight dart %}
//Data validation for custom data.
final DataValidation customValidation = sheet.getRangeByName(‘A3’).dataValidation;
customValidation.allowType = ExcelDataValidationType.formula;
customValidation.firstFormula = ‘=A1>10’;
{% endhighlight %}

The following complete code snippet includes all the above discussed data validation types.

{% highlight dart %}
//Create a new Excel Document and access the first sheet.
final Workbook workbook = Workbook(1);
final sheet = workbook.worksheets[0];

//Data Validation for Text Length.
final DataValidation textLengthValidation = sheet.getRangeByName(‘A3’).dataValidation;
sheet.getRangeByName(‘A1’).text = ’Enter the text in A3’;
textLengthValidation.allowType = ExcelDataValidationType.textLength;
textLengthValidation.comparisonOperator = ExcelDataValidationComparisonOperator.between;
textLengthValidation.firstFormula = ‘0’;
textLengthValidation.secondFormula = ‘5’;

//Show the error message.
textLengthValidation.showErrorBox = true;
textLengthValidation.errorBoxText = ‘Text length should be less than 5 characters’;
textLengthValidation.errorBoxTitle = ‘ERROR’;
textLengthValidation.promptBoxText = ‘Data validation for text length’;
textLengthValidation.showPromptBox = true;

//Data Validation for time.
final DataValidation timeDataValidation = sheet.getRangeByName(‘B3’).dataValidation;
sheet.getRangeByName(‘B1’).text = ’Enter the time between 10:00 and 12:00 ‘o Clock in B3’;
timeDataValidation.allowType = ExcelDataValidationType.time;
timeDataValidation.comparisonOperator = ExcelDataValidationComparisonOperator.between;
timeDataValidation.firstFormula = ’10:00’;
timeDataValidation.secondFormula = ’12:00’;

//Show the error message.
timeDataValidation.showErrorBox = true;
timeDataValidation.errorBoxText = ‘Enter a correct time’;
timeDataValidation.errorBoxTitle = ‘ERROR’;
timeDataValidation.promptBoxText = ‘Data validation for time’;
timeDataValidation.showPromptBox = true;

//Data Validation for List.
final DataValidation listValidation = sheet.getRangeByName(‘C3’).dataValidation;
sheet.getRangeByName(‘C1’).text = ‘Data Validation List in C3’;
listValidation.listOfValues = <String>[‘ListItem1’, ‘ListItem2’ , ‘ListItem3’];

//Show the error message.
listValidation.errorBoxText = ‘Choose the value from the list’;
listValidation.errorBoxTitle = ‘ERROR’;
listValidation.promptBoxText = ‘Data validation for list’;
listValidation.showPromptBox = true;

//Data Validation for Numbers.
final DataValidation numberValidation = sheet.getRangeByName(‘D3’).dataValidation;
sheet.getRangeByName(‘D1’).text =’Enter the Number in D3’;
numberValidation.allowType = ExcelDataValidationType.integer;
numberValidation.comparisonOperator = ExcelDataValidationComparisonOperator.between;
numberValidation.firstFormula = ’0’;
numberValidation.secondFormula = ’10’;

//Show the error message.
numberValidation.showErrorBox = true;
numberValidation.errorBoxText = ‘Enter Value between 0 to 10’;
numberValidation.errorBoxTitle = ‘ERROR’;
numberValidation.promptBoxText = ‘Data validation for numbers’;
numberValidation.showPromptBox = true;

//Data Validation for Date.
final DataValidation dateValidation = sheet.getRangeByName(‘E3’).dataValidation;
sheet.getRangeByName(‘E1’).text =’Enter the Date in E3’;
dateValidation.allowType = ExcelDataValidationType.date;
dateValidation.comparisonOperator = ExcelDataValidationComparisonOperator.between;
dateValidation.firstDateTime = DateTime(2003, 5 , 10);
dateValidation.secondDateTime = DateTime(2004, 5, 10);

//Show the error message.
dateValidation.showErrorBox = true;
dateValidation.errorBoxText = ‘Enter Value between 10/5/2003 to 10/5/2004’;
dateValidation.errorBoxTitle = ‘ERROR’;
dateValidation.promptBoxText = ‘Data validation for date’;
dateValidation.showPromptBox = true;

//Data validation for custom data.
final DataValidation customValidation = sheet.getRangeByName(‘F3’).dataValidation;
customValidation.allowType = ExcelDataValidationType.formula;
customValidation.firstFormula = ‘=F1>10’;

//Show the error message.
customValidation.errorBoxText = ‘Enter the value in F1 greater than 10’;
customValidation.errorBoxTitle = ‘ERROR’;
customValidation.promptBoxText = ‘Custom DataValidation’;
customValidation.showPromptBox = true;

//Data Validation for decimal.
final DataValidation decimalValidation = sheet.getRangeByName(‘G3’).dataValidation;
sheet.getRangeByName(‘G1’).text =’Enter the Decimal Number in G3’;
decimalValidation.allowType = ExcelDataValidationType.decimal;
decimalValidation.comparisonOperator = ExcelDataValidationComparisonOperator.between;
decimalValidation.firstFormula = ‘1.0’;
decimalValidation.secondFormula = ’10.0’;

//Show the error message.
decimalValidation.showErrorBox = true;
decimalValidation.errorBoxText = ‘Enter Value between 1.0 to 10.0’;
decimalValidation.errorBoxTitle = ‘ERROR’;
decimalValidation.promptBoxText = ‘Data validation for decimal’;
decimalValidation.showPromptBox = true;

//DataValidation as a list of the selected range in Excel-Sheet.
final DataValidation dataRangeValidation = sheet.getRangeByName(‘H3’).dataValidation;
sheet.getRangeByName(‘H1’).text = ‘Select the value provided in the list’;
sheet.getRangeByName(‘H4’).text = ‘ListItem1’;
sheet.getRangeByName(‘H5’).text = ‘ListItem2’;
dataRangeValidation.dataRange = sheet.getRangeByName(‘H4:H5’);

//Range of cells to be autofit
Sheet.getRangeByName(‘A1:H5’).autoFit();

//Save and dispose the Workbook
final List<int> bytes = workbook.saveAsStream();
saveAsExcel(bytes, ‘DataValidation.xlsx’);
workbook.dispose();
{% endhighlight %}

