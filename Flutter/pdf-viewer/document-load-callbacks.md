---
layout: post
title: Document Load Callbacks in Flutter PDF Viewer widget | Syncfusion
description: Learn here all about the document load callbacks in Syncfusion® Flutter PDF Viewer (SfPdfViewer) widget
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Document Load Callbacks in Flutter PDF Viewer (SfPdfViewer)

The [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) widget supports the [onDocumentLoaded](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onDocumentLoaded.html) and [onDocumentLoadFailed](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onDocumentLoadFailed.html) callbacks to notify whether the document has been loaded completely or not.

## Document Loaded Callback

The [onDocumentLoaded](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onDocumentLoaded.html) callback triggers after the `document` is loaded in the `SfPdfViewer`. The document in the [PdfDocumentLoadedDetails](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfDocumentLoadedDetails-class.html) will return the loaded [PdfDocument](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocument-class.html) instance. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="6 7 8" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
    'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
    onDocumentLoaded: (PdfDocumentLoadedDetails details) {
      print(details.document.pages.count);
    },
  ));
}

{% endhighlight %}
{% endtabs %}

## Document Load Failed Callback

The [onDocumentLoadFailed](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onDocumentLoadFailed.html) callback triggers when the document loading fails in the `SfPdfViewer`. That is,

* When any corrupted document is loaded.
* When any password-protected document is loaded with an invalid or empty password.
* When any improper input source value like a wrong URL or file path is given.
* When any non-PDF document is loaded.

The [PdfDocumentLoadFailedDetails](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfDocumentLoadFailedDetails-class.html) will return the `error` title and `description` message for the failure reason. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="26 27 28" %}

 /// Displays the error message.
  void showErrorDialog(BuildContext context, String error, String description) {
    showDialog<dynamic>(
        context: context,
        builder: (BuildContext context) {
          return AlertDialog(
            title: Text(error),
            content: Text(description),
            actions: <Widget>[
              TextButton(
                child: const Text('OK'),
                onPressed: () {
                  Navigator.of(context).pop();
                },
              ),
            ],
          );
        });
 }

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
    'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
    onDocumentLoadFailed: (PdfDocumentLoadFailedDetails details) {
        showErrorDialog(context, details.error, details.description);
    },
  ));
}

{% endhighlight %}
{% endtabs %}
