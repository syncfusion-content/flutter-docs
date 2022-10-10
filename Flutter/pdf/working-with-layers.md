---
layout: post
title: Layers in Flutter PDF library | Syncfusion
description: Learn here all about add, remove, and modify the layers feature of Syncfusion Flutter PDF non-UI library and more.
platform: flutter
control: PDF
documentation: ug
---

# Layers in Flutter PDF

Layers also known as Option content, refer to sections of content in a PDF document that can be selectively viewed or hidden by document authors or consumers.

Syncfusion Flutter PDF provides support to create, add, update, and remove the layers from the PDF document.

## Adding Layers in a PDF document

You can create a layer in a PDF page using the [`PdfPageLayer`](#) class. The following code sample shows how to add the multiple layers in a new PDF document.

{% highlight dart %}

//Creates a new PDF document
PdfDocument document = PdfDocument();

//Creates a new page
PdfPage page = document.pages.add();

//Add the first layer.
PdfPageLayer layer = page.layers.add(name: 'Layer1');

//Get the layer graphics.
PdfGraphics graphics = layer.graphics;
graphics.translateTransform(100, 60);

//Draw an Arc.
graphics.drawArc(Rect.fromLTWH(0, 0, 50, 50), 360, 360,
    pen: PdfPen(PdfColor(250, 0, 0), width: 50));
graphics.drawArc(Rect.fromLTWH(0, 0, 50, 50), 360, 360,
    pen: PdfPen(PdfColor(0, 0, 250), width: 30));
graphics.drawArc(Rect.fromLTWH(0, 0, 50, 50), 360, 360,
    pen: PdfPen(PdfColor(250, 250, 0), width: 20));
graphics.drawArc(Rect.fromLTWH(0, 0, 50, 50), 360, 360,
    pen: PdfPen(PdfColor(0, 250, 0), width: 10));

//Add another layer on the page.
layer = page.layers.add(name: 'Layer2', visible: false);

graphics = layer.graphics;
graphics.translateTransform(100, 180);

//Draw another set of elements.
graphics.drawArc(Rect.fromLTWH(0, 0, 50, 50), 360, 360,
    pen: PdfPen(PdfColor(250, 0, 0), width: 50));
graphics.drawArc(Rect.fromLTWH(0, 0, 50, 50), 360, 360,
    pen: PdfPen(PdfColor(0, 0, 250), width: 30));
graphics.drawArc(Rect.fromLTWH(0, 0, 50, 50), 360, 360,
    pen: PdfPen(PdfColor(250, 250, 0), width: 20));
graphics.drawArc(Rect.fromLTWH(0, 0, 50, 50), 360, 360,
    pen: PdfPen(PdfColor(0, 250, 0), width: 10));

//Save the PDF document.
File('output.pdf').writeAsBytes(await document.save());

{% endhighlight %}

The following code shows how to add the multiple layers in an existing PDF document.

{% highlight dart %}

//Load the existing PDF document.
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Add the first layer.
PdfPageLayer layer =
    document.pages[0].layers.add(name: 'Layer1', visible: true);

//Get the layer graphics.
PdfGraphics graphics = layer.graphics;

graphics.translateTransform(300, 360);

//Draw an Arc.
graphics.drawArc(Rect.fromLTWH(0, 0, 50, 50), 360, 360,
    pen: PdfPen(PdfColor(250, 0, 0), width: 50));
graphics.drawArc(Rect.fromLTWH(0, 0, 50, 50), 360, 360,
    pen: PdfPen(PdfColor(0, 0, 250), width: 30));
graphics.drawArc(Rect.fromLTWH(0, 0, 50, 50), 360, 360,
    pen: PdfPen(PdfColor(250, 250, 0), width: 20));
graphics.drawArc(Rect.fromLTWH(0, 0, 50, 50), 360, 360,
    pen: PdfPen(PdfColor(0, 250, 0), width: 10));

//Save the PDF document.
File('output.pdf').writeAsBytes(await document.save());

{% endhighlight %}

## Toggling the visibility of layers

The visibility of a layer can be mentioned while creating a new page layer.

The following code shows how to toggle the visibility of layers in a new PDF document.

{% highlight dart %}

//Creates a new PDF document
PdfDocument document = PdfDocument();

//Creates a new page
PdfPage page = document.pages.add();

//Add the first layer and enable visibility.
PdfPageLayer layer = page.layers.add(name: 'Layer1', visible: true);
PdfGraphics graphics = layer.graphics;
graphics.translateTransform(100, 60);
graphics.drawArc(Rect.fromLTWH(0, 0, 50, 50), 360, 360,
    pen: PdfPen(PdfColor(250, 0, 0), width: 50));

//Add another layer on the page and disable the visibility.
PdfPageLayer layer2 = page.layers.add(name: 'Layer2', visible: false);
graphics = layer2.graphics;
graphics.translateTransform(100, 180);
graphics.drawEllipse(Rect.fromLTWH(0, 0, 50, 50),
    pen: PdfPen(PdfColor(250, 0, 0), width: 50));

//Save the PDF document.
File('output.pdf').writeAsBytes(await document.save());

{% endhighlight %}

## Removing layers from an existing PDF document

You can remove the layers from the layer collection represented by the [`PdfPageLayerCollection`](#) of the loaded page. This is showed in the following code sample.

{% highlight dart %}

//Load the existing PDF document and remove the layer on the first page.
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync())
      ..pages[0].layers.removeAt(1);

//Save the PDF document.
File('output.pdf').writeAsBytes(await document.save());

{% endhighlight %}

## Nested Layers

Syncfusion Flutter PDF allows users to add nested layers in the PDF document. Refer to the following code sample.

{% highlight dart %}

//Creates a new PDF document
PdfDocument document = PdfDocument();

//Creates a new page
PdfPage page = document.pages.add();

//Add the first layer.
PdfLayer layer = document.layers.add(name: 'Layer1', visible: true)
  ..createGraphics(page).drawRectangle(
      bounds: Rect.fromLTWH(0, 0, 200, 100), brush: PdfBrushes.red);

//Create nested layer.
layer.layers.add(name: 'Nested Layer1', visible: true)
  ..createGraphics(page)
      .drawRectangle(bounds: Rect.fromLTWH(0, 120, 200, 100), brush: PdfBrushes.green);

//Save the PDF document.
File('output.pdf').writeAsBytes(await document.save());

{% endhighlight %}

## Flattening the layers in an existing PDF document

You can flatten a layer in a PDF document by removing it from the [`PdfLayerCollection`](#). The following code sample explains this.

{% highlight dart %}

//Load the existing PDF document and flatten the layer.
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync())..layers.removeAt(0, false);

//Save the PDF document.
File('output.pdf').writeAsBytes(await document.save());


{% endhighlight %}