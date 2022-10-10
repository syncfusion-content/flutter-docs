---
layout: post
title: Annotations in Flutter PDF library | Syncfusion
description: Learn here all about interactive Annotations feature of Syncfusion Flutter PDF non-UI library and more.
platform: flutter
control: PDF
documentation: ug
---

# Annotations in Flutter PDF

The Syncfusion Flutter PDF provides support for interactive annotations.

You can [`add`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfAnnotationCollection/add.html), remove, and modify the [`annotations`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPage/annotations.html) from the PDF documents.

## Adding annotations to a PDF document

You can add a rectangle annotation to the page using the PdfRectangleAnnotation class. The following code example explains this.

{% highlight dart %}

//Creates a new PDF document
PdfDocument document = PdfDocument();

//Adds a new PDF page
PdfPage page = document.pages.add();

//Creates a rectangle annotation
PdfRectangleAnnotation rectangleAnnotation = PdfRectangleAnnotation(
    Rect.fromLTWH(0, 30, 80, 80), 'Rectangle Annotation',
    author: 'Syncfusion',
    color: PdfColor(255, 0, 0),
    modifiedDate: DateTime.now());

//Adds the annotation to the PDF page
page.annotations.add(rectangleAnnotation);

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

To add annotations to an existing PDF document, use the following code example.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Loads the existing PDF page
PdfPage page = document.pages[0];

//Creates a rectangle annotation
PdfRectangleAnnotation rectangleAnnotation = PdfRectangleAnnotation(
    Rect.fromLTWH(40, 70, 80, 80), 'Rectangle Annotation',
    author: 'Syncfusion',
    color: PdfColor(255, 0, 0),
    modifiedDate: DateTime.now());

//Adds the annotation to the loaded page
page.annotations.add(rectangleAnnotation);

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

## Supported annotation types

### Rectangle Annotation

This annotation displays a rectangle/square on the page based on the input bounds. When you open it, it displays a pop-up window containing the text of the associated note.

The PdfRectangleAnnotation is used to create and set the properties of the Rectangle annotation.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Adds a new PDF page
PdfPage page = document.pages.add();

//Creates a rectangle annotation
PdfRectangleAnnotation rectangleAnnotation = PdfRectangleAnnotation(
    Rect.fromLTWH(40, 70, 80, 80), 'Rectangle Annotation',
    author: 'Syncfusion',
    color: PdfColor(255, 0, 0),
    innerColor: PdfColor(0, 0, 255),
    border: PdfAnnotationBorder(10),
    modifiedDate: DateTime.now());

//Adds annotation to the page
page.annotations.add(rectangleAnnotation);

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

### Ellipse Annotation

This annotation displays an ellipse/circle on the page based on the input bounds. When you open it, it displays a pop-up window containing the text of the associated note.

The PdfEllipseAnnotation is used to create and set the properties of the Ellipse annotation.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Adds a new PDF page
PdfPage page = document.pages.add();

//Creates an ellipse annotation
PdfEllipseAnnotation ellipseAnnotation = PdfEllipseAnnotation(
    Rect.fromLTWH(40, 70, 80, 80), 'Ellipse Annotation',
    author: 'Syncfusion',
    color: PdfColor(255, 0, 0),
    innerColor: PdfColor(0, 0, 255),
    border: PdfAnnotationBorder(10),
    modifiedDate: DateTime.now());

//Adds annotation to the page
page.annotations.add(ellipseAnnotation);

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

### Line Annotation

This annotation displays a single straight line on the page. When you open it, it displays a pop-up window containing the text of the associated note.

The PdfLineAnnotation is used to create and set the properties of the Line annotation.

{% highlight dart %}

//Creates a new PDF document
PdfDocument document = PdfDocument();

//Adds a new PDF page
PdfPage page = document.pages.add();

//Creates a line annotation
PdfLineAnnotation lineAnnotation = PdfLineAnnotation(
    [80, 420, 250, 420], 'Line Annotation',
    author: 'Syncfusion',
    opacity: 0.95,
    border: PdfAnnotationBorder(1),
    lineIntent: PdfLineIntent.lineDimension,
    beginLineStyle: PdfLineEndingStyle.butt,
    endLineStyle: PdfLineEndingStyle.square,
    innerColor: PdfColor(0, 255, 0),
    color: PdfColor(0, 0, 255),
    leaderLineExt: 10,
    leaderLine: 2,
    lineCaption: true,
    captionType: PdfLineCaptionType.top,
    modifiedDate: DateTime.now());

//Adds annotation to the page
page.annotations.add(lineAnnotation);

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

### Polygon Annotation

This annotation displays a polygon on the page based on the input coordinate points. When you open it, it displays a pop-up window containing the text of the associated note.

The PdfPolygonAnnotation is used to create and set the properties of the Polygon annotation.

{% highlight dart %}

//Creates a new PDF document
PdfDocument document = PdfDocument();

//Adds a new PDF page
PdfPage page = document.pages.add();

