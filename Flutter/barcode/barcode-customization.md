---
layout: post
title: Barcode customization of Syncfusion Flutter Barcode
description: This article explains how to customize the input value which is displayed as the text and the bar of barcode generator control in flutter.
platform: flutter
control: SfBarcodeGenerator
documentation: ug
---

# Customization

## Text customization 

**Displaying input value**

The provided input value of the barcode can be displayed by enabling its `showValue` property. By default, the `showValue` is false.

{% highlight dart %} 

    @override
        Widget build(BuildContext context) {
            return Scaffold(
                backgroundColor: Colors.white,
                body: Center(
                    child: Container(
                        height: 150,
                        width: 300,
                        child: SfBarcodeGenerator(
                            value: '12634388927',
                            showValue: true)
                    )
                )
            );
        }

{% endhighlight %}

![show text](images/text-customization/show-text.jpg)

**Text style customization**

The style of the text can be customized with the `textStyle` property of the barcode generator.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
        backgroundColor: Colors.white,
        body: Center(
            child: Container(
                height: 150,
                width: 300,
                child: SfBarcodeGenerator(
                    value: '12634388927',

                    textStyle: TextStyle(fontFamily: 'Times',
                        fontSize: 16, fontStyle: FontStyle.italic,
                        fontWeight: FontWeight.bold,
                        color: Colors.red),
                    showValue: true)
            )
        )
    );
  }

{% endhighlight %}

![text customization](images/text-customization/text-style.jpg)

**Text spacing**

The spacing between the text and the barcode can be controlled by the `textSpacing` property of barcode generator. By default, the value of `textSpacing` is 0. 

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
        backgroundColor: Colors.white,
        body: Center(
            child: Container(
                height: 150,
                width: 300,
                child: SfBarcodeGenerator(
                    value: '12634388927',
                    textSpacing: 25,
                    showValue: true)
            )
        )
    );
  }

{% endhighlight %}

![text spacing](images/text-customization/text-spacing.jpg)

**Text alignment**

The alignment of the text can be controlled by `textAlign` property of barcode generator. The displayed value can be positioned at `start`, `center` or `end` of the control. The default value of `textAlign` property is center.

{% highlight dart %} 
  
    @override
    Widget build(BuildContext context) {
    return Scaffold(
            backgroundColor: Colors.white,
            body: Center(
            child: Container(
                height: 150,
                width: 240,
                child: SfBarcodeGenerator(
                  value: '12634',
                  textAlign: TextAlign.end,
                  showValue: true)
            )
        )
      );
    }

{% endhighlight %}

![text align](images/text-customization/text-align.png)

## Bar customization

**Bar width customization**

Both the one dimensional and the two dimensional symbology support the `module` property. The property is used to define the size of the smallest line or dot of the barcode.

For one dimensional barcode, if this property is not set, the size of the smallest line of the barcode is calculated based on the available width and total number of bars for the provided input value. The barcode takes full available height as its height.

The following code snippet shows the one dimensional barcode with `module` property,

{% highlight dart %} 

      @override
    Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      body: Center(
          child: Container(
            height: 150,
            width: 230,
            child: SfBarcodeGenerator(
              backgroundColor: Colors.tealAccent,
              value: '123456789',
              showValue: true,
              symbology: Codabar(module: 1),),
          )
        ),
      );
    }

  {% endhighlight %}

![with module value](images/text-customization/with-module.jpg)

Below code snippet shows the one dimensional barcode without the `module` property,

{% highlight dart %} 

      @override
    Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      body: Center(
          child: Container(
            height: 150,
            width: 230,
            child: SfBarcodeGenerator(
              backgroundColor: Colors.tealAccent,
              value: '123456789',
              showValue: true,
              symbology: Codabar(),),
          )
      ),
    );
  }

  {% endhighlight %}

![without module value](images/text-customization/without-module.jpg)

For two dimensional barcode , if the `module` property is not set, the size of smallest line or dot is calculated based on the minimum of available size.

The following code snippet shows the two dimensional barcode with `module` property,

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      body: Center(
          child: Container(
            height: 150,
            width: 230,
            child: SfBarcodeGenerator(
               backgroundColor: Color.fromRGBO(193, 250, 250, 1),
              value: '123456789',
              symbology: QRCode(module: 2),),
          )
        ),
      );
    }

  {% endhighlight %}

  ![QR with module value](images/text-customization/qr-with-module.jpg)

  Below code snippet shows the two dimensional barcode without the `module` property,

  {% highlight dart %} 

     @override
    Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      body: Center(
          child: Container(
            height: 150,
            width: 230,
            child: SfBarcodeGenerator(
              backgroundColor: Color.fromRGBO(193, 250, 250, 1),
              value: '123456789',
              symbology: QRCode(),),
          )
        ),
      );
    }

  {% endhighlight %}

  ![QR without module value](images/text-customization/qr-without-module.jpg)

**Bar color customization**

The bar color of the barcode can be customized by using its `barColor` property as like the following code snippet,

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
    return Scaffold(
        backgroundColor: Colors.white,
        body: Center(
            child: Container(
                height: 150,
                width: 240,
                child: SfBarcodeGenerator(
                  value: '12634',
                   barColor: Colors.deepPurple,
                 )
            )
        )
     );
    }

{% endhighlight %}

![bar color](images/text-customization/bar-color.jpg)

**Background color customization**

The background color of barcode can be customized with the `backgroundColor` property of barcode generator as like the below code snippet,

{% highlight dart %} 

     @override
    Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      body: Center(
          child: Container(
            height: 150,
            width: 230,
            child: SfBarcodeGenerator(
              backgroundColor: Color.fromRGBO(193, 250, 250, 1),
              value: '123456789',
              symbology: Codabar(),),
          )
       ),
      );
     }

  {% endhighlight %}

  ![background color](images/text-customization/background-color.jpg)

