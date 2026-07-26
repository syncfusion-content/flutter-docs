---
layout: post
title: Working with Images | Syncfusion Flutter XlsIO
description: Learn how to add, format, and remove images in an Excel worksheet using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with Excel Images

Syncfusion Flutter XlsIO supports inserting JPEG and PNG images into a worksheet. Each image is represented by a `Picture` instance and is anchored to a top-left cell. The `Picture` class exposes properties for resizing, rotating, and flipping the image, and for moving it within the worksheet.

For prerequisites and installation steps, see the [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview). For background on worksheets, see [Working with Excel Worksheets](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-excel-worksheet).

N> The code samples in this document use `await workbook.save()`. Always call `workbook.dispose()` after saving to release the XlsIO DOM memory, ideally inside a `try/finally` block.

## Add an image

An image is added to a worksheet through the `sheet.pictures` collection. The `addStream` method accepts the 1-based row and column of the top-left anchor cell and the image bytes. The image bytes can be loaded from a file, an asset, or a `Uint8List` in memory.

```dart
import 'dart:io';
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> addImage() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Load the image bytes from a file. The path is relative to the current
  // working directory; replace with an absolute path or an asset path as
  // appropriate for your project.
  final List<int> imageBytes = await File('image.jpeg').readAsBytes();

  // Add the image to cell A1 (row 1, column 1).
  sheet.pictures.addStream(1, 1, imageBytes);

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
```

| `addStream` variant | Description |
|---------------------|-------------|
| `addStream(row, column, bytes)` | Add an image from a `List<int>` of bytes (for example, the result of `File.readAsBytes`). |
| `addBase64(row, column, base64String)` | Add an image from a base64-encoded string. |
| `add(row, column, image)` | Add an image from an in-memory image object (for example, a `ui.Image`). |

> The `addStream` and `addBase64` methods return the inserted `Picture`. Capture the return value if you need to modify the image (resize, rotate, hyperlink) later.

## Resize, flip, and rotate an image

The `Picture` class exposes the following properties for adjusting an image after it is added to the worksheet:

| Property | Type | Description |
|----------|------|-------------|
| `height` | `double` | Height of the image in pixels. |
| `width` | `double` | Width of the image in pixels. |
| `rotation` | `int` | Rotation angle in degrees (0 to 360, clockwise). |
| `horizontalFlip` | `bool` | Mirror the image along the vertical axis. |
| `verticalFlip` | `bool` | Mirror the image along the horizontal axis. |

```dart
import 'dart:io';
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> transformImage() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Load the image bytes and capture the Picture reference.
  final List<int> imageBytes = await File('image.jpeg').readAsBytes();
  final Picture picture = sheet.pictures.addStream(1, 1, imageBytes);

  // Resize the image to 200×200 pixels.
  picture.height = 200;
  picture.width = 200;

  // Rotate the image by 100 degrees clockwise.
  picture.rotation = 100;

  // Mirror the image horizontally.
  picture.horizontalFlip = true;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
```

## Position an image

The position of an image is set through the `topRow`, `bottomRow`, `leftColumn`, and `rightColumn` properties of the `Picture` class. These values are 1-based and define the cells that the image spans.

```dart
import 'dart:io';
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> positionImage() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  final List<int> imageBytes = await File('image.jpeg').readAsBytes();
  final Picture picture = sheet.pictures.addStream(1, 1, imageBytes);

  // Position the image across cells A1 to D5.
  picture.topRow = 1;
  picture.bottomRow = 5;
  picture.leftColumn = 1;
  picture.rightColumn = 4;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
```

## Remove an image

An image can be removed from the worksheet through the `removeAt` method of the `sheet.pictures` collection. The `Picture` instance is no longer valid after removal.

```dart
import 'dart:io';
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

Future<void> removeImage() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  final List<int> imageBytes = await File('image.jpeg').readAsBytes();
  sheet.pictures.addStream(1, 1, imageBytes);

  // Remove the first image.
  sheet.pictures.removeAt(0);

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
```

## See also

* [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview)
* [Working with Excel Worksheets](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-excel-worksheet)
* [Working with Workbook](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-workbook)
* [Picture API reference](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Picture-class.html)
* [Pictures collection API reference](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Pictures-class.html)
* [Release notes](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/release-notes)
