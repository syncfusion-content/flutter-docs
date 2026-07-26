---
layout: post
title: Working with Rows and Columns | Syncfusion Flutter XlsIO
description: Learn how to insert, delete, and resize rows and columns in an Excel worksheet using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with Worksheet Rows and Columns

Syncfusion Flutter XlsIO provides row and column manipulation options equivalent to Microsoft Excel, including insertion, deletion, resizing, auto-fitting, and showing or hiding.

The following table summarizes the operations documented in this page:

| Operation | Methods |
|-----------|---------|
| Insert rows and columns | `insertRow`, `insertColumn` |
| Delete rows and columns | `deleteRow`, `deleteColumn` |
| Resize a single row or column | `setRowHeightInPixels`, `setColumnWidthInPixels` |
| Auto-fit a single row or column | `autoFitRow`, `autoFitColumn` |
| Auto-fit a range of rows or columns | `Range.autoFitRows`, `Range.autoFitColumns` |
| Show or hide rows and columns | `Range.showRows`, `Range.showColumns`, `Range.showRange` |

N> All row and column indexes in this page are **1-based**: the first row is `1`, the first column is `1`.

For prerequisites and installation steps, see the [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview). For more information on worksheets, see [Working with Excel Worksheets](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-excel-worksheet).

N> The code samples in this document use `await workbook.save()`. Always call `workbook.dispose()` after saving to release the XlsIO DOM memory, ideally inside a `try/finally` block.

## Insert rows and columns

Rows and columns can be inserted with the `insertRow` and `insertColumn` methods of the `Worksheet` class. Both methods accept the 1-based index at which to insert, the number of rows or columns to insert, and an `ExcelInsertOptions` value that controls the formatting of the inserted range:

| `ExcelInsertOptions` value | Description |
|----------------------------|-------------|
| `formatAsBefore` | The inserted range uses the formatting of the row or column immediately above (for rows) or to the left (for columns). |
| `formatAsAfter` | The inserted range uses the formatting of the row or column immediately below (for rows) or to the right (for columns). |

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> insertRowsAndColumns() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  sheet.getRangeByName('A1').setText('Hello');
  sheet.getRangeByName('B1').setText('World');

  // Insert one row at index 1, formatted as the row after it.
  sheet.insertRow(1, 1, ExcelInsertOptions.formatAsAfter);

  // Insert one column at index 2, formatted as the column before it.
  sheet.insertColumn(2, 1, ExcelInsertOptions.formatAsBefore);

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Delete rows and columns

Rows and columns can be deleted with the `deleteRow` and `deleteColumn` methods. The first argument is the 1-based index of the first row or column to delete, and the second argument is the number of rows or columns to delete. Data, formulas, and merged cells in the deleted range are removed; data below (for rows) or to the right (for columns) shifts up or left to fill the gap.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> deleteRowsAndColumns() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  sheet.getRangeByName('A2').setText('Hello');
  sheet.getRangeByName('C2').setText('World');

  // Delete one row at index 1.
  sheet.deleteRow(1, 1);

  // Delete one column at index 2.
  sheet.deleteColumn(2, 1);

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Auto-fit rows and columns

Auto-fit resizes a row or column to match its content. A single row or column can be auto-fit through the `Worksheet.autoFitRow` and `Worksheet.autoFitColumn` methods. A range of rows or columns can be auto-fit through the `Range.autoFitRows` and `Range.autoFitColumns` methods.

### Auto-fit a single row

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> autoFitRow() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Set a long wrapped text in A1.
  final Range range1 = sheet.getRangeByName('A1');
  range1.setText('WrapTextWrapTextWrapTextWrapText');
  range1.cellStyle.wrapText = true;

  // Auto-fit the first row to the content.
  sheet.autoFitRow(1);

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Auto-fit a single column

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> autoFitColumn() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  sheet.getRangeByName('A1').setText('This is long text');

  // Auto-fit the first column to the content.
  sheet.autoFitColumn(1);

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Auto-fit a range of rows

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> autoFitRows() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Set wrapped text in A1:A4.
  final Range range = sheet.getRangeByName('A1:A4');
  range.setText('This is Long Text');
  range.cellStyle.wrapText = true;

  // Auto-fit every row in the range.
  range.autoFitRows();

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Auto-fit a range of columns

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> autoFitColumns() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Set text in A1:D1.
  final Range range = sheet.getRangeByName('A1:D1');
  range.setText('This is Long Text');

  // Auto-fit every column in the range.
  range.autoFitColumns();

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Show or hide rows and columns

The visibility of rows and columns can be toggled through the `showRows` and `showColumns` methods of the `Range` class. When called on a range that includes a full row or a full column, the method hides the entire row or column; when called on a smaller range, the visibility change is limited to that range.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> hideRowsAndColumns() async {
  final Workbook workbook = Workbook(1);
  final Worksheet sheet = workbook.worksheets[0];

  // Hide row 1 and rows 2 to 5.
  sheet.getRangeByName('A1').showRows(false);
  sheet.getRangeByName('A2:A5').showRows(false);

  // Hide column C and columns D to E.
  sheet.getRangeByName('C10').showColumns(false);
  sheet.getRangeByName('D10:E10').showColumns(false);

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

N> Hidden rows and columns are not displayed in the worksheet view, but the data they contain is preserved and can still be referenced by formulas.

## Show or hide a specific range

The `showRange` method of the `Range` class toggles the visibility of a range without restricting the change to a single row or column. This is useful when a range spans multiple rows and columns and only the cells within the range should be hidden.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> hideRange() async {
  final Workbook workbook = Workbook(1);
  final Worksheet sheet = workbook.worksheets[0];

  // Hide the cell G15 and the range J22:J25.
  sheet.getRangeByName('G15').showRange(false);
  sheet.getRangeByName('J22:J25').showRange(false);

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## See also

* [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview)
* [Working with Excel Worksheets](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-excel-worksheet)
* [Working with Cells](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-cells)
* [Working with Cell Formatting](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-cell-formatting)
* [Worksheet API reference](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Worksheet-class.html)
* [Range API reference](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Range-class.html)
* [Release notes](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/release-notes)
