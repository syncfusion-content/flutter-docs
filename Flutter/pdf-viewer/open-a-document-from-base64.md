---
layout: post
title: Open a Document From base64 in Flutter PDF Viewer | Syncfusion
description: Learn here about opening a PDF document from memory in Syncfusion® Flutter PDF Viewer widget (SfPdfViewer).
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Open a Document From Base64 in Flutter PDF Viewer (SfPdfViewer)

## Using SfPdfViewer.memory

To load a document from a base64 string, you can convert the base64 string to a [Uint8List](https://api.flutter.dev/flutter/dart-typed_data/Uint8List-class.html) using the [base64Decode](https://api.flutter.dev/flutter/dart-convert/base64Decode.html) method and pass it to the [SfPdfViewer.memory](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/SfPdfViewer.memory.html) constructor. The following code example explains the same.

* Import the `dart:convert` package to use the [base64Decode](https://api.flutter.dev/flutter/dart-convert/base64Decode.html) method.

{% tabs %}
{% highlight dart %}

import 'dart:convert';

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_pdfviewer/pdfviewer.dart';

void main() {
  runApp(const MaterialApp(
    home: MainApp(),
  ));
}

class MainApp extends StatelessWidget {
  const MainApp({super.key});

  @override
  Widget build(BuildContext context) {
    // Pass the base64 string of the PDF document to the SyncfusionPDFViewer widget.
    return const SyncfusionPDFViewer(base64: base64);
  }
}

class SyncfusionPDFViewer extends StatefulWidget {
  const SyncfusionPDFViewer({super.key, required this.base64});

  /// Base64 string of the PDF document.
  final String base64;

  @override
  State<SyncfusionPDFViewer> createState() => _SyncfusionPDFViewerState();
}

class _SyncfusionPDFViewerState extends State<SyncfusionPDFViewer> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SfPdfViewer.memory(
        // Decoding the base64 string to Uint8List.
        base64Decode(widget.base64),
      ),
    );
  }
}

{% endhighlight %}
{% endtabs %}

## Using Custom PDFSource

To load a document from a base64 string, you can convert the base64 string to a [Uint8List](https://api.flutter.dev/flutter/dart-typed_data/Uint8List-class.html) using the [base64Decode](https://api.flutter.dev/flutter/dart-convert/base64Decode.html) method and pass it to the [SfPdfViewer.memory](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/SfPdfViewer.memory.html) constructor. The following code example explains the same.

* Import the `dart:convert` package to use the [base64Decode](https://api.flutter.dev/flutter/dart-convert/base64Decode.html) method.

{% tabs %}
{% highlight dart %}

import 'dart:convert';
import 'dart:typed_data';

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_pdfviewer/pdfviewer.dart';

void main() {
  runApp(const MaterialApp(
    home: MainApp(),
  ));
}

class MainApp extends StatelessWidget {
  const MainApp({super.key});

  @override
  Widget build(BuildContext context) {
    // Pass the base64 string of the PDF document to the SyncfusionPDFViewer widget.
    return const SyncfusionPDFViewer(base64: _base64);
  }
}

class SyncfusionPDFViewer extends StatefulWidget {
  const SyncfusionPDFViewer({super.key, required this.base64});

  /// Base64 string of the PDF document.
  final String base64;

  @override
  State<SyncfusionPDFViewer> createState() => _SyncfusionPDFViewerState();
}

class _SyncfusionPDFViewerState extends State<SyncfusionPDFViewer> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SfPdfViewer(
        source: Base64PDFSource(widget.base64),
      ),
    );
  }
}

/// Custom PDFSource implementation for loading PDF from base64 encoded string.
class Base64PDFSource extends PDFSource {
  /// Creates a new instance of Base64PDFSource with the provided base64 string.
  Base64PDFSource(this._base64);

  /// The base64 encoded string of the PDF document.
  final String _base64;

  /// Cached PDF bytes to avoid repeated decoding.
  Uint8List? _pdfBytes;

  @override
  Future<Uint8List> getBytes(BuildContext context) async {
    // Decode the base64 string to bytes if not already cached
    return _pdfBytes ??= base64Decode(_base64);
  }
}


{% endhighlight %}
{% endtabs %}