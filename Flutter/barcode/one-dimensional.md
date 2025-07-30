---
layout: post
title: One-dimensional symbology in Flutter Barcodes widget | Syncfusion 
description: Learn here all about One-dimensional symbology feature of Syncfusion Flutter Barcodes (SfBarcodeGenerator) widget and more.
platform: flutter
control: SfBarcodeGenerator
documentation: ug
---

# One-dimensional symbology in Flutter Barcodes (SfBarcodeGenerator)

One-dimensional barcodes represent data by varying the widths and spacings of parallel lines. These barcode types are also known as linear barcode types. The Syncfusion<sup>&reg;</sup> flutter barcode generator supports the following one-dimensional barcode types:

* [`Codabar`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Codabar-class.html)
* [`Code39`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code39-class.html)
* [`Code39Extended`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code39Extended-class.html)
* [`Code93`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code93-class.html)
* [`UPCA`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/UPCA-class.html)
* [`UPCE`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/UPCE-class.html)
* [`EAN8`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/EAN8-class.html)
* [`EAN13`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/EAN13-class.html)
* [`Code128`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code128-class.html)
* [`Code128A`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code128A-class.html)
* [`Code128B`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code128B-class.html)
* [`Code128C`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code128C-class.html)

## Codabar

* [`Codabar`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Codabar-class.html) is a discrete numeric symbology that is used in libraries, blood banks and a variety of other information processing applications.

* Encodes only numeric characters and some special characters like dash (-), colon (:), slash (/), plus (+).
* Each character has three bars and four spaces.
* Uses characters of A, B, C, D as start and stop characters.

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      body: Center(
        child: Container(
          height: 150,
          child: SfBarcodeGenerator(
            value: '123456789',
            showValue: true,
            symbology: Codabar(module: 2),
          ),
        ),
      ),
    );
  }

{% endhighlight %}

![codabar symbology](images/one-dimensional/codabar.jpg)

## Code39

[`Code 39`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code39-class.html) is a discrete, variable-length symbology that encodes alphanumeric characters into a series of bars. A special start / stop character is placed at the beginning and ending of each barcode. Code 39 is self-checking, a check digit is not usually required for common use. For certain cases, applications requiring an extremely high level of accuracy of the checksum digit might be added.

* Allows character set of digits (0-9), upper case alphabets (A-Z), and symbols like space, minus (-), plus (+), period (.), dollar sign ($), slash (/), and percent (%).
* Each character is encoded with 5 bars and 4 spaces where 3 are wide and 6 are narrow.

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      body: Center(
        child: Container(
          height: 150,
          child: SfBarcodeGenerator(
            value: 'CODE39',
            showValue: true,
            symbology: Code39(module: 2),
          ),
        ),
      ),
    );
  }

{% endhighlight %}

![code39 symbology](images/one-dimensional/code39.jpg)

The [`enableCheckSum`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code39/enableCheckSum.html) property of [`Code39`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code39-class.html) barcode allows to add the check digit along with the input value. The default value of [`enableCheckSum`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code39/enableCheckSum.html) property is true.

## Code39 Extended

[`Code39 Extended`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code39Extended-class.html) symbology is an extended version of Code39 that supports all 128 ASCII characters set. So, it encodes lower case alphabets (a-z) as well as special characters.

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      body: Center(
        child: Container(
          height: 150,
          child: SfBarcodeGenerator(
            value: '051091',
            showValue: true,
            symbology: Code39Extended(module: 2),
          ),
        ),
      ),
    );
  }

{% endhighlight %}

![code39 extended symbology](images/one-dimensional/code39-extended.jpg)

As like [`Code39`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code39-class.html), the [`Code39 Extended`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code39Extended-class.html) supports the [`enableCheckSum`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code39/enableCheckSum.html) property.

## Code93

[`Code93`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code93-class.html) is designed to complement and enhance [`Code39`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code39-class.html). It represents the complete ASCII character set by using a combination of 2 characters. It is a continuous, variable-length symbology and produces a denser code.

* Encodes character set of uppercase alphabets (A-Z), digits (0-9), and special characters such as asterisk (*), dash (-), dollar ($), percent (%), Space, dot (.), slash (/), plus (+) and so on. 
* The asterisk (*) is not a true encoding character, but it is the start and stop symbol for [`Code93`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code93-class.html) Symbology.

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      body: Center(
        child: Container(
          height: 150,
          child: SfBarcodeGenerator(
            value: '01234567',
            showValue: true,
            symbology: Code93(module: 2),
          ),
        ),
      ),
    );
  }

{% endhighlight %}

![code93 symbology](images/one-dimensional/code93.jpg)

## Code128

[`Code 128`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code128-class.html) is a highly efficient, high-density linear barcode symbology that allows the encoding of alphanumeric data. It is capable of encoding full ASCII character set and extended character sets. This symbology contains the checksum digit for verification and the barcode can also be verified character-by-character for the parity of each data byte.

The [`Code128`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code128-class.html) symbology encodes the input symbols supported by [`Code128A`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code128A-class.html), [`Code128B`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code128B-class.html), [`Code128C`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code128C-class.html). The default symbology type of barcode generator is [`Code128`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code128-class.html)

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      body: Center(
        child: Container(
          height: 150,
          child: SfBarcodeGenerator(
            value: 'CODE128',
            showValue: true,
            symbology: Code128(module: 2),
          ),
        ),
      ),
    );
  }

{% endhighlight %}

