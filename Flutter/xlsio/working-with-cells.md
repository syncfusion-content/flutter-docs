---
layout: post
title: Working with Cells | Syncfusion Flutter XlsIO
description: Learn how to add text, number, date-time, and generic values to Excel worksheet cells, work with hyperlinks, and apply data filters using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with Worksheet Cells

A `Range` represents one or more cells on a worksheet. Syncfusion Flutter XlsIO exposes dedicated methods for setting the most common value types on a `Range`, and a generic `setValue()` for cases where the value type is determined at runtime.

For prerequisites and installation steps, see the [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview). For information on saving and disposing of a workbook, see [Working with Workbook](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-workbook).

N> The code samples in this document use `await workbook.save()`. Always call `workbook.dispose()` after saving to release the XlsIO DOM memory, ideally inside a `try/finally` block.

## Add a value to a cell

The `setValue()` method assigns a value to a range. The value can be a number, a text, or a date-time value; the underlying data type is detected automatically.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> addValue() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Set a numeric value.
  sheet.getRangeByName('A1').setValue(44);

  // Set a text value.
  sheet.getRangeByName('A2').setValue('Hello');

  // Set a date-time value.
  sheet.getRangeByName('A3').setValue(DateTime(2020, 7, 7, 1, 0, 0));

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

The dedicated methods documented below provide the same result with stronger typing and a clearer intent.

## Add text to a cell

Use the `setText()` method to add a text value to a range. To add a text value without going through `setText()`, you can also assign a `String` to the `text` getter on the range; both have the same effect.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> addText() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Add a text value using setText().
  sheet.getRangeByName('A1').setText('Hello World');

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Add a number to a cell

Use the `setNumber()` method to add a numeric value. The method accepts any `num` (including `int` and `double`).

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> addNumber() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Add a numeric value using setNumber().
  sheet.getRangeByName('A1').setNumber(4444);

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Add a date-time value to a cell

Use the `setDateTime()` method to add a `DateTime` value. The value is stored as an Excel date serial; the time component is preserved.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> addDateTime() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Add a date-time value using setDateTime().
  sheet.getRangeByName('A1').setDateTime(DateTime(2020, 7, 7, 1, 0, 0));

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Hyperlinks

A hyperlink provides quick access to a web page, a location in the workbook, an e-mail address, or an external file. A hyperlink can be added to a cell range or to a picture.

The supported `HyperlinkType` values are:

| Value | Description |
|-------|-------------|
| `HyperlinkType.url` | A web URL (also used for `mailto:` e-mail links). |
| `HyperlinkType.workbook` | A cell reference within the workbook, formatted as `SheetName!CellAddress`. |
| `HyperlinkType.file` | A path to an external file. |
| `HyperlinkType.unc` | A UNC path to a file on a network share. |

Common properties on a `Hyperlink` include `textToDisplay` (the visible label) and `screenTip` (the tooltip shown on hover).

### Hyperlinks on a cell range

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> addHyperlinks() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Hyperlink to a web URL.
  final Hyperlink hyperlink = sheet.hyperlinks.add(
    sheet.getRangeByName('A1'),
    HyperlinkType.url,
    'http://www.syncfusion.com',
  );
  hyperlink.screenTip = 'To know more about Syncfusion products, go through this link.';
  hyperlink.textToDisplay = 'Syncfusion';

  // Hyperlink to an e-mail address (use a mailto: URL with HyperlinkType.url).
  final Hyperlink hyperlink1 = sheet.hyperlinks.add(
    sheet.getRangeByName('A3'),
    HyperlinkType.url,
    'mailto:Username@syncfusion.com',
  );
  hyperlink1.screenTip = 'Send Mail';

  // Hyperlink to an external file.
  final Hyperlink hyperlink2 = sheet.hyperlinks.add(
    sheet.getRangeByName('A5'),
    HyperlinkType.file,
    r'C:\Program files',
  );
  hyperlink2.screenTip = 'File path';
  hyperlink2.textToDisplay = 'Hyperlink for files using File as type';

  // Hyperlink to a UNC path.
  final Hyperlink hyperlink3 = sheet.hyperlinks.add(
    sheet.getRangeByName('A7'),
    HyperlinkType.unc,
    r'C:\Documents and Settings',
  );
  hyperlink3.screenTip = 'Click here for files';
  hyperlink3.textToDisplay = 'Hyperlink for files using UNC as type';

  // Hyperlink to another cell in the workbook.
  final Hyperlink hyperlink4 = sheet.hyperlinks.add(
    sheet.getRangeByName('A9'),
    HyperlinkType.workbook,
    'Sheet1!A15',
  );
  hyperlink4.screenTip = 'Click Here';
  hyperlink4.textToDisplay = 'Hyperlink to cell A15';

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Hyperlinks on a picture