//Creates a polygon annotation
PdfPolygonAnnotation polygonAnnotation = PdfPolygonAnnotation(
    [50, 298, 100, 325, 200, 355, 300, 230, 180, 230], 'Polygon Annotation',
    author: 'Syncfusion',
    color: PdfColor(255, 0, 0),
    innerColor: PdfColor(255, 0, 255),
    modifiedDate: DateTime.now());

//Adds annotation to the page
page.annotations.add(polygonAnnotation);

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

### Document Link Annotation

This annotation is used to navigate to a specific destination within the document.

The [`PdfDocumentLinkAnnotation`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocumentLinkAnnotation-class.html) is used to add a document link annotation in the PDF document.

{% highlight dart %}

//Creates a new PDF document
PdfDocument document = PdfDocument();

//Creates a new page
PdfPage page = document.pages.add();

//Creates a new document link annotation
PdfDocumentLinkAnnotation documentLinkAnnotation =
    PdfDocumentLinkAnnotation(Rect.fromLTWH(10, 40, 30, 30),
        PdfDestination(document.pages.add(), Offset(10, 0)));

//Adds this annotation the page.
page.annotations.add(documentLinkAnnotation);

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

### URI Annotation

The URI annotation is used to navigate to a particular web URI.

The following code example explains how to add URI annotation in a PDF document using the [`PdfUriAnnotation`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfUriAnnotation-class.html).

{% highlight dart %}

//Creates a new PDF document
PdfDocument document = PdfDocument();

//Adds a new PDF page
PdfPage page = document.pages.add();

//Creates a new URI annotation
PdfUriAnnotation uriAnnotation = PdfUriAnnotation(
    bounds: Rect.fromLTWH(10, 10, 100, 30), uri: 'http://www.google.com');

//Adds this annotation to the page.
page.annotations.add(uriAnnotation);

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

### Text Web Link Annotation

This annotation is used to navigate to a particular web URI while clicking on the link text.

The following code example explains how to add the Text Web Link annotation in a PDF document using the PdfTextWebLinkAnnotation.

{% highlight dart %}

//Creates a new PDF document
PdfDocument document = PdfDocument();

//Adds a new PDF page
PdfPage page = document.pages.add();

//Creates a new text web link annotation
PdfTextWebLink textWebLink = PdfTextWebLink(
    url: 'http://www.google.com',
    text: 'Google',
    font: PdfStandardFont(PdfFontFamily.helvetica, 10,
        style: PdfFontStyle.bold),
    brush: PdfBrushes.red,
    pen: PdfPen(PdfColor(0, 0, 255)));

//Draws the text web link to the page
textWebLink.draw(page, Offset(10, 10));

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

## Flatten annotation

Annotations can be flattened by removing the existing annotation and replacing it with the graphics objects that would resemble the annotation and it cannot be edited.

This can be achieved by enabling the flattenAllAnnotations method . Please refer to the sample for flattening all the annotations in the PDF document.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Gets all the pages
for (int i = 0; i < document.pages.count; i++) {
    
  //Loads the existing PDF page
  PdfPage page = document.pages[i];

  //Gets the annotation collection from page
  PdfAnnotationCollection annotationCollection = page.annotations;

  //Flattens all the annotations in the page
  annotationCollection.flattenAllAnnotations();
}

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

To flatten the specific annotation in the PDF document, use the following code example.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Gets all the pages
for (int i = 0; i < document.pages.count; i++) {

  //Loads the existing PDF page
  PdfPage page = document.pages[i];

  //Gets the annotation collection from the page
  PdfAnnotationCollection collection = page.annotations;

  //Gets all the annotations in the page
  for (int j = 0; j < collection.count; j++) {

    //Gets the annotation from the annotation collection
    PdfAnnotation annotation = collection[j];

    //Checks for the rectangle annotation
    if (annotation is PdfRectangleAnnotation) {
        
      //Flattens the rectangle annotation
      annotation.flatten();
    }
  }
}

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

## Modifying the annotations

The Syncfusion Flutter PDF allows you to modify the annotation of an existing document. The following code explains this.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Loads the existing PDF page
PdfPage page = document.pages[0];

//Gets the first annotation and modify the properties
PdfRectangleAnnotation annotation =
    page.annotations[0] as PdfRectangleAnnotation;
annotation.border = PdfAnnotationBorder(4);
annotation.bounds = Rect.fromLTWH(300, 300, 100, 100);
annotation.color = PdfColor(0, 0, 255);
annotation.innerColor = PdfColor(0, 255, 0);
annotation.text = 'Modified Annotation';
annotation.author = 'Syncfusion';
annotation.modifiedDate = DateTime.now();

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

## Removing annotations from an existing PDF

You can remove the annotation from the annotation collection, represented by the [`PdfAnnotationCollection`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfAnnotationCollection-class.html) of the page. The following code explains this.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Loads the existing PDF page
PdfPage page = document.pages[0];

//Gets the annotation collection from the loaded page
PdfAnnotationCollection collection = page.annotations;

//Removes the first annotation from the annotation collection
collection.remove(collection[0]);

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}
