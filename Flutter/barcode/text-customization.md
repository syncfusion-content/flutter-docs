---
layout: post
title: Text customization of Syncfusion Flutter Barcode
description: This article explains how to customize the text of barcode generator control
platform: flutter
control: SfBarcodeGenerator
documentation: ug
---

# Text customization of Barcode Generator 

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
                            textSpacing: 15,
                            textStyle: TextStyle(fontFamily: 'Times', 
                            fontSize: 16,
                            fontWeight: FontWeight.bold,
                             color: Colors.red),
                            showValue: true)
                    )
                )
            );
        }

{% endhighlight %}

![text customization](images/text-customization/text-customization.jpg)

The spacing between the text and the barcode can be controlled by the `textSpacing` property. By default, the value of `textSpacing` is 0. 

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

The bar color of the barcode can be customized by using its`barColor` property as like the following code snippet,

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