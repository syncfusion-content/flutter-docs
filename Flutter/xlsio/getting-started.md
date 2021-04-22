---
layout: post
title: Getting Started for Syncfusion Flutter XlsIO
description: Learn how to create Excel document with all basic elements and save it in browser or mobile devices by using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Getting Started for Syncfusion Flutter XlsIO

This section explains the steps required to create a Excel document by few lines of code. This section covers only the minimal features needed to learn to get started with the Excel.

## Steps to create Excel document in Flutter application

Create a simple project using the instructions given in the [`Getting Started with your first Flutter app'](https://flutter.dev/docs/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion Flutter XlsIO dependency to your pub spec file.

{% highlight dart %}

dependencies: 
syncfusion_flutter_xlsio: ^xx.x.xx

{% endhighlight %}

N> Here **xx.x.xx** denotes the current version of ['Syncfusion Flutter XlsIO'](https://pub.dev/packages/syncfusion_flutter_xlsio/versions) package.

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

Add a new button widget as a child of your container widget.

{% highlight dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
	body: Center(
	  child: RaisedButton(
		onPressed: _createExcel,
		  child: Text('Create Excel')
		)
	 )
  );
}

{% endhighlight %}

Include the following code snippet in the button click event to create a Excel file.

{% highlight dart %}

Future<void> _createExcel() async {
// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Set the text value.
sheet.getRangeByName('A1').setText('Hello World!');

// Save and dispose the document.
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

// Save the Excel file in the local machine.
File('Output.xlsx').writeAsBytes(bytes);

}

{% endhighlight %}

## Create a Excel document in mobile

You can create a Excel document in mobile by using the following steps:

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

Include the following code snippet to create a Excel document in mobile.

{% highlight dart %}

Future<void> _createExcel() async {
// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Set the text value.
sheet.getRangeByName('A1').setText('Hello World!');

// Save and dispose the document.
final List<int> bytes = workbook.saveAsStream();
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

## Create a Excel document in web

You can create a Excel document in web by using the following steps.

**Import package**

{% highlight dart %}

import 'dart:async';
import 'dart:convert';
import 'dart:js' as js;

{% endhighlight %}

Include the following code snippet to create a excel document in web.

{% highlight dart %}
Future<void> _createExcel() async {
// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Set the text value.
sheet.getRangeByName('A1').setText('Hello World!');

// Save and dispose the document.
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

js.context['excelData'] = base64.encode(bytes);
js.context['filename'] = 'Output.xlsx'; 
Timer.run(() { 
js.context.callMethod('_createExcel');
 });

{% endhighlight %}

Add the following code in the header section of index.html file under the web folder.

{% highlight dart %}

<script>
 async function _createExcel() {
  var excelAsDataUri = "data:application/vnd.openxmlformats-officedocument.spreadsheetml.sheet;base64, " + exceldata;
  var link = document.createElement('a');
  link.download = filename;
  link.href = excelAsDataUri;
  link.type = 'application/vnd.openxmlformats-officedocument.spreadsheetml.sheet';
  link.click();
}
</script>

{% endhighlight %}
