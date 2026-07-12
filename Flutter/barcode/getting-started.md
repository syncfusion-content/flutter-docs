---
layout: post
title: 	Getting started with Flutter Barcodes widget | Syncfusion
description: Learn here about getting started with Syncfusion Flutter Barcodes (SfBarcodeGenerator) widget, its elements, and more.
platform: flutter
control: SfBarcodeGenerator
documentation: ug
---

# Getting started with Flutter Barcodes (SfBarcodeGenerator)

This section explains the steps required to add the barcode and set its symbology. This section covers only basic features needed to get started with Syncfusion<sup>&reg;</sup> barcode generator widget. 


## Add Flutter Barcode to an application

Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://docs.flutter.dev/get-started/test-drive#choose-your-ide) documentation.

**Add dependency**

Add the Syncfusion<sup>&reg;</sup> Flutter Barcode dependency to your pubspec.yaml file.

{% tabs %}

{% highlight dart %} 

    dependencies:

    syncfusion_flutter_barcodes: ^xx.x.xx

{% endhighlight %}

{% endtabs %}

N> Here **xx.x.xx** denotes the current version of the [Syncfusion<sup>&reg;</sup> Flutter Barcodes](https://pub.dev/packages/syncfusion_flutter_barcodes/versions) package. You can check the latest version available on [pub.dev](https://pub.dev/packages/syncfusion_flutter_barcodes/install).

**Get packages**

Run the following command to get the required packages.

{% tabs %}

{% highlight dart %} 

    $ flutter pub get

{% endhighlight %}

{% endtabs %}

**Import package**

Import the following package in your Dart code.

{% tabs %}

{% highlight dart %} 

    import 'package:syncfusion_flutter_barcodes/barcodes.dart';

{% endhighlight %}

{% endtabs %}

## Initialize the barcode

Add the Barcode Generator widget as a child of any widget. Here, the widget is added as a child of the container widget and the height to the container is specified (otherwise, it will occupy the full available height).

{% tabs %}

{% highlight dart %} 

  import 'package:flutter/material.dart';
  import 'package:syncfusion_flutter_barcodes/barcodes.dart';

  void main() {
    runApp(MyApp());
  }

  class MyApp extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      return MaterialApp(
        home: Scaffold(
          body: Center(
            child: Container(
              height: 150,
              child: SfBarcodeGenerator(value: 'http://www.syncfusion.com'),
            ),
          ),
        ),
      );
    }
  }

{% endhighlight %}

{% endtabs %}

N> The default symbology of SfBarcodeGenerator is [`Code128`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code128-class.html).

![Initialize barcode generator](images/getting-started/getting_started1.jpg)

## Initialize QR Code symbology

You can set the required symbology type to the barcode generator based on input value by initializing the [`symbology`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Symbology-class.html) property. In the following code snippet, the QR code is set as the barcode symbology.

{% tabs %}

{% highlight dart %} 

  import 'package:flutter/material.dart';
  import 'package:syncfusion_flutter_barcodes/barcodes.dart';

  void main() {
    runApp(MyApp());
  }

  class MyApp extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      return MaterialApp(
        home: Scaffold(
          body: Center(
            child: Container(
              height: 350,
              width: 350,
              child: SfBarcodeGenerator(
                value: 'http://www.syncfusion.com',
                symbology: QRCode(),
              ),
            ),
          ),
        ),
      );
    }
  }

{% endhighlight %}

{% endtabs %}

![symbology to barcode](images/getting-started/getting_started2.jpg)

## Display input value

The provided input value can be displayed below the barcode by enabling the [`showValue`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/SfBarcodeGenerator/showValue.html) property of barcode as shown in the following code snippet.

{% tabs %}

{% highlight dart %} 

  import 'package:flutter/material.dart';
  import 'package:syncfusion_flutter_barcodes/barcodes.dart';

  void main() {
    runApp(MyApp());
  }

  class MyApp extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      return MaterialApp(
        home: Scaffold(
          body: Center(
            child: Container(
              height: 350,
              width: 350,
              child: SfBarcodeGenerator(
                value: 'http://www.syncfusion.com',
                showValue: true,
                textSpacing: 15,
                symbology: QRCode(),
              ),
            ),
          ),
        ),
      );
    }
  }

{% endhighlight %}

{% endtabs %}

![Text to barcode](images/getting-started/getting_started3.jpg)

