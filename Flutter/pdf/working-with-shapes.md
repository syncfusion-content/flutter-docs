---
layout: post
title: Shapes drawing in Flutter PDF library | Syncfusion
description: Learn here all about drawing different types of Shapes feature of Syncfusion Flutter PDF non-UI library and more.
platform: flutter
control: PDF
documentation: ug
---

# Shapes Drawing in Flutter PDF

Syncfusion Flutter PDF has support for adding the following shapes:

* Polygon
* Line
* Curve
* Path
* Rectangle
* Pie
* Arc
* Bezier
* Ellipse

## Adding shapes to a PDF document

This package supports adding shapes with various color and transparency levels.

### Polygon

You can draw a polygon in PDF document by using the [`drawPolygon`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics/drawPolygon.html) method of [`PdfGraphics`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics-class.html). The following code snippet explains how to draw a polygon in the new PDF document.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Draw a polygon on PDF document
document.pages.add().graphics.drawPolygon(
    [Offset(10, 100), Offset(10, 200), Offset(100, 100), Offset(55, 150)],
    pen: PdfPens.black, brush: PdfSolidBrush(PdfColor(165, 42, 42)));

//Save the PDF document
File('Polygon.pdf').writeAsBytes(await document.save());

//Dispose the document
document.dispose();

{% endhighlight %}

### Line

You can draw a line in PDF document by using the [`drawLine`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics/drawLine.html) method of [`PdfGraphics`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics-class.html). The following code snippet explains how to draw a line in the new PDF document.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Draw a line on PDF document
document.pages.add().graphics.drawLine(
    PdfPen(PdfColor(165, 42, 42), width: 5),
    Offset(10, 100),
    Offset(10, 200));

//Save the PDF document
File('Line.pdf').writeAsBytes(await document.save());

//Dispose the document
document.dispose();

{% endhighlight %}

### Curve

You can draw a curve in PDF document by using the [`draw`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfLayoutElement/draw.html) method of [`PdfBezierCurve`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfBezierCurve-class.html). The following code snippet explains how to draw a curve in the new PDF document.

{% highlight dart %}

//Create a new PDF document
final PdfDocument document = PdfDocument();

//Create an instance of Bezier curve
final PdfBezierCurve bezier = PdfBezierCurve(
    Offset(100, 10), Offset(150, 50), Offset(50, 80), Offset(100, 10));

//Draw a Bezier curve
bezier.draw(
    page: document.pages.add(), bounds: Rect.fromLTWH(200, 100, 0, 0));

//Save the PDF document
File('Curve.pdf').writeAsBytes(await document.save());

//Dispose the document
document.dispose();

{% endhighlight %}

### Path

You can draw a path in PDF document by using the draw method of [`PdfPath`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPath-class.html). The following code snippet explains how to draw a path in the new PDF document.

{% highlight dart %}

//Create a new PDF document
final PdfDocument document = PdfDocument();

//Create an instance of the path
final PdfPath path = PdfPath();

//Add the lines to draw path
path.addLine(Offset(10, 100), Offset(10, 200));
path.addLine(Offset(100, 100), Offset(100, 200));
path.addLine(Offset(100, 200), Offset(55, 150));

//Draw the path
path.draw(page: document.pages.add(), bounds: Rect.zero);

//Save the PDF document
File('Path.pdf').writeAsBytes(await document.save());

//Dispose the document
document.dispose();

{% endhighlight %}

### Rectangle

You can draw a rectangle in PDF document by using the [`drawRectangle`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics/drawRectangle.html) method of [`PdfGraphics`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics-class.html). The following code snippet explains how to draw a rectangle in the new PDF document.

{% highlight dart %}

//Create a new PDF document
final PdfDocument document = PdfDocument();

//Draw the rectangle on PDF document
document.pages.add().graphics.drawRectangle(
    brush: PdfBrushes.chocolate, bounds: Rect.fromLTWH(10, 10, 100, 50));

//Save the PDF document
File('Rectangle.pdf').writeAsBytes(await document.save());

//Dispose the document
document.dispose();

{% endhighlight %}

### Pie

You can draw a pie in PDF document by using the [`drawPie`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics/drawPie.html) method of [`PdfGraphics`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics-class.html). The following code snippet explains how to draw a pie in the new PDF document.

{% highlight dart %}

//Create a new PDF document
final PdfDocument document = PdfDocument();

//Draw a pie on page
document.pages.add().graphics.drawPie(
    Rect.fromLTWH(10, 50, 200, 200), 90, 180,
    pen: PdfPen(PdfColor(165, 42, 42), width: 5), brush: PdfBrushes.green);

//Save the PDF document
File('Pie.pdf').writeAsBytes(await document.save());

//Dispose the document
document.dispose();

{% endhighlight %}

### Arc

You can draw an arc in PDF document by using the [`drawArc`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics-class.html) method of [`PdfGraphics`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics-class.html). The following code snippet explains how to draw an arc in the new PDF document.

{% highlight dart %}

//Create a new PDF document
final PdfDocument document = PdfDocument();

//Draw arc on page
document.pages.add().graphics.drawArc(
    Rect.fromLTWH(100, 140, 200, 400), 70, 190,
    pen: PdfPen(PdfColor(165, 42, 42), width: 5));

//Save the PDF document
File('Arc.pdf').writeAsBytes(await document.save());

//Dispose the document
document.dispose();

{% endhighlight %}

### Bezier

You can draw a bezier in PDF document by using the [`drawBezier`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics/drawBezier.html) method of [`PdfGraphics`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics-class.html). The following code snippet explains how to draw a bezier in the new PDF document.

{% highlight dart %}

//Create a new PDF document
final PdfDocument document = PdfDocument();

//Draw Bezier on page
document.pages.add().graphics.drawBezier(
    Offset(100, 10), Offset(150, 50), Offset(50, 80), Offset(100, 10),
    pen: PdfPen(PdfColor(165, 42, 42), width: 1));

//Save the PDF document
File('Bezier.pdf').writeAsBytes(await document.save());

//Dispose the document
document.dispose();

{% endhighlight %}

### Ellipse

You can draw an ellipse in PDF document by using the [`drawEllipse`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics/drawEllipse.html) method of [`PdfGraphics`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics-class.html). The following code snippet explains how to draw an ellipse in the new PDF document.

{% highlight dart %}

//Create a new PDF document
final PdfDocument document = PdfDocument();

//Draw an Ellipse on page
document.pages.add().graphics.drawEllipse(Rect.fromLTWH(10, 200, 450, 150),
    pen: PdfPen(PdfColor(165, 42, 42), width: 5),
    brush: PdfBrushes.darkOrange);

//Save the PDF document
File('Ellipse.pdf').writeAsBytes(await document.save());

//Dispose the document
document.dispose();

{% endhighlight %}
