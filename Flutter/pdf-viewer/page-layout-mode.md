---
layout: post
title: PageLayout modes in Flutter PDF Viewer widget | Syncfusion
description: Learn here all about PageLayout modes feature of Syncfusion Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: Flutter
control: SfPdfViewer
documentation: ug
---

# Page Layout modes in Flutter PDF Viewer (SfPdfViewer)

The [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) supports the following PageLayout modes for the transition of pages.

* continuous
* single

## Continuous page mode

By default, the `continuous` pagelayoutmode will be enabled and it allows to scroll the page continuously. Refer to the following code to enable the `continuous` pagelayoutmode in `SfPdfViewer`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Container(
          child: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf', 
              pageLayoutMode: PdfPageLayoutMode.continuous)));
}

{% endhighlight %}
{% endtabs %}

## Single page mode

In `single` pagelayoutmode,user can scroll the pages from one page to another page. Refer to the following code to enable the `single` pagelayoutmode in `SfPdfViewer`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Container(
          child: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf', 
             pageLayoutMode: PdfPageLayoutMode.single)));
}

{% endhighlight %}
{% endtabs %}