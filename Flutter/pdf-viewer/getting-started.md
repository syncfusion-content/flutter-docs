---
layout: post
title: Getting started with Flutter PDF Viewer widget | Syncfusion
description: Learn here about getting started with Syncfusion® Flutter PDF Viewer (SfPdfViewer) widget, its features, and more.
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Getting started with Flutter PDF Viewer (SfPdfViewer)
This section explains the steps to add the [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) widget to your Flutter application and load a PDF document.

To get started quickly, you can also check out our video tutorial below. 

<style>#FlutterSfPdfViewerGettingStartedTutorial{width : 90% !important; height: 400px !important }</style> <iframe id='FlutterSfPdfViewerGettingStartedTutorial' src="https://www.youtube.com/embed/f1zEJZRdo7w?si=KaBtOjAEbrrRBw5y"></iframe>

## Add the Flutter PDF Viewer to an application
Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://docs.flutter.dev/get-started/test-drive#choose-your-ide) documentation.

**Add dependency**

Add the Syncfusion<sup>&reg;</sup> Flutter PDF Viewer dependency to your pubspec.yaml file.

{% highlight dart %}

dependencies:

syncfusion_flutter_pdfviewer: ^xx.x.xx

{% endhighlight %}

N> Here **xx.x.xx** denotes the current version of the [Syncfusion<sup>&reg;</sup> Flutter PDF Viewer](https://pub.dev/packages/syncfusion_flutter_pdfviewer/versions) package.

For the web platform, we have used [PdfJs](https://cdnjs.cloudflare.com/ajax/libs/pdf.js/2.11.338/pdf.min.js) for rendering the PDF pages, so the script file must be referred to in your `web/index.html` file.

On your `web/index.html` file, add the following `script` tags, somewhere in the `head` or `body` of the document:

For PdfJs library version 4.0 and above
```html
<script type="module" async>
  import * as pdfjsLib from 'https://cdnjs.cloudflare.com/ajax/libs/pdf.js/4.10.38/pdf.min.mjs';
  pdfjsLib.GlobalWorkerOptions.workerSrc = "https://cdnjs.cloudflare.com/ajax/libs/pdf.js/4.10.38/pdf.worker.min.mjs";
</script>
```

For PdfJs library versions below 4.0
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/2.11.338/pdf.min.js"></script>
<script type="text/javascript">
  pdfjsLib.GlobalWorkerOptions.workerSrc = "https://cdnjs.cloudflare.com/ajax/libs/pdf.js/2.11.338/pdf.worker.min.js";
</script>
```

N> Version above **2.11.338** is recommended for using annotation support. This will not flatten the unsupported annotations while rendering the pages.

**Get packages** 

Run the following command to get the required packages.

{% highlight dart %}

$ flutter pub get

{% endhighlight %}

**Import package**

Import the following package in your Dart code.

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_pdfviewer/pdfviewer.dart';

{% endhighlight %}
{% endtabs %}

**Initialize the PDF Viewer**

Once the package has been imported, add the `SfPdfViewer` widget as a child of any widget. In the following shown examples, the `SfPdfViewer` widget is added as a child of the Scaffold widget.

**Load document**

To display a PDF document in the PDF Viewer, add the PDF document to the application assets and use [SfPdfViewer.asset](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/SfPdfViewer.asset.html) to load it from the [AssetBundle](https://api.flutter.dev/flutter/services/AssetBundle-class.html). The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="4 5" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.asset(
              'assets/flutter-succinctly.pdf'));
}

{% endhighlight %}
{% endtabs %}

N> You can refer to our [Flutter PDF Viewer](https://www.syncfusion.com/flutter-widgets/flutter-pdf-viewer) feature tour page for its groundbreaking feature representations. You can also explore our [Flutter PDF Viewer example](https://flutter.syncfusion.com/#/pdf-viewer/getting-started) that shows you how to render and configure the PDF Viewer.