---
layout: post
title: Text drawing in Flutter PDF library | Syncfusion
description: Learn here all about Text extraction and find text feature of Syncfusion Flutter PDF non-UI library and more.
platform: flutter
control: PDF
documentation: ug
---

# Text Drawing in Flutter PDF

## Drawing text in PDF document

You can add text to the PDF document by using the [`drawString`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics/drawString.html) method of [`PdfGraphics`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics-class.html) class as shown in the following code sample.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Draw text
document.pages.add().graphics.drawString(
    'Hello World!!!', PdfStandardFont(PdfFontFamily.helvetica, 20),
    brush: PdfBrushes.black, bounds: Rect.fromLTWH(10, 10, 300, 50));

//Saves the document
File('Output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

## Drawing text in an existing document

The following code sample explains how to add text in the existing PDF document by using the [`drawString`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGraphics/drawString.html) method.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());
  
//Gets the first page from the document
PdfPage page = document.pages[0];

//Draw the text
page.graphics.drawString(
    'Hello World!', PdfStandardFont(PdfFontFamily.helvetica, 20),
    bounds: Rect.fromLTWH(40, 40, 500, 40));
 
//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

## Drawing text using different fonts

The Syncfusion Flutter PDF allows you to add text to the PDF document using the following types of fonts:

* Standard fonts
* TrueType fonts
* Chinese, Japanese and Korean (CJK) fonts

### Draw text using standard fonts

PDF has fourteen base fonts also known as standard fonts, which has special significance. The details can be referred from the link below.

