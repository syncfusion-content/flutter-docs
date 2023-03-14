---
layout: post
title: Workbook of Syncfusion Flutter XlsIO
description: Learn how to save the created workbook using different ways and close the workbook using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with Workbook

## Saving a Excel workbook to file system

You can save the created or manipulated workbook to file system using saveAsStream() method of Workbook. The workbook is saved in the XLSX format.

{% highlight dart %}

// Creates a new instance for workbook.
final Workbook workbook = Workbook();

// Save the workbook in file system as XLSX format.
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

File('Output.xlsx').writeAsBytes(bytes);

{% endhighlight %}

Flutter XlsIO also supports saving an Excel document using save() method of Workbook.

{% highlight dart %}

// Creates a new instance for workbook.
final Workbook workbook = Workbook();

// Save the workbook in file system as XLSX format.
final List<int> bytes = await workbook.save();
workbook.dispose();

File('Output.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Closing a workbook

Once after the workbook manipulation and save operation are completed, you should dispose the instance of Workbook, in order to release all the memory consumed by XlsIO’s DOM. The following code snippet illustrates how dispose the instance of Workbook.

{% highlight dart %}

// Creates a new instance for workbook.
final Workbook workbook = new Workbook();

// Save the workbook in file system as XLSX format.
final List<int> bytes = workbook.saveAsStream();

// Dipose the workbook.
workbook.dispose();

File('Output.xlsx').writeAsBytes(bytes);

{% endhighlight %}

