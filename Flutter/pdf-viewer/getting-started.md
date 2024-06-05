---
layout: post
title: Getting started with Flutter PDF Viewer widget | Syncfusion
description: Learn here about getting started with Syncfusion Flutter PDF Viewer (SfPdfViewer) widget, its elements, and more.
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Getting started with Flutter PDF Viewer (SfPdfViewer)
This section explains the steps required to add the [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) widget and its features. This section covers only the basic features needed to get started with the Syncfusion Flutter PDF Viewer plugin.

## Add the Flutter PDF Viewer to an application
Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://docs.flutter.dev/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion Flutter PDF Viewer dependency to your pubspec.yaml file.

{% highlight dart %}

dependencies:

syncfusion_flutter_pdfviewer: ^xx.x.xx

{% endhighlight %}

N> Here **xx.x.xx** denotes the current version of the [`Syncfusion Flutter PDF Viewer`](https://pub.dev/packages/syncfusion_flutter_pdfviewer/versions) package.

For the web platform, we have used [PdfJs](https://cdnjs.cloudflare.com/ajax/libs/pdf.js/2.11.338/pdf.min.js) for rendering the PDF pages, so the script file must be referred to in your `web/index.html` file.

On your `web/index.html` file, add the following `script` tags, somewhere in the `head` or `body` of the document:

```html

<script src="//cdnjs.cloudflare.com/ajax/libs/pdf.js/2.11.338/pdf.min.js"></script>
<script type="text/javascript">
   pdfjsLib.GlobalWorkerOptions.workerSrc = "//cdnjs.cloudflare.com/ajax/libs/pdf.js/2.11.338/pdf.worker.min.js";
</script>

```

N> Version **2.11.338** is recommended for using annotation support. This will not flatten the unsupported annotations while rendering the pages.

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

**Load Document**

Once the package has been imported, initialize the `SfPdfViewer` as a child of any widget. In the following shown example, the `SfPdfViewer` widget is added as a child of the container widget.

The [SfPdfViewer.asset](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/SfPdfViewer.asset.html) creates a widget that displays the PDF document obtained from an [`AssetBundle`](https://api.flutter.dev/flutter/services/AssetBundle-class.html). The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="43 44" %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_pdfviewer/pdfviewer.dart';

void main() {
  runApp(MaterialApp(
    title: 'Syncfusion PDF Viewer Demo',
    home: HomePage(),
  ));
}

/// Represents Homepage for Navigation
class HomePage extends StatefulWidget {
  @override
  _HomePage createState() => _HomePage();
}

class _HomePage extends State<HomePage> {
  final GlobalKey<SfPdfViewerState> _pdfViewerKey = GlobalKey();

  @override
  void initState() {
    super.initState();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Syncfusion Flutter PDF Viewer'),
        actions: <Widget>[
          IconButton(
            icon: const Icon(
              Icons.bookmark,
              color: Colors.white,
              semanticLabel: 'Bookmark',
            ),
            onPressed: () {
              _pdfViewerKey.currentState?.openBookmarkView();
            },
          ),
        ],
      ),
      body: SfPdfViewer.asset(
        'flutter-succinctly.pdf',
        key: _pdfViewerKey,
      ),
    );
  }
}

{% endhighlight %}
{% endtabs %}

N> You can refer to our [Flutter PDF Viewer](https://www.syncfusion.com/flutter-widgets/flutter-pdf-viewer) feature tour page for its groundbreaking feature representations. You can also explore our [Flutter PDF Viewer example](https://flutter.syncfusion.com/#/pdf-viewer/getting-started) that shows you how to render and configure the PDF Viewer.