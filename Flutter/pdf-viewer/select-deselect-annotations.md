---
layout: post
title: Select and Deselect Annotations in Flutter PDF Viewer | Syncfusion
description: Learn here all about select and deselect annotations in PDF documents using the Syncfusion® Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Select and Deselect Annotations in Flutter PDF Viewer Widget (SfPdfViewer)

This section will go through the various functions available in the `SfPdfViewer` for selecting and deselecting annotations in a PDF document.

## Select an Annotation

You can select an annotation by simply tapping on the annotation using touch or mouse. When the annotation is selected, the selection border (selector) appears, indicating that the annotation is selected. 

### Select an Annotation Programmatically

You can select an annotation programmatically by providing the annotation instance as the parameter to the [selectAnnotation](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/selectAnnotation.html) method of the [PdfViewerController](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController-class.html). The annotation instance can be found using the [getAnnotations](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/getAnnotations.html) method of the [PdfViewerController](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController-class.html). The following example explains how to select the first annotation in the annotation collection.

{% tabs %}
{% highlight dart hl_lines="8" %}

void selectFirstAnnotation() {
  // Get the list of annotations in the PDF document.
  List<Annotation> annotations = _pdfViewerController.getAnnotations();
  if (annotations.isNotEmpty) {
    // Get the first annotation from the PDF document.
    Annotation firstAnnotation = annotations.first;
    // Select the first annotation in the PDF document.
    _pdfViewerController.selectAnnotation(firstAnnotation);
  }
}

{% endhighlight %}
{% endtabs %}

### Annotation Selected Callback

The callback provided to the [onAnnotationSelected](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onAnnotationSelected.html) property is triggered when an annotation is selected interactively or programmatically. The selected annotation instance can be obtained from the callback details. The following code sample explains how to use this callback.

{% tabs %}
{% highlight dart hl_lines="7 8 9 10" %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: SfPdfViewer.network(
        'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
        onAnnotationSelected: (Annotation annotation) {
          // Instance of the selected annotation.
          Annotation selectedAnnotation = annotation;
        },
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

### Customizing Selector Appearance

The [selector](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfAnnotationSettings/selector.html) property of the [annotationSettings](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/annotationSettings.html) property of `PdfViewerController` allows you to customize the default selector color.

* [color](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfAnnotationSelectorSettings/color.html) - Specifies the selector color when the selected annotation is not locked.
* [lockedColor](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfAnnotationSelectorSettings/lockedColor.html) - Specifies the selector color when the selected annotation is locked.

The following example explains how to customize the selector color for locked and unlocked annotations.

{% tabs %}
{% highlight dart %}

void customizeSelectorAppearance() {
  PdfAnnotationSettings annotationSettings =
      _pdfViewerController.annotationSettings;
  // For unlocked annotations.
  annotationSettings.selector.color = Colors.blue;
  // For locked annotations.
  annotationSettings.selector.lockedColor = Colors.grey;
}

{% endhighlight %}
{% endtabs %}

## Deselect an Annotation

You can deselect an annotation by tapping outside its bounds using touch or mouse. When the annotation is deselected, the selection border (selector) disappears, indicating that the annotation is deselected.
* In desktop platforms like Windows, macOS, Linux, and desktop web, you can also use the keyboard shortcut Esc to deselect an annotation.

### Deselect an Annotation Programmatically

You can deselect the annotation programmatically by providing the selected annotation instance as the parameter to the [deselectAnnotation](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/deselectAnnotation.html) method. The selected annotation instance can be obtained from the [onAnnotationSelected](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onAnnotationSelected.html) callback. The following example shows how to deselect the selected annotation.

{% tabs %}
{% highlight dart hl_lines="3" %}

void deselectAnnotation(Annotation selectedAnnotation) {
  // Deselect the selected annotation.
  _pdfViewerController.deselectAnnotation(selectedAnnotation);
}

{% endhighlight %}
{% endtabs %}

### Annotation Deselected Callback

The callback provided to the [onAnnotationDeselected](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onAnnotationDeselected.html) property is triggered when an annotation is deselected interactively or programmatically. The following code sample explains how to use this callback.

{% tabs %}
{% highlight dart hl_lines="7 8 9 10" %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: SfPdfViewer.network(
        'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
        onAnnotationDeselected: (Annotation annotation) {
          // Instance of the deselected annotation.
          Annotation deselectedAnnotation = annotation;
        },
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}