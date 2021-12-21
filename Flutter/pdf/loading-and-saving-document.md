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
List<int> bytes = document.save();

//Saves the bytes to the file system
File('output.pdf').writeAsBytes(bytes);

{% endhighlight %}
