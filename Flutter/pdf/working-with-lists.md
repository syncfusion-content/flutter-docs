---
layout: post
title: Bullets and Lists in Flutter PDF library | Syncfusion
description: Learn here all about add ordered and unordered lists feature of Syncfusion Flutter PDF non-UI library and more.
platform: flutter
control: PDF
documentation: ug
---

# Bullets and Lists in Flutter PDF

The Syncfusion Flutter PDF allows you list the content in ordered and unordered list. The ordered list can be number or alphabets and the unordered list can be bullets, circles, and images.

## Adding an ordered list

The Syncfusion Flutter PDF allows you to create an ordered list in the document. An ordered list is represented by the [`PdfOrderedList`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfOrderedList-class.html) class. The following code snippet explains the same.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Create ordered list and draw on page
PdfOrderedList(
        items: PdfListItemCollection(<String>[
          'Mammals',
          'Reptiles',
          'Birds',
          'Insects',
          'Aquatic Animals'
        ]),
        font: PdfStandardFont(PdfFontFamily.timesRoman, 20,
            style: PdfFontStyle.italic),
        indent: 20,
        format: PdfStringFormat(lineSpacing: 10))
    .draw(page: document.pages.add(), bounds: Rect.fromLTWH(0, 20, 0, 0));

//Saves the document
File('Output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();
	
{% endhighlight %}

## Adding an unordered list

The Syncfusion Flutter PDF also provides support to create an unordered list that is represented by the [`PdfUnorderedList`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfUnorderedList-class.html) class. The following code snippet explains the same.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Create unordered list and draw list on page
PdfUnorderedList(
        text: 'Mammals\nReptiles\nBirds\nInsects\nAquatic Animals',
        style: PdfUnorderedMarkerStyle.disk,
        font: PdfStandardFont(PdfFontFamily.helvetica, 12),
        indent: 10,
        textIndent: 10,
        format: PdfStringFormat(lineSpacing: 10))
    .draw(page: document.pages.add(), bounds: Rect.fromLTWH(0, 10, 0, 0));

//Saves the document
File('Output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

## Adding a sub list

The Syncfusion Flutter PDF also provides support to create a sub list to a [`PdfList`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfList-class.html). A sub list can be created under both [`PdfOrderedList`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfOrderedList-class.html) and [`PdfUnorderedList`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfUnorderedList-class.html). The following code snippet explains the same.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Adds a page to the document
PdfPage page = document.pages.add();

//Create font
PdfFont font = PdfStandardFont(PdfFontFamily.helvetica, 16);

PdfListItemCollection item = PdfListItemCollection(['Mammals', 'Reptiles']);

PdfListItemCollection item_2 = PdfListItemCollection([
  'body covered by scales',
  'cold-blooded',
  'have a backbone',
  'most lay hard-shelled eggs on land',
]);
PdfListItemCollection item_3 = PdfListItemCollection([
  'body covered by scales',
  'cold-blooded',
  'have a backbone',
  'most lay hard-shelled eggs on land'
]);

//Create a string format
PdfStringFormat format = PdfStringFormat(lineSpacing: 10);

//Create ordered list
PdfOrderedList oList =
    PdfOrderedList(items: item, font: font, format: format);

//Create ordered sub list
oList.items[0].subList = PdfOrderedList(
    items: item_2, font: font, format: format, markerHierarchy: true);

//Create ordered sub list
oList.items[1].subList = PdfOrderedList(
    items: item_3, font: font, format: format, markerHierarchy: true);

//Draw ordered list with sub list
oList.draw(
    page: page,
    bounds: Rect.fromLTWH(
        0, 10, page.getClientSize().width, page.getClientSize().height));

//Create unordered list
PdfUnorderedList uList = PdfUnorderedList(
    items: item,
    font: font,
    format: format,
    style: PdfUnorderedMarkerStyle.disk);

//Create unordered sub list
uList.items[0].subList = PdfUnorderedList(
    items: item_2,
    font: font,
    format: format,
    style: PdfUnorderedMarkerStyle.circle);

//Create unordered sub list
uList.items[1].subList = PdfUnorderedList(
    items: item_3,
    font: font,
    format: format,
    style: PdfUnorderedMarkerStyle.circle);

//Draw unordered list with sub list
uList.draw(
    page: page,
    bounds: Rect.fromLTWH(
        0, 400, page.getClientSize().width, page.getClientSize().height));

//Saves the document
File('Output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();
  
{% endhighlight %}
