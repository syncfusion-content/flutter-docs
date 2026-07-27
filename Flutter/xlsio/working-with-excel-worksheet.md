---
layout: post
title: Working with Worksheets | Syncfusion Flutter XlsIO
description: Learn how to create, access, and manipulate worksheets in a workbook using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with Excel Worksheets

A `Workbook` contains a collection of worksheets where the actual data resides, and a `Worksheet` instance represents an individual worksheet. With Syncfusion Flutter XlsIO, you can create, access, and manipulate worksheets programmatically.

For prerequisites and installation steps, see the [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview). For information on saving and disposing of a workbook, see [Working with Workbook](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-workbook).

> The code samples in this document use the `saveAsStream()` (synchronous) and `save()` (asynchronous) methods. Always call `workbook.dispose()` after saving to release the XlsIO DOM memory, ideally inside a `try/finally` block.

## Create a worksheet

A new worksheet can be added to a workbook through the `workbook.worksheets` collection. If you do not specify the number of worksheets when creating a `Workbook`, one worksheet is added by default. Worksheet names must be unique within a workbook.

The following samples show the supported ways to add worksheets to a workbook.

### Add a worksheet with a name

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> createWorksheetWithName() async {
  // Create a new workbook with one worksheet.
  final Workbook workbook = Workbook();

  // Add a worksheet with the name "Sample".
  final Worksheet sheet = workbook.worksheets.addWithName('Sample');

  // Save the workbook and dispose of it.
  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Add a worksheet with the default name

{% highlight dart %}
// Add a worksheet using the default name (for example, "Sheet2").
final Worksheet sheet = workbook.worksheets.add();
{% endhighlight %}

### Add a worksheet from a Worksheet instance

{% highlight dart %}
// Create a Worksheet instance and add it to the workbook.
final Worksheet sheet = Worksheet(workbook);
workbook.worksheets.addWithSheet(sheet);
{% endhighlight %}

## Access a worksheet

The `workbook.worksheets` collection holds every worksheet in the workbook. A particular worksheet can be accessed either by its zero-based index or by its name.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> accessWorksheet() async {
  // Create a new workbook.
  final Workbook workbook = Workbook();
  workbook.worksheets.addWithName('Sample');

  // Access a worksheet by its index (zero-based).
  final Worksheet sheet = workbook.worksheets[0];

  // Access a worksheet by its name. Name lookup is case-insensitive.
  final Worksheet namedSheet = workbook.worksheets['Sample'];

  // Save the workbook and dispose of it.
  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

If a name does not exist in the collection, it returns `null`. The indexer throws `RangeError` if the index is out of range.

## Worksheet tab color

A worksheet tab can be highlighted with a custom color using the `tabColor` property. The color value can be specified as a 6-digit hex string (`#RRGGBB`) or as an `ExcelKnownColor` value.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> setTabColor() async {
  // Create a new workbook with two worksheets.
  final Workbook workbook = Workbook(2);

  // Access the second worksheet.
  final Worksheet sheet = workbook.worksheets[1];
  sheet.getRangeByName('A1:M10').setText('TabColor');

  // Apply a blue tab color to the worksheet.
  sheet.tabColor = '#0000FF';

  // Save the workbook and dispose of it.
  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## View settings

### Show or hide gridlines

The gridlines that appear in the worksheet view can be hidden or shown using the `showGridlines` property.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> hideGridlines() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Hide the gridlines.
  sheet.showGridlines = false;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Page setup settings

Worksheets can be customized with page setup options such as orientation, margins, scaling, paper size, print area, gridlines, black and white, draft quality, row and column headings, and page order. The following sample demonstrates the most common `pageSetup` properties.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> configurePageSetup() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Add text to a range.
  sheet.getRangeByName('A1:Z100').text = 'Hello';

  // Center on the page.
  sheet.pageSetup.isCenterHorizontally = true;
  sheet.pageSetup.isCenterVertically = true;

  // Page orientation.
  sheet.pageSetup.orientation = ExcelPageOrientation.landscape;

  // Margins (in inches).
  sheet.pageSetup.topMargin = 1;
  sheet.pageSetup.leftMargin = 2;
  sheet.pageSetup.rightMargin = 1.25;
  sheet.pageSetup.bottomMargin = 1;
  sheet.pageSetup.footerMargin = 4;
  sheet.pageSetup.headerMargin = 3.5;

  // Paper size.
  sheet.pageSetup.paperSize = ExcelPaperSize.a2Paper;

  // Print area.
  sheet.pageSetup.printArea = 'A1:D20';

  // Show gridlines in the print output.
  sheet.pageSetup.showGridlines = true;

  // Print in black and white.
  sheet.pageSetup.isBlackAndWhite = true;

  // Print as draft quality.
  sheet.pageSetup.isDraft = true;

  // Show row and column headings in the print output.
  sheet.pageSetup.showHeadings = true;

  // Page order.
  sheet.pageSetup.order = ExcelPageOrder.overThenDown;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

The `ExcelPageOrientation`, `ExcelPaperSize`, and `ExcelPageOrder` enums define the valid values. Margins are expressed in inches.

## Show or hide a worksheet

The visibility of a worksheet can be controlled through the `visibility` property. The available `WorksheetVisibility` values are `visible`, `hidden`, and `veryHidden`.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> hideWorksheet() async {
  // Create a workbook with ten worksheets.
  final Workbook workbook = Workbook(10);

  // Hide the third worksheet.
  final Worksheet sheet = workbook.worksheets[2];
  sheet.getRangeByName('A1:M10').setText('Visibility');
  sheet.visibility = WorksheetVisibility.hidden;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Adjust row height and column width

### Resize a range of rows or columns

Single or multiple rows and columns can be resized using the `rowHeight` and `columnWidth` properties of a `Range`. The values are expressed in points.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> resizeRange() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Row height for a single row and a range of rows.
  sheet.getRangeByName('A1').rowHeight = 10;
  sheet.getRangeByName('A2:A5').rowHeight = 20;

  // Column width for a single column and a range of columns.
  sheet.getRangeByName('A1').columnWidth = 20;
  sheet.getRangeByName('A2:A5').columnWidth = 30;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Resize a single row or column in pixels

A single row or column can also be resized using the `setRowHeightInPixels` and `setColumnWidthInPixels` methods of the `Worksheet`. Both methods take the row or column index and the new size in pixels.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> resizeSingle() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Set the height of row 2 to 30 pixels.
  sheet.setRowHeightInPixels(2, 30);

  // Set the width of column 2 to 20 pixels.
  sheet.setColumnWidthInPixels(2, 20);

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Move a worksheet

Worksheets can be reordered by using the `moveTo` method of the `Worksheets` collection. You can move a worksheet by passing either the source `Worksheet` reference or its zero-based index, along with the new zero-based position.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> moveWorksheet() async {
  // Create a workbook with twenty worksheets.
  final Workbook workbook = Workbook(20);

  // Get references to two worksheets.
  final Worksheet sourceA = workbook.worksheets[10];
  final Worksheet sourceB = workbook.worksheets[3];

  // Move sourceA to position 5 and sourceB to position 15.
  workbook.worksheets.moveTo(sourceA, 5);
  workbook.worksheets.moveTo(sourceB, 15);

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Freeze panes

A portion of the worksheet can be frozen to keep specific rows or columns visible while scrolling. Call `freezePanes()` on the cell that should mark the boundary: all rows above and columns to the left of that cell remain frozen.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> freezePanes() async {
  final Workbook workbook = Workbook(1);
  final Worksheet worksheet = workbook.worksheets[0];
  worksheet.getRangeByName('A1:H10').text = 'FreezePanes';

  // Freeze row 1 by passing A2 as the boundary cell.
  worksheet.getRangeByName('A2').freezePanes();

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Unfreeze panes

Existing freeze panes can be removed by calling `unfreezePanes()` on the worksheet.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> unfreezePanes() async {
  final Workbook workbook = Workbook(1);
  final Worksheet worksheet = workbook.worksheets[0];
  worksheet.getRangeByName('A1:H10').text = 'FreezePanes';

  // Freeze and then unfreeze the panes.
  worksheet.getRangeByName('A2').freezePanes();
  worksheet.unfreezePanes();

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Right-to-left direction

### Worksheet-level RTL

The display direction of a single worksheet can be switched to right-to-left through the `isRightToLeft` property of the `Worksheet`.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> worksheetRtl() async {
  final Workbook workbook = Workbook(1);
  final Worksheet sheet = workbook.worksheets[0];

  // Display the worksheet in right-to-left direction.
  sheet.isRightToLeft = true;
  sheet.getRangeByName('A1').setText('Hello World');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Workbook-level RTL

The display direction of the entire workbook can be switched to right-to-left through the `isRightToLeft` property of the `Workbook`. This setting applies to every worksheet in the workbook.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> workbookRtl() async {
  final Workbook workbook = Workbook(2);
  final Worksheet sheet1 = workbook.worksheets[0];
  final Worksheet sheet2 = workbook.worksheets[1];

  // Display every worksheet in right-to-left direction.
  workbook.isRightToLeft = true;

  sheet1.getRangeByName('A1').setText('Hello World');
  sheet2.getRangeByName('A1').setText('Hello World');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Save as CSV

A worksheet that contains text, date-time, and number values can be exported to CSV format. The default separator is a comma (`,`); a custom separator can be passed to `saveAsCSV`.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> saveAsCsv() async {
  final Workbook workbook = Workbook();
  final Worksheet worksheet = workbook.worksheets[0];

  // Rename the worksheet.
  worksheet.name = 'csv format';
  worksheet.showGridlines = false;
  worksheet.enableSheetCalculations();

  // Header row.
  worksheet.getRangeByName('A1').setText('Date');
  worksheet.getRangeByName('B1').setText('Region');
  worksheet.getRangeByName('C1').setText('Employee');
  worksheet.getRangeByName('D1').setText('Item');
  worksheet.getRangeByName('E1').setText('Units');
  worksheet.getRangeByName('F1').setText('Unit Cost');
  worksheet.getRangeByName('G1').setText('Total');

  // Date column.
  worksheet.getRangeByName('A2').setDateTime(DateTime(2007, 12, 15));
  worksheet.getRangeByName('A3').setDateTime(DateTime(2007, 12, 18));
  worksheet.getRangeByName('A4').setDateTime(DateTime(2007, 12, 21));
  worksheet.getRangeByName('A5').setDateTime(DateTime(2007, 12, 24));
  worksheet.getRangeByName('A6').setDateTime(DateTime(2007, 12, 27));
  worksheet.getRangeByName('A7').setDateTime(DateTime(2007, 12, 30));
  worksheet.getRangeByName('A8').setDateTime(DateTime(2008, 1, 2));

  // Region column.
  worksheet.getRangeByName('B2').setText('Central');
  worksheet.getRangeByName('B3').setText('Wast');
  worksheet.getRangeByName('B4').setText('Central');
  worksheet.getRangeByName('B5').setText('East');
  worksheet.getRangeByName('B6').setText('East');
  worksheet.getRangeByName('B7').setText('East');
  worksheet.getRangeByName('B8').setText('East');

  // Employee column.
  worksheet.getRangeByName('C2').setText('Jones');
  worksheet.getRangeByName('C3').setText('Kivell');
  worksheet.getRangeByName('C4').setText('Howard');
  worksheet.getRangeByName('C5').setText('Gill');
  worksheet.getRangeByName('C6').setText('Anderson');
  worksheet.getRangeByName('C7').setText('Anderson');
  worksheet.getRangeByName('C8').setText('Anderson');

  // Item column.
  worksheet.getRangeByName('D2').setText('Pen Set');
  worksheet.getRangeByName('D3').setText('Binder');
  worksheet.getRangeByName('D4').setText('Pen & Pencil');
  worksheet.getRangeByName('D5').setText('Pen');
  worksheet.getRangeByName('D6').setText('Binder');
  worksheet.getRangeByName('D7').setText('Pen Set');
  worksheet.getRangeByName('D8').setText('Pen Set');

  // Units column.
  worksheet.getRangeByName('E2').number = 700;
  worksheet.getRangeByName('E3').number = 85;
  worksheet.getRangeByName('E4').number = 62;
  worksheet.getRangeByName('E5').number = 58;
  worksheet.getRangeByName('E6').number = 10;
  worksheet.getRangeByName('E7').number = 19;
  worksheet.getRangeByName('E8').number = 6;

  // Unit cost column.
  worksheet.getRangeByName('F2').number = 1.99;
  worksheet.getRangeByName('F3').number = 19.99;
  worksheet.getRangeByName('F4').number = 4.99;
  worksheet.getRangeByName('F5').number = 19.99;
  worksheet.getRangeByName('F6').number = 4.99;
  worksheet.getRangeByName('F7').number = 2.99;
  worksheet.getRangeByName('F8').number = 1.99;

  // Apply currency format to the unit cost column.
  worksheet.getRangeByName('F2:F8').numberFormat = r"'$'#,##0.00";

  // Total column (formula).
  worksheet.getRangeByName('G2').formula = 'E2*F2';
  worksheet.getRangeByName('G3').formula = 'E3*F3';
  worksheet.getRangeByName('G4').formula = 'E4*F4';
  worksheet.getRangeByName('G5').formula = 'E5*F5';
  worksheet.getRangeByName('G6').formula = 'E6*F6';
  worksheet.getRangeByName('G7').formula = 'E7*F7';
  worksheet.getRangeByName('G8').formula = 'E8*F8';

  // Apply currency format to the total column.
  worksheet.getRangeByName('G2:G8').numberFormat = r"'$'#,##0_)";

  // Save the workbook as CSV using a comma separator.
  final List<int> bytes = workbook.saveAsCSV(',');
  workbook.dispose();
}
{% endhighlight %}

## Named ranges

A named range is one or more cells that have been given a name. Named ranges make formulas easier to read and understand. A named range can be defined at the workbook level (visible to every worksheet) or at the worksheet level (scoped to a single worksheet). Names are case-insensitive and must be unique within their scope.

### Define a workbook-level named range

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> workbookNamedRange() async {
  final Workbook workbook = Workbook(1);
  final Worksheet worksheet = workbook.worksheets[0];
  final Range range = worksheet.getRangeByName('A1:C1');

  // Define a named range at the workbook level.
  workbook.names.add('BookName', range);

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Define a worksheet-level named range

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> worksheetNamedRange() async {
  final Workbook workbook = Workbook(1);
  final Worksheet worksheet = workbook.worksheets[0];
  final Range range = worksheet.getRangeByName('A1:C1');

  // Define a named range at the worksheet level.
  worksheet.names.add('SheetName', range);

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Use a named range in a formula

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> namedRangeInFormula() async {
  final Workbook workbook = Workbook(1);
  final Worksheet worksheet = workbook.worksheets[0];

  // Set values in cells.
  worksheet.getRangeByName('A1').setNumber(10);
  worksheet.getRangeByName('A2').setNumber(20);

  // Define two worksheet-level named ranges.
  final Range range1 = worksheet.getRangeByName('A1');
  worksheet.names.add('FirstRange', range1);

  final Range range2 = worksheet.getRangeByName('A2');
  worksheet.names.add('SecondRange', range2);

  // Use the named ranges in a formula.
  worksheet.getRangeByName('A3').formula =
      '=IF(FirstRange<SecondRange, "Yes", "No")';

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Delete a named range

Both workbook- and worksheet-level named ranges can be removed by calling `delete()` on the `Name` object.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> deleteNamedRange() async {
  final Workbook workbook = Workbook(1);
  final Worksheet worksheet = workbook.worksheets[0];
  worksheet.getRangeByName('A1:D4').setText('NamedRange');

  // Define several worksheet-level named ranges.
  final Name name1 =
      worksheet.names.add('named1', worksheet.getRangeByName('A1:C1'));
  final Name name2 =
      worksheet.names.add('named2', worksheet.getRangeByName('A2:C2'));
  final Name name3 =
      worksheet.names.add('named3', worksheet.getRangeByName('A3:C3'));
  final Name name4 =
      worksheet.names.add('named4', worksheet.getRangeByName('A4:C4'));

  // Delete the second named range.
  name2.delete();

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## See also

* [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview)
* [Working with Workbook](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-workbook)
* [Working with Formulas](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-formulas)
* [Worksheet API reference](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Worksheet-class.html)
