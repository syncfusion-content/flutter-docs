---
layout: post
title: Tables in Flutter PDF library | Syncfusion
description: Learn here all about draw and customize cells, rows, and columns in Tables feature of Syncfusion Flutter PDF non-UI library and more.
platform: flutter
control: PDF
documentation: ug
---

# Tables in Flutter PDF

The Syncfusion Flutter PDF provides support for creating customizable tables in a PDF document by using [`PdfGrid`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGrid-class.html) table model. It is designed with advanced customization, styling, and formatting.

## Creating a table

[`PdfGrid`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGrid-class.html) allows you to create table by entering the data manually.

The following code example explains how to create a table directly using [`PdfGrid`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGrid-class.html) with [`PdfGridStyle`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGridStyle-class.html), [`PdfGridColumn`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGridColumn-class.html) and [`PdfGridRow`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGridRow-class.html) classes.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Create a PdfGrid class
PdfGrid grid = PdfGrid();

//Add the columns to the grid
grid.columns.add(count: 3);

//Add header to the grid
grid.headers.add(1);

//Add the rows to the grid
PdfGridRow header = grid.headers[0];
header.cells[0].value = 'Employee ID';
header.cells[1].value = 'Employee Name';
header.cells[2].value = 'Salary';

//Add rows to grid
PdfGridRow row = grid.rows.add();
row.cells[0].value = 'E01';
row.cells[1].value = 'Clay';
row.cells[2].value = '\$10,000';

row = grid.rows.add();
row.cells[0].value = 'E02';
row.cells[1].value = 'Simon';
row.cells[2].value = '\$12,000';

//Set the grid style
grid.style = PdfGridStyle(
    cellPadding: PdfPaddings(left: 2, right: 3, top: 4, bottom: 5),
    backgroundBrush: PdfBrushes.blue,
    textBrush: PdfBrushes.white,
    font: PdfStandardFont(PdfFontFamily.timesRoman, 25));

//Draw the grid
grid.draw(
    page: document.pages.add(), bounds: const Rect.fromLTWH(0, 0, 0, 0));

//Save and dispose the PDF document
File('SampleOutput.pdf').writeAsBytes(await document.save());
document.dispose();

{% endhighlight %}

## Cell customization in PdfGrid

[`PdfGridCell`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGridCell-class.html) provides various direct options to customize cells such as [`columnSpan`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGridCell/columnSpan.html), [`rowSpan`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGridCell/rowSpan.html), [`textPen`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGridStyleBase/textPen.html), [`backgroundBrush`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGridStyleBase/backgroundBrush.html), and more.

The following code snippet explains how to customize the cell in [`PdfGrid`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGrid-class.html).

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Create a PdfGrid
PdfGrid grid = PdfGrid();

//Add columns to grid
grid.columns.add(count: 3);

//Add headers to grid
PdfGridRow header = grid.headers.add(1)[0];
header.cells[0].value = 'Employee ID';
header.cells[1].value = 'Employee Name';
header.cells[2].value = 'Salary';

//Add the styles to specific cell
header.cells[0].style.stringFormat = PdfStringFormat(
    alignment: PdfTextAlignment.center,
    lineAlignment: PdfVerticalAlignment.bottom,
    wordSpacing: 10);
header.cells[1].style.textPen = PdfPens.mediumVioletRed;
header.cells[2].style.backgroundBrush = PdfBrushes.yellow;
header.cells[2].style.textBrush = PdfBrushes.darkOrange;

//Add rows to grid
PdfGridRow row1 = grid.rows.add();
row1.cells[0].value = 'E01';
row1.cells[1].value = 'Clay';
row1.cells[2].value = '\$10,000';

//Apply the cell style to specific row cells
row1.cells[0].style = PdfGridCellStyle(
  backgroundBrush: PdfBrushes.lightYellow,
  cellPadding: PdfPaddings(left: 2, right: 3, top: 4, bottom: 5),
  font: PdfStandardFont(PdfFontFamily.timesRoman, 17),
  textBrush: PdfBrushes.white,
  textPen: PdfPens.orange,
);

