---
layout: post
title: Open a Document in Flutter PDF Viewer | Syncfusion
description: Learn here all about opening a PDF document in Syncfusion® Flutter PDF Viewer (SfPdfViewer) and more.
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Open a Document in Flutter PDF Viewer (SfPdfViewer)

The [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) widget allows you to open PDF documents from various sources, like local storage, memory, or URLs using respective constructors. It also lets you view password-protected documents.

This section walks you through the loading of documents in `SfPdfViewer` and handling the load-specific events.

## Supported Constructor Types

The `SfPdfViewer` supports the following constructor types:
1. Asset
2. Network
3. Memory
4. File

## Load the Document with the Specified Page

The `SfPdfViewer` allows you to load the document with the specified page using the `initialPageNumber` property. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="6" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
              initialPageNumber: 5));
}

{% endhighlight %}
{% endtabs %}

N> It is recommended not to use both the [initialScrollOffset](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/initialScrollOffset.html) and [initialPageNumber](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/initialPageNumber.html) properties at the same time. If both properties are defined, the [initialPageNumber](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/initialPageNumber.html) will be prioritized over the [initialScrollOffset](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/initialScrollOffset.html).

## Load Document with the Specified Scroll Offset Position or Zoom Level 

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