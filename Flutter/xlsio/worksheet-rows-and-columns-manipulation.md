---
layout: post
title: Worksheet Rows and Columns Manipulation using Syncfusion Flutter XlsIO
description: Learn how to apply and manipulate rows cells and columns cells in Excel Worksheet of workbook using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Worksheet Rows and Columns Manipulation

The Flutter XlsIO provides rows and columns manipulation options equivalent to Excel such as insertion, deletion and adjusting the dimensions.

## Insert Rows and Columns

The following code snippet illustrates how to insert rows and columns in a worksheet.

{% highlight dart %} 

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

Range range = sheet.getRangeByName('A1');
range.setText('Hello');

range = sheet.getRangeByName('B1');
range.setText('World');

// Insert a row
sheet.insertRow(1, 1, ExcelInsertOptions.formatAsAfter);

// Insert a column.
sheet.insertColumn(2, 1, ExcelInsertOptions.formatAsBefore);

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('InsertRowandColumn.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

N> Row and Column indexes are "one based".

## Delete Rows and Columns 

The following code shows how to delete rows and columns.

{% highlight dart %} 

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

Range range = sheet.getRangeByName('A2');
range.setText('Hello');

range = sheet.getRangeByName('C2');
range.setText('World');

// Delete a row
sheet.deleteRow(1, 1);

// Delete a column.
sheet.deleteColumn(2, 1);

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('DeleteRowandColumn.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

## Auto-Fit Rows and Columns

The Flutter XlsIO allows to auto-size the width and height of a cell to fit its content. This section demonstrates various methods to auto-fit rows and columns of a worksheet.

### Auto-Fit a Single Row or Column

The following code snippet shows how a row is re-sized to its content.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

final Range range1 = sheet.getRangeByName('A1');
range1.setText('WrapTextWrapTextWrapTextWrapText');
range1.cellStyle.wrapText = true;

// AutoFit applied to a single row
sheet.autoFitRow(1);

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('AutoFitRow.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

The following code snippet shows how a Column is re-sized to its content.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

final Range range1 = sheet.getRangeByName('A1');
range1.setText('This is long text');

// AutoFit applied to a single Column.
sheet.autoFitColumn(1);

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('AutoFitColumn.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}


### Auto-Fit Multiple Rows or Columns

Multiple rows or columns can be auto fitted based on the range specified.

The following code snippet shows how to use auto fit for multiple rows.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Assigning text to cells
final Range range = sheet.getRangeByName('A1:A4');
range.setText('This is Long Text');
range.cellStyle.wrapText = true;

// Auto-Fit row the range
range.autoFitRows();

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('AutoFitRows.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}


The following code snippet shows how to use auto fit for multiple Columns.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Assigning text to cells
final Range range = sheet.getRangeByName('A1:D1');
range.setText('This is Long Text');

// Auto-Fit column the range
range.autoFitColumns();

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('AutoFitColumns.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

## Show or Hide Rows and Columns

Visibility of rows and columns can be set by using the [showRows](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Range/showRows.html) and [showColumns](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Range/showColumns.html) methods as shown below.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook(1);

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Show or hide rows in the given range. TRUE by default.
sheet.getRangeByName('A1').showRows(false);    
sheet.getRangeByName('A2:A5').showRows(false);   

// Show or hide columns in the given range. TRUE by default.
sheet.getRangeByName('C10').showColumns(false);
sheet.getRangeByName('D10:E10').showColumns(false);
       
// Save and dispose workbook.
final List<int>? bytes = workbook.saveAsStream();
File('HideRowsAndColumns.xlsx').writeAsBytes(bytes!);
workbook.dispose();

{% endhighlight %}

## Show or Hide Specific Range

The following code snippet shows how to set the visibility for a specific range through [showRange](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Range/showRange.html) method .

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook(1);

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Show or hide rows and columns in the given range. TRUE by default.
sheet.getRangeByName('G15').showRange(false);
sheet.getRangeByName('J22:J25').showRange(false);
       
// Save and dispose workbook.
final List<int>? bytes = workbook.saveAsStream();
File('HideRowsAndColumns.xlsx').writeAsBytes(bytes!);
workbook.dispose();

{% endhighlight %}

