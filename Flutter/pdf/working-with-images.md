---
layout: post
title: Images in Flutter PDF library | Syncfusion
description: Learn here all about draw raster images and applying transparency and rotation to the images feature of Syncfusion Flutter PDF non-UI library and more.
platform: flutter
control: PDF
documentation: ug
---

# Images in Flutter PDF

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

## Inserting image to PDF using a web URL

The ['PdfBitmap'](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfBitmap-class.html) API accepts List<int> and base64 string as  inputs, so you can retrieve the image from the web URL as base64 or List<int> and assign it to the bitmap class. 

Steps to insert an image to the PDF using Web URL:
 1.	Add **http** package to the dependencies section of the **pubspec.yaml** file
 {% highlight dart %}
dependencies: 
http: ^0.13.4
{%endhighlight%}

2.	Import the following package into your dart file.
{%highlight dart%}
import 'package:http/http.dart' show get;
{%endhighlight%}

This is explained in the following code snippet.

{% highlight dart %}

    //Create a PDF document.
    PdfDocument document = PdfDocument();

    //Add a page to the PDF.
    PdfPage page = document.pages.add();

    
    //Read the image data from the weblink.
    var url =
        "https://cdn.pixabay.com/photo/2015/04/23/22/00/tree-736885_1280.jpg";
    var response = await get(Uri.parse(url));
    var data = response.bodyBytes;

    //Create a bitmap object.
    PdfBitmap image = PdfBitmap(data);

    //Draw an image to the document.
    page.graphics.drawImage(
        image,
        Rect.fromLTWH(
            0, 0, page.getClientSize().width, page.getClientSize().height));

    //Save and launch the document.
    final List<int> bytes = document.save();

    //Dispose the document.
    document.dispose();

	
{% endhighlight %}
