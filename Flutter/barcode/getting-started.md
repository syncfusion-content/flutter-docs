---
layout: post
title: Getting Started for Syncfusion Flutter Barcode
description: A quick tour to initial users on Syncfusion SfBarcodeGenerator for flutter platform
platform: flutter
control: SfBarcodeGenerator
documentation: ug
---

# Getting Started

This section explains the steps required to add the barcode and set its symbology. This section covers only basic features needed to know to get started with Syncfusion barcode control. 


## Add Flutter Barcode to an application

Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://flutter.dev/docs/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion Flutter Barcode dependency to your pubspec.yaml file.

{% highlight dart %} 

    dependencies:

    syncfusion_flutter_barcodes: ^1.0.0-beta

{% endhighlight %}

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

After the package has been imported, initialize the SfBarcodeGenerator as a child of any widget such as container widget.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return MaterialApp(
            home: Scaffold(
                body: Center(
                    child: Container(
                         height: 150,
                         width: 400,
                        child:SfBarcodeGenerator(value:'http://www.syncfusion.com')
                        )
                    )
                )      
            );
        }

{% endhighlight %}

The default symbology of SfBarcodeGenerator is Code128.

![Initialize barcode generator](images/getting-started/getting_started1.jpg)

## Initialize QR Code symbology

You can set the required symbology to the barcode generator by initializing the `symbology` property. In the following code snippet, the QR Code is set as the barcode symbology,

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

## Add text

The provided input value can be displayed below the barcode by enabling the `showValue` property of barcode as like the following code snippet,

{% highlight dart %} 

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

