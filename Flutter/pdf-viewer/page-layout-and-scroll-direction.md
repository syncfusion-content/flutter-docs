---
layout: post
title: Page layout and Scrolling options in Flutter PDF Viewer | Syncfusion
description: Learn here all about page layout and scrolling options feature of Syncfusion® Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Page Layout and Scrolling Options in Flutter PDF Viewer (SfPdfViewer)

Page layout modes describe how the PDF page is displayed, and scrolling options describe the direction in which the PDF pages can be scrolled in [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html).

## Page Layout Modes

The [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) supports the following page layout modes:

* Continuous page layout mode
* Single page layout mode

### Continuous Page Layout Mode

By default, the `continuous` page layout mode is enabled, which scrolls the PDF pages vertically and horizontally. To enable the `continuous` page layout mode in `SfPdfViewer`, use the following code sample.

{% tabs %}
{% highlight dart hl_lines="6" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
              pageLayoutMode: PdfPageLayoutMode.continuous));
}

{% endhighlight %}
{% endtabs %}

### Single Page Layout Mode

In `Single` page layout mode, PDFs will be displayed page by page horizontally. To enable the `Single` page layout mode in `SfPdfViewer`, use the following code sample.

{% tabs %}
{% highlight dart hl_lines="6" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
              pageLayoutMode: PdfPageLayoutMode.single));
}

{% endhighlight %}
{% endtabs %}

![Single page layout mode in Flutter PDF Viewer.](images/page-layout-and-scroll-direction/flutter-pdf-viewer-page-by-page.gif)

## Scrolling Options

The [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) supports the following scrolling options:

* Vertical scrolling
* Horizontal scrolling

If the scroll direction is not specified, continuous page layout mode defaults to vertical scrolling, and single page layout mode defaults to horizontal scrolling.

### Vertical Scrolling

By default, `Vertical` scrolling is enabled, which moves the PDF pages from up to down. To enable the `Vertical` scrolling in `SfPdfViewer`, use the following code sample.

{% tabs %}
{% highlight dart hl_lines="6" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
              scrollDirection: PdfScrollDirection.vertical));
}

{% endhighlight %}
{% endtabs %}

### Horizontal Scrolling

In `Horizontal` scrolling, PDF pages can be scrolled from left to right. To enable the `Horizontal` scrolling in `SfPdfViewer`, use the following code sample.

{% tabs %}
{% highlight dart hl_lines="6" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
              scrollDirection: PdfScrollDirection.horizontal));
}

{% endhighlight %}
{% endtabs %}

![Horizontal scrolling in Flutter PDF Viewer.](images/page-layout-and-scroll-direction/flutter-pdf-viewer-horizontal-scrolling.gif)