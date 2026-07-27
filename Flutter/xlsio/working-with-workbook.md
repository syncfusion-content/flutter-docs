---
layout: post
title: Working with Workbook in Syncfusion Flutter XlsIO | Syncfusion
description: Learn how to save the created workbook in different ways and dispose of it using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with Workbook

After creating or manipulating a workbook with the Syncfusion Flutter XlsIO library, you must save it to the file system and then dispose of the `Workbook` instance to release the memory consumed by the XlsIO DOM.

## Saving an Excel workbook to the file system

The Syncfusion Flutter XlsIO library provides both synchronous and asynchronous APIs to save a workbook in the XLSX format. Use the asynchronous `save()` method in production code to avoid blocking the UI thread.

### Synchronous save

The `saveAsStream()` method writes the workbook to an in-memory byte buffer synchronously.

{% highlight dart %}
import 'dart:io';
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> saveWorkbookSync() async {
  // Create a new workbook.
  final Workbook workbook = Workbook();

  // Access the first worksheet and write a value.
  final Worksheet sheet = workbook.worksheets[0];
  sheet.getRangeByName('A1').setText('Hello, Syncfusion Flutter XlsIO!');

  // Save the workbook as a byte array (XLSX format).
  final List<int> bytes = workbook.saveAsStream();

  // Dispose the workbook to release the XlsIO DOM memory.
  workbook.dispose();

  // Write the bytes to a file. The path is relative to the current working directory.
  await File('Output.xlsx').writeAsBytes(bytes);
}
{% endhighlight %}

### Asynchronous save

The `save()` method writes the workbook to an in-memory byte buffer asynchronously and is preferred for long-running operations.

{% highlight dart %}
import 'dart:io';
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> saveWorkbookAsync() async {
  // Create a new workbook.
  final Workbook workbook = Workbook();

  // Access the first worksheet and write a value.
  final Worksheet sheet = workbook.worksheets[0];
  sheet.getRangeByName('A1').setText('Hello, Syncfusion Flutter XlsIO!');

  // Save the workbook as a byte array (XLSX format).
  final List<int> bytes = await workbook.save();

  // Dispose the workbook to release the XlsIO DOM memory.
  workbook.dispose();

  // Write the bytes to a file. The path is relative to the current working directory.
  await File('Output.xlsx').writeAsBytes(bytes);
}
{% endhighlight %}

## Closing a workbook

Always call `dispose()` on the `Workbook` instance after you finish saving it. Failing to dispose of the workbook keeps the XlsIO DOM in memory, which can lead to memory pressure, especially in long-running mobile or web applications. The following code illustrates the recommended try/finally pattern to ensure `dispose()` is always called, even when an error occurs.

{% highlight dart %}
import 'dart:io';
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> saveAndDisposeWorkbook() async {
  // Create a new workbook.
  final Workbook workbook = Workbook();

  try {
    // Save the workbook as a byte array (XLSX format).
    final List<int> bytes = await workbook.save();

    // Write the bytes to a file.
    await File('Output.xlsx').writeAsBytes(bytes);
  } finally {
    // Dispose the workbook to release the XlsIO DOM memory.
    workbook.dispose();
  }
}
{% endhighlight %}

## See also

* [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview)
* [Workbook API reference](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Workbook-class.html)
