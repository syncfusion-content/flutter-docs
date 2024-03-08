---
layout: post
title: Annotations in Flutter PDF library | Syncfusion
description: Learn here all about interactive annotations feature of Syncfusion Flutter PDF non-UI library and more.
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
    setAppearance: true,
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
    setAppearance: true,
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
    setAppearance: true,
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
    setAppearance: true,
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
    setAppearance: true,
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
    setAppearance: true,
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
    setAppearance: true,
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
    bounds: Rect.fromLTWH(10, 10, 100, 30), setAppearance: true,
     uri: 'http://www.google.com');

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
    setAppearance: true,
    pen: PdfPen(PdfColor(0, 0, 255)));

//Draws the text web link to the page
textWebLink.draw(page, Offset(10, 10));

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

### Text Markup Annotation

The PdfTextMarkupAnnotation class is used to annotate the text in a PDF document with various formats, including highlight, squiggly, strikeout, and underline. The following code demonstrates how to highlight text in a PDF document. 

{% highlight dart %}

//Create a new PDF document.
PdfDocument document = PdfDocument();
//Create a new page.
PdfPage page = document.pages.add();
//Create PDF font with font style.
PdfFont font = PdfStandardFont(PdfFontFamily.courier, 14, style: PdfFontStyle.bold);
String markupText = 'Text Markup';
//Measure the text size.
Size textSize = font.measureString(markupText);
//Draw the text.
page.graphics.drawString(markupText, font,
    brush: PdfBrushes.black, bounds: const Rect.fromLTWH(175, 40, 0, 0));
//Create a text markup annotation.
PdfTextMarkupAnnotation markupAnnotation = PdfTextMarkupAnnotation(
    Rect.fromLTWH(175, 40, textSize.width, textSize.height),
    'Markup annotation',
    PdfColor(128, 43, 226),
    author: 'Syncfusion',
    subject: 'Text Markup Annotation',
    textMarkupAnnotationType: PdfTextMarkupAnnotationType.highlight,
    modifiedDate: DateTime.now(),
    setAppearance: true);
//Add the annotation to the page.
page.annotations.add(markupAnnotation);
//Save the document.
File('output.pdf').writeAsBytes(await document.save());
//Dispose of the document.
document.dispose();

{% endhighlight %}

To add text markup annotation to an existing PDF document, use the following code example.

{% highlight dart %}

//Load the PDF document.
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());
//Create a text markup annotation.
final PdfTextMarkupAnnotation textMarkupAnnotation = PdfTextMarkupAnnotation(
    const Rect.fromLTWH(60, 165, 495, 45),
    'Text Markup Highlight',
    PdfColor(255, 255, 0),
    author: 'Syncfusion',
    subject: 'Text Markup Annotation',
    textMarkupAnnotationType: PdfTextMarkupAnnotationType.highlight,
    modifiedDate: DateTime.now());
//Add the bounds collection to highlight the text on more than one line.
textMarkupAnnotation.boundsCollection = <Rect>[
    const Rect.fromLTWH(251, 165, 304, 15),
    const Rect.fromLTWH(60, 180, 495, 15),
    const Rect.fromLTWH(60, 195, 100, 15)
];
//Add the text markup annotation to the page.
document.pages[0].annotations.add(textMarkupAnnotation);
//Save the document.
File('output.pdf').writeAsBytesSync(await document.save());
//Dispose of the document.
document.dispose();

{% endhighlight %}

### Pop-up Annotation

Pop-up annotation displays text in a pop-up window for entry and editing.

It typically does not appear alone but is associated with markup annotation, its parent annotation.

PdfPopupAnnotation is used to add pop-up annotation in a PDF document.

{% highlight dart %}

//Create a new PDF document.
PdfDocument document = PdfDocument();
//Create a new page.
PdfPage page = document.pages.add();
//Create a new popup annotation.
PdfPopupAnnotation popup = PdfPopupAnnotation(
    Rect.fromLTWH(10, 40, 30, 30), 'Popup Annotation',
    author: 'Syncfusion',
    subject: 'Popup Annotation',
    open: true,
    icon: PdfPopupIcon.comment,
    setAppearance: true);
