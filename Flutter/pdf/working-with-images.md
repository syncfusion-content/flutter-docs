---
layout: post
title: Images of Syncfusion Flutter PDF
description: Learn how to draw raster images and applying transparency and rotation to the images in the Flutter PDF.
platform: flutter
control: PDF
documentation: ug
---

# Working with PDF Images

Images are supported through the [`PdfImage`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfImage-class.html) class, which is an abstract base class that provides functionality for [`PdfBitmap`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfBitmap-class.html) class.

## Inserting an image in PDF document

The following raster images are supported in Flutter PDF:

* JPEG
* PNG

You can load image data in [`PdfBitmap`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfBitmap-class.html) object to draw the images using the [`drawImage`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics/drawImage.html) method of the [`PdfGraphics`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics-class.html) class. The image data can be initialized as list of bytes or base64 string format.

The following code snippet shows how to draw an image to the PDF document.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Adds a page to the document
PdfPage page = document.pages.add();

//Draw the image
page.graphics.drawImage(
    PdfBitmap(File('image.jpg').readAsBytesSync()),
    Rect.fromLTWH(
        0, 0, page.getClientSize().width, page.getClientSize().height));

//Saves the document
File('Output.pdf').writeAsBytes(document.save());

//Disposes the document
document.dispose();
  
{% endhighlight %}

## Applying transparency and rotation to the image

You can add transparency and rotation to the image using the [`setTransparency`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics/setTransparency.html) and [`rotateTransform`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics/rotateTransform.html) methods of [`PdfGraphics`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics-class.html) respectively. This is explained in the following code snippet.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Adds a page to the document
PdfPage page = document.pages.add();

//Save the current graphics state
PdfGraphicsState state = page.graphics.save();

//Translate the coordinate system to the  required position
page.graphics.translateTransform(20, 100);

//Apply transparency
page.graphics.setTransparency(0.5);

//Rotate the coordinate system
page.graphics.rotateTransform(-45);

//Draw image
page.graphics.drawImage(
    PdfBitmap(File('image.jpg').readAsBytesSync()),
    Rect.fromLTWH(
        0, 0, page.getClientSize().width, page.getClientSize().height));

//Restore the graphics state
page.graphics.restore(state);

//Saves the document
File('Output.pdf').writeAsBytes(document.save());

//Disposes the document
document.dispose();
	
{% endhighlight %}
