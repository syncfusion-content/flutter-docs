---
layout: post
title: Load document by Page Number, Scroll Offset, or Zoom Level in Flutter PDF Viewer | Syncfusion
description: Learn here all about loading document by Page Number, Scroll Offset, or Zoom Level feature of Syncfusion Flutter PDF Viewer (SfPdfViewer) widget.
platform: Flutter
control: SfPdfViewer
documentation: ug
---

# Load document by Page Number, Scroll Offset, or Zoom Level in Flutter PDF Viewer (SfPdfViewer)

## Load the document with the specified page

The `SfPdfViewer` allows you to load the document with the specified page using the [initialPageNumber](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/initialPageNumber.html) property. The following code example explains the same.

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

N> It is recommended not to use both the [initialScrollOffset](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/initialScrollOffset.html) and [initialPageNumber](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/initialPageNumber.html) properties at the same time. If both properties are defined, the [initialPageNumber](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/initialPageNumber.html) will be prioritized over the [initialScrollOffset](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/initialScrollOffset.html)

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