//Add the popup annotation to the page.
page.annotations.add(popup);
//Save the document.
File('output.pdf').writeAsBytes(await document.save());
//Dispose of the document.
document.dispose();

{% endhighlight %}

To add popup annotation to an existing PDF document, use the following code example.

{% highlight dart %}

//Load the PDF document.
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());
//Create a popup annotation.
final PdfPopupAnnotation popupAnnotation = PdfPopupAnnotation(
    const Rect.fromLTWH(225, 371, 20, 20), 'Popup Annotation',
    author: 'Syncfusion',
    subject: 'Popup Annotation Comment',
    color: PdfColor(255, 255, 0),
    icon: PdfPopupIcon.comment,
    open: true,
    setAppearance: true);
//Add the popup annotation to the page.
document.pages[0].annotations.add(popupAnnotation);
//Save the document.
File('output.pdf').writeAsBytesSync(await document.save());
//Dispose of the document.
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
annotation.setAppearance: true;

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

## Annotation Flags

Annotation flags are elements added to annotations to provide additional information or interactivity. Flags associated with annotations help specify their appearance, behavior, and other properties. We can set the annotation flag using the annotationFlags property.

The following table explains annotation flags.

<table>
<thead>
<tr>
<th>
Member<br/><br/></th><th>
Meaning<br/><br/></th></tr>
</thead>
<tbody>
<tr>
<td>
invisible<br/><br/></td><td>
If set, do not display the annotation if it does not belong to one of the standard annotation types and no annotation handler is available.<br/><br/></td></tr>
<tr>
<td>
hidden<br/><br/></td><td>
If set, do not display or print the annotation, or allow the user to interact with the annotation, regardless of annotation type or annotation handler.<br/><br/></td></tr>
<tr>
<td>
print<br/><br/></td><td>
If set, print the annotation when the page is printed.<br/><br/></td></tr>
<tr>
<td>
noZoom<br/><br/></td><td>
If set, do not scale the annotation’s appearance to match the magnification of the page.<br/><br/></td></tr>
<tr>
<td>
noRotate<br/><br/></td><td>
If set, do not rotate the annotation’s appearance to match the rotation of the page.<br/><br/></td></tr>
<tr>
<td>
noView<br/><br/></td><td>
If set, do not display the annotation on the screens or allow the user to interact with the annotation.<br/><br/></td></tr>
<tr>
<td>
readOnly<br/><br/></td><td>
If set, do not allow the user to interact with annotation.<br/><br/></td></tr>
<tr>
<td>
locked<br/><br/></td><td>
If set, do not allow the annotation to be deleted or its properties to be modified by the user.<br/><br/></td></tr>
<tr>
<td>
toggleNoView<br/><br/></td><td>
If set, invert the interpretation of the noView flat for certain events.<br/><br/></td></tr>
</tbody>
</table>

The following code example illustrates how to set annotation flags in the PDF document.

{% highlight dart %}

//Create a new PDF document.
PdfDocument document = PdfDocument();
//Add new PDF page.
PdfPage page = document.pages.add();
//Create an annotation with annotation flags.
PdfRectangleAnnotation rectangleAnnotation = PdfRectangleAnnotation(
    Rect.fromLTWH(40, 70, 80, 80), 'Rectangle Annotation',
    flags: <PdfAnnotationFlags>[
      PdfAnnotationFlags.print,
      PdfAnnotationFlags.readOnly
    ],
    author: 'Syncfusion',
    subject: 'Rectangle Annotation',
    color: PdfColor(255, 0, 0),
    innerColor: PdfColor(0, 0, 255),
    border: PdfAnnotationBorder(10),
    setAppearance: true,
    modifiedDate: DateTime.now());
//Add annotation to the page.
page.annotations.add(rectangleAnnotation);
//Save the document.
File('output.pdf').writeAsBytes(await document.save());
//Dispose of the document.
document.dispose();

{% endhighlight %}

To add annotation flags to an existing annotation, use the following code example.

{% highlight dart %}

