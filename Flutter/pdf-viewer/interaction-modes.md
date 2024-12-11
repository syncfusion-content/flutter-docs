---
layout: post
title: Interaction modes in Flutter PDF Viewer widget | Syncfusion<sup>&reg;</sup>
description: Learn here all about interaction modes feature of Syncfusion<sup>&reg;</sup> Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Interaction modes in Flutter PDF Viewer (SfPdfViewer)

The [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) supports the following interaction modes for easy interaction with the PDF documents on a desktop web browser,

* selection
* pan

N> On a touch device, setting the [interactionMode](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/interactionMode.html) property to the `selection` mode will have no effect since panning is the default mode for scrolling and the selection is made by long-pressing a word in the document.

## Selection mode

By default, the `selection` interaction mode will be enabled on a desktop web browser and allows users to select and copy text from the PDF files. This also helps to copy and share the text content. Refer to the following code to enable the `selection` mode in `SfPdfViewer`.

{% tabs %}
{% highlight dart hl_lines="6" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf', 
              interactionMode: PdfInteractionMode.selection));
}

{% endhighlight %}
{% endtabs %}

## Pan mode

In `pan` mode, the dragging and scrolling of the pages can be performed in any direction using the mouse and touch interactions on a desktop web browser, but the text selection cannot be performed. Refer to the following code to enable the `pan` mode in `SfPdfViewer`.

{% tabs %}
{% highlight dart hl_lines="6" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf', 
              interactionMode: PdfInteractionMode.pan));
}

{% endhighlight %}
{% endtabs %}