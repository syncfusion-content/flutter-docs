---
layout: post
title: Document of Syncfusion Flutter PDF
description: Learn how to add document settings like page size, orientation and rotation in the Flutter PDF.
platform: flutter
control: PDF
documentation: ug
---

# Working with PDF Document

## Adding the document settings

Flutter PDF supports various page setting options to control the page display, using the pageSettings property of PdfDocument.

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
    File('Output.pdf').writeAsBytes(document.save());
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
    File('Output.pdf').writeAsBytes(document.save());
    document.dispose();
	
{% endhighlight %}

You can change the page orientation from portrait to landscape using the PdfPageOrientation enum by the following code snippet.

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
    File('Output.pdf').writeAsBytes(document.save());
    document.dispose();
	
{% endhighlight %}

You can also change the orientation by setting the rotation angle using the PdfPageRotateAngle enum. The following code snippet explains the same.

{% highlight dart %}

	//Create a new PDF documentation
    PdfDocument document = PdfDocument();

    //Set the page size
    document.pageSettings.size = PdfPageSize.a4;

    //Change the page orientation to 90°
    document.pageSettings.rotate = PdfPageRotateAngle.rotateAngle90;

    //Draw the text by adding page to the document
    document.pages.add().graphics.drawString(
        'Hello World!!!', PdfStandardFont(PdfFontFamily.helvetica, 27),
        brush: PdfBrushes.mediumVioletRed,
        bounds: const Rect.fromLTWH(170, 100, 0, 0));

    //Save and close the PDF document
    File('Output.pdf').writeAsBytes(document.save());
    document.dispose();
	
{% endhighlight %}

## Creating sections in a PDF

PDF sections are parts of a PDF document, which may contain one or more pages with their unique page settings. The following code snippet explains how to create a PdfSection in a PDF document.

{% highlight dart %}

	//Create a new PDF documentation
    PdfDocument document = PdfDocument();

    //Add a section to PDF document
    PdfSection section = document.sections.add();

    //Draw the text by section page graphics
    section.pages.add().graphics.drawString(
        'Hello World!!!', PdfStandardFont(PdfFontFamily.helvetica, 27),
        brush: PdfBrushes.mediumVioletRed,
        bounds: const Rect.fromLTWH(170, 100, 0, 0));

    //Save and close the PDF document
    File('Output.pdf').writeAsBytes(document.save());
    document.dispose();
	
{% endhighlight %}
