---
layout: post
title: Export in Flutter Radial Gauge widget | Syncfusion
description: Learn here all about Export feature of Syncfusion Flutter Radial Gauge (SfRadialGauge) widget and more.
platform: Flutter
control: SfRadialGauge
documentation: ug
---

# Export in Flutter Radial Gauge (SfRadialGauge)

[`SfRadialGauge`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfRadialGauge-class.html) provides support to export the Radial Gauge as a PNG image or as PDF document.

## Export image

To export the Radial Gauge as a PNG image, we can get the image by calling [`toImage`](https://api.flutter.dev/flutter/rendering/RenderRepaintBoundary/toImage.html) method in repaint boundary.

{% highlight dart %} 

GlobalKey _globalKey = GlobalKey();

 @override
 Widget build(BuildContext context) {
    return Scaffold(
      body: Column(
        children: [
          Container(
            height: 400,
            width: 400,
            child: RepaintBoundary(
              key: _globalKey,
              child: SfRadialGauge(
                axes: <RadialAxis>[
                  RadialAxis(
                    minimum: 0,
                    maximum: 150,
                    ranges: <GaugeRange>[
                      GaugeRange(
                          startValue: 0,
                          endValue: 50,
                          color: Colors.green,
                          startWidth: 10,
                          endWidth: 10),
                      GaugeRange(
                          startValue: 50,
                          endValue: 100,
                          color: Colors.orange,
                          startWidth: 10,
                          endWidth: 10),
                      GaugeRange(
                          startValue: 100,
                          endValue: 150,
                          color: Colors.red,
                          startWidth: 10,
                          endWidth: 10)
                    ],
                    pointers: <GaugePointer>[NeedlePointer(value: 90)],
                  )
                ],
              ),
            ),
          ),
          Padding(
            padding: const EdgeInsets.only(top: 5.0),
            child: ElevatedButton(
              onPressed: _renderGaugeImage,
              child: Text('Gauge to image'),
            ),
          ),
        ],
      ),
    );
 }

 Future<void> _renderGaugeImage() async {
    final RenderRepaintBoundary boundary =
        _globalKey.currentContext?.findRenderObject() as RenderRepaintBoundary;
    final ui.Image data = await boundary.toImage(pixelRatio: 3.0);
    final bytes = await data.toByteData(format: ui.ImageByteFormat.png);
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

![image_export](images\export-radial-gauge\export-gauge-image.png)

## Export PDF

Similar to the above way, we can also export the rendered chart as a PDF document. We create the pdf document using pdf component. This can be done in the application level itself and please find the code snippet below. Add the below four packages in your pubspec file and import the respective libraries in your main.dart file.

* syncfusion_flutter_pdf
* syncfusion_flutter_gauges
* path_provider
* open_file

{% highlight dart %}

GlobalKey _globalKey = GlobalKey();

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(title: Text('RenderGaugePdf')),
    body: Column(
        children: [
          Container(
            height: 400,
            width: 400,
            child: RepaintBoundary(
              key: _globalKey,
              child: SfRadialGauge(
                axes: <RadialAxis>[
                  RadialAxis(
                    minimum: 0,
                    maximum: 150,
                    ranges: <GaugeRange>[
                      GaugeRange(
                          startValue: 0,
                          endValue: 50,
                          color: Colors.green,
                          startWidth: 10,
                          endWidth: 10),
                      GaugeRange(
                          startValue: 50,
                          endValue: 100,
                          color: Colors.orange,
                          startWidth: 10,
                          endWidth: 10),
                      GaugeRange(
                          startValue: 100,
                          endValue: 150,
                          color: Colors.red,
                          startWidth: 10,
                          endWidth: 10)
                    ],
                    pointers: <GaugePointer>[NeedlePointer(value: 90)],
                  )
                ],
              ),
            ),
          ),
          Padding(
            padding: const EdgeInsets.only(top: 5.0),
            child: ElevatedButton(
              onPressed: _renderGaugePDF,
              child: Text('Gauges to pdf'),
            ),
          ),
        ],
      ),
    );
  }

  Future<void> _renderGaugePDF() async {
    var document = PdfDocument();
    PdfPage page = document.pages.add();
    final RenderRepaintBoundary boundary =
        _globalKey.currentContext?.findRenderObject() as RenderRepaintBoundary;
    final ui.Image data = await boundary.toImage(pixelRatio: 3.0);
    final bytes = await data.toByteData(format: ui.ImageByteFormat.png);
    final Uint8List imageBytes =
        bytes!.buffer.asUint8List(bytes.offsetInBytes, bytes.lengthInBytes);
    page.graphics
        .drawImage(PdfBitmap(imageBytes), Rect.fromLTWH(25, 50, 300, 300));
    var byteData = document.save();
    document.dispose();
    Directory? directory = await getExternalStorageDirectory();
    String path = directory!.path;
    File file = File('$path/Output.pdf');
    await file.writeAsBytes(byteData, flush: true);
    OpenFile.open('$path/Output.pdf');
  }

 {% endhighlight %}
  
 ![pdf_export](images\export-radial-gauge\export-radial-gauge.png)