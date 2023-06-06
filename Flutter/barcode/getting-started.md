---
layout: post
title: 	Getting started with Flutter Barcodes widget | Syncfusion
description: Learn here about getting started with Syncfusion Flutter Barcodes (SfBarcodeGenerator) widget, its elements, and more.
platform: flutter
control: SfBarcodeGenerator
documentation: ug
---

# Getting started with Flutter Barcodes (SfBarcodeGenerator)

This section explains the steps required to add the barcode and set its symbology. This section covers only basic features needed to get started with Syncfusion barcode generator widget. 


## Add Flutter Barcode to an application

Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://docs.flutter.dev/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion Flutter Barcode dependency to your pubspec.yaml file.

{% highlight dart %} 

    dependencies:

    syncfusion_flutter_barcodes: ^xx.x.xx

{% endhighlight %}

N> Here **xx.x.xx** denotes the current version of [`Syncfusion Flutter Barcodes`](https://pub.dev/packages/syncfusion_flutter_barcodes/versions) package.

**Get packages**

Run the following command to get the required packages.

{% highlight dart %} 

    $ flutter pub get

{% endhighlight %}

**Import package**

Import the following package in your Dart code.

{% highlight dart %} 

    import 'package:syncfusion_flutter_barcodes/barcodes.dart';

{% endhighlight %}

## Initialize the barcode

Add the Barcode Generator widget as a child of any widget. Here, the widget is added as a child of the container widget and the height to the container is specified (otherwise it will take full container height).

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return MaterialApp(
            home: Scaffold(
                body: Center(
                    child: Container(
                         height: 150,
                        child:SfBarcodeGenerator(value:'http://www.syncfusion.com')
                        )
                    )
                )      
            );
        }

{% endhighlight %}

N> The default symbology of SfBarcodeGenerator is [`Code128`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code128-class.html).

![Initialize barcode generator](images/getting-started/getting_started1.jpg)

## Initialize QR Code symbology

You can set the required symbology type to the barcode generator based on input value by initializing the [`symbology`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Symbology-class.html) property. In the following code snippet, the QR code is set as the barcode symbology.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return MaterialApp(
            home: Scaffold(
                body: Center(
                    child: Container(
                        height: 350,
                        width: 350,
                        child:SfBarcodeGenerator(value:'http://www.syncfusion.com',
                         symbology: QRCode())
                        )
                    )
                )      
            );
        }

{% endhighlight %}

![symbology to barcode](images/getting-started/getting_started2.jpg)

## Display input value

The provided input value can be displayed below the barcode by enabling the [`showValue`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/SfBarcodeGenerator/showValue.html) property of barcode as like the following code snippet,

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return MaterialApp(
            home: Scaffold(
                body: Center(
                    child: Container(
                        height: 350,
                        width: 350,
                        child:SfBarcodeGenerator(value:'http://www.syncfusion.com',
                         showValue: true, textSpacing: 15,
                         symbology: QRCode())
                        )
                    )
                )      
            );
        }

{% endhighlight %}

![Text to barcode](images/getting-started/getting_started3.jpg)