//Load the PDF document.
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());
//Get the first page.
PdfPage page = document.pages[0];
//Add annotation flags to existing annotation.
page.annotations[0].annotationFlags.addAll(<PdfAnnotationFlags>[
    PdfAnnotationFlags.print,
    PdfAnnotationFlags.readOnly
]);
//Save the document.
File('output.pdf').writeAsBytesSync(await document.save());
//Dispose of the document.
document.dispose();

{% endhighlight %}
 
## Importing annotations from FDF file

FDF stands for Forms Data Format. FDF is a file format for representing annotations present in a PDF document. You can import annotation data from the FDF file to PDF using the importAnnotation method in the PdfDocument class.

{% highlight dart %}

    //Load an existing PDF document.
    PdfDocument document =
        PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());
    //Import the annotations to FDF file format.
    document.importAnnotation(
        File('import.fdf').readAsBytesSync(), PdfAnnotationDataFormat.fdf);
    //Save the PDF document.
    File('output.pdf').writeAsBytesSync(await document.save());
    //Dispose the document.
  document.dispose();

{% endhighlight %}

## Importing annotations from XFDF file

XFDF stands for XML Forms Data Format. XFDF is the XML version of FDF for representing annotations that are contained in a PDF document. You can import annotation data from the XFDF file to PDF using the importAnnotation method in PdfDocument class.

{% highlight dart %}

    //Load an existing PDF document.
    PdfDocument document =
        PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());
    //Import the annotations to XFDF file format.
    document.importAnnotation(
        File('import.xfdf').readAsBytesSync(), PdfAnnotationDataFormat.xfdf);
    //Save the PDF document.
    File('output.pdf').writeAsBytesSync(await document.save());
    //Dispose the document.
    document.dispose();

{% endhighlight %}

## Importing annotations from JSON file

JSON stands for JavaScript Object Notation. It is a collection of key or value pairs, and it is used for serializing and transmitting the structured data over a network connection. You can import the annotation data from the JSON file to PDF using the importAnnotation method in PdfDocument class.

{% highlight dart %}

    //Load an existing PDF document.
    PdfDocument document =
        PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());
    //Import the annotations to JSON file format.
    document.importAnnotation(
        File('import.json').readAsBytesSync(), PdfAnnotationDataFormat.json);
    //Save the PDF document.
    File('output.pdf').writeAsBytesSync(await document.save());
    //Dispose the document.
    document.dispose();

{% endhighlight %}

## Exporting annotations to FDF file

To export annotation data to the FDF file from the PDF document, you can use the exportAnnotation method in PdfDocument class.

{% highlight dart %}

    //Load an existing PDF document.
    PdfDocument document =
        PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());
    //Export the annotations to FDF file format
    List<int> bytes = document.exportAnnotation(PdfAnnotationDataFormat.fdf);
    //Save the FDF file.
    File('export.fdf').writeAsBytesSync(bytes);
    //Dispose the document
Sri-hari-haran-g marked this conversation as resolved.
    document.dispose();

{% endhighlight %}

## Exporting annotations to XFDF file

To export annotation data to the XFDF file from the PDF document, you can use the exportAnnotation method in PdfDocument class.

{% highlight dart %}

    //Load an existing PDF document.
    PdfDocument document =
        PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());
    //Export the annotations to XFDF file format.
    List<int> bytes = document.exportAnnotation(PdfAnnotationDataFormat.xfdf);
    //Save the FDF file.
    File('export.xfdf').writeAsBytesSync(bytes);
    //Dispose the document.
    document.dispose();

{% endhighlight %}

## Exporting annotations to JSON file

To export annotation data to the JSON file from the PDF document, you can use the exportAnnotation method in PdfDocument class.

{% highlight dart %}

    //Load an existing PDF document.
    PdfDocument document =
        PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());
    //Export the annotations to JSON file format.
    List<int> bytes = document.exportAnnotation(PdfAnnotationDataFormat.json);
    //Save the FDF file.
    File('export.json').writeAsBytesSync(bytes);
    //Dispose the document.
    document.dispose();

{% endhighlight %}