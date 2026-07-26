---
layout: post
title: Excel Tables Syncfusion Flutter XlsIO
description: Learn various features of Excel tables — creating, formatting, and removing — using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with Excel Tables

Excel tables help to organize and analyze data, and Flutter XlsIO supports creating and manipulating these tables.

N> Before you begin, complete the [Getting Started with Flutter XlsIO](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/getting-started) steps, then import the package in your Dart file:

{% highlight dart %}
import 'dart:io'; // for File
import 'package:syncfusion_flutter_xlsio/xlsio.dart';
{% endhighlight %}

N> In production code, use `await workbook.save()` and wrap workbook usage in a `try/finally` block to guarantee `workbook.dispose()`. The samples below use `saveSync()` for brevity.

## Creating a Table

`sheet.tableCollection.create(name, range)` adds a new table over the supplied range. The `name` must be unique within the workbook, must follow Excel's table-naming rules (cannot start with a digit, cannot contain spaces or special characters, must be 1–255 characters), and the range must contain header text in its top row.

The following code snippet creates a simple table from scratch.

{% highlight dart %}
// Create a new Excel document.
final Workbook workbook = Workbook();

// Access the first sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Insert sample data into the sheet.
sheet.getRangeByName('A1').setText('Fruits');
sheet.getRangeByName('A2').setText('banana');
sheet.getRangeByName('A3').setText('Cherry');
sheet.getRangeByName('A4').setText('Banana');

sheet.getRangeByName('B1').setText('CostA');
sheet.getRangeByName('B2').setNumber(744.6);
sheet.getRangeByName('B3').setNumber(5079.6);
sheet.getRangeByName('B4').setNumber(1267.5);

sheet.getRangeByName('C1').setText('CostB');
sheet.getRangeByName('C2').setNumber(162.56);
sheet.getRangeByName('C3').setNumber(1249.2);
sheet.getRangeByName('C4').setNumber(1062.5);

// Create a table with the data in the given range.
final ExcelTable table = sheet.tableCollection.create('Table1', sheet.getRangeByName('A1:C4'));

final List<int> bytes = workbook.saveSync();
File('Table.xlsx').writeAsBytes(bytes);
workbook.dispose();
{% endhighlight %}

## Built-In Table Styles

You can apply the built-in table styles available in Microsoft Excel through the `ExcelTableBuiltInStyle` enum of Flutter XlsIO. The enum lists every style that Excel exposes (Light 1–21, Medium 1–28, Dark 1–11, and the special `none` value); the table's default style when none is set is `tableStyleMedium2`. The following code snippet illustrates this.

{% highlight dart %}
// Create a new Excel document.
final Workbook workbook = Workbook();

// Access the first sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Insert sample data into the sheet.
sheet.getRangeByName('A1').setText('Fruits');
sheet.getRangeByName('A2').setText('banana');
sheet.getRangeByName('A3').setText('Cherry');
sheet.getRangeByName('A4').setText('Banana');

sheet.getRangeByName('B1').setText('CostA');
sheet.getRangeByName('B2').setNumber(744.6);
sheet.getRangeByName('B3').setNumber(5079.6);
sheet.getRangeByName('B4').setNumber(1267.5);

sheet.getRangeByName('C1').setText('CostB');
sheet.getRangeByName('C2').setNumber(162.56);
sheet.getRangeByName('C3').setNumber(1249.2);
sheet.getRangeByName('C4').setNumber(1062.5);

// Create a table with the data in the given range.
final ExcelTable table = sheet.tableCollection.create('Table1', sheet.getRangeByName('A1:C4'));

// Format the table with a built-in style.
table.builtInTableStyle = ExcelTableBuiltInStyle.tableStyleDark10;

final List<int> bytes = workbook.saveSync();
File('BuiltInStyle.xlsx').writeAsBytes(bytes);
workbook.dispose();
{% endhighlight %}

## Table Style Options