The `addBase64(row, column, base64String)` method of `Worksheet.pictures` adds a picture from a base64-encoded string. The first two arguments are the 1-based row and column of the picture's top-left corner.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

// Base64-encoded image used in this sample.
const String image1jpg = '<BASE64_IMAGE_DATA>';

Future<void> addPictureHyperlink() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Add a picture at row 1, column 1 from a base64 string.
  final Picture picture1 = sheet.pictures.addBase64(1, 1, image1jpg);

  // Attach a hyperlink to the picture.
  final Hyperlink link = sheet.hyperlinks.addImage(
    picture1,
    HyperlinkType.url,
    'http://www.syncfusion.com',
  );
  link.screenTip = 'About Syncfusion';

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Data filtering

Data filtering displays only the rows that meet user-specified criteria and hides the rest. Syncfusion Flutter XlsIO supports the following filter types: text, custom, date, dynamic, and color. All filter types are applied through the `AutoFilter` class after a filter range has been set on the worksheet.

To avoid duplication, the samples in this section reuse the following helper that populates a worksheet with sample data and assigns the filter range:

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

void populateFilterSampleData(Worksheet worksheet) {
  final List<String> titles = <String>[
    'Title',
    'Sales Representative',
    'Owner',
    'Owner',
    'Sales Representative',
    'Order Administrator',
    'Sales Representative',
    'Marketing Manager',
    'Owner',
    'Owner',
  ];

  final List<DateTime> dojs = <DateTime>[
    DateTime(2006, 9, 10),
    DateTime(2000, 6, 10),
    DateTime(2002, 9, 18),
    DateTime(2009, 5, 23),
    DateTime(2012, 1, 6),
    DateTime(2007, 7, 19),
    DateTime(2008, 6, 30),
    DateTime(2002, 4, 16),
    DateTime(2008, 11, 29),
  ];

  final List<String> cities = <String>[
    'Berlin',
    'Mexico D.F.',
    'Mexico D.F.',
    'London',
    'Lulea',
    'Mannheim',
    'Strasbourg',
    'Madrid',
    'Marseille',
  ];

  worksheet.getRangeByName('A1').setText('Title');
  worksheet.getRangeByName('B1').setText('DOJ');
  worksheet.getRangeByName('C1').setText('City');

  for (int i = 0; i < titles.length - 1; i++) {
    worksheet.getRangeByName('A${i + 2}').setText(titles[i + 1]);
    worksheet.getRangeByName('B${i + 2}').dateTime = dojs[i];
    worksheet.getRangeByName('C${i + 2}').setText(cities[i]);
  }

  // Set the filter range to A1:C10.
  worksheet.autoFilters.filterRange = worksheet.getRangeByName('A1:C10');
}
{% endhighlight %}

### Text filter

