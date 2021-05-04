---
layout: post
title: Watermarks in Flutter PDF library | Syncfusion
description: Learn here all about add text and image Watermarks feature of Syncfusion Flutter PDF non-UI library and more.
platform: flutter
control: PDF
documentation: ug
---

# Watermarks in Flutter PDF

The Syncfusion Flutter PDF provides support for adding watermarks to a PDF document using [`PdfGraphics`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics-class.html).

## Adding text watermark to a PDF document

The Syncfusion Flutter PDF allows you draw the text watermark to the PDF document using graphics elements.

The following code example explains how to draw the text watermark to the PDF document.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Add a page to the document and get page graphics
PdfGraphics graphics = document.pages.add().graphics;

//Watermark text
PdfGraphicsState state = graphics.save();

graphics.setTransparency(0.25);

graphics.rotateTransform(-40);

graphics.drawString('Imported using Essential PDF',
    PdfStandardFont(PdfFontFamily.helvetica, 20),
    pen: PdfPens.red,
    brush: PdfBrushes.red,
    bounds: Rect.fromLTWH(-150, 450, 0, 0));

graphics.restore(state);

//Save and dispose the PDF document
File('SampleOutput.pdf').writeAsBytes(document.save());
document.dispose();

{% endhighlight %}

## Adding image watermark to a PDF document

To add the image watermark to a PDF document, you can draw the image with transparency in [`PdfGraphics`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics-class.html).

The following code example explains how to draw an image watermark to the PDF document.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Add a page to the document and get page graphics
PdfGraphics graphics = document.pages.add().graphics;

//Watermark image
PdfGraphicsState state = graphics.save();
graphics.setTransparency(0.25);
graphics.drawImage(
    PdfBitmap.fromBase64String(imageData),
    Rect.fromLTWH(
        0, 0, graphics.clientSize.width, graphics.clientSize.height));
graphics.restore(state);

//Save and dispose the PDF document
File('SampleOutput.pdf').writeAsBytes(document.save());
document.dispose();

{% endhighlight %}