You can customize a table with style-toggle properties that control which parts of the table receive the chosen style: first column, last column, header row, total row, banded rows, and banded columns. The snippets below assume `table` is the `ExcelTable` reference returned from `sheet.tableCollection.create(...)` — see the [Creating a Table](#creating-a-table) section.

### Show First Column

Setting `showFirstColumn` to `true` applies the built-in style's first-column emphasis to the first column of the table. Its default value is `false`.

{% highlight dart %}
// Gets or sets a Boolean value indicating whether the first column format is present.
table.showFirstColumn = true;
{% endhighlight %}

### Show Last Column

Setting `showLastColumn` to `true` applies the built-in style's last-column emphasis to the last column of the table. Its default value is `false`.

{% highlight dart %}
// Gets or sets a Boolean value indicating whether the last column format is present.
table.showLastColumn = true;
{% endhighlight %}

### Show Header Row

Setting `showHeaderRow` to `false` hides the header row of the table. Its default value is `true`.

{% highlight dart %}
// Gets or sets a Boolean value indicating whether to hide or display the table's header row.
table.showHeaderRow = false;
{% endhighlight %}

### Show Total Row

Setting `showTotalRow` to `true` shows the total row of the table (you must also populate the total row separately). Its default value is `false`.

{% highlight dart %}
// Gets or sets a Boolean value indicating whether to hide or display the table's total row.
table.showTotalRow = true;
{% endhighlight %}

### Show Banded Rows

Setting `showBandedRows` to `false` removes the row banding for table rows. Its default value is `true`.

{% highlight dart %}
// Gets or sets a Boolean value indicating whether banded row stripes should be present.
table.showBandedRows = false;
{% endhighlight %}

### Show Banded Columns

Setting `showBandedColumns` to `true` adds banding to the table's columns. Its default value is `false`.

{% highlight dart %}
// Gets or sets a Boolean value indicating whether banded column stripes should be present.
table.showBandedColumns = true;
{% endhighlight %}

## Removing a Table

You can remove a table from an Excel document in two ways:

* Using a `table` object: `sheet.tableCollection.remove(table)`.
* Using a specific index: `sheet.tableCollection.removeAt(index)`. The index is 0-based.

The following code snippet illustrates how to remove a table from an Excel document using a `table` object.

{% highlight dart %}
// Create a new Excel document.
final Workbook workbook = Workbook();

// Access the first sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Insert sample data into the sheet.
sheet.getRangeByName('A1').setText('Fruits');
sheet.getRangeByName('A2').setText('banana');
sheet.getRangeByName('A3').setText('Cherry');
sheet.getRangeByName('A4').setText('Banana');

sheet.getRangeByName('B1').setText('CostA');
sheet.getRangeByName('B2').setNumber(744.6);
sheet.getRangeByName('B3').setNumber(5079.6);
sheet.getRangeByName('B4').setNumber(1267.5);

sheet.getRangeByName('C1').setText('CostB');
sheet.getRangeByName('C2').setNumber(162.56);
sheet.getRangeByName('C3').setNumber(1249.2);
sheet.getRangeByName('C4').setNumber(1062.5);

sheet.getRangeByName('F1').setText('Vegetables');
sheet.getRangeByName('F2').setText('Egg Plant');
sheet.getRangeByName('F3').setText('Lettuce');
sheet.getRangeByName('F4').setText('Tomato');

sheet.getRangeByName('G1').setText('CostA1');
sheet.getRangeByName('G2').setNumber(744.6);
sheet.getRangeByName('G3').setNumber(5079.6);
sheet.getRangeByName('G4').setNumber(1267.5);

sheet.getRangeByName('H1').setText('CostB1');
sheet.getRangeByName('H2').setNumber(162.56);
sheet.getRangeByName('H3').setNumber(1249.2);
sheet.getRangeByName('H4').setNumber(1062.5);

// Create tables with the data in the given range.
final ExcelTable table1 = sheet.tableCollection.create('Table1', sheet.getRangeByName('A1:C4'));
final ExcelTable table2 = sheet.tableCollection.create('Table2', sheet.getRangeByName('F1:H4'));

// Remove the table referenced by table1 from the worksheet.
sheet.tableCollection.remove(table1);

final List<int> bytes = workbook.saveSync();
File('RemoveTable.xlsx').writeAsBytes(bytes);
workbook.dispose();
{% endhighlight %}

The following code snippet illustrates how to remove a table from an Excel document using a specific index. After the first table is removed by reference and a third table is added, calling `removeAt(1)` removes the third table (`Table3`).

{% highlight dart %}
// Create a new Excel document.
final Workbook workbook = Workbook();

// Access the first sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Insert sample data into the sheet.
sheet.getRangeByName('A1').setText('Fruits');
sheet.getRangeByName('A2').setText('banana');
sheet.getRangeByName('A3').setText('Cherry');
sheet.getRangeByName('A4').setText('Banana');

sheet.getRangeByName('B1').setText('CostA');
sheet.getRangeByName('B2').setNumber(744.6);
sheet.getRangeByName('B3').setNumber(5079.6);
sheet.getRangeByName('B4').setNumber(1267.5);

sheet.getRangeByName('C1').setText('CostB');
sheet.getRangeByName('C2').setNumber(162.56);
sheet.getRangeByName('C3').setNumber(1249.2);
sheet.getRangeByName('C4').setNumber(1062.5);

sheet.getRangeByName('F1').setText('Vegetables');
sheet.getRangeByName('F2').setText('Egg Plant');
sheet.getRangeByName('F3').setText('Lettuce');
sheet.getRangeByName('F4').setText('Tomato');

sheet.getRangeByName('G1').setText('CostA1');
sheet.getRangeByName('G2').setNumber(744.6);
sheet.getRangeByName('G3').setNumber(5079.6);
sheet.getRangeByName('G4').setNumber(1267.5);

sheet.getRangeByName('H1').setText('CostB1');
sheet.getRangeByName('H2').setNumber(162.56);
sheet.getRangeByName('H3').setNumber(1249.2);
sheet.getRangeByName('H4').setNumber(1062.5);

sheet.getRangeByName('D6').setText('Product A');
sheet.getRangeByName('D7').setText('shirt');
sheet.getRangeByName('D8').setText('bags');
sheet.getRangeByName('D9').setText('Trousers');

sheet.getRangeByName('E6').setText('Cost1');
sheet.getRangeByName('E7').setNumber(654);
sheet.getRangeByName('E8').setNumber(745);
sheet.getRangeByName('E9').setNumber(187);
sheet.getRangeByName('F6').setText('Cost2');
sheet.getRangeByName('F7').setNumber(967);
sheet.getRangeByName('F8').setNumber(543);
sheet.getRangeByName('F9').setNumber(864);

// Create tables with the data in the given range.
final ExcelTable table1 = sheet.tableCollection.create('Table1', sheet.getRangeByName('A1:C4'));
final ExcelTable table2 = sheet.tableCollection.create('Table2', sheet.getRangeByName('F1:H4'));
final ExcelTable table3 = sheet.tableCollection.create('Table3', sheet.getRangeByName('D6:F9'));

// Remove the table at index 1 (the second table in the collection, which is Table3).
sheet.tableCollection.removeAt(1);

final List<int> bytes = workbook.saveSync();
File('RemoveTable.xlsx').writeAsBytes(bytes);
workbook.dispose();
{% endhighlight %}

N> Removing a table does not delete the underlying cell values, only the table definition that groups them. If you need to clear the data as well, follow up with the appropriate `range.clear()` calls.

## See also

* [Getting Started with Flutter XlsIO](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/getting-started)
* [Working with Workbook](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-workbook)
* [Working with Excel Worksheet](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-excel-worksheet)
* [Working with Cells](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-cells)
