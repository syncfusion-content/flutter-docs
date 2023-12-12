---
layout: post
title: Annotation Collection in Flutter PDF Viewer widget | Syncfusion
description: Learn here all about annotation collection in the Syncfusion Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: Flutter
control: SfPdfViewer
documentation: ug
---

# Annotation Collection in Flutter PDF Viewer widget (Syncfusion)

The annotations in the PDF document can be accessed by the `getAnnotations` method of the `PdfViewerController`. The return value of the function will have Annotation collection as soon as the document is loaded in the PDF viewer. The following code example shows how the annotation collection can be accessed.

{% tabs %}
{% highlight dart hl_lines="7 8" %}

final PdfViewerController _pdfViewerController = PdfViewerController();

@override
Widget build(BuildContext context) {
  return SfPdfViewer.asset(
    'assets/annotations.pdf',
    controller: _pdfViewerController,
    onDocumentLoaded: (PdfDocumentLoadedDetails details) {
      final List<Annotation> annotations =
          _pdfViewerController.getAnnotations();
      if (annotations.isNotEmpty) {
        // Gets the first annotation from the collection.
        final Annotation annotation = annotations.first;
        if (annotation is HighlightAnnotation) {
          final Color color = annotation.color;
          final double opacity = annotation.opacity;
        }
      }
    },
  );
}

{% endhighlight %}
{% endtabs %}