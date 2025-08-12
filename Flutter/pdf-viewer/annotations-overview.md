---
layout: post
title: Annotations in Flutter PDF Viewer widget | Syncfusion
description: Learn here all about annotations feature of the Syncfusion® Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Annotations in Flutter PDF Viewer (SfPdfViewer)

The `SfPdfViewer` allows you to add, remove, and modify annotations in PDF documents. This section will go through the various types and functionalities available in the PDF Viewer for working with annotations.

## Supported Annotation Types

The `SfPdfViewer` supports the following annotation types:
1. Highlight
2. Squiggly
3. Strikethrough
4. Underline
5. Sticky Note

## Setting the Default Author for Annotations

You can define a default author name for all annotations added to the PDF document using the [author](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfAnnotationSettings/author.html) property of the [PdfViewerController.annotationSettings](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/annotationSettings.html). This helps identify who created the annotations, especially in collaborative or review workflows.

The following code explains how to set a default author name for the annotations.

{% tabs %}
{% highlight dart %}

void setDefaultAuthor() {
  // Set the default author name for all annotations added after this setting is applie
  _pdfViewerController.annotationSettings.author = 'John Doe';
}

{% endhighlight %}
{% endtabs %}

## Setting the Author and Subject for Individual Annotations

In addition to setting a default author for all annotations, you can assign a specific [author](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/Annotation/author.html) and [subject](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/Annotation/subject.html) to each annotation individually using an [Annotation](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/Annotation-class.html) instance.

The following code explains how to set the author name and subject for individual annotation.

{% tabs %}
{% highlight dart %}

/// Sets the author and subject for the last annotation in the PDF document.
void setMetadataForLastAnnotation() {
  // Get the list of annotations in the PDF document.
  List<Annotation> annotations = _pdfViewerController.getAnnotations();

  if (annotations.isNotEmpty) {
    // Get the last annotation from the list.
    Annotation lastAnnotation = annotations.last;

    // Set the author and subject for the last annotation.
    lastAnnotation.author = 'John Doe';
    lastAnnotation.subject = 'Reviewed';
  }
}

{% endhighlight %}
{% endtabs %}
