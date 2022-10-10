---
layout: post
title: Pages in Flutter PDF library | Syncfusion
description: Learn here all about add, rotate pages and customize page settings feature of Syncfusion Flutter PDF non-UI library and more.
platform: flutter
control: PDF
documentation: ug
---

# Pages in Flutter PDF

## Adding a new page to the PDF document

The following code sample explains how to add a [`PdfPage`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPage-class.html) to a PDF document. When multiple pages are added, the new page will always be added to the end of the document.

{% highlight dart %}

//Create a new PDF documentation
PdfDocument document = PdfDocument();

//Create a new PDF page and draw the text
document.pages.add().graphics.drawString(
    'Hello World!!!', PdfStandardFont(PdfFontFamily.helvetica, 27),
    brush: PdfBrushes.darkBlue, bounds: const Rect.fromLTWH(170, 100, 0, 0));

//Save and dispose the PDF document
File('Output.pdf').writeAsBytes(await document.save());
document.dispose();
	
{% endhighlight %}

## Inserting pages in an existing document

You can insert an empty page at any location in the existing PDF document using the insert method. The following code sample explains the same.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());
  
//Inserts a new page at index 0
document.pages.insert(0);

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}


## Adding margin to the PDF pages

You can add [`margin`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPageSettings/margins.html) to all the PDF pages of a PDF document using the [`pageSettings`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocument/pageSettings.html) property. The following code snippet explains the same.

{% highlight dart %}

//Create a new PDF documentation
PdfDocument document = PdfDocument();

//Set margin for all the pages
document.pageSettings.margins.all = 200;

//Draw the text by adding page to the document
document.pages.add().graphics.drawString(
    'Hello World!!!', PdfStandardFont(PdfFontFamily.helvetica, 27),
    brush: PdfBrushes.darkBlue);

//Save and dispose the PDF document
List<int> bytes =await document.save();
document.dispose();

{% endhighlight %}

## Adding sections with different page settings

Flutter PDF supports adding sections with different page settings such as [`margins`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPageSettings/margins.html), [`orientation`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPageSettings/orientation.html), [`rotate`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPageSettings/rotate.html), [`size`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPageSettings/size.html). You can add sections to a PDF document by using the [`PdfSection`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfSection-class.html) available in [`PdfDocument`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocument-class.html) instance and create page settings to the [`PdfSection`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfSection-class.html) using the [`pageSettings`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfSection/pageSettings.html) property.

The following code snippet explains how to add more sections to a PDF document with different page settings.

{% highlight dart %}

//Create a PDF document
PdfDocument document = PdfDocument();

//Set the font
PdfFont font = PdfStandardFont(PdfFontFamily.helvetica, 14);

//Section - 1
//Add section to the document
PdfSection section = document.sections!.add();

//Create page settings to the section
section.pageSettings.rotate = PdfPageRotateAngle.rotateAngle0;
section.pageSettings.size = const Size(300, 400);

//Draw simple text on the page
section.pages.add().graphics.drawString('Rotated by 0 degrees', font,
    brush: PdfBrushes.black, bounds: const Rect.fromLTWH(20, 20, 0, 0));

//Section - 2
//Add section to the document
section = document.sections!.add();

//Create page settings to the section
section.pageSettings.rotate = PdfPageRotateAngle.rotateAngle90;
section.pageSettings.size = const Size(300, 400);

//Draw simple text on the page
section.pages.add().graphics.drawString('Rotated by 90 degrees', font,
    brush: PdfBrushes.black, bounds: const Rect.fromLTWH(20, 20, 0, 0));

//Section - 3
//Add section to the document
section = document.sections!.add();

//Create page settings to the section
section.pageSettings.rotate = PdfPageRotateAngle.rotateAngle180;
section.pageSettings.size = const Size(500, 200);

//Draw simple text on the page
section.pages.add().graphics.drawString('Rotated by 180 degrees', font,
    brush: PdfBrushes.black, bounds: const Rect.fromLTWH(20, 20, 0, 0));

//Section - 4
//Add section to the document
section = document.sections!.add();

//Create page settings to the section
section.pageSettings.rotate = PdfPageRotateAngle.rotateAngle270;
section.pageSettings.size = const Size(300, 200);

//Draw simple text on the page
section.pages.add().graphics.drawString('Rotated by 270 degrees', font,
    brush: PdfBrushes.black, bounds: const Rect.fromLTWH(20, 20, 0, 0));

//Save and dispose the PDF document
File('Output.pdf').writeAsBytes(await document.save());
document.dispose();

{% endhighlight %}

## Get the number of pages from a PDF document

You can get the page count from the existing PDF document as shown in the following code sample.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Gets the pages count
int pageCount = document.pages.count;

//Disposes the document
document.dispose();

{% endhighlight %}

## Rotating a PDF page

You can [`rotate`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPageSettings/rotate.html) a PDF page in the PDF document using the [`PdfPageRotateAngle`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPageRotateAngle.html) enum as shown in the following code snippet.

{% highlight dart %}

//Create a PDF document
PdfDocument document = PdfDocument();

//Add section to the document
PdfSection section = document.sections!.add();

//Create page settings to the section
section.pageSettings.rotate = PdfPageRotateAngle.rotateAngle180;
section.pageSettings.size = PdfPageSize.a4;

//Draw simple text on the page
section.pages.add().graphics.drawString(
    'Rotated by 180 degrees', PdfStandardFont(PdfFontFamily.helvetica, 14),
    brush: PdfBrushes.black, bounds: const Rect.fromLTWH(20, 20, 0, 0));

//Add section to the document
section = document.sections!.add();

//Create page settings to the section
section.pageSettings.rotate = PdfPageRotateAngle.rotateAngle270;
section.pageSettings.size = PdfPageSize.a4;

//Draw simple text on the page
section.pages.add().graphics.drawString(
    'Rotated by 270 degrees', PdfStandardFont(PdfFontFamily.helvetica, 14),
    brush: PdfBrushes.black, bounds: const Rect.fromLTWH(20, 20, 0, 0));

//Save and dispose the PDF document
File('Output.pdf').writeAsBytes(await document.save());
document.dispose();
	
{% endhighlight %}

## Removing pages from a document

You can remove the pages from the existing PDF document using the remove or removeAt method as shown in the following code sample.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());
 
//Gets the second page of the document
PdfPage page = document.pages[1];

//Removes the second page from the document
document.pages.remove(page);

//Removes the first page from the document
document.pages.removeAt(0);

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}
