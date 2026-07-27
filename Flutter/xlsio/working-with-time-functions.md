---
layout: post
title: Working with Time Function Formulas | Syncfusion Flutter XlsIO
description: Learn how to apply time function formulas and read calculated values in the cells of an Excel worksheet using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with Time Function Formulas

Time function formulas return the current date, the current date and time, or a date-time value derived from cell arguments. Syncfusion Flutter XlsIO supports the following time functions:

* [NOW](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-time-functions#now-function) — returns the serial number of the current date and time.
* [TODAY](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-time-functions#today-function) — returns the serial number of the current date.

N> Both `NOW` and `TODAY` are recalculated every time the workbook is loaded into Syncfusion Flutter XlsIO. The returned value reflects the date and time of the device that performs the calculation.

For prerequisites and installation steps, see the [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview). For background on formulas and how to enable calculation, see [Working with Formulas](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-formulas).

N> The code samples in this document use `await workbook.save()`. Always call `workbook.dispose()` after saving to release the XlsIO DOM memory, ideally inside a `try/finally` block. Each function sample calls `enableSheetCalculations()` so the calculated value is available through the `calculatedValue` property of a `Range`.

## NOW function

The `NOW` function returns the serial number of the current date and time. It takes no arguments. The returned value is a numeric serial number; apply a number format such as `m/d/yyyy h:mm` to display it as a date and time.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> nowFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  sheet.enableSheetCalculations();

  // Write the current date and time to A1.
  final Range range = sheet.getRangeByName('A1');
  range.setFormula('=NOW()');

  // Apply a date-time number format so the value is displayed as a date and time.
  range.numberFormat = 'm/d/yyyy h:mm';

  // The calculated value is available as a string. Parse it to a double if needed.
  final String result = range.calculatedValue;
  // ignore: avoid_print
  print(result);

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## TODAY function

The `TODAY` function returns the serial number of the current date. It takes no arguments. The returned value is a numeric serial number; apply a number format such as `mm/dd/yyyy` to display it as a date.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> todayFormula() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  sheet.enableSheetCalculations();

  // Write the current date to A1.
  final Range range = sheet.getRangeByName('A1');
  range.setFormula('=TODAY()');

  // Apply a date number format so the value is displayed as a date.
  range.numberFormat = 'mm/dd/yyyy';

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Related functions

The following time-related functions are also supported by Syncfusion Flutter XlsIO:

| Function | Description |
|----------|-------------|
| `DATE` | Returns the serial number of a date assembled from year, month, and day arguments. |
| `TIME` | Returns the serial number of a time assembled from hour, minute, and second arguments. |
| `YEAR`, `MONTH`, `DAY` | Extract the corresponding component from a date. |
| `HOUR`, `MINUTE`, `SECOND` | Extract the corresponding component from a time. |
| `DATEVALUE`, `TIMEVALUE` | Convert a text representation of a date or time to a serial number. |

For the complete list of supported format codes, see [Working with Cell Formatting](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-cell-formatting#apply-number-formats).

## See also

* [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview)
* [Working with Formulas](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-formulas)
* [Working with Cell Formatting](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-cell-formatting)
* [Working with Cells](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-cells)
* [Range API reference](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Range-class.html)