[`Standard type 1 fonts`](https://en.wikipedia.org/wiki/PDF#Standard_Type_1_Fonts_.28Standard_14_Fonts.29)

You can add text using the standard PDF fonts, by initializing the [`PdfFont`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfFont-class.html) class as [`PdfStandardFont`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfStandardFont-class.html) class. The following code snippet explains this.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Draw text
document.pages.add().graphics.drawString(
    'Hello World!!!', PdfStandardFont(PdfFontFamily.helvetica, 16),
    brush: PdfBrushes.black, bounds: Rect.fromLTWH(10, 10, 300, 50));

//Saves the document
File('Output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

### Draw text using TrueType fonts

You can add text using the font data, by initializing [`PdfFont`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfFont-class.html) class as [`PdfTrueTypeFont`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfTrueTypeFont-class.html) class. The font data can be loaded from the disk. The font data can be initialized to [`PdfTrueTypeFont`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfTrueTypeFont-class.html) as a list of bytes or base64 string format. The following code snippet explains this.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Draw text
document.pages.add().graphics.drawString('Hello World!!!',
    PdfTrueTypeFont(File('Arial.ttf').readAsBytesSync(), 14),
    brush: PdfBrushes.black, bounds: Rect.fromLTWH(10, 10, 300, 50));

//Saves the document
File('Output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

### Draw text using CJK fonts

The Syncfusion Flutter PDF provides support to draw a CJK (Chinese, Japanese, Korean) text using some of the standard CJK fonts. The font data can be initialized by initializing [`PdfFont`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfFont-class.html) class as PDF CJK StandardFont. The following code sample explains this.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Create page and draw text
document.pages.add().graphics.drawString(
    'こんにちは世界', PdfCjkStandardFont(PdfCjkFontFamily.heiseiMinchoW3, 20),
    brush: PdfBrushes.black, bounds: Rect.fromLTWH(10, 10, 300, 50));

//Saves the document
File('Output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

## Measuring a string

The Syncfusion Flutter PDF allows you to measure the size of a string which uses the [`PdfFont`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfFont-class.html) using the [`measureString`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfFont/measureString.html) method of it and returns the size. Refer to the following code sample.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Set a standard font
PdfFont font = PdfStandardFont(PdfFontFamily.helvetica, 12);

String text = 'Hello World!!!';

//Measure the text
Size size = font.measureString(text);

//Draw text
document.pages.add().graphics.drawString(text, font,
    brush: PdfBrushes.black,
    bounds: Rect.fromLTWH(0, 0, size.width, size.height));

//Saves the document
File('Output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

## Drawing Right-To-Left text

The Syncfusion Flutter PDF allows you to draw the right-to-left language text in a PDF document. To draw RTL scripts such as Arabic, Hebrew, Persian, and Urdu, set the value of [`textDirection`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfStringFormat/textDirection.html) property in the [`PdfStringFormat`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfStringFormat-class.html) class to rightToLeft using [`PdfTextDirection`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfTextDirection-class.html) enum. The languages (e.g., Sindhi and Kurdish) that have more than one script and can be written in either right-to-left or left-to-right format. The leftToRight value of the [`textDirection`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfStringFormat/textDirection.html) property is used to draw RTL text in the left-to-right format. Refer to the following code sample.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Adds a page to the document
PdfPage page = document.pages.add();

String text =
    'سنبدأ بنظرة عامة مفاهيمية على مستند PDF بسيط. تم تصميم هذا الفصل ليكون توجيهًا مختصرًا قبل الغوص في مستند حقيقي وإنشاءه من البداية.\r\n \r\nيمكن تقسيم ملف PDF إلى أربعة أجزاء: الرأس والجسم والجدول الإسناد الترافقي والمقطورة. يضع الرأس الملف كملف PDF ، حيث يحدد النص المستند المرئي ، ويسرد جدول الإسناد الترافقي موقع كل شيء في الملف ، ويوفر المقطع الدعائي تعليمات حول كيفية بدء قراءة الملف.\r\n\r\nرأس الصفحة هو ببساطة رقم إصدار PDF وتسلسل عشوائي للبيانات الثنائية. البيانات الثنائية تمنع التطبيقات الساذجة من معالجة ملف PDF كملف نصي. سيؤدي ذلك إلى ملف تالف ، لأن ملف PDF يتكون عادةً من نص عادي وبيانات ثنائية (على سبيل المثال ، يمكن تضمين ملف خط ثنائي بشكل مباشر في ملف PDF).\r\n\r\nלאחר הכותרת והגוף מגיע טבלת הפניה המקושרת. הוא מתעדת את מיקום הבית של כל אובייקט בגוף הקובץ. זה מאפשר גישה אקראית של המסמך, ולכן בעת עיבוד דף, רק את האובייקטים הנדרשים עבור דף זה נקראים מתוך הקובץ. זה עושה מסמכי PDF הרבה יותר מהר מאשר קודמיו PostScript, אשר היה צריך לקרוא את כל הקובץ לפני עיבוד זה.';

//Draw text
page.graphics.drawString(
    text, PdfTrueTypeFont(File('Arial.ttf').readAsBytesSync(), 14),
    brush: PdfBrushes.black,
    bounds: Rect.fromLTWH(
        0, 0, page.getClientSize().width, page.getClientSize().height),
    format: PdfStringFormat(
        textDirection: PdfTextDirection.rightToLeft,
        alignment: PdfTextAlignment.right,
        paragraphIndent: 35));

//Saves the document
File('Output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();
  
{% endhighlight %}

## Creating a multicolumn PDF document

Syncfusion Flutter PDF allows you to create a multi-column text in PDF document by using [`PdfTextElement`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfTextElement-class.html) class. The following code example explains the same.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Adds a page to the document
PdfPage page = document.pages.add();

String text =
    'Adventure Works Cycles, the fictitious company on which the AdventureWorks sample databases are based, is a large, multinational manufacturing company. The company manufactures and sells metal and composite bicycles to North American, European and Asian commercial markets. While its base operation is located in Washington with 290 employees, several regional sales teams are located throughout their market base.';

//Create a text element with the text and font
//Draw the text in the first column
PdfTextElement(
        text: text, font: PdfStandardFont(PdfFontFamily.timesRoman, 14))
    .draw(
        page: page,
        bounds: Rect.fromLTWH(0, 0, page.getClientSize().width / 2,
            page.getClientSize().height / 2));

//Create a text element with the text and font
//Draw the text in second column
PdfTextElement(
        text: text, font: PdfStandardFont(PdfFontFamily.timesRoman, 14))
    .draw(
        page: page,
        bounds: Rect.fromLTWH(page.getClientSize().width / 2, 0,
            page.getClientSize().width / 2, page.getClientSize().height / 2));

//Saves the document
File('Output.pdf').writeAsBytes(await document.save());

// Disposes the document
document.dispose();

{% endhighlight %}

The [`PdfLayoutFormat`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfLayoutFormat-class.html) class helps to allow the text to flow across pages. The [`PdfLayoutResult`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfLayoutResult-class.html) class provides the rendered bounds of the previously added text, which can be used to place successive elements without overlapping.

The following code snippet explains how to add elements relatively and also allow the text to flow across multiple pages.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Adds a page to the document
PdfPage page = document.pages.add();

String text =
    'Adventure Works Cycles, the fictitious company on which the AdventureWorks sample databases are based, is a large, multinational manufacturing company. The company manufactures and sells metal and composite bicycles to North American, European and Asian commercial markets. While its base operation is located in Washington with 290 employees, several regional sales teams are located throughout their market base.';

//Create a text element with the text and font
PdfTextElement textElement = PdfTextElement(
    text: text, font: PdfStandardFont(PdfFontFamily.timesRoman, 20));

//Create layout format
PdfLayoutFormat layoutFormat = PdfLayoutFormat(
    layoutType: PdfLayoutType.paginate,
    breakType: PdfLayoutBreakType.fitPage);

//Draw the first paragraph
PdfLayoutResult result = textElement.draw(
    page: page,
    bounds: Rect.fromLTWH(0, 0, page.getClientSize().width / 2,
        page.getClientSize().height),
    format: layoutFormat)!;

//Draw the second paragraph from the first paragraph end position
textElement.draw(
    page: page,
    bounds: Rect.fromLTWH(0, result.bounds.bottom + 300,
        page.getClientSize().width / 2, page.getClientSize().height),
    format: layoutFormat);

//Saves the document
File('Output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();
	
{% endhighlight %}

## Draw text with Pens and Brushes

Pens and brushes are used to draw the content on PDF document with specific color and style.

{% highlight dart %}

//Create a new PDF document
final PdfDocument document = PdfDocument();

//Add a new page and draw text using PdfPen and PdfSolidBrush
document.pages.add().graphics.drawString(
    'Hello World!', PdfStandardFont(PdfFontFamily.helvetica, 20),
    brush: PdfSolidBrush(PdfColor(0, 0, 0)),
    pen: PdfPen(PdfColor(255, 0, 0), width : 0.5),
    bounds: const Rect.fromLTWH(0, 0, 500, 50));

//Save the document
final List<int> bytes =await document.save();

//Dispose the document
document.dispose();

{% endhighlight %}

The Syncfusion Flutter PDF has [`Pens`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPens-class.html) and [`Brushes`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfBrushes-class.html) with various built-in colors to draw the content on PDF document.