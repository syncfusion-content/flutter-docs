---
layout: post
title: Excel Data Syncfusion Flutter XlsIO
description: In this section,Learn how to import data to Excel document from objects, Collections, List using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Importing Data to Worksheets
 Flutter XlsIO provides the ability to import data into a worksheet using List.

## Import Data from List

The following code snippet shows how to import list of data into a worksheet using **importList** method.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

//Initialize the list
final List<Object> List = [
  'Toatal Income',
  20000,
  'On Date',
  DateTime(2021, 11, 11)
];

//Import the Object list to Sheet
sheet.importList(list, 1, 1, true);

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('Importlist.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}