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

