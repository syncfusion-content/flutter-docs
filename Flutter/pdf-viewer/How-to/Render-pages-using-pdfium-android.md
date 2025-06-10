---
layout: post
title: Rendering PDF pages using PDFium on Android| Syncfusion
description: You can learn here all about rendering the PDF pages using PDFium on Android
platform: flutter
control: SfPdfViewer
documentation: ug
keywords: flutter pdf viewer, flutter view pdf, pdf viewer in flutter, flutter open pdf, flutter pdf view
---

# How to render PDF pages using PDFium on Android?

The Syncfusion Flutter PDF Viewer allows users to render PDF pages using the PDFium library on Android. This enables rendering PDF pages with better performance on Android devices running API levels below 35. By default, the PDF Viewer uses the [PdfRenderer](https://developer.android.com/reference/android/graphics/pdf/PdfRenderer) to render PDF pages on the Android platform.

However, the `PdfRenderer` does not support loading password-protected documents on Android devices running API levels below 35. To load password-protected documents on Android, we decrypt the PDF document using the `syncfusion_flutter_pdf` library and employ the decrypted bytes to load the PDF document.

To improve the performance of loading password-protected PDF documents on API levels below 35, we can use the PDFium library to load and render the PDF documents.

To render PDF pages using PDFium on Android devices running API levels below 35, add the syncfusion_pdfviewer_android dependency in the `pubspec.yaml` file.

{% highlight dart %}

dependencies:

syncfusion_flutter_pdfviewer: ^xx.x.xx 
syncfusion_pdfviewer_android: ^xx.x.xx

{% endhighlight %}

N> Here **xx.x.xx** denotes the current version of the [Syncfusion<sup>&reg;</sup> Flutter PDF Viewer](https://pub.dev/packages/syncfusion_flutter_pdfviewer/versions) package. Please use the same version as the `syncfusion_flutter_pdfviewer` package.

N> PdfRenderer will be used for rendering PDF pages on Android devices running API levels 35 and above, even if the `syncfusion_pdfviewer_android` dependency is added.
