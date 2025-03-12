---
layout: post
title: UI Customization in Flutter PDF Viewer widget | Syncfusion
description: Learn here all about the UI customization options in Syncfusion® Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: flutter
control: SfPdfViewer
documentation: ug
---

# UI Customization in Flutter PDF Viewer (SfPdfViewer)

This section walks you through the UI customization options supported in the [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) widget.

## Customize the space being displayed between the PDF pages 

By default, the `SfPdfViewer` displays the spacing between the PDF pages with the value of **4 pixels**. You can customize the space being displayed using the [pageSpacing](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/pageSpacing.html) property. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="6" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
              pageSpacing: 2));
}

{% endhighlight %}
{% endtabs %}

## Customize the visibility of scroll head and scroll status

By default, the `SfPdfViewer` displays the scroll head and scroll status. You can customize the visibility of these items using the [canShowScrollHead](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/canShowScrollHead.html) and [canShowScrollStatus](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/canShowScrollStatus.html) properties. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="6 7" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
              canShowScrollHead: false,
              canShowScrollStatus: false));
}

{% endhighlight %}
{% endtabs %}

N> On a desktop or mobile web browser, this `canShowScrollHead` property will have no effect since the scroll head will not be displayed there.

## Customize the visibility of page navigation dialog

By default, the page navigation dialog will be displayed when the scroll head is tapped. You can customize the visibility of the page navigation dialog using the [canShowPaginationDialog](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/canShowPaginationDialog.html) property. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="6" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf', 
              canShowPaginationDialog: false));
}

{% endhighlight %}
{% endtabs %}

N> On a desktop or mobile web browser, this `canShowPaginationDialog` property will have no effect since the pagination dialog will not be displayed there.

## Customize the visibility of page loading busy indicator 

By default, the `SfPdfViewer` displays the page loading busy indicator. You can customize the visibility of this using the [canShowPageLoadingIndicator](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/canShowPageLoadingIndicator.html) property. The following code example explains the same. 

{% tabs %}
{% highlight dart hl_lines="6" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf', 
              canShowPageLoadingIndicator: false));
}

{% endhighlight %}
{% endtabs %}