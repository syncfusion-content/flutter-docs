---
layout: post
title: Getting started with Flutter PDF library | Syncfusion
description: Learn here about getting started with Syncfusion Flutter PDF non-UI library, its elements, and more.
control: PDF
documentation: ug
---

# Getting started with Flutter PDF

This section explains the steps required to create a [Flutter PDF library](https://www.syncfusion.com/flutter-widgets/pdf-library) document by a single button click. This section covers only the minimal features needed to learn to get started with the PDF.

## Steps to create PDF document in Flutter application

Create a simple project using the instructions given in the [`Getting Started with your first Flutter app'](https://flutter.dev/docs/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion Flutter PDF dependency to your pub spec file.

{% highlight dart %} 

dependencies:
  syncfusion_flutter_pdf: ^xx.x.xx

{% endhighlight %}

N> Here **xx.x.xx** denotes the current version of [`Syncfusion Flutter PDF`](https://pub.dev/packages/syncfusion_flutter_pdf/versions) package.

**Get packages**

Run the following command to get the required packages.

{% highlight dart %} 

$ flutter pub get

{% endhighlight %}

**Import package**

Import the following package in your Dart code.

{% highlight dart %} 

import 'package:syncfusion_flutter_pdf/pdf.dart';

{% endhighlight %}

Add a new button widget as a child of your container widget.

{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return Scaffold(
	body: Center(
	  child: RaisedButton(
		onPressed: _createPDF,
		  child: Text('Create PDF')
		)
	 )
  );
}

{% endhighlight %}

Include the following code snippet in the button click event to create a PDF file.

{% highlight dart %}

Future<void> _createPDF() async {
  //Create a new PDF document
  PdfDocument document = PdfDocument();

  //Add a new page and draw text
  document.pages.add().graphics.drawString(
      'Hello World!', PdfStandardFont(PdfFontFamily.helvetica, 20),
      brush: PdfSolidBrush(PdfColor(0, 0, 0)),
      bounds: Rect.fromLTWH(0, 0, 500, 50));

  //Save the document
  List<int> bytes = document.save();

  //Dispose the document
  document.dispose();
}

{% endhighlight %}

## Save and open a PDF document in mobile

You can save and open a PDF document in mobile by using the following steps:

**Add dependency**

Add the following packages to your pub spec file.

{% highlight dart %} 

path_provider: ^1.6.5
open_file: ^3.0.1

{% endhighlight %}

**Import package**

{% highlight dart %}

import 'dart:io';
import 'package:open_file/open_file.dart';
import 'package:path_provider/path_provider.dart';

{% endhighlight %}

Include the following code snippet in _createPDF method to open the PDF document in mobile after saving it.

{% highlight dart %}

//Get external storage directory
final directory = await getExternalStorageDirectory();

//Get directory path
final path = directory.path;

//Create an empty file to write PDF data
File file = File('$path/Output.pdf');

//Write PDF data
await file.writeAsBytes(bytes, flush: true);

//Open the PDF document in mobile
OpenFile.open('$path/Output.pdf');

{% endhighlight %}

## Save and download a PDF document in web

You can save and download a PDF document in web by using the following steps.

**Import package**

{% highlight dart %}

import 'dart:async';
import 'dart:convert';
import 'dart:js' as js;

{% endhighlight %}

Include the following code snippet in _createPDF method to open the document in web after saving it.

{% highlight dart %}

js.context['pdfData'] = base64.encode(bytes);
js.context['filename'] = 'Output.pdf';
Timer.run(() {
  js.context.callMethod('download');
});

{% endhighlight %}

Add the following code in the header section of index.html file under the web folder.

{% highlight dart %}

<script>
    async function download() {
      var pdfAsDataUri = "data:application/pdf;base64, " + pdfData;
      var link = document.createElement('a');
      link.download = filename;
      link.href = pdfAsDataUri;
      link.type = 'application/pdf';
      link.click();
    }
</script>

{% endhighlight %}

By executing the above code sample, you will get the PDF document as follows.

![Getting started PDF](images/getting-started/default.jpg)

## Creating a PDF document with image

The following code example shows how to create a PDF document with an image.

{% highlight dart %}

//Creates a new PDF document
PdfDocument document = PdfDocument();

//Draw the image
document.pages.add().graphics.drawImage(
    PdfBitmap(File('image.jpg').readAsBytesSync()),
    Rect.fromLTWH(0, 0, 100, 100));

//Saves the document
File('Output.pdf').writeAsBytes(document.save());

//Dispose the document
document.dispose();

{% endhighlight %}

## Creating a PDF document with table

{% highlight dart %}

//Creates a new PDF document
PdfDocument document = PdfDocument();

//Create a PdfGrid
PdfGrid grid = PdfGrid();

//Add the columns to the grid
grid.columns.add(count: 3);

//Add header to the grid
grid.headers.add(1);

//Add the rows to the grid
PdfGridRow header = grid.headers[0];
header.cells[0].value = 'RollNo';
header.cells[1].value = 'Name';
header.cells[2].value = 'Class';

//Add rows to grid
PdfGridRow row = grid.rows.add();
row.cells[0].value = '1';
row.cells[1].value = 'Arya';
row.cells[2].value = '6';
row = grid.rows.add();
row.cells[0].value = '12';
row.cells[1].value = 'John';
row.cells[2].value = '9';
row = grid.rows.add();
row.cells[0].value = '42';
row.cells[1].value = 'Tony';
row.cells[2].value = '8';

//Draw grid to the page of the PDF document
grid.draw(
    page: document.pages.add(), bounds: const Rect.fromLTWH(0, 0, 0, 0));

//Saves the document
File('Output.pdf').writeAsBytes(document.save());

//Dispose the document
document.dispose();

{% endhighlight %}

## Creating a simple PDF document with basic elements

The [`PdfDocument`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocument-class.html) object represents an entire PDF document that is being created. The following code example shows how to create a PDF document and add a [`PdfPage`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPage-class.html) to it along with the [`PdfPageSettings`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPageSettings-class.html).

{% highlight dart %}

//Creates a new PDF document
PdfDocument document = PdfDocument();

//Adds page settings
document.pageSettings.orientation = PdfPageOrientation.landscape;
document.pageSettings.margins.all = 50;

//Adds a page to the document
PdfPage page = document.pages.add();
PdfGraphics graphics = page.graphics;

{% endhighlight %}

* All the units are measured in point instead of pixel.
* In PDF, all the elements are placed in absolute positions and has the possibility for content overlapping if misplaced.
* Syncfusion PDF provides the rendered bounds for each and every element added through [`PdfLayoutResult`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfLayoutResult-class.html) objects. This can be used to add successive elements and prevent content overlap.

The following code example explains how to add an image from base64 string to a PDF document, by providing the rectangle coordinates.

{% highlight dart %}

//Loads the image from base64 string
PdfImage image = PdfBitmap.fromBase64String('/9j/4AAQSkZJRgABAQEAYABgAAD/4Q');

//Draws the image to the PDF page
page.graphics.drawImage(image, Rect.fromLTWH(176, 0, 390, 130));

{% endhighlight %}

The following methods can be used to add text to a PDF document.

* [`drawString`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics/drawString.html) method of the [`PdfGraphics`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics-class.html)
* [`PdfTextElement`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfTextElement-class.html) class.

The [`PdfTextElement`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfTextElement-class.html) provides the layout result of the added text by using the location of the next element that decides to prevent content overlapping. This is not available in the [`drawString`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics/drawString.html) method.

The following code example adds the necessary text such as address, invoice number and date to create a basic invoice application.

{% highlight dart %}

PdfBrush solidBrush = PdfSolidBrush(PdfColor(126, 151, 173));
Rect bounds = Rect.fromLTWH(0, 160, graphics.clientSize.width, 30);

//Draws a rectangle to place the heading in that region
graphics.drawRectangle(brush: solidBrush, bounds: bounds);

//Creates a font for adding the heading in the page
PdfFont subHeadingFont = PdfStandardFont(PdfFontFamily.timesRoman, 14);

//Creates a text element to add the invoice number
PdfTextElement element =
    PdfTextElement(text: 'INVOICE 001', font: subHeadingFont);
element.brush = PdfBrushes.white;

//Draws the heading on the page
PdfLayoutResult result = element.draw(
    page: page, bounds: Rect.fromLTWH(10, bounds.top + 8, 0, 0))!;
String currentDate = 'DATE ' + DateFormat.yMMMd().format(DateTime.now());

//Measures the width of the text to place it in the correct location
Size textSize = subHeadingFont.measureString(currentDate);
Offset textPosition = Offset(
    graphics.clientSize.width - textSize.width - 10, result.bounds.top);

//Draws the date by using drawString method
graphics.drawString(currentDate, subHeadingFont,
    brush: element.brush,
    bounds: Offset(graphics.clientSize.width - textSize.width - 10,
            result.bounds.top) &
        Size(textSize.width + 2, 20));

//Creates text elements to add the address and draw it to the page
element = PdfTextElement(
    text: 'BILL TO ',
    font: PdfStandardFont(PdfFontFamily.timesRoman, 10,
        style: PdfFontStyle.bold));
element.brush = PdfSolidBrush(PdfColor(126, 155, 203));
result = element.draw(
    page: page, bounds: Rect.fromLTWH(10, result.bounds.bottom + 25, 0, 0))!;

PdfFont timesRoman = PdfStandardFont(PdfFontFamily.timesRoman, 10);

element = PdfTextElement(text: 'Victuailles en stock ', font: timesRoman);
element.brush = PdfBrushes.black;
result = element.draw(
    page: page, bounds: Rect.fromLTWH(10, result.bounds.bottom + 10, 0, 0))!;

element = PdfTextElement(
    text: '2, rue du Commerce, Lyon, France ', font: timesRoman);
element.brush = PdfBrushes.black;
result = element.draw(
    page: page, bounds: Rect.fromLTWH(10, result.bounds.bottom + 10, 0, 0))!;

//Draws a line at the bottom of the address
graphics.drawLine(
    PdfPen(PdfColor(126, 151, 173), width: 0.7),
    Offset(0, result.bounds.bottom + 3),
    Offset(graphics.clientSize.width, result.bounds.bottom + 3));

{% endhighlight %}

Since the invoice document requires only simple cell customizations, the given code example explains how to create a simple invoice table by using [`PdfGrid`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGrid-class.html).

{% highlight dart %}

//Creates a PDF grid
PdfGrid grid = PdfGrid();

//Add the columns to the grid
grid.columns.add(count: 5);

//Add header to the grid
grid.headers.add(1);

//Set values to the header cells
PdfGridRow header = grid.headers[0];
header.cells[0].value = 'Product Id';
header.cells[1].value = 'Product Name';
header.cells[2].value = 'Price';
header.cells[3].value = 'Quantity';
header.cells[4].value = 'Total';

//Creates the header style
PdfGridCellStyle headerStyle = PdfGridCellStyle();
headerStyle.borders.all = PdfPen(PdfColor(126, 151, 173));
headerStyle.backgroundBrush = PdfSolidBrush(PdfColor(126, 151, 173));
headerStyle.textBrush = PdfBrushes.white;
headerStyle.font = PdfStandardFont(PdfFontFamily.timesRoman, 14,
    style: PdfFontStyle.regular);

//Adds cell customizations
for (int i = 0; i < header.cells.count; i++) {
  if (i == 0 || i == 1) {
    header.cells[i].stringFormat = PdfStringFormat(
        alignment: PdfTextAlignment.left,
        lineAlignment: PdfVerticalAlignment.middle);
  } else {
    header.cells[i].stringFormat = PdfStringFormat(
        alignment: PdfTextAlignment.right,
        lineAlignment: PdfVerticalAlignment.middle);
  }
  header.cells[i].style = headerStyle;
}

//Add rows to grid
PdfGridRow row = grid.rows.add();
row.cells[0].value = 'CA-1098';
row.cells[1].value = 'AWC Logo Cap';
row.cells[2].value = '\$8.99';
row.cells[3].value = '2';
row.cells[4].value = '\$17.98';
row = grid.rows.add();
row.cells[0].value = 'LJ-0192';
row.cells[1].value = 'Long-Sleeve Logo Jersey,M';
row.cells[2].value = '\$49.99';
row.cells[3].value = '3';
row.cells[4].value = '\$149.97';
row = grid.rows.add();
row.cells[0].value = 'So-B909-M';
row.cells[1].value = 'Mountain Bike Socks,M';
row.cells[2].value = '\$9.5';
row.cells[3].value = '2';
row.cells[4].value = '\$19';
row = grid.rows.add();
row.cells[0].value = 'LJ-0192';
row.cells[1].value = 'Long-Sleeve Logo Jersey,M';
row.cells[2].value = '\$49.99';
row.cells[3].value = '4';
row.cells[4].value = '\$199.96';

//Set padding for grid cells
grid.style.cellPadding = PdfPaddings(left: 2, right: 2, top: 2, bottom: 2);

//Creates the grid cell styles
PdfGridCellStyle cellStyle = PdfGridCellStyle();
cellStyle.borders.all = PdfPens.white;
cellStyle.borders.bottom = PdfPen(PdfColor(217, 217, 217), width: 0.70);
cellStyle.font = PdfStandardFont(PdfFontFamily.timesRoman, 12);
cellStyle.textBrush = PdfSolidBrush(PdfColor(131, 130, 136));
//Adds cell customizations
for (int i = 0; i < grid.rows.count; i++) {
  PdfGridRow row = grid.rows[i];
  for (int j = 0; j < row.cells.count; j++) {
    row.cells[j].style = cellStyle;
    if (j == 0 || j == 1) {
      row.cells[j].stringFormat = PdfStringFormat(
          alignment: PdfTextAlignment.left,
          lineAlignment: PdfVerticalAlignment.middle);
    } else {
      row.cells[j].stringFormat = PdfStringFormat(
          alignment: PdfTextAlignment.right,
          lineAlignment: PdfVerticalAlignment.middle);
    }
  }
}

//Creates layout format settings to allow the table pagination
PdfLayoutFormat layoutFormat =
    PdfLayoutFormat(layoutType: PdfLayoutType.paginate);

//Draws the grid to the PDF page
PdfLayoutResult gridResult = grid.draw(
    page: page,
    bounds: Rect.fromLTWH(0, result.bounds.bottom + 20,
        graphics.clientSize.width, graphics.clientSize.height - 100),
    format: layoutFormat)!;

gridResult.page.graphics.drawString(
    'Grand Total :                             \$386.91', subHeadingFont,
    brush: PdfSolidBrush(PdfColor(126, 155, 203)),
    bounds: Rect.fromLTWH(520, gridResult.bounds.bottom + 30, 0, 0));

gridResult.page.graphics.drawString(
    'Thank you for your business !', subHeadingFont,
    brush: PdfBrushes.black,
    bounds: Rect.fromLTWH(520, gridResult.bounds.bottom + 60, 0, 0));

{% endhighlight %}

The following code example shows how to save the invoice document and dispose the [`PdfDocument`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocument-class.html) object.

{% highlight dart %}

//Saves the document
File('Output.pdf').writeAsBytes(document.save());

//Dispose the document
document.dispose();

{% endhighlight %}

The following screenshot shows the invoice PDF document created by the Syncfusion Flutter PDF.

![Invoice PDF](images/getting-started/invoice.jpg)

N> You can also explore our [Flutter PDF library](https://github.com/syncfusion/flutter-examples/tree/master/lib/samples/pdf) demo that shows how to create and modify PDF files from C# with just five lines of code.