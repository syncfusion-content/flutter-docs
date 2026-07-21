---
layout: post
title: Getting Started for Syncfusion Flutter XlsIO
description: Learn how to create Excel document with all basic elements and save it in browser or mobile devices by using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Getting Started with Flutter XlsIO

This section explains the steps required to create an Excel document with a few lines of code. This section covers only the minimal features needed to get started with Excel.

## Steps to create Excel document in Flutter application

Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://docs.flutter.dev/get-started/test-drive#choose-your-ide) documentation.

**Add dependency**

Add the Syncfusion Flutter XlsIO dependency to your pubspec.yaml file.

{% highlight dart %}

dependencies: 
syncfusion_flutter_xlsio: ^xx.x.xx

{% endhighlight %}

N> Here **xx.x.xx** denotes the current version of [Syncfusion Flutter XlsIO](https://pub.dev/packages/syncfusion_flutter_xlsio/versions) package.

**Get packages**

Run the following command to get the required packages.

{% highlight dart %}

$ flutter pub get

{% endhighlight %}

**Import package**

Import the following package in your Dart code.

{% highlight dart %}

import 'package:syncfusion_flutter_xlsio/xlsio.dart';

{% endhighlight %}

Add a new button widget inside the Center widget.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
      child: ElevatedButton(
        onPressed: _createExcel,
        child: const Text('Create Excel'),
      ),
    ),
  );
}

{% endhighlight %}

Include the following code snippet in the button click event to create an Excel file.

{% highlight dart %}

Future<void> _createExcel() async {
  // Create a new Excel Document.
  final Workbook workbook = Workbook();

  // Accessing worksheet via index.
  final Worksheet sheet = workbook.worksheets[0];

  // Set the text value.
  sheet.getRangeByName('A1').setText('Hello World!');

  // Save and dispose the document.
  final List<int> bytes = workbook.saveSync();
  workbook.dispose();

  // Save the Excel file in the local machine.
  File('Output.xlsx').writeAsBytes(bytes);
}

{% endhighlight %}

> This sample writes the file to the current working directory and is intended for desktop targets. For mobile and web, refer to the platform-specific sections below.

## Create an Excel document on mobile

You can create an Excel document in mobile by using the following steps:

**Add dependency**

Add the following packages to your pub spec file.

{% highlight dart %}

path_provider: ^1.6.5
open_file: ^3.0.1

{% endhighlight %}

**Import package**

{% highlight dart %}

import 'dart:io';
import 'package:open_file/open_file.dart';
import 'package:path_provider/path_provider.dart';

{% endhighlight %}

Include the following code snippet to create an Excel document in mobile.

{% highlight dart %}

Future<void> _createExcel() async {
// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Set the text value.
sheet.getRangeByName('A1').setText('Hello World!');

// Save and dispose the document.
final List<int> bytes = workbook.saveSync();
workbook.dispose();

// Get external storage directory
final directory = await getExternalStorageDirectory();

// Get directory path
final path = directory.path;

// Create an empty file to write Excel data
File file = File('$path/Output.xlsx');

// Write Excel data
await file.writeAsBytes(bytes, flush: true);

// Open the Excel document in mobile
OpenFile.open('$path/Output.xlsx');

}


{% endhighlight %}

## Create an Excel document on the web

You can create an Excel document on the web by using the following steps.

**Import package**

{% highlight dart %}

import 'dart:convert';
import 'dart:html';

{% endhighlight %}

Include the following code snippet to create an Excel document on the web.

{% highlight dart %}
Future<void> _createExcel() async {
  // Create a new Excel Document.
  final Workbook workbook = Workbook();

  // Accessing worksheet via index.
  final Worksheet sheet = workbook.worksheets[0];

  // Set the text value.
  sheet.getRangeByName('A1').setText('Hello World!');

  // Save and dispose the document.
  final List<int> bytes = workbook.saveSync();
  workbook.dispose();

  // Download the output file on the web.
  AnchorElement(
    href:
        "data:application/octet-stream;charset=utf-16le;base64,${base64.encode(bytes)}")
    ..setAttribute("download", "output.xlsx")
    ..click();
}
{% endhighlight %}

## Create an Excel document on desktop

Run `flutter config --enable-windows-desktop --enable-macos-desktop --enable-linux-desktop` to enable desktop support, then follow the steps in the [Flutter desktop guide](https://flutter.dev/multi-platform/desktop).

You can create an Excel document on desktop by using the following steps:

**Add dependency**

Add the following packages to your pubspec.yaml file.

{% highlight dart %}

path_provider: ^2.0.1

{% endhighlight %}

**Import package**

{% highlight dart %}

import 'package:path_provider/path_provider.dart';

{% endhighlight %}

Include the following code snippet to create an Excel document on desktop.

{% highlight dart %}

Future<void> _createExcel() async {
  // Create a new Excel Document.
  final Workbook workbook = Workbook();

  // Accessing worksheet via index.
  final Worksheet sheet = workbook.worksheets[0];

  // Set the text value.
  sheet.getRangeByName('A1').setText('Hello World!');

  // Save and dispose the document.
  final List<int> bytes = workbook.saveSync();
  workbook.dispose();

  // Get the storage folder location using the path_provider package.
  final Directory directory = await getApplicationSupportDirectory();
  final String path = directory.path;
  final File file =
      File(Platform.isWindows ? '$path\\Output.xlsx' : '$path/Output.xlsx');
  await file.writeAsBytes(bytes, flush: true);
  if (Platform.isWindows) {
    await Process.run('start', <String>['$path\\Output.xlsx'],
        runInShell: true);
  } else if (Platform.isMacOS) {
    await Process.run('open', <String>['$path/Output.xlsx'],
        runInShell: true);
  } else if (Platform.isLinux) {
    await Process.run('xdg-open', <String>['$path/Output.xlsx'],
        runInShell: true);
  }
}

{% endhighlight %}   