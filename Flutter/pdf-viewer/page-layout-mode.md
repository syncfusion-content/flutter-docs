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

By default, the `continuous` page layout mode will be enabled and the user can scroll the page vertical and horizontal direction. Refer to the following code to enable the `continuous` page layout mode in `SfPdfViewer`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Container(
          child: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
              scrollDirection: PdfScrollDirection.horizontal,  
              pageLayoutMode: PdfPageLayoutMode.continuous)));
}

{% endhighlight %}
{% endtabs %}

## Single page mode

In `single` page layout mode,user can scroll the pages from one page to another page. Refer to the following code to enable the `single` page layout mode in `SfPdfViewer`.

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

N> On single page mode,only horizontal scrolling is supported.