A text filter keeps only the rows that contain the specified text. The filter is case-sensitive and is applied through `addTextFilter()`.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> textFilter() async {
  final Workbook workbook = Workbook();
  final Worksheet worksheet = workbook.worksheets[0];

  populateFilterSampleData(worksheet);

  // Apply a text filter on the first column of the filter range.
  final AutoFilter autofilter = worksheet.autoFilters[0];
  autofilter.addTextFilter(<String>{'Owner'});

  worksheet.getRangeByName('A1:C10').autoFitColumns();

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Custom filter

A custom filter keeps only the rows that match one or two numeric comparisons. The comparisons are configured through the `firstCondition` and `secondCondition` properties of the `AutoFilter`. Use the `logicalOperator` property to choose how the two conditions are combined (AND or OR).

The supported `ExcelFilterCondition` operators include `equal`, `notEqual`, `greaterThan`, `greaterOrEqual`, `lessThan`, `less`, `between`, and `notBetween`.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> customFilter() async {
  final Workbook workbook = Workbook();
  final Worksheet worksheet = workbook.worksheets[0];

  populateFilterSampleData(worksheet);

  final AutoFilter autofilter = worksheet.autoFilters[1];

  // First condition: date serial >= 10.
  autofilter.firstCondition.conditionOperator = ExcelFilterCondition.greaterOrEqual;
  autofilter.firstCondition.numberValue = 10;

  // Second condition: date serial < 15.
  autofilter.secondCondition.conditionOperator = ExcelFilterCondition.less;
  autofilter.secondCondition.numberValue = 15;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Date filter

A date filter keeps only the rows whose date values match a specific year, month, or day. The filter is applied through `addDateFilter()`, which reads the relevant part of the supplied `DateTime` value depending on the `DateTimeFilterType` (for example, `year` reads only the year, `month` reads the year and month).

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> dateFilter() async {
  final Workbook workbook = Workbook();
  final Worksheet worksheet = workbook.worksheets[0];

  populateFilterSampleData(worksheet);

  // Apply a date filter on the second column of the filter range (the DOJ column).
  final AutoFilter autofilter = worksheet.autoFilters[1];
  autofilter.addDateFilter(DateTime(2002), DateTimeFilterType.year);

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Dynamic filter

A dynamic filter keeps only the rows whose date values fall in a relative calendar range such as a quarter or a month. The filter is applied through `addDynamicFilter()`. The available `DynamicFilterType` values include `quarter1`, `quarter2`, `quarter3`, `quarter4`, `january`, `february`, and so on.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> dynamicFilter() async {
  final Workbook workbook = Workbook();
  final Worksheet worksheet = workbook.worksheets[0];

  populateFilterSampleData(worksheet);

  // Apply a dynamic filter on the second column of the filter range (the DOJ column).
  final AutoFilter autofilter = worksheet.autoFilters[1];
  autofilter.addDynamicFilter(DynamicFilterType.quarter2);

  worksheet.getRangeByName('A1:C10').autoFitColumns();

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Color filter

A color filter keeps only the rows whose cell color or font color matches the supplied color string. The color must already be set on the cell for the filter to match. The `ExcelColorFilterType` enum selects between `fontColor` and `cellColor`.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

void applyColorFormatting(Worksheet worksheet) {
  // Cell background colors.
  worksheet.getRangeByName('A2').cellStyle.backColor = '#008000';
  worksheet.getRangeByName('A3').cellStyle.backColor = '#0000FF';
  worksheet.getRangeByName('A4').cellStyle.backColor = '#FF0000';
  worksheet.getRangeByName('A5').cellStyle.backColor = '#FF0000';
  worksheet.getRangeByName('A6').cellStyle.backColor = '#FFFFFF';
  worksheet.getRangeByName('A7').cellStyle.backColor = '#FF0000';
  worksheet.getRangeByName('A8').cellStyle.backColor = '#FFFFFF';
  worksheet.getRangeByName('A9').cellStyle.backColor = '#0000FF';
  worksheet.getRangeByName('A10').cellStyle.backColor = '#008000';

  // Font colors.
  worksheet.getRangeByName('C2').cellStyle.fontColor = '#FF0000';
  worksheet.getRangeByName('C3').cellStyle.fontColor = '#008000';
  worksheet.getRangeByName('C4').cellStyle.fontColor = '#0000FF';
  worksheet.getRangeByName('C5').cellStyle.fontColor = '#000000';
  worksheet.getRangeByName('C6').cellStyle.fontColor = '#FF0000';
  worksheet.getRangeByName('C7').cellStyle.fontColor = '#008000';
  worksheet.getRangeByName('C8').cellStyle.fontColor = '#0000FF';
  worksheet.getRangeByName('C9').cellStyle.fontColor = '#000000';
  worksheet.getRangeByName('C10').cellStyle.fontColor = '#FF0000';
}
{% endhighlight %}

#### Font color filter

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> fontColorFilter() async {
  final Workbook workbook = Workbook();
  final Worksheet worksheet = workbook.worksheets[0];

  populateFilterSampleData(worksheet);
  applyColorFormatting(worksheet);

  // Apply a font color filter on the third column of the filter range (the City column).
  final AutoFilter autofilter = worksheet.autoFilters[2];
  autofilter.addColorFilter('#0000FF', ExcelColorFilterType.fontColor);

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

#### Cell color filter

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> cellColorFilter() async {
  final Workbook workbook = Workbook();
  final Worksheet worksheet = workbook.worksheets[0];

  populateFilterSampleData(worksheet);
  applyColorFormatting(worksheet);

  // Apply a cell color filter on the first column of the filter range (the Title column).
  final AutoFilter autofilter = worksheet.autoFilters[0];
  autofilter.addColorFilter('#FF0000', ExcelColorFilterType.cellColor);

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

> The `autoFilters` index in the samples above corresponds to the column position within the filter range. `autoFilters[0]` is the first column, `autoFilters[1]` is the second, and so on.

## See also

* [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview)
* [Working with Workbook](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-workbook)
* [Working with Cell Formatting](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/cell-formatting)
* [Working with Data Validation](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/data-validation)
* [Range API reference](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Range-class.html)
* [AutoFilter API reference](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/AutoFilter-class.html)
* [Release notes](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/release-notes)
