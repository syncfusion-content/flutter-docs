---
layout: post
title: Open a Document From Memory in Flutter PDF Viewer widget (SfPdfViewer) | Syncfusion
description: Learn here about opening a PDF document from memory in Syncfusion Flutter PDF Viewer widget (SfPdfViewer).
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Open a Document From Memory in Flutter PDF Viewer (SfPdfViewer)
The [SfPdfViewer.memory](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/SfPdfViewer.memory.html) creates a widget that displays the PDF document obtained from the [`Uint8List`](https://api.flutter.dev/flutter/dart-typed_data/Uint8List-class.html). The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="4 5" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.memory(
              bytes));
}

{% endhighlight %}
{% endtabs %}