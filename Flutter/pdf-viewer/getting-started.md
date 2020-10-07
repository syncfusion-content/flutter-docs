---
layout: post
title: Getting started for Syncfusion Flutter PDF Viewer | Syncfusion
description: This section explains about the steps required to add the PDF Viewer widget and its elements such as scroll head, scroll status and page navigation dialog.
platform: Flutter
control: SfPdfViewer
documentation: ug
---

# Getting Started with Flutter PDF Viewer (SfPdfViewer)
This section explains the steps required to add the [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) widget and its features. This section covers only the basic features needed to get started with the Syncfusion Flutter PDF Viewer widget.

## Add the Flutter PDF Viewer to an application
Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://flutter.dev/docs/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion Flutter PDF Viewer dependency to your pubspec.yaml file.

{% highlight dart %}

dependencies:

syncfusion_flutter_pdfviewer: ^xx.x.xx

{% endhighlight %}

N> Here **xx.x.xx** denotes the current version of [`Syncfusion Flutter PDF Viewer`](https://pub.dev/packages/syncfusion_flutter_pdfviewer/versions) package.

**Get packages** 

Run the following command to get the required packages.

{% highlight dart %}

$ flutter pub get

{% endhighlight %}

**Import package**

Import the following package in your Dart code.

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_pdfviewer/pdfviewer.dart';

{% endhighlight %}
{% endtabs %}

## Initialize the PDF Viewer

Once the package has been imported, initialize the `SfPdfViewer` as a child of any widget. In the following shown examples, the `SfPdfViewer` widget is added as a child of the container widget. Several constructors are provided for the various ways that a PDF document can be loaded. They are,

* Asset
* Network
* File
* Memory

N> Currently, we do not support viewing the password-protected PDF document.

### Load document from the Asset

The [SfPdfViewer.asset](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/SfPdfViewer.asset.html) creates a widget that displays the PDF document obtained from an [`AssetBundle`](https://api.flutter.dev/flutter/services/AssetBundle-class.html). The following code example explains the same.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Container(
          child: SfPdfViewer.asset(
              'assets/flutter-succinctly.pdf')));
}

{% endhighlight %}
{% endtabs %}

### Load document from the Network

The [SfPdfViewer.network](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/SfPdfViewer.network.html) creates a widget that displays the PDF document obtained from a URL. The following code example explains the same.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Container(
          child: SfPdfViewer.network(
              'http://ebooks.syncfusion.com/downloads/flutter-succinctly/flutter-succinctly.pdf')));
}

{% endhighlight %}
{% endtabs %}

### Load document from the File

The [SfPdfViewer.file](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/SfPdfViewer.file.html) creates a widget that displays the PDF document obtained from a [`File`](https://api.flutter.dev/flutter/dart-io/File-class.html). The following code example explains the same.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Container(
          child: SfPdfViewer.file(
              File('storage/emulated/0/Download/flutter-succinctly.pdf'))));
}

{% endhighlight %}
{% endtabs %}

N> On Android, this may require the `android.permission.READ_EXTERNAL_STORAGE`.

### Load document from the Memory

The [SfPdfViewer.memory](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/SfPdfViewer.memory.html) creates a widget that displays the PDF document obtained from the [`Uint8List`](https://api.flutter.dev/flutter/dart-typed_data/Uint8List-class.html). The following code example explains the same.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Container(
          child: SfPdfViewer.memory(
              bytes)));
}

{% endhighlight %}
{% endtabs %}

## Customize the visibility of scroll head and scroll status

By default, the `SfPdfViewer` displays the scroll head and scroll status. You can customize the visibility of these items using the [canShowScrollHead](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/canShowScrollHead.html) and [canShowScrollStatus](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/canShowScrollStatus.html) properties. The following code example explains the same.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Container(
          child: SfPdfViewer.network(
              'http://ebooks.syncfusion.com/downloads/flutter-succinctly/flutter-succinctly.pdf',
              canShowScrollHead: false,
              canShowScrollStatus: false)));
}

{% endhighlight %}
{% endtabs %}

## Customize the visibility of page navigation dialog

By default, the page navigation dialog will be displayed when the scroll head is tapped. You can customize the visibility of the page navigation dialog using the [canShowPaginationDialog](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/canShowPaginationDialog.html) property. The following code example explains the same.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Container(
          child: SfPdfViewer.network(
              'http://ebooks.syncfusion.com/downloads/flutter-succinctly/flutter-succinctly.pdf', 
              canShowPaginationDialog: false)));
}

{% endhighlight %}
{% endtabs %}

## Callbacks

The `SfPdfViewer` loading supports the [PdfDocumentLoadedCallback](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfDocumentLoadedCallback.html) and [PdfDocumentLoadFailedCallback](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfDocumentLoadFailedCallback.html) to notify whether the document has been loaded completely or not.

### Document loaded callback

The [onDocumentLoaded](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onDocumentLoaded.html) callback triggers after the `document` are loaded in the `SfPdfViewer`. The document in the [PdfDocumentLoadedDetails](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfDocumentLoadedDetails-class.html) will return the loaded [PdfDocument](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocument-class.html) instance. The following code example explains the same.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Container(
          child: SfPdfViewer.network(
    'http://ebooks.syncfusion.com/downloads/flutter-succinctly/flutter-succinctly.pdf',
    onDocumentLoaded: (PdfDocumentLoadedDetails details) {
      print(details.document.pages.count);
    },
  )));
}

{% endhighlight %}
{% endtabs %}

### Document load failed callback

The [onDocumentLoadFailed](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onDocumentLoadFailed.html) callback triggers when the document loading fails in the `SfPdfViewer`. That is,

* When any corrupted document is loaded.
* When any password-protected document is loaded.
* When any improper input source value like the wrong URL or file path is given.
* When any non-PDF document is loaded.

The [PdfDocumentLoadFailedDetails](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfDocumentLoadFailedDetails-class.html) will return the `error` title and `description` message for the failure reason. The following code example explains the same.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Container(
          child: SfPdfViewer.network(
    'http://ebooks.syncfusion.com/downloads/flutter-succinctly/flutter-succintly.pdf',
    onDocumentLoadFailed: (PdfDocumentLoadFailedDetails details) {
      AlertDialog(
        title: Text(details.error),
        content: Text(details.description),
        actions: <Widget>[
          FlatButton(
            child: Text('OK'),
            onPressed: () {
              Navigator.of(context).pop();
            },
          ),
        ],
      );
    },
  )));
}

{% endhighlight %}
{% endtabs %}