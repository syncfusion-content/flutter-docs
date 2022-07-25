---
layout: post
title: Getting started with Flutter PDF Viewer widget | Syncfusion
description: Learn here about getting started with Syncfusion Flutter PDF Viewer (SfPdfViewer) widget, its elements, and more.
platform: Flutter
control: SfPdfViewer
documentation: ug
---

# Getting started with Flutter PDF Viewer (SfPdfViewer)
This section explains the steps required to add the [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) widget and its features. This section covers only the basic features needed to get started with the Syncfusion Flutter PDF Viewer plugin.

## Add the Flutter PDF Viewer to an application
Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://flutter.dev/docs/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion Flutter PDF Viewer dependency to your pubspec.yaml file.

{% highlight dart %}

dependencies:

syncfusion_flutter_pdfviewer: ^xx.x.xx

{% endhighlight %}

N> Here **xx.x.xx** denotes the current version of the [`Syncfusion Flutter PDF Viewer`](https://pub.dev/packages/syncfusion_flutter_pdfviewer/versions) package.

For the web platform, we have used [PdfJs](https://cdnjs.cloudflare.com/ajax/libs/pdf.js/2.4.456/pdf.min.js) for rendering the PDF pages, so the script file must be referred to in your `web/index.html` file.

On your `web/index.html` file, add the following `script` tags, somewhere in the `head` or `body` of the document:

```html

<script src="//cdnjs.cloudflare.com/ajax/libs/pdf.js/2.4.456/pdf.min.js"></script>
<script type="text/javascript">
   pdfjsLib.GlobalWorkerOptions.workerSrc = "//cdnjs.cloudflare.com/ajax/libs/pdf.js/2.4.456/pdf.worker.min.js";
</script>

```

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

### Load document from the Asset

The [SfPdfViewer.asset](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/SfPdfViewer.asset.html) creates a widget that displays the PDF document obtained from an [`AssetBundle`](https://api.flutter.dev/flutter/services/AssetBundle-class.html). The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="4 5" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.asset(
              'assets/flutter-succinctly.pdf'));
}

{% endhighlight %}
{% endtabs %}

### Load document from the Network

The [SfPdfViewer.network](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/SfPdfViewer.network.html) creates a widget that displays the PDF document obtained from a URL. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="4 5" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf'));
}

{% endhighlight %}
{% endtabs %}

To load PDF from network using [SfPdfViewer.network](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/SfPdfViewer.network.html) in macOS, network access must be enabled in your macOS application. On your `macos/Runner/DebugProfile.entitlements` file, add the following lines inside the `<dict>`
tag to enable the network access in your application:

```html
<key>com.apple.security.network.client</key>
<true/>
```

N> Due to CORS security restriction in web application, some PDF obtained from URL is not loaded in the SfPdfViewer web platform. Kindly refer the following flutter forum,
https://github.com/flutter/flutter/issues/51125

The issue can be resolved by configure the CORS settings in the requested server or by disabling the security settings in chrome. dart as mentioned below steps:

1. Go to flutter\bin\cache and remove a file named: flutter_tools.stamp
2. Go to flutter\packages\flutter_tools\lib\src\web and open the file chrome.dart.
3. Find '--disable-extensions'.
4. Add '--disable-web-security'.

### Load document from the File

The [SfPdfViewer.file](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/SfPdfViewer.file.html) creates a widget that displays the PDF document obtained from a [`File`](https://api.flutter.dev/flutter/dart-io/File-class.html). The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="4 5" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.file(
              File('storage/emulated/0/Download/flutter-succinctly.pdf')));
}

{% endhighlight %}
{% endtabs %}

N> On Android, this may require the `android.permission.READ_EXTERNAL_STORAGE`.

### Load document from the Memory

The [SfPdfViewer.memory](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/SfPdfViewer.memory.html) creates a widget that displays the PDF document obtained from the [`Uint8List`](https://api.flutter.dev/flutter/dart-typed_data/Uint8List-class.html). The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="4 5" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.memory(
              bytes));
}

{% endhighlight %}
{% endtabs %}

## Load document with the specified scroll offset position or zoom level 

