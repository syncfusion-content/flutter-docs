---
layout: post
title: Flow layout in Flutter PDF library | Syncfusion
description: Learn here all about drawing images, paragraph text, header text and tables using Flow layout feature of Syncfusion Flutter non-UI PDF library and more.
platform: flutter
control: PDF
documentation: ug
---

# Flow layout in Flutter PDF

The Syncfusion<sup>&reg;</sup> Flutter PDF supports creating a PDF document with flow model by maintaining the position of previously drawn element.

## Flow model using PdfLayoutResult

The following code snippet explains how to create a PDF document with image, paragraph text, header text, and a table using flow model with the help of [`PdfLayoutResult`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfLayoutResult-class.html).

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Add a page to the document
PdfPage page = document.pages.add();

//Draw image on the page in the specified location and with required size
page.graphics.drawImage(
    PdfBitmap(File('AdventureCycle.jpg').readAsBytesSync()),
    Rect.fromLTWH(150, 30, 200, 100));

//Load the paragraph text into PdfTextElement with standard font
PdfTextElement textElement = PdfTextElement(
    text:
        'Adventure Works Cycles, the fictitious company on which the AdventureWorks sample databases are based, is a large, multinational manufacturing company. The company manufactures and sells metal and composite bicycles to North American, European and Asian commercial markets. While its base operation is located in Bothell, Washington with 290 employees, several regional sales teams are located throughout their market base.',
    font: PdfStandardFont(PdfFontFamily.helvetica, 12));

//Draw the paragraph text on page and maintain the position in PdfLayoutResult
PdfLayoutResult layoutResult = textElement.draw(
    page: page,
    bounds: Rect.fromLTWH(0, 150, page.getClientSize().width,
        page.getClientSize().height))!;

//Assign header text to PdfTextElement
textElement.text = 'Top 5 sales stores';

//Assign standard font to PdfTextElement
textElement.font = PdfStandardFont(PdfFontFamily.helvetica, 14,
    style: PdfFontStyle.bold);

//Draw the header text on page, below the paragraph text with a height gap of 20 and maintain the position in PdfLayoutResult
layoutResult = textElement.draw(
    page: page,
    bounds: Rect.fromLTWH(0, layoutResult.bounds.bottom + 20, 0, 0))!;

//Initialize PdfGrid for drawing the table
PdfGrid grid = PdfGrid();
grid.columns.add(count: 3);
grid.headers.add(1);
PdfGridRow header = grid.headers[0];
header.cells[0].value = 'ID';
header.cells[1].value = 'Name';
header.cells[2].value = 'Salary';
PdfGridRow row1 = grid.rows.add();
row1.cells[0].value = 'E01';
row1.cells[1].value = 'Clay';
row1.cells[2].value = '\$10,000';
PdfGridRow row2 = grid.rows.add();
row2.cells[0].value = 'E02';
row2.cells[1].value = 'Thomas';
row2.cells[2].value = '\$10,500';
PdfGridRow row3 = grid.rows.add();
row3.cells[0].value = 'E02';
row3.cells[1].value = 'Simon';
row3.cells[2].value = '\$12,000';

//Draws the grid
grid.draw(
    page: page,
    bounds: Rect.fromLTWH(0, layoutResult.bounds.bottom + 20, 0, 0));

//Saves the document
File('Output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}
