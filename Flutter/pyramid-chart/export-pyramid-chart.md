---
layout: post
title: Exporting in Flutter Pyramid Chart widget | Syncfusion 
description: Learn here all about Exporting feature of Syncfusion Flutter Pyramid Chart (SfPyramidChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Exporting in Flutter Pyramid Chart (SfPyramidChart)

[`SfPyramidChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfPyramidChart-class.html) provides support to export the pyramid chart as a PNG image or as PDF document.

## Export image

To export the pyramid chart as a PNG image, we can get the image by calling [`toImage`](https://api.flutter.dev/flutter/rendering/RenderRepaintBoundary/toImage.html) method in repaint boundary.

{% tabs %}
{% highlight Dart %} 

    Future<void> _renderPyramidImage() async {
      dart_ui.Image data =
          await _pyramidChartKey.currentState!.toImage(pixelRatio: 3.0);
      final bytes = await data.toByteData(format: dart_ui.ImageByteFormat.png);
      if (data != null) {
        await Navigator.of(context).push(
          MaterialPageRoute(
            builder: (BuildContext context) {
              return Scaffold(
                appBar: AppBar(),
                body: Center(
                  child: Container(
                    color: Colors.white,
                    child: Image.memory(bytes!.buffer.asUint8List()),
                  ),
                ),
              );
            },
          ),
        );
      }
     }

  {% endhighlight %}
{% endtabs %}

### Export PDF

Similar to the above way, we can also export the rendered chart as a PDF document. We create the pdf document using pdf component. This can be done in the application level itself and please find the code snippet below.

{% tabs %}
{% highlight Dart %} 

    Future<void> _renderPyramidPDF() async {
      var document = PdfDocument();
      PdfPage page = document.pages.add();
      dart_ui.Image data =
          await _pyramidChartKey.currentState!.toImage(pixelRatio: 3.0);
      final bytes = await data.toByteData(format: dart_ui.ImageByteFormat.png);
      final Uint8List imageBytes =
          bytes!.buffer.asUint8List(bytes.offsetInBytes, bytes.lengthInBytes);
      page.graphics
          .drawImage(PdfBitmap(imageBytes), Rect.fromLTWH(25, 50, 300, 300));
      var byteData = document.save();
      document.dispose();
      Directory directory = await getExternalStorageDirectory();
      String path = directory.path;
      File file = File('$path/Output.pdf');
      await file.writeAsBytes(byteData, flush: true);
      OpenFile.open('$path/Output.pdf');
    }
  
{% endhighlight %}
{% endtabs %}

![pdf_export](images/export-pyramid-chart/pdf_view.png)
