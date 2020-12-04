---
layout: post
title: PDF Conformance of Syncfusion Flutter PDF
description: Learn how to create a PDF conformance document specialized for uses such as archiving, long-term preservation and more using Flutter PDF.
platform: flutter
control: PDF
documentation: ug
---

# Working with PDF Conformance

The Syncfusion Flutter PDF currently supports the following PDF conformances:

* PDF/A-1b conformance
* PDF/A-2b conformance
* PDF/A-3b conformance

## PDF/A-1b conformance

The PDF/A-1b conformance is a constrained form of Adobe PDF version 1.4. It indicates minimal compliance to ensure that the rendered visual appearance of a conforming file is preservable over the long term.

You can create a PDF/A-1b document by specifying the conformance level as a1b through PdfConformanceLevel enum when creating the new PDF document as follows.

{% highlight dart %}

//Creates a new document with the PDF/A-1b standard
PdfDocument document = PdfDocument(conformanceLevel: PdfConformanceLevel.a1b);

//Adds a PDF page
PdfPage page = document.pages.add();

//Draws the text
page.graphics.drawString(
    'Hello World!', PdfTrueTypeFont(File('arial.ttf').readAsBytesSync(), 12),
    bounds: Rect.fromLTWH(20, 20, 200, 50));

//Saves the document
File('output.pdf').writeAsBytes(document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

## PDF/A-2b conformance

The PDF/A-2b conformance is a constrained form of Adobe PDF version 1.7. It indicates minimal compliance to ensure that the rendered visual appearance of a conforming file is preservable over the long term.

You can create a PDF/A-2b document by specifying the conformance level as a2b through PdfConformanceLevel enum when creating the new PDF document as follows.

{% highlight dart %}

//Creates a new document with the PDF/A-2b standard
PdfDocument document = PdfDocument(conformanceLevel: PdfConformanceLevel.a2b);

//Adds a PDF page
PdfPage page = document.pages.add();

//Draws the text
page.graphics.drawString(
    'Hello World!', PdfTrueTypeFont(File('arial.ttf').readAsBytesSync(), 12),
    bounds: Rect.fromLTWH(20, 20, 200, 50));

//Saves the document
File('output.pdf').writeAsBytes(document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

## PDF/A-3b conformance

The PDF/A-3b conformance is a constrained form of Adobe PDF version 1.7. It supports the external files as attachment to the PDF document, so you can attach any document format such as Excel, Word, HTML, CAD, or XML files.

You can create a PDF/A-3b document by specifying the conformance level as a3b through PdfConformanceLevel enum when creating the new PDF document as follows.

{% highlight dart %}

//Creates a new document with the PDF/A-3b standard
PdfDocument document = PdfDocument(conformanceLevel: PdfConformanceLevel.a3b);

//Adds a PDF page
PdfPage page = document.pages.add();

//Creates an attachment
PdfAttachment attachment = PdfAttachment(
    'input.txt', File('input.txt').readAsBytesSync(),
    description: 'Input text', mimeType: 'application/txt');
attachment.relationship = PdfAttachmentRelationship.alternative;
attachment.modificationDate = DateTime.now();

//Adds the attachment to the document
document.attachments.add(attachment);

//Draws the text
page.graphics.drawString(
    'Hello World!', PdfTrueTypeFont(File('arial.ttf').readAsBytesSync(), 12),
    bounds: Rect.fromLTWH(20, 20, 200, 50));

//Saves the document
File('output.pdf').writeAsBytes(document.save());

//Disposes the document
document.dispose();

{% endhighlight %}
