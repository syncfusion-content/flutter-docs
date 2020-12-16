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




