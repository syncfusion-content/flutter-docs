---
layout: post
title: Conformance in Flutter PDF library | Syncfusion
description: Learn here all about different types of Conformance feature of Syncfusion Flutter PDF non-UI library and more.
platform: flutter
control: PDF
documentation: ug
---

# Conformance in Flutter PDF

The Syncfusion<sup>&reg;</sup> Flutter PDF currently supports the following PDF conformances:

* PDF/A-1b conformance
* PDF/A-2b conformance
* PDF/A-3b conformance

N> To know more details about PDF/A standard refer [`https://en.wikipedia.org/wiki/PDF/A#Description`](https://en.wikipedia.org/wiki/PDF/A#Description)

## PDF/A-1b conformance

You can create a PDF/A-1b document by specifying the conformance level as a1b through PdfConformanceLevel enum when creating the new PDF document as follows.

{% highlight dart %}

//Creates a new document with the PDF/A-1b standard
PdfDocument document = PdfDocument(conformanceLevel: PdfConformanceLevel.a1b)
  ..pages.add().graphics.drawString('Hello World!',
      PdfTrueTypeFont(File('arial.ttf').readAsBytesSync(), 12),
      bounds: Rect.fromLTWH(20, 20, 200, 50));

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

## PDF/A-2b conformance

You can create a PDF/A-2b document by specifying the conformance level as a2b through PdfConformanceLevel enum when creating the new PDF document as follows.

{% highlight dart %}

//Creates a new document with the PDF/A-2b standard
PdfDocument document = PdfDocument(conformanceLevel: PdfConformanceLevel.a2b)
  ..pages.add().graphics.drawString('Hello World!',
      PdfTrueTypeFont(File('arial.ttf').readAsBytesSync(), 12),
      bounds: Rect.fromLTWH(20, 20, 200, 50));

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

## PDF/A-3b conformance

The PDF/A-3b conformance supports the external files as attachment to the PDF document, so you can attach any document format such as Excel, Word, HTML, CAD, or XML files.

You can create a PDF/A-3b document by specifying the conformance level as a3b through PdfConformanceLevel enum when creating the new PDF document as follows.

{% highlight dart %}

//Creates a new document with the PDF/A-3b standard
PdfDocument document = PdfDocument(conformanceLevel: PdfConformanceLevel.a3b)
  ..pages.add().graphics.drawString('Hello World!',
      PdfTrueTypeFont(File('arial.ttf').readAsBytesSync(), 12),
      bounds: Rect.fromLTWH(20, 20, 200, 50));

//Creates an attachment
PdfAttachment attachment = PdfAttachment(
    'input.txt', File('input.txt').readAsBytesSync(),
    description: 'Input text', mimeType: 'application/txt')
  ..relationship = PdfAttachmentRelationship.alternative
  ..modificationDate = DateTime.now();

//Adds the attachment to the document
document.attachments.add(attachment);

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}
