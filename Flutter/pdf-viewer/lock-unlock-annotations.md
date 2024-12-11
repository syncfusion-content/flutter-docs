---
layout: post
title: Locking and Unlocking Annotations in Flutter PDF Viewer Widget | Syncfusion
description: Learn here all about locking and unlocking annotations in PDF documents using the Syncfusion<sup>&reg;</sup> Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Lock and Unlock Annotations in Flutter PDF Viewer widget (Syncfusion<sup>&reg;</sup>)

You can lock an annotation to prevent it from being edited. The annotation that has been locked cannot be removed or edited further until it is unlocked. This section will go through the process of locking and unlocking annotations in a PDF document.

## Lock all annotations in a document

To lock all annotations in a document, set the `isLocked` property of the `annotationSettings` to true. The following example explains how to lock all annotations in a document.

{% tabs %}
{% highlight dart hl_lines="3" %}

void lockAllAnnotations() {
  // Lock all the annotations in the PDF document.
  _pdfViewerController.annotationSettings.isLocked = true;
}

{% endhighlight %}
{% endtabs %}

* Similarly, to unlock all the annotations, set the `isLocked` property value to false.

## Lock a specific annotation

To lock a specific annotation in a document, access the annotation instance and set the `isLocked` property of the annotation to true. The following example explains how to lock the first annotation in a PDF document.

{% tabs %}
{% highlight dart hl_lines="8" %}

void lockFirstAnnotation() {
  // Get the list of annotations in the PDF document.
  List<Annotation> annotations = _pdfViewerController.getAnnotations();
  if (annotations.isNotEmpty) {
    // Get the first annotation from the PDF document.
    Annotation firstAnnotation = annotations.first;
    // Lock the first annotation in the PDF document.
    firstAnnotation.isLocked = true;
  }
}

{% endhighlight %}
{% endtabs %}

* Similarly, to unlock the annotation, set the `isLocked` property value to false.

## Lock specific annotation types

You can also use the `annotationSettings` property to lock a specific annotation type in a document. The following example explains how to lock all the underline annotations in a document by accessing the underline annotation settings. Similarly, you can lock other types of annotation.

{% tabs %}
{% highlight dart %}

void lockUnderlineAnnotations() {
  // Get the underline annotation settings.
  PdfTextMarkupAnnotationSettings underlineAnnotationSettings =
      _pdfViewerController.annotationSettings.underline;
  // Lock all the underline annotations in the PDF document.
  underlineAnnotationSettings.isLocked = true;
}

{% endhighlight %}
{% endtabs %}

* Similarly, to unlock the specific annotation types, set the `isLocked` property value to false.

## Lock the selected annotation

To lock the selected annotation, access the selected annotation instance and set the `isLocked` property to true. The selected annotation instance may be obtained from the `onAnnotationSelected` callback. The following example explains locking the selected annotation in a PDF document.

{% tabs %}
{% highlight dart %}

void lockSelectedAnnotation(Annotation selectedAnnotation) {
  // Lock the selected annotation.
  selectedAnnotation.isLocked = true;
}

{% endhighlight %}
{% endtabs %}

* Similarly, to unlock the selected annotation, set the `isLocked` property value to false.
