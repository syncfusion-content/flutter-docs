---
layout: post
title: Layers of Syncfusion Flutter PDF
description: Learn how to add, remove, and modify the layers in a PDF document and its pages for the Flutter PDF.
platform: flutter
control: PDF
documentation: ug
---

# Working with layers in a PDF document

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
PdfGraphics graphics = layer.graphics;
graphics.translateTransform(100, 60);

//Draw an Arc.
PdfPen pen = PdfPen(PdfColor(250, 0, 0), width: 50);
const Rect rect = Rect.fromLTWH(0, 0, 50, 50);
graphics.drawArc(rect, 360, 360, pen: pen);

pen = PdfPen(PdfColor(0, 0, 250), width: 30);
graphics.drawArc(const Rect.fromLTWH(0, 0, 50, 50), 360, 360, pen: pen);

pen = PdfPen(PdfColor(250, 250, 0), width: 20);
graphics.drawArc(rect, 360, 360, pen: pen);

pen = PdfPen(PdfColor(0, 250, 0), width: 10);
graphics.drawArc(const Rect.fromLTWH(0, 0, 50, 50), 360, 360, pen: pen);

//Add another layer on the page.
layer = page.layers.add(name: 'Layer2', visible: false);

graphics = layer.graphics;
graphics.translateTransform(100, 180);

//Draw another set of elements.
pen = PdfPen(PdfColor(250, 0, 0), width: 50);
graphics.drawArc(rect, 360, 360, pen: pen);
pen = PdfPen(PdfColor(0, 0, 250), width: 30);
graphics.drawArc(const Rect.fromLTWH(0, 0, 50, 50), 360, 360, pen: pen);
pen = PdfPen(PdfColor(250, 250, 0), width: 20);
graphics.drawArc(rect, 360, 360, pen: pen);
pen = PdfPen(PdfColor(0, 250, 0), width: 10);
graphics.drawArc(const Rect.fromLTWH(0, 0, 50, 50), 360, 360, pen: pen);

// Save the PDF document.
File('output.pdf').writeAsBytes(document.save());


{% endhighlight %}

The following code shows how to add the multiple layers in an existing PDF document.

{% highlight dart %}

// Load the existing PDF document.
PdfDocument document = 
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());
PdfPage page = document.pages[0];

//Add the first layer.
PdfPageLayer layer = page.layers.add(name: 'Layer1', visible: true);
PdfGraphics graphics = layer.graphics;
graphics.translateTransform(300, 360);

//Draw an Arc.
PdfPen pen = PdfPen(PdfColor(250, 0, 0), width: 50);
const Rect rect = Rect.fromLTWH(0, 0, 50, 50);
graphics.drawArc(rect, 360, 360, pen: pen);

pen = PdfPen(PdfColor(0, 0, 250), width: 30);
graphics.drawArc(const Rect.fromLTWH(0, 0, 50, 50), 360, 360, pen: pen);

pen = PdfPen(PdfColor(250, 250, 0), width: 20);
graphics.drawArc(rect, 360, 360, pen: pen);

pen = PdfPen(PdfColor(0, 250, 0), width: 10);
graphics.drawArc(const Rect.fromLTWH(0, 0, 50, 50), 360, 360, pen: pen);

// Save the PDF document.
File('output.pdf').writeAsBytes(document.save());

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
PdfPen pen = PdfPen(PdfColor(250, 0, 0), width: 50);
Rect rect = Rect.fromLTWH(0, 0, 50, 50);
graphics.drawArc(rect, 360, 360, pen: pen);

//Add another layer on the page and disable the visibility.
PdfPageLayer layer2 = page.layers.add(name: 'Layer2', visible: false);
graphics = layer2.graphics;
graphics.translateTransform(100, 180);
graphics.drawEllipse(rect, pen: pen);

// Save the PDF document.
File('output.pdf').writeAsBytes(document.save());

{% endhighlight %}

## Removing layers from an existing PDF document

You can remove the layers from the layer collection represented by the [`PdfPageLayerCollection`](#) of the loaded page. This is showed in the following code sample.

{% highlight dart %}

// Load the existing PDF document.
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Get the layer collection.
final PdfPageLayerCollection collection = document.pages[0].layers;

//Remove the layer.
collection.removeAt(1);

// Save the PDF document.
File('output.pdf').writeAsBytes(document.save());

{% endhighlight %}

## Nested Layers

Syncfusion Flutter PDF allows users to add nested layers in the PDF document. Refer to the following code sample.

{% highlight dart %}

//Creates a new PDF document
PdfDocument document = PdfDocument();

//Creates a new page
PdfPage page = document.pages.add();

//Add the first layer.
PdfLayer layer = document.layers.add(name: 'Layer1', visible: true);
PdfGraphics graphics = layer.createGraphics(page);
graphics.translateTransform(100, 60);

//Draw an Arc.
PdfPen pen = PdfPen(PdfColor(250, 0, 0), width: 50);
const Rect rect = Rect.fromLTWH(0, 0, 50, 50);
graphics.drawArc(rect, 360, 360, pen: pen);

pen = PdfPen(PdfColor(0, 0, 250), width: 30);
graphics.drawArc(const Rect.fromLTWH(0, 0, 50, 50), 360, 360, pen: pen);

pen = PdfPen(PdfColor(250, 250, 0), width: 20);
graphics.drawArc(rect, 360, 360, pen: pen);

pen = PdfPen(PdfColor(0, 250, 0), width: 10);
graphics.drawArc(const Rect.fromLTWH(0, 0, 50, 50), 360, 360, pen: pen);

// Save the PDF document.
File('output.pdf').writeAsBytes(document.save());

{% endhighlight %}

## Flattening the layers in an existing PDF document

You can flatten a layer in a PDF document by removing it from the [`PdfLayerCollection`](#). The following code sample explains this.

{% highlight dart %}

// Load the existing PDF document.
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

// Get layers from a collection.
final PdfLayerCollection layers = document.layers;

//Flatten a layer in the PDF document.
layers.removeAt(0, true);

// Save the PDF document.
File('output.pdf').writeAsBytes(document.save());

{% endhighlight %}