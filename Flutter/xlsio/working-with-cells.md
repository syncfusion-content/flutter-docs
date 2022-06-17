---
layout: post
title: Working with Cells using Syncfusion Flutter XlsIO
description: Learn how to add text, number, datetime and values to Excel worksheet using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with Worksheet Cells

## Adding a Text to Excel worksheet

You can add text to the Excel worksheet using setText() method of the Range class.

The following code snippet shows how to add text to Excel worksheet.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Adding text using setText() method.
sheet.getRangeByName('A1').setText('Hello World');

// Save and dispose workbook
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

File('Output.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Adding a Number to Excel worksheet

You can add number to the Excel worksheet using setNumber() method of the Range class.

The following code snippet shows how to add number to Excel worksheet.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

//Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Adding text using setnumber() method.
sheet.getRangeByName('A1').setNumber(4444);

// Save workbook
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

File('Output.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Adding a DateTime to Excel worksheet

You can add number to the Excel worksheet using setDateTime() method of the Range class.

The following code snippet shows how to add datetime to Excel worksheet.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Adding text using setDateTime() method.
sheet.getRangeByName('A1').setDateTime(DateTime(2020, 7, 7, 1, 0, 0));

// Save workbook
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

File('Output.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Adding a value to Excel Worksheet

You can add value to the Excel worksheet using setValue() method of the Range class. The value can be number, text or date time.

The following code snippet shows how to add value to Excel worksheet.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Adding text using setValue() method.
sheet.getRangeByName('A1').setValue(44);

// Save and dispose workbook
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

File('Output.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Hyperlinks

You can create hyperlink in a workbook to provide quick access to web pages, places in your document and files. Hyperlink may target to any one of the following

* Worksheet range
* Web URL
* E-mail
* External files

A Hyperlink can be added to a worksheet range or an image. The following code example illustrates how to insert various hyperlinks to worksheet range.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

//Creating a Hyperlink for a Website.
final Hyperlink hyperlink = sheet.hyperlinks.add(sheet.getRangeByName('A1'),
    HyperlinkType.url, 'http://www.syncfusion.com');
hyperlink.screenTip =
    'To know more about Syncfusion products, go through this link.';
hyperlink.textToDisplay = 'Syncfusion';

//Creating a Hyperlink for e-mail.
final Hyperlink hyperlink1 = sheet.hyperlinks.add(sheet.getRangeByName('A3'),
    HyperlinkType.url, 'mailto:Username@syncfusion.com');
hyperlink1.screenTip = 'Send Mail';

//Creating a Hyperlink for Opening Files using type as File.
final Hyperlink hyperlink2 = sheet.hyperlinks
    .add(sheet.getRangeByName('A5'), HyperlinkType.file, 'C:\\Program files');
hyperlink2.screenTip = 'File path';
hyperlink2.textToDisplay = 'Hyperlink for files using File as type';

// Creating a Hyperlink for Opening Files using type as Unc.
final Hyperlink hyperlink3 = sheet.hyperlinks.add(sheet.getRangeByName('A7'),
    HyperlinkType.unc, 'C:\\Documents and Settings');
hyperlink3.screenTip = 'Click here for files';
hyperlink3.textToDisplay = 'Hyperlink for files using Unc as type';

//Creating a Hyperlink to another cell using type as Workbook.
final Hyperlink hyperlink4 = sheet.hyperlinks
    .add(sheet.getRangeByName('A9'), HyperlinkType.workbook, 'Sheet1!A15');
hyperlink4.screenTip = 'Click Here';
hyperlink4.textToDisplay = 'Hyperlink to cell A15';

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('Hyperlinks.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

### Hyperlink on Picture

The following code example illustrates how to insert hyperlinks to pictures.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

//Adding hyperlink to picture.
final Picture picture1 = sheet.pictures.addBase64(1, 1, image1jpg);
final Hyperlink link = sheet.hyperlinks
    .addImage(picture1, HyperlinkType.url, 'http://www.syncfusion.com');
link.screenTip = 'About Syncfusion';

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('HyperlinksPicture.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

## Data Filtering

Using [AutoFilters](https://support.office.com/en-US/article/Filter-data-in-a-range-or-table-01832226-31b5-4568-8806-38c37dcc180e), data can be filtered to enable quick and easy way to find and work with a subset of data in a range of cells. When the data is filtered, entire rows are hidden if values in one or more columns does not meet the filtering criteria. The following are the types of filters that can be used in XlsIO.

* Text filter
* Custom filter
* Date filter
* Dynamic filter
* Font color filter
* Cell color filter

### Text Filter

Text filter can be applied through **addTextFilter** method of **AutoFilter** class. The following code snippet explains this.

{% highlight dart %}

final Workbook workbook = Workbook();
final Worksheet worksheet = workbook.worksheets[0];
worksheet.getRangeByName('A1').setText('Title');
worksheet.getRangeByName('A2').setText('Sales Representative');
worksheet.getRangeByName('A3').setText('Owner');
worksheet.getRangeByName('A4').setText('Owner');
worksheet.getRangeByName('A5').setText('Sales Representative');
worksheet.getRangeByName('A6').setText('Order Administrator');
worksheet.getRangeByName('A7').setText('Sales Representative');
worksheet.getRangeByName('A8').setText('Marketing Manager');
worksheet.getRangeByName('A9').setText('Owner');
worksheet.getRangeByName('A10').setText('Owner');

worksheet.getRangeByName('B1').setText('DOJ');
worksheet.getRangeByName('B2').dateTime = DateTime(2006, 9, 10);
worksheet.getRangeByName('B3').dateTime = DateTime(2000, 6, 10);
worksheet.getRangeByName('B4').dateTime = DateTime(2002, 9, 18);
worksheet.getRangeByName('B5').dateTime = DateTime(2009, 5, 23);
worksheet.getRangeByName('B6').dateTime = DateTime(2012, 1, 6);
worksheet.getRangeByName('B7').dateTime = DateTime(2007, 7, 19);
worksheet.getRangeByName('B8').dateTime = DateTime(2008, 6, 30);
worksheet.getRangeByName('B9').dateTime = DateTime(2002, 4, 16);
worksheet.getRangeByName('B10').dateTime = DateTime(2008, 11, 29);

worksheet.getRangeByName('C1').setText('City');
worksheet.getRangeByName('C2').setText('Berlin');
worksheet.getRangeByName('C3').setText('Mexico D.F.');
worksheet.getRangeByName('C4').setText('Mexico D.F.');
worksheet.getRangeByName('C5').setText('London');
worksheet.getRangeByName('C6').setText('Lulea');
worksheet.getRangeByName('C7').setText('Mannheim');
worksheet.getRangeByName('C8').setText('Strasbourg');
worksheet.getRangeByName('C9').setText('Madrid');
worksheet.getRangeByName('C10').setText('Marseille');

// Intialize filter range.
worksheet.autofilters.filterRange = worksheet.getRangeByName('A1:C10');

// Add text filter.
final AutoFilter autofilter = worksheet.autofilters[0];
autofilter.addTextFilter(<String>{'Owner'});
worksheet.getRangeByName('A1:C10').autoFitColumns();

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('TextFilter.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

### Custom Filter

The following code snippet explains how to apply a custom filter.

{% highlight dart %}

final Workbook workbook = Workbook();
final Worksheet worksheet = workbook.worksheets[0];
worksheet.getRangeByName('A1').setText('Title');
worksheet.getRangeByName('A2').setText('Sales Representative');
worksheet.getRangeByName('A3').setText('Owner');
worksheet.getRangeByName('A4').setText('Owner');
worksheet.getRangeByName('A5').setText('Sales Representative');
worksheet.getRangeByName('A6').setText('Order Administrator');
worksheet.getRangeByName('A7').setText('Sales Representative');
worksheet.getRangeByName('A8').setText('Marketing Manager');
worksheet.getRangeByName('A9').setText('Owner');
worksheet.getRangeByName('A10').setText('Owner');

worksheet.getRangeByName('B1').setText('DOJ');
worksheet.getRangeByName('B2').dateTime = DateTime(2006, 9, 10);
worksheet.getRangeByName('B3').dateTime = DateTime(2000, 6, 10);
worksheet.getRangeByName('B4').dateTime = DateTime(2002, 9, 18);
worksheet.getRangeByName('B5').dateTime = DateTime(2009, 5, 23);
worksheet.getRangeByName('B6').dateTime = DateTime(2012, 1, 6);
worksheet.getRangeByName('B7').dateTime = DateTime(2007, 7, 19);
worksheet.getRangeByName('B8').dateTime = DateTime(2008, 6, 30);
worksheet.getRangeByName('B9').dateTime = DateTime(2002, 4, 16);
worksheet.getRangeByName('B10').dateTime = DateTime(2008, 11, 29);

worksheet.getRangeByName('C1').setText('City');
worksheet.getRangeByName('C2').setText('Berlin');
worksheet.getRangeByName('C3').setText('Mexico D.F.');
worksheet.getRangeByName('C4').setText('Mexico D.F.');
worksheet.getRangeByName('C5').setText('London');
worksheet.getRangeByName('C6').setText('Lulea');
worksheet.getRangeByName('C7').setText('Mannheim');
worksheet.getRangeByName('C8').setText('Strasbourg');
worksheet.getRangeByName('C9').setText('Madrid');
worksheet.getRangeByName('C10').setText('Marseille');

// Intialize filter range.
worksheet.autofilters.filterRange = worksheet.getRangeByName('A1:C10');
final AutoFilter autofilter = worksheet.autofilters[0];

// First condition.
final AutoFilterCondition firstCondition = autofilter.firstCondition;
firstCondition.conditionOperator = ExcelFilterCondition.equal;
firstCondition.textValue = 'Owner';

// Second condition.
final AutoFilterCondition secondCondition = autofilter.secondCondition;
secondCondition.conditionOperator = ExcelFilterCondition.equal;
secondCondition.textValue = 'Sales Representative';

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('CustomFilter.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

### Date Filter

Date filter can be applied through **addDateFilter** method of **AutoFilter** class. The following code snippet explains this.

{% highlight dart %}

final Workbook workbook = Workbook();
final Worksheet worksheet = workbook.worksheets[0];
worksheet.getRangeByName('A1').setText('Title');
worksheet.getRangeByName('A2').setText('Sales Representative');
worksheet.getRangeByName('A3').setText('Owner');
worksheet.getRangeByName('A4').setText('Owner');
worksheet.getRangeByName('A5').setText('Sales Representative');
worksheet.getRangeByName('A6').setText('Order Administrator');
worksheet.getRangeByName('A7').setText('Sales Representative');
worksheet.getRangeByName('A8').setText('Marketing Manager');
worksheet.getRangeByName('A9').setText('Owner');
worksheet.getRangeByName('A10').setText('Owner');

worksheet.getRangeByName('B1').setText('DOJ');
worksheet.getRangeByName('B2').dateTime = DateTime(2006, 9, 10);
worksheet.getRangeByName('B3').dateTime = DateTime(2000, 6, 10);
worksheet.getRangeByName('B4').dateTime = DateTime(2002, 9, 18);
worksheet.getRangeByName('B5').dateTime = DateTime(2009, 5, 23);
worksheet.getRangeByName('B6').dateTime = DateTime(2012, 1, 6);
worksheet.getRangeByName('B7').dateTime = DateTime(2007, 7, 19);
worksheet.getRangeByName('B8').dateTime = DateTime(2008, 6, 30);
worksheet.getRangeByName('B9').dateTime = DateTime(2002, 4, 16);
worksheet.getRangeByName('B10').dateTime = DateTime(2008, 11, 29);

worksheet.getRangeByName('C1').setText('City');
worksheet.getRangeByName('C2').setText('Berlin');
worksheet.getRangeByName('C3').setText('Mexico D.F.');
worksheet.getRangeByName('C4').setText('Mexico D.F.');
worksheet.getRangeByName('C5').setText('London');
worksheet.getRangeByName('C6').setText('Lulea');
worksheet.getRangeByName('C7').setText('Mannheim');
worksheet.getRangeByName('C8').setText('Strasbourg');
worksheet.getRangeByName('C9').setText('Madrid');
worksheet.getRangeByName('C10').setText('Marseille');

// Intialize filter range.
worksheet.autofilters.filterRange = worksheet.getRangeByName('A1:C10');

// Add date filter.
final AutoFilter autofilter = worksheet.autofilters[1];
autofilter.addDateFilter(DateTime(2002), DateTimeFilterType.year);
autofilter.addDateFilter(DateTime(2009, 5), DateTimeFilterType.year);

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('DateFilter.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

### Dynamic Filter

Dynamic filter can be applied through **addDynamicFilter** method of **AutoFilter** class. The following code snippet explains this.

{% highlight dart %}

final Workbook workbook = Workbook();
final Worksheet worksheet = workbook.worksheets[0];
worksheet.getRangeByName('A1').setText('Title');
worksheet.getRangeByName('A2').setText('Sales Representative');
worksheet.getRangeByName('A3').setText('Owner');
worksheet.getRangeByName('A4').setText('Owner');
worksheet.getRangeByName('A5').setText('Sales Representative');
worksheet.getRangeByName('A6').setText('Order Administrator');
worksheet.getRangeByName('A7').setText('Sales Representative');
worksheet.getRangeByName('A8').setText('Marketing Manager');
worksheet.getRangeByName('A9').setText('Owner');
worksheet.getRangeByName('A10').setText('Owner');

worksheet.getRangeByName('B1').setText('DOJ');
worksheet.getRangeByName('B2').dateTime = DateTime(2006, 9, 10);
worksheet.getRangeByName('B3').dateTime = DateTime(2000, 6, 10);
worksheet.getRangeByName('B4').dateTime = DateTime(2002, 9, 18);
worksheet.getRangeByName('B5').dateTime = DateTime(2009, 5, 23);
worksheet.getRangeByName('B6').dateTime = DateTime(2012, 1, 6);
worksheet.getRangeByName('B7').dateTime = DateTime(2007, 7, 19);
worksheet.getRangeByName('B8').dateTime = DateTime(2008, 6, 30);
worksheet.getRangeByName('B9').dateTime = DateTime(2002, 4, 16);
worksheet.getRangeByName('B10').dateTime = DateTime(2008, 11, 29);

worksheet.getRangeByName('C1').setText('City');
worksheet.getRangeByName('C2').setText('Berlin');
worksheet.getRangeByName('C3').setText('Mexico D.F.');
worksheet.getRangeByName('C4').setText('Mexico D.F.');
worksheet.getRangeByName('C5').setText('London');
worksheet.getRangeByName('C6').setText('Lulea');
worksheet.getRangeByName('C7').setText('Mannheim');
worksheet.getRangeByName('C8').setText('Strasbourg');
worksheet.getRangeByName('C9').setText('Madrid');
worksheet.getRangeByName('C10').setText('Marseille');

// Intialize filter range.
worksheet.autofilters.filterRange = worksheet.getRangeByName('A1:C10');

// Add dynamic filter.
final AutoFilter autofilter = worksheet.autofilters[1];
autofilter.addDynamicFilter(DynamicFilterType.quarter2);
worksheet.getRangeByName('A1:C10').autoFitColumns();

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('DynamicFilter.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

### Font Color Filter

Font color filter can be applied through **addColorFilter** method of **AutoFilter** class and **fontColor** option of **ExcelColorFilterType** enumeratioon. The following code snippet explains this.

{% highlight dart %}

final Workbook workbook = Workbook();
final Worksheet worksheet = workbook.worksheets[0];
worksheet.getRangeByName('A1').setText('Title');
worksheet.getRangeByName('A2').setText('Sales Representative');
worksheet.getRangeByName('A3').setText('Owner');
worksheet.getRangeByName('A4').setText('Owner');
worksheet.getRangeByName('A5').setText('Sales Representative');
worksheet.getRangeByName('A6').setText('Order Administrator');
worksheet.getRangeByName('A7').setText('Sales Representative');
worksheet.getRangeByName('A8').setText('Marketing Manager');
worksheet.getRangeByName('A9').setText('Owner');
worksheet.getRangeByName('A10').setText('Owner');

worksheet.getRangeByName('B1').setText('DOJ');
worksheet.getRangeByName('B2').dateTime = DateTime(2006, 9, 10);
worksheet.getRangeByName('B3').dateTime = DateTime(2000, 6, 10);
worksheet.getRangeByName('B4').dateTime = DateTime(2002, 9, 18);
worksheet.getRangeByName('B5').dateTime = DateTime(2009, 5, 23);
worksheet.getRangeByName('B6').dateTime = DateTime(2012, 1, 6);
worksheet.getRangeByName('B7').dateTime = DateTime(2007, 7, 19);
worksheet.getRangeByName('B8').dateTime = DateTime(2008, 6, 30);
worksheet.getRangeByName('B9').dateTime = DateTime(2002, 4, 16);
worksheet.getRangeByName('B10').dateTime = DateTime(2008, 11, 29);

worksheet.getRangeByName('C1').setText('City');
worksheet.getRangeByName('C2').setText('Berlin');
worksheet.getRangeByName('C3').setText('Mexico D.F.');
worksheet.getRangeByName('C4').setText('Mexico D.F.');
worksheet.getRangeByName('C5').setText('London');
worksheet.getRangeByName('C6').setText('Lulea');
worksheet.getRangeByName('C7').setText('Mannheim');
worksheet.getRangeByName('C8').setText('Strasbourg');
worksheet.getRangeByName('C9').setText('Madrid');
worksheet.getRangeByName('C10').setText('Marseille');

worksheet.getRangeByName('A2').cellStyle.backColor = '#008000';
worksheet.getRangeByName('A3').cellStyle.backColor = '#0000FF';
worksheet.getRangeByName('A4').cellStyle.backColor = '#FF0000';
worksheet.getRangeByName('A5').cellStyle.backColor = '#FF0000';
worksheet.getRangeByName('A6').cellStyle.backColor = '#FFFFFF';
worksheet.getRangeByName('A7').cellStyle.backColor = '#FF0000';
worksheet.getRangeByName('A8').cellStyle.backColor = '#FFFFFF';
worksheet.getRangeByName('A9').cellStyle.backColor = '#0000FF';
worksheet.getRangeByName('A10').cellStyle.backColor = '#008000';

worksheet.getRangeByName('C2').cellStyle.fontColor = '#FF0000';
worksheet.getRangeByName('C3').cellStyle.fontColor = '#008000';
worksheet.getRangeByName('C4').cellStyle.fontColor = '#0000FF';
worksheet.getRangeByName('C5').cellStyle.fontColor = '#000000';
worksheet.getRangeByName('C6').cellStyle.fontColor = '#FF0000';
worksheet.getRangeByName('C7').cellStyle.fontColor = '#008000';
worksheet.getRangeByName('C8').cellStyle.fontColor = '#0000FF';
worksheet.getRangeByName('C9').cellStyle.fontColor = '#000000';
worksheet.getRangeByName('C10').cellStyle.fontColor = '#FF0000';

// Intialize filter range.
worksheet.autofilters.filterRange = worksheet.getRangeByName('A1:C10');

// Add font color filter.
final AutoFilter autofilter = worksheet.autofilters[2];
autofilter.addColorFilter('#0000FF', ExcelColorFilterType.fontColor);

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('FontColorFilter.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

### Cell Color Filter

Cell color filter can be applied through **addColorFilter** method of **AutoFilter** class and **cellColor** option of **ExcelColorFilterType** enumeratioon. The following code snippet explains this.

{% highlight dart %}

final Workbook workbook = Workbook();
final Worksheet worksheet = workbook.worksheets[0];
worksheet.getRangeByName('A1').setText('Title');
worksheet.getRangeByName('A2').setText('Sales Representative');
worksheet.getRangeByName('A3').setText('Owner');
worksheet.getRangeByName('A4').setText('Owner');
worksheet.getRangeByName('A5').setText('Sales Representative');
worksheet.getRangeByName('A6').setText('Order Administrator');
worksheet.getRangeByName('A7').setText('Sales Representative');
worksheet.getRangeByName('A8').setText('Marketing Manager');
worksheet.getRangeByName('A9').setText('Owner');
worksheet.getRangeByName('A10').setText('Owner');

worksheet.getRangeByName('B1').setText('DOJ');
worksheet.getRangeByName('B2').dateTime = DateTime(2006, 9, 10);
worksheet.getRangeByName('B3').dateTime = DateTime(2000, 6, 10);
worksheet.getRangeByName('B4').dateTime = DateTime(2002, 9, 18);
worksheet.getRangeByName('B5').dateTime = DateTime(2009, 5, 23);
worksheet.getRangeByName('B6').dateTime = DateTime(2012, 1, 6);
worksheet.getRangeByName('B7').dateTime = DateTime(2007, 7, 19);
worksheet.getRangeByName('B8').dateTime = DateTime(2008, 6, 30);
worksheet.getRangeByName('B9').dateTime = DateTime(2002, 4, 16);
worksheet.getRangeByName('B10').dateTime = DateTime(2008, 11, 29);

worksheet.getRangeByName('C1').setText('City');
worksheet.getRangeByName('C2').setText('Berlin');
worksheet.getRangeByName('C3').setText('Mexico D.F.');
worksheet.getRangeByName('C4').setText('Mexico D.F.');
worksheet.getRangeByName('C5').setText('London');
worksheet.getRangeByName('C6').setText('Lulea');
worksheet.getRangeByName('C7').setText('Mannheim');
worksheet.getRangeByName('C8').setText('Strasbourg');
worksheet.getRangeByName('C9').setText('Madrid');
worksheet.getRangeByName('C10').setText('Marseille');

worksheet.getRangeByName('A2').cellStyle.backColor = '#008000';
worksheet.getRangeByName('A3').cellStyle.backColor = '#0000FF';
worksheet.getRangeByName('A4').cellStyle.backColor = '#FF0000';
worksheet.getRangeByName('A5').cellStyle.backColor = '#FF0000';
worksheet.getRangeByName('A6').cellStyle.backColor = '#FFFFFF';
worksheet.getRangeByName('A7').cellStyle.backColor = '#FF0000';
worksheet.getRangeByName('A8').cellStyle.backColor = '#FFFFFF';
worksheet.getRangeByName('A9').cellStyle.backColor = '#0000FF';
worksheet.getRangeByName('A10').cellStyle.backColor = '#008000';

worksheet.getRangeByName('C2').cellStyle.fontColor = '#FF0000';
worksheet.getRangeByName('C3').cellStyle.fontColor = '#008000';
worksheet.getRangeByName('C4').cellStyle.fontColor = '#0000FF';
worksheet.getRangeByName('C5').cellStyle.fontColor = '#000000';
worksheet.getRangeByName('C6').cellStyle.fontColor = '#FF0000';
worksheet.getRangeByName('C7').cellStyle.fontColor = '#008000';
worksheet.getRangeByName('C8').cellStyle.fontColor = '#0000FF';
worksheet.getRangeByName('C9').cellStyle.fontColor = '#000000';
worksheet.getRangeByName('C10').cellStyle.fontColor = '#FF0000';

// Intialize filter range.
worksheet.autofilters.filterRange = worksheet.getRangeByName('A1:C10');

// Add cell color filter.
final AutoFilter autofilter = worksheet.autofilters[0];
autofilter.addColorFilter('#FF0000', ExcelColorFilterType.cellColor);

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('CellColorFilter.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}
