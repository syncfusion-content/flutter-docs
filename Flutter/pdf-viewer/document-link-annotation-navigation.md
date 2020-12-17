---
layout: post
title: Document link annotation in Syncfusion Flutter PDF Viewer | Syncfusion
description: This section explains about how to navigate to the desired topic in a PDF document by tapping the document link annotation in the table of contents.
platform: Flutter
control: SfPdfViewer
documentation: ug
---

# Document link annotation in Flutter PDF Viewer (SfPdfViewer)

By default, the [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) allows you to navigate to the desired topic or position by tapping its document link annotation in the table of contents in a PDF document.

## Enable or disable the document link annotation navigation

You can enable or disable the navigation of document link annotation using the [enableDocumentLinkAnnotation](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/enableDocumentLinkAnnotation.html) property. The following code example explains the same.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Container(
          child: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
              enableDocumentLinkAnnotation: false)));
}

{% endhighlight %}
{% endtabs %}