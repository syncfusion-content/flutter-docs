---
layout: post
title: Scrolling in Flutter PDF Viewer widget | Syncfusion
description: Learn here about scrolling functionality in Syncfusion® Flutter PDF Viewer (SfPdfViewer) widget including programmatically setting scroll positions.
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Scrolling in Flutter PDF Viewer (SfPdfViewer)

The Syncfusion<sup>&reg;</sup> [Flutter PDF Viewer](https://www.syncfusion.com/flutter-widgets/flutter-pdf-viewer) widget has scrolling capabilities that allow users to navigate through content seamlessly. This section will walk you through various aspects of scrolling, including programmatically setting scroll positions.

W> Please note that since the PDF Viewer has built-in scrolling capability, it is advised to avoid placing the PDF Viewer inside other controls that also offer scrolling, such as ScrollView. Nesting within such controls may cause unexpected issues.

## Navigate to the desired offset programmatically

The [jumpTo](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/jumpTo.html) controller method moves the scroll position of the `SfPdfViewer` to the specified horizontal and vertical offset. If the specified offset value is wrong, then the scroll will not happen, and the older position will be retained. 

N> Both the `xOffset` and `yOffset` are optional parameters and if the offset values are not provided, then the `SfPdfViewer` will be scrolled or moved to the default position (0, 0).

{% tabs %}
{% highlight dart hl_lines="21" %}

late PdfViewerController _pdfViewerController;

@override
void initState() {
  _pdfViewerController = PdfViewerController();
  super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: Text('Flutter PDF Viewer'),
      actions: <Widget>[
        IconButton(
          icon: Icon(
            Icons.arrow_drop_down_circle,
            color: Colors.white,
          ),
          onPressed: () {
            _pdfViewerController.jumpTo(yOffset:1500);
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


## Get the current scroll offset position

The `SfPdfViewer` allows you to get the current scroll offset position using the [scrollOffset](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/scrollOffset.html) property. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="16 17" %}

final PdfViewerController _pdfViewerController=PdfViewerController();

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: Text('Flutter PDF Viewer'),
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