The `SfPdfViewer` allows you to load the document with the specified scroll offset position or zoom level using the [initialScrollOffset](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/initialScrollOffset.html) and [initialZoomLevel](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/initialZoomLevel.html) properties. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="6 7" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
              initialScrollOffset: Offset(0, 500),
              initialZoomLevel: 1.5));
}

{% endhighlight %}
{% endtabs %}

## Get the current scroll offset position

The `SfPdfViewer` allows you to get the current scroll offset position using the [scrollOffset](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/scrollOffset.html) property. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="16 17" %}

final PdfViewerController _pdfViewerController=PdfViewerController();

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: Text('Syncfusion Flutter PDF Viewer'),
      actions: <Widget>[
        IconButton(
          icon: Icon(
            Icons.arrow_drop_down_circle,
            color: Colors.white,
          ),
          onPressed: () {
            _pdfViewerController.jumpToPage(3);
            print( _pdfViewerController.scrollOffset.dy);
            print( _pdfViewerController.scrollOffset.dx);
          },
        ),
      ],
    ),
    body: SfPdfViewer.network(
      'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
      controller: _pdfViewerController,
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Customize the space being displayed between the PDF pages 

By default, the `SfPdfViewer` displays the spacing between the PDF pages with the value of **4 pixels**. You can customize the space being displayed using the [pageSpacing](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/pageSpacing.html) property. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="6" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
              pageSpacing: 2));
}

{% endhighlight %}
{% endtabs %}

## Customize the visibility of scroll head and scroll status

By default, the `SfPdfViewer` displays the scroll head and scroll status. You can customize the visibility of these items using the [canShowScrollHead](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/canShowScrollHead.html) and [canShowScrollStatus](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/canShowScrollStatus.html) properties. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="6 7" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
              canShowScrollHead: false,
              canShowScrollStatus: false));
}

{% endhighlight %}
{% endtabs %}

N> On a desktop or mobile web browser, this `canShowScrollHead` property will have no effect since the scroll head will not be displayed there.

## Customize the visibility of page navigation dialog

By default, the page navigation dialog will be displayed when the scroll head is tapped. You can customize the visibility of the page navigation dialog using the [canShowPaginationDialog](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/canShowPaginationDialog.html) property. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="6" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf', 
              canShowPaginationDialog: false));
}

{% endhighlight %}
{% endtabs %}

N> On a desktop or mobile web browser, this `canShowPaginationDialog` property will have no effect since the pagination dialog will not be displayed there.

## Callbacks

The `SfPdfViewer` loading supports the [PdfDocumentLoadedCallback](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfDocumentLoadedCallback.html) and [PdfDocumentLoadFailedCallback](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfDocumentLoadFailedCallback.html) to notify whether the document has been loaded completely or not.

### Document loaded callback

The [onDocumentLoaded](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onDocumentLoaded.html) callback triggers after the `document` are loaded in the `SfPdfViewer`. The document in the [PdfDocumentLoadedDetails](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfDocumentLoadedDetails-class.html) will return the loaded [PdfDocument](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocument-class.html) instance. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="6 7 8" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
    'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
    onDocumentLoaded: (PdfDocumentLoadedDetails details) {
      print(details.document.pages.count);
    },
  ));
}

{% endhighlight %}
{% endtabs %}

### Document load failed callback

The [onDocumentLoadFailed](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onDocumentLoadFailed.html) callback triggers when the document loading fails in the `SfPdfViewer`. That is,

* When any corrupted document is loaded.
* When any password-protected document is loaded with invalid or empty password.
* When any improper input source value like the wrong URL or file path is given.
* When any non-PDF document is loaded.

The [PdfDocumentLoadFailedDetails](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfDocumentLoadFailedDetails-class.html) will return the `error` title and `description` message for the failure reason. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="6 7 8 9 10 11 12 13 14 15 16 17 18 19" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
    'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
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
  ));
}

{% endhighlight %}
{% endtabs %}

N> You can refer to our [Flutter PDF Viewer](https://www.syncfusion.com/flutter-widgets/flutter-pdf-viewer) feature tour page for its groundbreaking feature representations. You can also explore our [Flutter PDF Viewer example](https://flutter.syncfusion.com/#/pdf-viewer/getting-started) that shows you how to render and configure the PDF Viewer.