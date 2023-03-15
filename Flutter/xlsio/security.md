---
layout: post
title: Excel Security using Syncfusion Flutter XlsIO
description: Learn how to apply Excel security to Excel documents using Flutter XlsIO and briefs about Security in Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Excel Security using Flutter XlsIO

You can protect an anonymous user from viewing, moving, editing or deleting important data from a worksheet or workbook by [protecting a worksheet or workbook](https://support.office.com/en-ca/article/Password-protect-worksheet-or-workbook-elements-dbf706e0-ba22-4a08-84d8-552db16eef11#bmprotectelements), with or without a password.

## Protect workbook elements

To keep others from making structural changes to your documents such as moving, deleting and adding sheets, you can protect the workbook in Flutter XlsIO. 

The following code example illustrates how to protect a workbook with a password.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Assigning text to cells
final Range range = sheet.getRangeByName('A1');
range.setText('WorkBook Protected');

final bool isProtectWindow = true;
final bool isProtectContent = true;

// Protect Workbook
workbook.protect(isProtectWindow, isProtectContent, 'password');

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
File('WorkbookProtect.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

## Protect Worksheet 

Flutter XlsIO provides support for protecting elements in worksheets by using the **Protect** method of **Worksheet**.

The following code example illustrates how to protect a worksheet with a password. 

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Assigning text to cells
final Range range = sheet.getRangeByName('A1');
range.setText('Worksheet Protected');

// ExcelSheetProtectionOption
final ExcelSheetProtectionOption options = ExcelSheetProtectionOption();
options.all = true;

// Protecting the Worksheet by using a Password
sheet.protect('Password', options);

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
File('WorksheetProtect.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

N> By using the ExcelSheetProtectionOption class, you can set protection to the workbook elements/operations.

## Protect Cell

Flutter XlsIO supports locking and unlocking cells by using the cell's **Locked** property of __CellStyle__. This can be manipulated to make certain cells editable in a protected worksheet. 

N> By default, cells are locked. Lock or Unlock cell in an unprotected worksheet has no effect. 

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Assigning text to cells
final Range range = sheet.getRangeByName('A1');
range.setText('Worksheet Protected');

// Protecting the Worksheet by using a Password
sheet.protect('Password');

// Unlocking the cell to edit.
range.cellStyle.locked = false;

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
File('ProtectCell.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}