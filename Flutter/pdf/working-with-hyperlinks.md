---
layout: post
title: Hyperlinks in Flutter PDF library | Syncfusion
description: Learn here all about Hyperlinks or Web navigation feature of Syncfusion Flutter PDF non-UI library and more.
platform: flutter
control: PDF
documentation: ug
---

# Hyperlinks in Flutter PDF

In PDF, hyperlinks can be added to allow the users to navigate to another part of a PDF file and web page.

## Working with Web navigation

You can navigate to a specified URL from a PDF document by using the [`PdfTextWebLink`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfTextWebLink-class.html) class.

Refer to the following code snippet for navigating to the webpage.

{% highlight dart %}

//Create a new Pdf document
PdfDocument document = PdfDocument();

//Create and draw the web link in the PDF page
PdfTextWebLink(
        url: 'www.google.co.in',
        text: 'google',
        font: PdfStandardFont(PdfFontFamily.timesRoman, 14),
        brush: PdfSolidBrush(PdfColor(0, 0, 0)),
        pen: PdfPens.brown,
        format: PdfStringFormat(
            alignment: PdfTextAlignment.center,
            lineAlignment: PdfVerticalAlignment.middle))
    .draw(document.pages.add(), Offset(50, 40));

//Save the PDF document
File('Hyperlink.pdf').writeAsBytes(await document.save());

//Dispose document
document.dispose();

{% endhighlight %}

## Working with internal document navigation

To allow the users navigate to any other part of the same document, the [`PdfDocumentLinkAnnotation`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocumentLinkAnnotation-class.html) class can be used. 

The following code explains how to add the hyperlink for internal document navigation.

{% highlight dart %}

//Create a new Pdf document
PdfDocument document = PdfDocument();

//Create a page
PdfPage page = document.pages.add();

//Create a document link
PdfDocumentLinkAnnotation docLink = PdfDocumentLinkAnnotation(
    Rect.fromLTWH(10, 40, 30, 30),
    PdfDestination(document.pages.add(), Offset(10, 0)));

//Set the destination mode
docLink.destination!.mode = PdfDestinationMode.fitToPage;

//Add the document link to the page
page.annotations.add(docLink);

//Save the PDF document
File('Hyperlink.pdf').writeAsBytes(await document.save());

//Dispose document
document.dispose();

{% endhighlight %}