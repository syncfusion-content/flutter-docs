---
layout: post
title: Supported two dimensional symbology for Syncfusion Flutter Barcode
description: This article explains the supported two dimensional symbology types of syncfusion flutter barcode generator control
platform: flutter
control: SfBarcodeGenerator
documentation: ug
---

# Two-dimensional symbology

Two dimensional Barcode is a way to represent information by using the two-dimensional approach. It is similar to one dimensional Barcode, but can represent more data per unit area. The barcode generator control supports the following two dimensional symbology:

`QR Code`

## QR Code

A QR Code is a two-dimensional barcode that consists of a grid of dark and light dots or blocks that form a square. The data encoded in the barcode can be numeric, alphanumeric, or Shift JIS characters.

* The QR Code uses version from 1 to 40. Version 1 measures 21 modules x 21 modules, Version 2 measures 25 modules x 25 modules, and so on. The number of modules increases in steps of 4 modules per side up to Version 40 that measures 177 modules x 177 modules. 

* Each version has its own capacity. By default, the barcode control automatically sets the version according to the length of the input text.

* The QR Barcodes are designed for industrial uses and also commonly used in consumer advertising.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
        backgroundColor: Colors.white,
        body: Center(
            child: Container(
                height: 300,
                width: 300,
                child: SfBarcodeGenerator(
                  value: 'www.syncfusion.com',
                  showValue: true,
                  symbology: QRCode())
            )
        )
    );
  }

{% endhighlight %}

![qr-code](images/two-dimensional/qr-code.jpg)

The data that can be stored in the QR code depends upon the following property:

* `Error correction level`
* `QR code version`
* `Input mode`


As like one dimensional symbology, the two dimensional symbology also supports the `module` property. 
The property is used to define the size of the smallest line or dot of the barcode. If this property is not set, the size of the smallest dot of the barcode is calculated based on the available size.

**Error correction level**

The `errorCorrectionLevel` property employs error correction to generate a series of error correction code words that are added to the data code word sequence in order to enable the symbol to withstand damage without loss of data. By default, its value is set as high.

Low - it recovers the data up to 7%
Medium - it recovers the data up to 15%
Quartile - it recovers the data up to 25%
High - it recovers the data up to 30%

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
        backgroundColor: Colors.white,
        body: Center(
            child: Container(
                height: 300,
                width: 300,
                child: SfBarcodeGenerator(
                  value: 'www.syncfusion.com',
                  showValue: true,
                  symbology: QRCode(errorCorrectionLevel: ErrorCorrectionLevel.high),)
            )
        )
    );
  }

{% endhighlight %}

![error correction level](images/two-dimensional/qr-code.jpg)

The data can be read from the damaged image based on the error correction level,

![eror correction level](images/two-dimensional/error-correction.jpg)

**Input mode**

The `inputMode` property allows you to select a specific set of input characters. You may select the most suitable input mode. By default, its value is set as `binaryMode`.

numeric - supports from 0 to 9
alphaNumeric - supports 0 to 9, A to Z, space, $, %, *, +, -,., /, :
binary - supports Shift JIS characters

{% highlight dart %} 

    @override
        Widget build(BuildContext context) {
    return Scaffold(
        backgroundColor: Colors.white,
        body: Center(
            child: Container(
                height: 300,
                width: 300,
                child: SfBarcodeGenerator(
                  value: '1263438892737643894930872',
                  showValue: true,
                  symbology: QRCode(inputMode: QRInputMode.numeric),)
            )
        )
    );
  }

{% endhighlight %}

![input mode](images/two-dimensional/input-mode.jpg)

**QR code version**

The `version` property allows you to set various types of version for QR code from QRVersion enumeration. By default, its value is set as auto.

The QR Code uses version from 1 to 40. Version 1 measures 21 modules x 21 modules, Version 2 measures 25 modules x 25 modules, and so on. 

The number of modules increases in steps of 4 modules per side up to Version 40 that measures 177 modules x 177 modules. 

{% highlight dart %} 

    @override
        Widget build(BuildContext context) {
    return Scaffold(
        backgroundColor: Colors.white,
        body: Center(
            child: Container(
                height: 300,
                width: 300,
                child: SfBarcodeGenerator(
                  value: 'www.syncfusion.com',
                  showValue: true,
                  symbology: QRCode(codeVersion: QRCodeVersion.version09))
            )
        )
    );
  }

{% endhighlight %}

![QR version](images/two-dimensional/version09.jpg)
