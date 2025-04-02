---
layout: post
title: Document in Flutter PDF library | Syncfusion
description: Learn here all about different types of Document settings feature of Syncfusion Flutter PDF non-UI library and more.
platform: flutter
control: PDF
documentation: ug
---

# Document in Flutter PDF

## Adding the document settings

Flutter PDF supports various page setting options to control the page display, using the [`pageSettings`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocument/pageSettings.html) property of [`PdfDocument`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocument-class.html).

You can choose the standard or custom page size when you add a page to the PDF document. The following sample explains how to create a PDF document with standard page size.

{% highlight dart %}

//Create a new PDF documentation
PdfDocument document = PdfDocument();

//Set the page size
document.pageSettings.size = PdfPageSize.a4;

//Draw the text by adding page to the document
document.pages.add().graphics.drawString(
    'Hello World!!!', PdfStandardFont(PdfFontFamily.helvetica, 27),
    brush: PdfBrushes.mediumVioletRed,
    bounds: const Rect.fromLTWH(170, 100, 0, 0));

//Save and dispose the PDF document
File('Output.pdf').writeAsBytes(await document.save());
document.dispose();
	
{% endhighlight %}

You can create a PDF document with custom page size by using the following code snippet.

{% highlight dart %}

//Create a new PDF documentation
PdfDocument document = PdfDocument();

//Set the page size
document.pageSettings.size = const Size(200, 300);

//Draw the text by adding page to the document
document.pages.add().graphics.drawString(
    'Hello World!!!', PdfStandardFont(PdfFontFamily.helvetica, 19),
    brush: PdfBrushes.mediumVioletRed);

//Save and close the PDF document
File('Output.pdf').writeAsBytes(await document.save());
document.dispose();
	
{% endhighlight %}

You can change the page [`orientation`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPageSettings/orientation.html) from [`portrait`] to landscape using the [`PdfPageOrientation`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPageOrientation.html) enum by the following code snippet.

{% highlight dart %}

//Create a new PDF documentation
PdfDocument document = PdfDocument();

//Set the page size
document.pageSettings.size = PdfPageSize.a4;

//Change the page orientation to landscape
document.pageSettings.orientation = PdfPageOrientation.landscape;

//Draw the text by adding page to the document
document.pages.add().graphics.drawString(
    'Hello World!!!', PdfStandardFont(PdfFontFamily.helvetica, 27),
    brush: PdfBrushes.mediumVioletRed,
    bounds: const Rect.fromLTWH(170, 100, 0, 0));

//Save and close the PDF document
File('Output.pdf').writeAsBytes(await document.save());
document.dispose();
	
{% endhighlight %}

You can also change the [`orientation`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPageSettings/orientation.html) by setting the [`rotation angle`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPageSettings/rotate.html) using the [`PdfPageRotateAngle`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPageRotateAngle.html) enum. The following code snippet explains the same.

{% highlight dart %}

//Create a new PDF documentation
PdfDocument document = PdfDocument();

//Set the page size
document.pageSettings.size = PdfPageSize.a4;

//Change the page orientation to 90 degree
document.pageSettings.rotate = PdfPageRotateAngle.rotateAngle90;

//Draw the text by adding page to the document
document.pages.add().graphics.drawString(
    'Hello World!!!', PdfStandardFont(PdfFontFamily.helvetica, 27),
    brush: PdfBrushes.mediumVioletRed,
    bounds: const Rect.fromLTWH(170, 100, 0, 0));

//Save and close the PDF document
File('Output.pdf').writeAsBytes(await document.save());
document.dispose();
	
{% endhighlight %}

## Creating sections in a PDF

PDF [`sections`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocument/sections.html) are parts of a PDF document, which may contain one or more pages with their unique page settings. The following code snippet explains how to create a [`PdfSection`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfSection-class.html) in a PDF document.

{% highlight dart %}

//Create a new PDF documentation
PdfDocument document = PdfDocument();

//Add a section to PDF document
PdfSection section = document.sections!.add();

//Draw the text by section page graphics
section.pages.add().graphics.drawString(
    'Hello World!!!', PdfStandardFont(PdfFontFamily.helvetica, 27),
    brush: PdfBrushes.mediumVioletRed,
    bounds: const Rect.fromLTWH(170, 100, 0, 0));

//Save and close the PDF document
File('Output.pdf').writeAsBytes(await document.save());
document.dispose();
	
{% endhighlight %}

## Performing incremental update for the PDF document

The Syncfusion<sup>&reg;</sup> Flutter PDF supports incremental update for the PDF document. The content of a PDF file can be updated incrementally without rewriting the entire file. The changes are appended to the end of the file, leaving its original contents intact. The main benefit is small changes to a large PDF document can be saved quickly but the resultant document size gets increased compared with the original PDF document. Disabling the incrementalUpdate of [`PdfFileStructure`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfFileStructure-class.html) will rewrite the entire file, which results in a smaller PDF. This is explained in the following code sample.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Disable the incremental update
document.fileStructure.incrementalUpdate = false;

//Set the compression level
document.compressionLevel = PdfCompressionLevel.best;

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}
