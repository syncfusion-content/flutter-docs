---
layout: post
title: Gesture callback in Flutter PDF Viewer widget | Syncfusion
description: Learn here about gesture callbacks provided by Syncfusion Flutter PDF Viewer (SfPdfViewer) widget.
platform: Flutter
control: SfPdfViewer
documentation: ug
---

# Gesture callback

The [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) supports the `PdfGestureCallback`, to notify the touch or mouse interaction with the widget.

## Tap callback

The `onTap` callback triggers when the user taps on the `SfPdfViewer` widget and the `PdfGestureDetails` returns the following information,

* `pageNumber` – This property returns the page number on which the tap took place. The value ranges from 1 to the total number of pages in the PDF document. If the tap occurs outside of any PDF page boundaries, the result will be -1.

* `pagePositon` – The property returns the page’s tapped position in the PDF coordinates. The coordinates have their origin at the top-left of the page. The number of the tapped page is identified by the PageNumber property. If the tap occurs outside of any PDF page boundaries, the result will be (-1, -1).

* `position` – This property returns the tapped position on the PDF Viewer widget. The coordinate space starts at the top left of the widget.

The following code example illustrates how to use onTap callback. 

{% tabs %}
{% highlight dart hl_lines="9 10" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: Text('Syncfusion Flutter PDF Viewer'),
    ),
    body: SfPdfViewer.network(
      '<https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf>',
      onTap: (PdfGestureDetails details) {
        // Handle the Tap callback here.
      },
    ),
  );
}

{% endhighlight %}
{% endtabs %}