PdfGridRow row2 = grid.rows.add();
row2.cells[0].value = 'E02';
row2.cells[1].value = 'Simon';
row2.cells[2].value = '\$12,000';

//Add the style to specific cell
row2.cells[2].style.borders = PdfBorders(
    left: PdfPen(PdfColor(240, 0, 0), width: 2),
    top: PdfPen(PdfColor(0, 240, 0), width: 3),
    bottom: PdfPen(PdfColor(0, 0, 240), width: 4),
    right: PdfPen(PdfColor(240, 100, 240), width: 5));

//Draw the grid in PDF document page
grid.draw(
    page: document.pages.add(), bounds: const Rect.fromLTWH(0, 0, 0, 0));

//Save and dispose the PDF document
File('SampleOutput.pdf').writeAsBytes(await document.save());
document.dispose();

{% endhighlight %}

## Row customization in PdfGrid

You can customize row height and styles using the [`rows`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGrid/rows.html) property in [`PdfGrid`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGrid-class.html) class.

The following code snippet explains how to customize the row in [`PdfGrid`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGrid-class.html).

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Create a PdfGrid
PdfGrid grid = PdfGrid();

//Add columns to grid
grid.columns.add(count: 3);

//Add headers to grid
grid.headers.add(2);
PdfGridRow header = grid.headers[0];
header.cells[0].value = 'Employee ID';
header.cells[1].value = 'Employee Name';
header.cells[2].value = 'Salary';

//Add rows to grid
PdfGridRow row1 = grid.rows.add();
row1.cells[0].value = 'E01';
row1.cells[1].value = 'Clay';
row1.cells[2].value = '\$10,000';
PdfGridRow row2 = grid.rows.add();
row2.cells[0].value = 'E02';
row2.cells[1].value = 'Simon';
row2.cells[2].value = '\$12,000';

//Set the row span
row1.cells[1].rowSpan = 2;

//Set the row height
row2.height = 20;

//Set the row style
row1.style = PdfGridRowStyle(
    backgroundBrush: PdfBrushes.dimGray,
    textPen: PdfPens.lightGoldenrodYellow,
    textBrush: PdfBrushes.darkOrange,
    font: PdfStandardFont(PdfFontFamily.timesRoman, 12));

//Create the PDF grid row style. Assign to second row
PdfGridRowStyle rowStyle = PdfGridRowStyle(
    backgroundBrush: PdfBrushes.lightGoldenrodYellow,
    textPen: PdfPens.indianRed,
    textBrush: PdfBrushes.lightYellow,
    font: PdfStandardFont(PdfFontFamily.timesRoman, 12));
row2.style = rowStyle;

//Draw the grid in PDF document page
grid.draw(
    page: document.pages.add(), bounds: const Rect.fromLTWH(0, 0, 0, 0));

//Save and dispose the PDF document
File('SampleOutput.pdf').writeAsBytes(await document.save());
document.dispose();

{% endhighlight %}

## Columns customization in PdfGrid

You can customize the column width and text formats using the [`columns`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGrid/columns.html) property in [`PdfGrid`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGrid-class.html) class.

The following code snippet explains how to customize the column in [`PdfGrid`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGrid-class.html).

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Create a PdfGrid
PdfGrid grid = PdfGrid();

//Add columns to grid
grid.columns.add(count: 3);

//Add headers to grid
grid.headers.add(1);
PdfGridRow header = grid.headers[0];
header.cells[0].value = 'Employee ID';
header.cells[1].value = 'Employee Name';
header.cells[2].value = 'Salary';

//Add rows to grid
PdfGridRow row1 = grid.rows.add();
row1.cells[0].value = 'E01';
row1.cells[1].value = 'Clay';
row1.cells[2].value = '\$10,000';
PdfGridRow row2 = grid.rows.add();
row2.cells[0].value = 'E02';
row2.cells[1].value = 'Simon';
row2.cells[2].value = '\$12,000';

