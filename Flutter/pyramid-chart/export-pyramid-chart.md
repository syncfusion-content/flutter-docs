---
layout: post
title: Exporting Syncfusion Pyramid Chart types
description: Learn how to be exporting image or PDF document in Pyramid Charts
platform: flutter
control: Chart
documentation: ug
---

# Export Image or PDF for chart
To export the pyramid chart as a PNG image or as PDF document.

## Export image
To export the pyramid chart as a PNG image, we can get the image by calling [`toImage`]() method in repaint boundary.

{% highlight dart %} 

    Future<void> _renderPyramidImage() async {
      dart_ui.Image data =
          await _pyramidChartKey.currentState.toImage(pixelRatio: 3.0);
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
                    child: Image.memory(bytes.buffer.asUint8List()),
                  ),
                ),
              );
            },
          ),
        );
      }
     }

  {% endhighlight %}

### Export PDF

{% highlight dart %} 

    Future<void> _renderPyramidPDF() async {
    var document = PdfDocument();
    PdfPage page = document.pages.add();
    dart_ui.Image data =
        await _pyramidChartKey.currentState.toImage(pixelRatio: 3.0);
    final bytes = await data.toByteData(format: dart_ui.ImageByteFormat.png);
    final Uint8List imageBytes =
        bytes.buffer.asUint8List(bytes.offsetInBytes, bytes.lengthInBytes);
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
    }
  {% endhighlight %}

![image_export](images/export-pyramid-chart/pdf_view.png)
