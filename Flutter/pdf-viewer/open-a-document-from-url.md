---
layout: post
title: Open a Document From URL in Flutter PDF Viewer widget (SfPdfViewer) | Syncfusion
description: Learn here about opening a PDF document from URL in Syncfusion Flutter PDF Viewer widget (SfPdfViewer).
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Open a Document From URL in Flutter PDF Viewer (SfPdfViewer)
The [SfPdfViewer.network](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/SfPdfViewer.network.html) creates a widget that displays the PDF document obtained from a URL. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="4 5" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf'));
}

{% endhighlight %}
{% endtabs %}

To load PDF from network using [SfPdfViewer.network](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/SfPdfViewer.network.html) in mac OS, network access must be enabled in your mac OS application. On your `macos/Runner/DebugProfile.entitlements` file, add the following lines inside the `<dict>`
tag to enable the network access in your application:

```html
<key>com.apple.security.network.client</key>
<true/>
```

N> Due to CORS security restrictions in a web application, some PDFs obtained from URLs might not be loaded in the `SfPdfViewer` web platform. Kindly refer to the flutter [forum](https://github.com/flutter/flutter/issues/51125) reported on the same.

This issue can be resolved by configuring the CORS settings in the requested server or by disabling the security settings in **chrome.dart** as mentioned in the below steps:

1. Go to **flutter\bin\cache** and remove a file named: **flutter_tools.stamp**
2. Go to **flutter\packages\flutter_tools\lib\src\web** and open the file **chrome.dart**.
3. Find **'--disable-extensions'**.
4. Add **'--disable-web-security'**.