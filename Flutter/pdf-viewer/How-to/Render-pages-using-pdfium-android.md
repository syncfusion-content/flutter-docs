---
layout: post
title: Rendering PDF pages using PDFium on Android| Syncfusion
description: You can learn all about rendering PDF pages using the PDFium library on Android devices running API levels below 35 with the SfPdfViewer widget.
platform: flutter
control: SfPdfViewer
documentation: ug
keywords: flutter pdf viewer, flutter view pdf, pdf viewer in flutter, flutter open pdf, flutter pdf view
---

# How to render PDF pages using PDFium on Android?

The Syncfusion<sup>&reg;</sup> Flutter PDF Viewer allows users to render PDF pages using the PDFium library on Android devices running API levels below 35 through an optional package, [syncfusion_pdfviewer_android](https://pub.dev/packages/syncfusion_pdfviewer_android).

This optional package significantly enhances the loading performance of large password-protected PDF files on Android devices running API levels below 35, with performance improvements of up to approximately 13 times faster.

To render PDF pages using PDFium on Android devices running API levels below 35, add the `syncfusion_pdfviewer_android` dependency in the `pubspec.yaml` file.

{% highlight dart %}

dependencies:

syncfusion_flutter_pdfviewer: ^xx.x.xx 
syncfusion_pdfviewer_android: ^xx.x.xx

{% endhighlight %}

N> Here, **xx.x.xx** denotes the current version of the [Syncfusion<sup>&reg;</sup> Flutter PDF Viewer](https://pub.dev/packages/syncfusion_flutter_pdfviewer/versions) package. Please ensure that the `syncfusion_pdfviewer_android` package uses the same version as `syncfusion_flutter_pdfviewer`.

N> The `syncfusion_pdfviewer_android` package is supported from version 29.2.10 onwards.

N> `PdfRenderer` will be used to render PDF pages on Android devices running API level 35 and above, even if the `syncfusion_pdfviewer_android` dependency is included.
