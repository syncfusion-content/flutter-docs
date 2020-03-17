---
layout: post
title: Pages of Syncfusion Flutter PDF
description: Learn how to add, rotate pages and customize page settings based on PDF sections in the Flutter PDF.
platform: flutter
control: PDF
documentation: ug
---

# Working with PDF Pages

## Adding a new page to the PDF document

The following code sample explains how to add a PdfPage to a PDF document. When multiple pages are added, the new page will always be added to the end of the document.

{% highlight dart %}

//Create a new PDF documentation
PdfDocument document = PdfDocument();

//Create a new PDF page and draw the text
document.pages.add().graphics.drawString(
  'Hello World!!!', PdfStandardFont(PdfFontFamily.helvetica, 27),
  brush: PdfBrushes.darkBlue, bounds: const Rect.fromLTWH(170, 100, 0, 0));

//Save and dispose the PDF document
File('Output.pdf').writeAsBytes(document.save());
document.dispose();
	
{% endhighlight %}

## Adding margin to the PDF pages

You can add margin to all the PDF pages of a PDF document using the pageSettings property. The following code snippet explains the same.

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
List<int> bytes = document.save();
document.dispose();

{% endhighlight %}

## Adding sections with different page settings

Flutter PDF supports adding sections with different page settings such as margins, orientation, rotate, size. You can add sections to a PDF document by using the PdfSection available in PdfDocument instance and create page settings to the PdfSection using the PageSettings property.

The following code snippet explains how to add more sections to a PDF document with different page settings.

{% highlight dart %}

//Create a PDF document
PdfDocument document = PdfDocument();

//Set the font
PdfFont font = PdfStandardFont(PdfFontFamily.helvetica, 14);

//Section - 1
//Add section to the document
PdfSection section = document.sections.add();

//Create page settings to the section
section.pageSettings.rotate = PdfPageRotateAngle.rotateAngle0;
section.pageSettings.size = const Size(300, 400);

//Draw simple text on the page
section.pages.add().graphics.drawString('Rotated by 0 degrees', font,
	brush: PdfBrushes.black, bounds: const Rect.fromLTWH(20, 20, 0, 0));

//Section - 2
//Add section to the document
section = document.sections.add();

//Create page settings to the section
section.pageSettings.rotate = PdfPageRotateAngle.rotateAngle90;
section.pageSettings.size = const Size(300, 400);

//Draw simple text on the page
section.pages.add().graphics.drawString('Rotated by 90 degrees', font,
	brush: PdfBrushes.black, bounds: const Rect.fromLTWH(20, 20, 0, 0));

//Section - 3
//Add section to the document
section = document.sections.add();

//Create page settings to the section
section.pageSettings.rotate = PdfPageRotateAngle.rotateAngle180;
section.pageSettings.size = const Size(500, 200);

//Draw simple text on the page
section.pages.add().graphics.drawString('Rotated by 180 degrees', font,
	brush: PdfBrushes.black, bounds: const Rect.fromLTWH(20, 20, 0, 0));

//Section - 4
//Add section to the document
section = document.sections.add();

//Create page settings to the section
section.pageSettings.rotate = PdfPageRotateAngle.rotateAngle270;
section.pageSettings.size = const Size(300, 200);

//Draw simple text on the page
section.pages.add().graphics.drawString('Rotated by 270 degrees', font,
	brush: PdfBrushes.black, bounds: const Rect.fromLTWH(20, 20, 0, 0));

//Save and dispose the PDF document
File('Output.pdf').writeAsBytes(document.save());
document.dispose();

{% endhighlight %}

## Rotating a PDF page

You can rotate a PDF page in the PDF document using the PdfPageRotateAngle enum as shown in the following code snippet.

{% highlight dart %}

//Create a PDF document
PdfDocument document = PdfDocument();

//Add section to the document
PdfSection section = document.sections.add();

//Create page settings to the section
section.pageSettings.rotate = PdfPageRotateAngle.rotateAngle180;
section.pageSettings.size = PdfPageSize.a4;

//Draw simple text on the page
section.pages.add().graphics.drawString(
	'Rotated by 180 degrees', PdfStandardFont(PdfFontFamily.helvetica, 14),
	brush: PdfBrushes.black, bounds: const Rect.fromLTWH(20, 20, 0, 0));

//Add section to the document
section = document.sections.add();

//Create page settings to the section
section.pageSettings.rotate = PdfPageRotateAngle.rotateAngle270;
section.pageSettings.size = PdfPageSize.a4;

//Draw simple text on the page
section.pages.add().graphics.drawString(
	'Rotated by 270 degrees', PdfStandardFont(PdfFontFamily.helvetica, 14),
	brush: PdfBrushes.black, bounds: const Rect.fromLTWH(20, 20, 0, 0));

//Save and dispose the PDF document
File('Output.pdf').writeAsBytes(document.save());
document.dispose();
	
{% endhighlight %}
