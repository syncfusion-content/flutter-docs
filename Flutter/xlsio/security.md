---
layout: post
title: Excel Security using Syncfusion Flutter XlsIO
description: Learn how to apply Excel security to Excel documents using Flutter XlsIO and briefs about Security in Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Excel Security using Syncfusion XlsIO for Flutter

You can protect other users from viewing, moving, editing, or deleting important data in a worksheet or workbook by [protecting a worksheet or workbook](https://support.office.com/en-us/article/Password-protect-worksheet-or-workbook-elements-dbf706e0-ba22-4a08-84d8-552db16eef11), with or without a password.

N> Before you begin, make sure you have completed the [Getting Started with Flutter XlsIO](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/getting-started) steps to add the package and import it.

N> In production code, use `await workbook.save()` (asynchronous) and wrap workbook usage in a `try/finally` block to call `workbook.dispose()`. The samples below use `saveSync()` and direct disposal for brevity.

## Protect workbook elements

To keep others from making structural changes to your document — such as moving, deleting, and adding sheets — you can protect the workbook in Flutter XlsIO. The `workbook.protect` method accepts two flags:

* `isProtectWindow` – Prevents users from changing the position or size of the workbook window.
* `isProtectContent` – Prevents users from adding, removing, renaming, hiding, or moving worksheets.

The following code example illustrates how to protect a workbook with a password.

{% highlight dart %}

import 'dart:io';
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Assigning text to cells.
final Range range = sheet.getRangeByName('A1');
range.setText('WorkBook Protected');

final bool isProtectWindow = true;
final bool isProtectContent = true;

// Protect Workbook
workbook.protect(isProtectWindow, isProtectContent, 'password');

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
await File('WorkbookProtect.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

To remove workbook protection, call `workbook.unprotect('password')`.

## Protect Worksheet

Flutter XlsIO provides support for protecting elements in a worksheet by using the `protect` method of `Worksheet`. You can fine-tune which operations are allowed for the user by setting properties on the `ExcelSheetProtectionOption` class, such as `all`, `insertRows`, `deleteRows`, `insertColumns`, `deleteColumns`, `formatCells`, `formatColumns`, `formatRows`, `selectLockedCells`, `selectUnlockedCells`, `sort`, and `useAutoFilter`. Setting `options.all = true` disables all of them.

The following code example illustrates how to protect a worksheet with a password.

{% highlight dart %}

import 'dart:io';
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Assigning text to cells.
final Range range = sheet.getRangeByName('A1');
range.setText('Worksheet Protected');

// ExcelSheetProtectionOption.
final ExcelSheetProtectionOption options = ExcelSheetProtectionOption();
options.all = true;

// Protecting the Worksheet by using a Password.
sheet.protect('Password', options);

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
await File('WorksheetProtect.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

N> By using the `ExcelSheetProtectionOption` class, you can set protection for individual worksheet elements/operations. To remove worksheet protection, call `sheet.unprotect('Password')`.

## Protect Cell

Flutter XlsIO supports locking and unlocking cells by using the cell's `Locked` property of `CellStyle`. This can be manipulated to make certain cells editable in a protected worksheet. The cell's lock state is only enforced when the worksheet itself is protected, so the cell style and `sheet.protect(...)` must both be configured before saving.

The following code example illustrates how to lock a worksheet and then unlock a specific cell so that it remains editable.

{% highlight dart %}

import 'dart:io';
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Assigning text to cells.
final Range range = sheet.getRangeByName('A1');
range.setText('Worksheet Protected');

// Unlock the cell so it remains editable after the worksheet is protected.
range.cellStyle.locked = false;

// Protecting the Worksheet by using a Password.
sheet.protect('Password');

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
await File('ProtectCell.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

N> By default, cells are locked. Locking or unlocking a cell in an unprotected worksheet has no visible effect until the worksheet is protected.

## See also

* [Getting Started with Flutter XlsIO](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/getting-started)
* [Working with Workbook](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-workbook)
* [Working with Excel Worksheet](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-excel-worksheet)
* [Working with Cells](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-cells)