![code128 symbology](images/one-dimensional/code128.jpg)

## Code128A

[`Code128A`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code128A-class.html) (or Chars Set A) includes all the standard upper case U.S. alphanumeric keyboard characters and punctuation characters together with the control characters, (characters with ASCII values from 0 to 95 inclusive), and seven special characters.

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      body: Center(
        child: Container(
          height: 150,
          child: SfBarcodeGenerator(
            value: 'CODE128A',
            showValue: true,
            symbology: Code128A(module: 2),
          ),
        ),
      ),
    );
  }

{% endhighlight %}

![code128A symbology](images/one-dimensional/code128A.jpg)

## Code128B

[`Code128B`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code128B-class.html)  (or Chars Set B) includes all the standard upper case alphanumeric keyboard characters and punctuation characters together with lower case alphabetic characters (characters with ASCII values from 32 to 127 inclusive), and seven special characters.

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      body: Center(
        child: Container(
          height: 150,
          child: SfBarcodeGenerator(
            value: 'CODE128B',
            showValue: true,
            symbology: Code128B(module: 2),
          ),
        ),
      ),
    );
  }

{% endhighlight %}

![code128B symbology](images/one-dimensional/code128B.jpg)

## Code128C

[`Code128C`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Code128C-class.html) (or Chars Set C) includes a set of 100 digit pairs from 00 to 99 inclusive, as well as three special characters. This allows numeric data to be encoded as two data digits per symbol character effectively twice the density of standard data.

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      body: Center(
        child: Container(
          height: 150,
          child: SfBarcodeGenerator(
            value: '1234567890',
            showValue: true,
            symbology: Code128C(module: 2),
          ),
        ),
      ),
    );
  }

{% endhighlight %}

![code128C symbology](images/one-dimensional/code128c.jpg)

**Code 128 Special characters**

The last seven characters of Code Sets A and B (character values 96 - 102) and the last three characters of Code Set C (character values 100 - 102) are special non-data characters with no ASCII character equivalents that have a particular significance to the Barcode reading device.

## UPC-A

[`UPC-A`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/UPCA-class.html) symbology supports only numeric characters. It encodes 11 digits of provided numeric input (0 to 9) along with a check digit at its end, for a total of 12 digits of input data. If you give 11 numeric inputs, the check digit should automatically calculate at the end, and if you give 12 numeric inputs, the last digit should be check digit, otherwise it will not be accepted.

* This type is mainly used for worldwide retail.

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      body: Center(
        child: Container(
          height: 150,
          child: SfBarcodeGenerator(
            value: '72527273070',
            showValue: true,
            symbology: UPCA(module: 2),
          ),
        ),
      ),
    );
  }

{% endhighlight %}

![UPCA symbology](images/one-dimensional/upca-symbology.png)

## UPC-E

As like [`UPC-A`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/UPCA-class.html), the [`UPC-E`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/UPCE-class.html) symbology supports only numeric character. It is a zero suppressed version of [`UPC-A`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/UPCA-class.html) symbology where it uses only 6 digits of product code and does not use the middle guard. By default, the number system(0) will add at the front and check digit at the end along with 6 digits of the input product code.

* This type is mainly used on products with very small packaging details.

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      body: Center(
        child: Container(
          height: 150,
          child: SfBarcodeGenerator(
            value: '310194',
            showValue: true,
            symbology: UPCE(module: 2),
          ),
        ),
      ),
    );
  }

{% endhighlight %}

![UPCE symbology](images/one-dimensional/upce.png)

## EAN-13

[`EAN-13`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/EAN13-class.html), based on the UPC-A standard. As like [`UPC-A`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/UPCA-class.html), it supports only the numeric character. It encodes the 12 digits of input data with the check digit at its end.

* This difference between the [`UPCA`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/UPCA-class.html) and [`EAN13`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/EAN13-class.html) is that number system used in the [`EAN13`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/EAN13-class.html) is 2 digits ranges from 00 to 99 whereas the number system used in [`UPCA`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/UPCA-class.html) is single digits range from 0 to 9.

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      body: Center(
        child: Container(
          height: 150,
          child: SfBarcodeGenerator(
            value: '9735940564824',
            showValue: true,
            symbology: EAN13(module: 2),
          ),
        ),
      ),
    );
  }

{% endhighlight %}

![EAN13 symbology](images/one-dimensional/ean-13.png)

## EAN-8

[`EAN8`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/EAN8-class.html) is equivalent to the [`UPCE`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/UPCE-class.html) for small packaging details. It is shorter than the [`EAN13`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/EAN13-class.html) barcode and it is longer than [`UPCE`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/UPCE-class.html).

As like [`EAN13`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/EAN13-class.html) and [`UPCE`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/UPCE-class.html), it encodes 7 digits of numeric data with the check digit at its end.

{% highlight dart %} 

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      body: Center(
        child: Container(
          height: 150,
          child: SfBarcodeGenerator(
            value: '11223344',
            showValue: true,
            symbology: EAN8(module: 2),
          ),
        ),
      ),
    );
  }

{% endhighlight %}

![EAN8 symbology](images/one-dimensional/ean-8.png)

All the one dimensional symbology supports the [`module`](https://pub.dev/documentation/syncfusion_flutter_barcodes/latest/barcodes/Symbology/module.html) property. The property is used to define the size of the smallest line or dot of the barcode. If this property is not set, the size of the smallest line of the barcode is calculated based on the available size and total number of bars for the provided input value.