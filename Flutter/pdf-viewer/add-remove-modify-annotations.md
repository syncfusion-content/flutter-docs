---
layout: post
title: Add, Remove, and Edit Annotations in Flutter PDF Viewer | Syncfusion
description: Learn here all about adding, removing, and editing annotations in a PDF document using the Syncfusion<sup>&reg;</sup> Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Add, Remove, Edit Annotations in Flutter PDF Viewer (Syncfusion<sup>&reg;</sup>)

This section will go through the various functions available in the `SfPdfViewer` for adding, removing, and editing annotations in a PDF document.

## Add annotations to a PDF document

This section will go through how to add annotations to a PDF document programmatically.

### Add annotations programmatically

You can programmatically add a new annotation to the PDF document by creating an annotation instance and providing it as a parameter to the [addAnnotation](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/addAnnotation.html) method of the `PdfViewerController` class. The following example shows how to create an instance of a highlight annotation and add it to the PDF document. Similarly, you can create and add other types of annotation.

{% tabs %}
{% highlight dart hl_lines="11" %}

void addHighlightAnnotation() {
  // Get the selected text lines.
  List<PdfTextLine>? textLines =
      _pdfViewerKey.currentState?.getSelectedTextLines();
  if (textLines != null && textLines.isNotEmpty) {
    // Create the highlight annotation.
    final HighlightAnnotation highlightAnnotation = HighlightAnnotation(
      textBoundsCollection: textLines,
    );
    // Add the annotation to the PDF document.
    _pdfViewerController.addAnnotation(highlightAnnotation);
  }
}

{% endhighlight %}
{% endtabs %}

### Annotation added callback

The callback provided to the [onAnnotationAdded](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onAnnotationAdded.html) property is triggered when an annotation is successfully added to the PDF document. The following example shows how to use this callback.

{% tabs %}
{% highlight dart hl_lines="7 8 9" %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: SfPdfViewer.network(
        'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
        onAnnotationAdded: (Annotation annotation) {
          print('${annotation.runtimeType} is added successfully');
        },
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Remove annotations from the PDF document

This section will go through different methods of removing annotations from a PDF document.

### Remove a specific annotation programmatically

You can programmatically remove an annotation from the document by providing the specific annotation instance as the parameter to the [removeAnnotation](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/removeAnnotation.html) method of `PdfViewerController`. The following example shows how to remove the first annotation in the annotation collection from a PDF document.

{% tabs %}
{% highlight dart hl_lines="8" %}

void removeFirstAnnotation() {
  // Get the list of annotations in the PDF document.
  List<Annotation> annotations = _pdfViewerController.getAnnotations();
  if (annotations.isNotEmpty) {
    // Get the first annotation from the PDF document.
    Annotation firstAnnotation = annotations.first;
    // Remove the first annotation from the PDF document.
    _pdfViewerController.removeAnnotation(firstAnnotation);
  }
}

{% endhighlight %}
{% endtabs %}

### Remove all the annotations

You can programmatically remove all the annotations from a document by calling the [removeAllAnnotations](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/removeAllAnnotations.html) method. The optional `pageNumber` parameter can be used to clear the form field data on a specific page. By default, the pageNumber parameter is 0. Refer to the following code example. 

{% tabs %}
{% highlight dart hl_lines="3 8" %}

void removeAllAnnotations() {
  // Remove all the annotations from the PDF document.
  _pdfViewerController.removeAllAnnotations();
}

void removeAllAnnotationsInFirstPage() {
  // Remove all the annotations in the first page of the PDF document.
  _pdfViewerController.removeAllAnnotations(pageNumber: 1);
}

{% endhighlight %}
{% endtabs %}

### Annotation removed callback

The callback provided to the [onAnnotationRemoved](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onAnnotationRemoved.html) property is triggered when an annotation is removed successfully from the PDF document. The following example shows how to use this callback.

{% tabs %}
{% highlight dart hl_lines="7 8 9" %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: SfPdfViewer.network(
        'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
        onAnnotationRemoved: (Annotation annotation) {
          print('${annotation.runtimeType} is removed successfully');
        },
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Edit annotations

This section will go through different methods of editing annotations in a PDF document programmatically.

### Edit a specific annotation

You can edit the properties of an annotation from the document programmatically by accessing the specific annotation instance from the Annotation collection. The following example shows how to edit the first annotation in the annotation collection. Similarly, you can modify the other properties also.

{% tabs %}
{% highlight dart hl_lines="9 10" %}

void editAnnotation() {
  // Get the list of annotations in the PDF document.
  List<Annotation> annotations = _pdfViewerController.getAnnotations();

  if (annotations.isNotEmpty) {
    // Get the first annotation from the PDF document.
    Annotation firstAnnotation = annotations.first;
    // Edit the first annotation in the PDF document.
    firstAnnotation.color = Colors.red; // Change the color of the annotation.
    firstAnnotation.opacity = 0.5; // Change the opacity of the annotation.
  }
}

{% endhighlight %}
{% endtabs %}

### Annotation edited callback

The callback provided to the [onAnnotationEdited](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onAnnotationEdited.html) property is triggered when an annotation is edited in the PDF document. The following code sample explains how to use this callback.

{% tabs %}
{% highlight dart hl_lines="7 8 9 10" %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: SfPdfViewer.network(
        'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
        onAnnotationEdited: (Annotation annotation) {
          // Instance of the edited annotation.
          Annotation editedAnnotation = annotation;
        },
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}
