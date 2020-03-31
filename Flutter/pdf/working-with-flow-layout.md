---
layout: post
title: Flow Layout of Syncfusion Flutter PDF
description: Learn how to add image, paragraph text, header text, and a table using flow layout by maintaining the drawn positions in the Flutter PDF.
platform: flutter
control: PDF
documentation: ug
---

# Working with flow layout

The Syncfusion Flutter PDF supports creating a PDF document with flow model by maintaining the position of previously drawn element.

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
    bounds: Rect.fromLTWH(
        0, 150, page.getClientSize().width, page.getClientSize().height));

//Assign header text to PdfTextElement
textElement.text = 'Top 5 sales stores';

//Assign standard font to PdfTextElement
textElement.font =
    PdfStandardFont(PdfFontFamily.helvetica, 14, style: PdfFontStyle.bold);

//Draw the header text on page, below the paragraph text with a height gap of 20 and maintain the position in PdfLayoutResult
layoutResult = textElement.draw(
    page: page,
    bounds: Rect.fromLTWH(0, layoutResult.bounds.bottom + 20, 0, 0));

//Initialize PdfGrid for drawing the table
PdfGrid grid = PdfGrid();

//Create data table and set it as a grid source
grid.dataSource = DataTable(
  columns: [
    DataColumn(label: Text('ID')),
    DataColumn(label: Text('Name')),
    DataColumn(label: Text('Salary'))
  ],
  rows: <DataRow>[
    DataRow(cells: [
      DataCell(Text('E01')),
      DataCell(Text('Clay')),
      DataCell(Text('\$10,000'))
    ]),
    DataRow(cells: [
      DataCell(Text('E02')),
      DataCell(Text('Thomas')),
      DataCell(Text('\$10,500'))
    ]),
    DataRow(cells: [
      DataCell(Text('E02')),
      DataCell(Text('Simon')),
      DataCell(Text('\$12,000'))
    ])
  ],
);

//Draws the grid
grid.draw(
    page: page,
    bounds: Rect.fromLTWH(0, layoutResult.bounds.bottom + 20, 0, 0));

//Saves the document
File('Output.pdf').writeAsBytes(document.save());

//Disposes the document
document.dispose();

{% endhighlight %}
