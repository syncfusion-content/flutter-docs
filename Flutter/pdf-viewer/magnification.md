---
layout: post
title: Magnification in Flutter PDF Viewer widget | Syncfusion
description: Learn here all about magnification feature of Syncfusion Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: Flutter
control: SfPdfViewer
documentation: ug
---

# Magnification in Flutter PDF Viewer (SfPdfViewer)

The content of a document can be zoomed in and out either by pinch to zoom or changing the zoom level factor programmatically.

## Change the zoom level factor programmatically

You can change or control the zoom level factor programmatically using the [zoomLevel](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/zoomLevel.html) property. The zoom level factor value can be set between 1.0 and 3.0. The default value is 1.0. The following code example explains the same.

{% tabs %}
{% highlight Dart %}

late PdfViewerController _pdfViewerController;

@override
void initState() {
  _pdfViewerController = PdfViewerController();
  super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: Text('Syncfusion Flutter PdfViewer'),
      actions: <Widget>[
        IconButton(
          icon: Icon(
            Icons.zoom_in,
            color: Colors.white,
          ),
          onPressed: () {
            _pdfViewerController.zoomLevel = 2;
          },
        ),
      ],
    ),
    body: SfPdfViewer.network(
      'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
      controller: _pdfViewerController,
    ),
  );
}

{% endhighlight %}
{% endtabs %}

N> The maximum allowed zoom level is 3.0 and if any value is set beyond that, then it will be restricted to 3.0.

## Enable or disable the double-tap zoom.

By default, the `SfPdfViewer` will be zoomed in and out when double-tapped. You can enable or disable the double-tap zoom using the [enableDoubleTapZooming](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/enableDoubleTapZooming.html) property. The following code example explains the same.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf', 
              enableDoubleTapZooming: false));
}

{% endhighlight %}
{% endtabs %}

N> On a desktop web browser, this `enableDoubleTapZooming` property will have no effect on mouse interaction.

## Callbacks

The `SfPdfViewer` magnification supports the [PdfZoomLevelChangedCallback](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfZoomLevelChangedCallback.html) to notify the zoom level changes.

### Zoom level changed callback

The [onZoomLevelChanged](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onZoomLevelChanged.html) callback triggers when the zoom level is changed in the `SfPdfViewer`. That is,

•	When the pinch zoom is performed.
•	When the double-tap zoom is performed.
•	When the `zoomLevel` property is changed.

The [PdfZoomDetails](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfZoomDetails-class.html) will return the `oldZoomLevel` title and `newZoomLevel` values. The following code example explains the same.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
    'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
    onZoomLevelChanged: (PdfZoomDetails details) {
      print(details.newZoomLevel);
    },
  ));
}

{% endhighlight %}
{% endtabs %}