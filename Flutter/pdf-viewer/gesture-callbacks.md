---
layout: post
title: Gesture callbacks in Flutter PDF Viewer widget | Syncfusion
description: Learn here about the gesture callbacks provided in Syncfusion® Flutter PDF Viewer (SfPdfViewer) widget.
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Gesture callbacks in Flutter PDF Viewer (SfPdfViewer)

The [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) supports the [PdfGestureCallback](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfGestureTapCallback.html), to notify the touch or mouse interaction with the widget.

## Tap callback

The [onTap](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onTap.html) callback triggers when the user taps on the `SfPdfViewer` widget and the [PdfGestureDetails](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfGestureDetails-class.html) returns the following information,

* [pageNumber](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfGestureDetails/pageNumber.html) – This property returns the page number on which the tap took place. The value ranges from 1 to the total number of pages in the PDF document. If the tap occurs outside any PDF page boundaries, the result will be -1.

* [pagePosition](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfGestureDetails/pagePosition.html) – The property returns the page’s tapped position in the PDF coordinates. The coordinates have their origin at the top-left of the page. The number of the tapped page is identified by the PageNumber property. If the tap occurs outside any PDF page boundaries, the result will be (-1, -1).

* [position](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfGestureDetails/position.html) – This property returns the tapped position on the PDF Viewer widget. The coordinate space starts at the top left of the widget.

The following code example illustrates how to retrieve information from the `PdfGestureDetails` and handle the `onTap` callback. 

{% tabs %}
{% highlight dart hl_lines="9 10 11" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: Text('Syncfusion Flutter PDF Viewer'),
    ),
    body: SfPdfViewer.network(
      'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
      onTap: (PdfGestureDetails details) {
        print('${details.pageNumber}');
      },
    ),
  );
}

{% endhighlight %}
{% endtabs %}
