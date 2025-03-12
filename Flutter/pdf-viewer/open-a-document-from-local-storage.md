---
layout: post
title: Open a PDF From Local Storage in Flutter PDF Viewer widget (SfPdfViewer) | Syncfusion
description: Learn here about opening a PDF document from local storage in Syncfusion Flutter PDF Viewer widget (SfPdfViewer).
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Open a PDF From Local Storage in Flutter PDF Viewer (SfPdfViewer)

The [SfPdfViewer.file](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/SfPdfViewer.file.html) creates a widget that displays the PDF document obtained from a [`File`](https://api.flutter.dev/flutter/dart-io/File-class.html). The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="4 5" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.file(
              File('storage/emulated/0/Download/flutter-succinctly.pdf')));
}

{% endhighlight %}
{% endtabs %}

N> On Android, this may require the `android.permission.READ_EXTERNAL_STORAGE`.

N> Since the file system is not accessible from the browser, [SfPdfViewer.file](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/SfPdfViewer.file.html) is not supported on Flutter Web.