---
layout: post
title: Hyperlink navigation in Flutter PDF Viewer widget | Syncfusion
description: Learn here all about the Hyperlink navigation feature of Syncfusion Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: Flutter
control: SfPdfViewer
documentation: ug
---

# Hyperlink navigation in Flutter PDF Viewer (SfPdfViewer)

The SfPdfViewer supports the hyperlink navigation that enables the hyperlinks in the PDF document and tapping on the hyperlink it will open in the browser.

![Hyperlink navigation dialog](images/hyperlink-navigation/hyperlink_navigation_dialog.jpg)

## Enable or disable the hyperlink navigation

You can enable or disable the navigation of hyperlinks using the enableHyperlinkNavigation property. The following code example explains the same.

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

## Customize the visibility of hyperlink navigation dialog

By default, the hyperlink navigation dialog will be displayed when the hyperlink is clicked. You can customize the visibility of the hyperlink navigation dialog using the canShowHyperlinkDialog property. The following code example explains the same.

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

The `SfPdfViewer` hyperlink navigation supports the PdfHyperlinkClickedCallback, which holds the information of `uri`clicked in the PDF document.

### Hyperlink clicked callback

The onHyperlinkClicked callback triggers when a hyperlink in the `SfPdfViewer` is tapped. The PdfHyperlinkClickedDetails will return the `uri` clicked in the PDF document. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="9 10" %}

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