//Set the width
grid.columns[1].width = 50;
//Create and customize the string formats
PdfStringFormat format = PdfStringFormat();
format.alignment = PdfTextAlignment.center;
format.lineAlignment = PdfVerticalAlignment.bottom;

//Set the column text format
grid.columns[0].format = format;

//Draw the grid in PDF document page
grid.draw(
    page: document.pages.add(), bounds: const Rect.fromLTWH(0, 0, 0, 0));

//Save and dispose the PDF document
File('SampleOutput.pdf').writeAsBytes(await document.save());
document.dispose();

{% endhighlight %}

## Table customization in PdfGrid

Flutter PDF supports users to create a customizable PDF table like [`cellSpacing`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGridStyle/cellSpacing.html), [`cellPadding`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGridStyle/cellPadding.html), [`borderOverLapStyle`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGridStyle/borderOverlapStyle.html), and more. This can be achieved by using the [`PdfGridStyle`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGridStyle-class.html) class.

The following code snippet explains how to customize the [`PdfGrid`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGrid-class.html) using [`PdfGridStyle`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGridStyle-class.html).

{% highlight dart %}

//Create a new Pdf document
PdfDocument document = PdfDocument();

//Create a border
PdfBorders border = PdfBorders(
    left: PdfPen(PdfColor(240, 0, 0), width: 2),
    top: PdfPen(PdfColor(0, 240, 0), width: 3),
    bottom: PdfPen(PdfColor(0, 0, 240), width: 4),
    right: PdfPen(PdfColor(240, 100, 240), width: 5));

//Create a string format
PdfStringFormat format = PdfStringFormat(
    alignment: PdfTextAlignment.center,
    lineAlignment: PdfVerticalAlignment.bottom,
    wordSpacing: 10);

//Create a cell style
PdfGridCellStyle cellStyle = PdfGridCellStyle(
  backgroundBrush: PdfBrushes.lightYellow,
  borders: border,
  cellPadding: PdfPaddings(left: 2, right: 3, top: 4, bottom: 5),
  font: PdfStandardFont(PdfFontFamily.timesRoman, 17),
  format: format,
  textBrush: PdfBrushes.white,
  textPen: PdfPens.orange,
);

//Create a grid style
PdfGridStyle gridStyle = PdfGridStyle(
  cellSpacing: 2,
  cellPadding: PdfPaddings(left: 2, right: 3, top: 4, bottom: 5),
  borderOverlapStyle: PdfBorderOverlapStyle.inside,
  backgroundBrush: PdfBrushes.lightGray,
  textPen: PdfPens.black,
  textBrush: PdfBrushes.white,
  font: PdfStandardFont(PdfFontFamily.timesRoman, 17),
);

//Create a grid
PdfGrid grid = PdfGrid();

//Adds the columns to the grid
grid.columns.add(count: 3);
grid.headers.add(1);
PdfGridRow header = grid.headers[0];
header.cells[0].value = 'Employee Id';
header.cells[1].value = 'Employee name';
header.cells[2].value = 'Employee role';

//Apply the grid style
grid.rows.applyStyle(gridStyle);

//Add rows to grid. Set the cells style
PdfGridRow row1 = grid.rows.add();
row1.cells[0].value = 'E01';
row1.cells[1].value = 'Clay';
row1.cells[2].value = 'Product manager';
PdfGridRow row2 = grid.rows.add();
row2.cells[0].value = 'E02';
row2.cells[1].value = 'Thomas';
row2.cells[2].value = 'Software engineer';
PdfGridRow row3 = grid.rows.add();
row3.cells[0].value = 'E03';
row3.cells[1].value = 'Albert';
row3.cells[2].value = 'Test engineer';

//Set the row cells style
for (int i = 0; i < grid.columns.count; i++) {
  row1.cells[i].style = cellStyle;
  row2.cells[i].style = cellStyle;
  row3.cells[i].style = cellStyle;
}

//Draw the grid in PDF document page
grid.draw(
    page: document.pages.add(), bounds: const Rect.fromLTWH(0, 0, 0, 0));

