---
layout: post
title: Open and save PDF file in Flutter PDF library | Syncfusion
description: Learn here all about Open and save PDF file feature of Syncfusion Flutter PDF non-UI library and more.
platform: flutter
control: PDF
documentation: ug
---

# Open and save PDF file in Flutter PDF

## Opening an existing PDF document

You can open an existing PDF document by using the [`PdfDocument`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocument-class.html) class. The following example shows how to load an existing document from the list of bytes.

{% highlight dart %}

//Opens an existing document from the list of bytes
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

{% endhighlight %}

## Opening an existing PDF document from the base 64 string

You can open an existing document from the base 64 string by using the [`PdfDocument`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocument-class.html) class as shown below.

{% highlight dart %}

//Opens an existing document from the base 64 string
PdfDocument document = PdfDocument.fromBase64String(
    'JVBERi0xLjcNCiWDkvr+DQoxIDAgb2JqDQo8PA0KL1R5cGUgL0NhdGFsb2cNCi9QYWdlcyAyIDAgUg0KPj4NCmVuZG9iag0KMiAwIG9iag0KPDwNCi9UeXBlIC9QYWdlcw0KL0tpZHMgWzMgMCBSXQ0KL0NvdW50IDENCi9SZXNvdXJjZXMgPDw+Pg0KDQovTWVkaWFCb3ggWzAgMCA1OTUgODQyXQ0KPj4NCmVuZG9iag0KMyAwIG9iag0KPDwNCi9Db3VudCAxDQovVHlwZSAvUGFnZXMNCi9LaWRzIFs0IDAgUl0NCi9QYXJlbnQgMiAwIFINCj4+DQplbmRvYmoNCjQgMCBvYmoNCjw8DQovVHlwZSAvUGFnZQ0KL1BhcmVudCAzIDAgUg0KPj4NCmVuZG9iag0KeHJlZg0KMCA1DQowMDAwMDAwMDAwIDY1NTM1IGYNCjAwMDAwMDAwMTcgMDAwMDAgbg0KMDAwMDAwMDA3MiAwMDAwMCBuDQowMDAwMDAwMTgwIDAwMDAwIG4NCjAwMDAwMDAyNTkgMDAwMDAgbg0KdHJhaWxlcg0KPDwNCi9Sb290IDEgMCBSDQovU2l6ZSA1DQo+Pg0KDQpzdGFydHhyZWYNCjMxMg0KJSVFT0Y=');

{% endhighlight %}

## Saving a PDF document to list of bytes

You can save the manipulated PDF document as a list of bytes using the [`save`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocument/save.html) method of [`PdfDocument`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocument-class.html) class. Also, you can save the list of bytes to the file system as follows.

{% highlight dart %}

//Opens an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Saves the document into a list of bytes
List<int> bytes =await document.save();

//Saves the bytes to the file system
File('output.pdf').writeAsBytes(bytes);

{% endhighlight %}

## Save and open a PDF document in desktop

You can save and open a PDF document in desktop by using the following steps:

**Set up**

Configure and enable the desktop support to run the app.

{% highlight dart %} 

flutter config --enable-<platform>-desktop

{% endhighlight %}

N> You only need to execute `flutter config --enable-<platform>-desktop` once. You can always check the status of your configuration using the no-argument flutter config command.

Here you can get more details about [`How to add desktop support in the app`](https://docs.flutter.dev/desktop)

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

Include the following code snippet in _createPDF method to open the PDF document in mobile after saving it.

{% highlight dart %}

//Get external storage directory
final directory = await getExternalStorageDirectory();

//Get directory path
final path = directory.path;

//Create an empty file to write PDF data
File file = File('$path/Output.pdf');

//Write PDF data
await file.writeAsBytes(bytes, flush: true);

//Open the PDF document in mobile
OpenFile.open('$path/Output.pdf');

{% endhighlight %}
