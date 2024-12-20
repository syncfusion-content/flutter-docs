---
layout: post
title: Hyperlink navigation in Flutter PDF Viewer widget | Syncfusion
description: Learn here all about the hyperlink navigation feature of Syncfusion Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Hyperlink navigation in Flutter PDF Viewer (SfPdfViewer)

The [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) allows you to open URLs or website links in the default browser. You can hide the built-in hyperlink navigation dialog or add a customized one with supported functionalities.

![Hyperlink navigation dialog](images/hyperlink-navigation/hyperlink_navigation_dialog.jpg)

## Enable or disable the hyperlink navigation

You can enable or disable the hyperlink navigation using the [enableHyperlinkNavigation](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/enableHyperlinkNavigation.html) property. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="9" %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Syncfusion Flutter PDF Viewer'),
      ),
      body: SfPdfViewer.network(
        'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
        enableHyperlinkNavigation: false,
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Customize the visibility of the hyperlink navigation dialog

By default, the built-in hyperlink navigation dialog will be displayed when any hyperlink is clicked. You can customize the visibility of the hyperlink navigation dialog using the [canShowHyperlinkDialog](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/canShowHyperlinkDialog.html) property. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="9" %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Syncfusion Flutter PDF Viewer'),
      ),
      body: SfPdfViewer.network(
        'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
        canShowHyperlinkDialog: false,
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Callbacks

The [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) hyperlink navigation supports the [PdfHyperlinkClickedCallback](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfHyperlinkClickedCallback.html) to notify when any hyperlink is clicked.

### Hyperlink clicked callback

The [onHyperlinkClicked](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onHyperlinkClicked.html) callback triggers when any hyperlink in the PDF document is clicked. The [PdfHyperlinkClickedDetails](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfHyperlinkClickedDetails-class.html) will return the [uri](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfHyperlinkClickedDetails/uri.html) clicked in the PDF document. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="9 10 11" %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Syncfusion Flutter PDF Viewer'),
      ),
      body: SfPdfViewer.network(
        'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
        onHyperlinkClicked: (PdfHyperlinkClickedDetails details) {
          print(details.uri);
        },
      ),
    );
  }

{% endhighlight %}
{% endtabs %}