//Save and dispose the PDF document
File('SampleOutput.pdf').writeAsBytes(await document.save());
document.dispose();

{% endhighlight %}

## Pagination in PdfGrid

Flutter PDF supports to paginate the [`PdfGrid`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGrid-class.html) using the [`PdfLayoutFormat`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfLayoutFormat-class.html) class.

The following sample explains how to allow [`PdfGrid`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGrid-class.html) to flow across pages.

{% highlight dart %}

//Create a new PDF documentation
PdfDocument document = PdfDocument();

//Create a PdfGrid
PdfGrid grid = PdfGrid();

//Add the columns to the grid
grid.columns.add(count: 3);
grid.headers.add(1);
PdfGridRow header = grid.headers[0];
header.cells[0].value = 'Name';
header.cells[1].value = 'Age';
header.cells[2].value = 'Sex';

//Add rows to grid. Set the cells style
PdfGridRow row1 = grid.rows.add();
row1.cells[0].value = 'Bob';
row1.cells[1].value = '22';
row1.cells[2].value = 'Male';
PdfGridRow row2 = grid.rows.add();
row2.cells[0].value = 'Sam';
row2.cells[1].value = '23';
row2.cells[2].value = 'Male';
PdfGridRow row3 = grid.rows.add();
row3.cells[0].value = 'Falitha';
row3.cells[1].value = '19';
row3.cells[2].value = 'Female';

//Create a PdfLayoutFormat for pagination
PdfLayoutFormat format = PdfLayoutFormat(
    breakType: PdfLayoutBreakType.fitColumnsToPage,
    layoutType: PdfLayoutType.paginate);

//Draw the grid in PDF document page
grid.draw(
    page: document.pages.add(),
    bounds: const Rect.fromLTWH(0, 0, 0, 0),
    format: format);

//Save and dispose the PDF document
File('SampleOutput.pdf').writeAsBytes(await document.save());
document.dispose();

{% endhighlight %}

## Adding multiple tables

The Flutter PDF supports maintaining the position of a PDF grid drawn on PDF page using [`PdfLayoutResult`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfLayoutResult-class.html). It provides the rendered bounds of previously added grid, which can be used to place successive elements without overlapping. You can add multiple PDF grids using the bottom position of previously rendered PDF grid. The following code snippet explains this.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Create a PdfGrid
PdfGrid grid = PdfGrid();

//Add the columns to the grid
grid.columns.add(count: 3);
grid.headers.add(1);
PdfGridRow header = grid.headers[0];
header.cells[0].value = 'Product Id';
header.cells[1].value = 'Product name';
header.cells[2].value = 'Price';

//Add rows to grid
PdfGridRow row1 = grid.rows.add();
row1.cells[0].value = 'P01';
row1.cells[1].value = 'Water bottle';
row1.cells[2].value = 'Rs: 100';
PdfGridRow row2 = grid.rows.add();
row2.cells[0].value = 'P02';
row2.cells[1].value = 'Trimmer';
row2.cells[2].value = 'Rs: 1200';

//Draw grid on the page of PDF document and store the grid position in PdfLayoutResult
PdfLayoutResult result = grid.draw(
    page: document.pages.add(),
    bounds: const Rect.fromLTWH(0, 0, 400, 300)) as PdfLayoutResult;

//Create a second PdfGrid in the same page
PdfGrid grid2 = PdfGrid();

//Add columns to second grid
grid2.columns.add(count: 3);
grid2.headers.add(1);
PdfGridRow header1 = grid2.headers[0];
header1.cells[0].value = 'Employee ID';
header1.cells[1].value = 'Employee Name';
header1.cells[2].value = 'Salary';

//Add rows to grid
PdfGridRow row11 = grid2.rows.add();
row11.cells[0].value = 'E01';
row11.cells[1].value = 'Clay';
row11.cells[2].value = '\$10,000';
PdfGridRow row12 = grid2.rows.add();
row12.cells[0].value = 'E02';
row12.cells[1].value = 'Simon';
row12.cells[2].value = '\$12,000';

//Draw the grid in PDF document page
grid2.draw(
    page: result.page,
    bounds: Rect.fromLTWH(0, result.bounds.bottom + 20, 400, 300));

//Save and dispose the PDF document
File('SampleOutput.pdf').writeAsBytes(await document.save());
document.dispose();

{% endhighlight %}

## Apply built-in grid style

Essential Flutter PDF supports Built-in table styles. This will help you  apply background colors and styles to your grid. This is applicable to the ['PdfGrid']('https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGrid-class.html') model, and the appearance is identical to Microsoft Word’s built-in table styles. You can also apply in-built table styles with the following additional table style options.
•	Banded columns
•	Banded rows
•	First column
•	Last column
•	Header row
•	Last row
We have various built-in styles for ['PdfGrid'](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGrid-class.html) and  some of the styles have no changes to the background color property. For example, the below listed styles do not have a background color. As the default background color is white, it is directly applied to each row in the grid. 
•	PdfGridBuiltInStyle.gridTable1Light
•	PdfGridBuiltInStyle.gridTable1LightAccent1
•	PdfGridBuiltInStyle.gridTable1LightAccent2
•	PdfGridBuiltInStyle.gridTable1LightAccent3
•	PdfGridBuiltInStyle.gridTable1LightAccent4
•	PdfGridBuiltInStyle.gridTable1LightAccent5
•	PdfGridBuiltInStyle.gridTable1LightAccent6
And we have some styles that have background color only in the header rows. Please find the below list for the same, 
•	PdfGridBuiltInStyle.listTable3
•	PdfGridBuiltInStyle.listTable3Accent1
•	PdfGridBuiltInStyle.listTable3Accent2
•	PdfGridBuiltInStyle.listTable3Accent3
•	PdfGridBuiltInStyle.listTable3Accent4
•	PdfGridBuiltInStyle.listTable3Accent5
•	PdfGridBuiltInStyle.listTable3Accent6

N>  We can also customize the background color of the ['PdfGrid'](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGrid-class.html) by using the PdfGrid.style.backgroundBrush, PdfGridRow.style.backgroundBrush and PdfGridCell.style.backgroundBrush properties. Please note that the changes in the above properties are not considered, when we apply the ['PdfGridBuiltInStyle'](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGridBuiltInStyle.html) . 
The below code example illustrates how to apply a built-in table style using the ['applyBuiltInStyle'](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGrid/applyBuiltInStyle.html ) method of the PdfGrid with styles from the ['PdfGridBuiltInStyle'](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGridBuiltInStyle.html) Enum.

{% highlight dart %}
//Create a new PDF document.
PdfDocument document = PdfDocument();
//Create a PdfGrid class.
PdfGrid grid = PdfGrid();
//Add columns to the grid.
grid.columns.add(count: 3);
//Add a header to the grid.
grid.headers.add(1);
//Add rows to the grid.
PdfGridRow header = grid.headers[0];
header.cells[0].value = 'Employee ID';
header.cells[1].value = 'Employee Name';
header.cells[2].value = 'Salary';
//Add rows to the grid.
PdfGridRow row = grid.rows.add();
row.cells[0].value = 'E01';
row.cells[1].value = 'Clay';
row.cells[2].value = '\$10,000';
row = grid.rows.add();
row.cells[0].value = 'E02';
row.cells[1].value = 'Simon';
row.cells[2].value = '\$12,000';
PdfGridBuiltInStyleSettings tableStyleOption =  PdfGridBuiltInStyleSettings();
tableStyleOption.applyStyleForBandedRows = true;
tableStyleOption.applyStyleForHeaderRow = true;
//Apply built-in table style.
grid.applyBuiltInStyle(PdfGridBuiltInStyle.listTable6ColorfulAccent1,
    settings: tableStyleOption);
//Draw the grid.
grid.draw(
    page: document.pages.add(), bounds: const Rect.fromLTWH(10, 10, 0, 0));
//Save the document.
List<int> bytes =await document.save();
//Dispose the document.
document.dispose();

{% endhighlight %}
