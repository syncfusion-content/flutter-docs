---
layout: post
title: Bookmarks in Flutter PDF library | Syncfusion
description: Learn here all about add, insert, and remove Bookmarks feature of Syncfusion Flutter PDF non-UI library and more.
platform: flutter
control: PDF
documentation: ug
---

# Bookmarks in Flutter PDF

The Syncfusion Flutter PDF provides support to add [`bookmarks`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocument/bookmarks.html) to a PDF document to navigate interactively from one part of the document to another. It provides customization such as title font, color, size and more. It also provides support to [`insert`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfBookmarkBase/insert.html), [`remove`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfBookmarkBase/remove.html), and modify the bookmarks in an existing PDF Document.

## Adding bookmarks to a PDF

The [`PdfBookmarkBase`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfBookmarkBase-class.html) collection represents the bookmarks in a PDF document. You can add a bookmark to a new PDF document using [`PdfBookmark`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfBookmark-class.html) class. Refer to the following code example.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Creates document bookmark
PdfBookmark bookmark = document.bookmarks.add('page 1');

//Sets the destination page and destination location
bookmark.destination = PdfDestination(document.pages.add(), Offset(100, 100));

//Sets the text style
bookmark.textStyle = [PdfTextStyle.bold];

//Sets the bookmark color(RGB)
bookmark.color = PdfColor(255, 0, 0);

//Save the document
File('Output.pdf').writeAsBytes(await document.save());

//Dispose the document
document.dispose();
  
{% endhighlight %}

## Adding a child to the bookmarks

You can add a child bookmark by using the [`insert`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfBookmarkBase/insert.html) or [`add`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfBookmarkBase/add.html) method. Refer to the following code example.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Add a page
PdfPage page = document.pages.add();

//Creates document bookmark
PdfBookmark bookmark = document.bookmarks.add('page 1');

//Inserts the child bookmark
PdfBookmark childBookmark1 = bookmark.insert(0, 'heading 1');

//Adds the child bookmark
PdfBookmark childBookmark2 = bookmark.add('heading 2');

//Sets the text style
childBookmark1.textStyle = [PdfTextStyle.bold, PdfTextStyle.italic];
childBookmark2.textStyle = [PdfTextStyle.italic];

//Sets the destination page and destination location
childBookmark1.destination = PdfDestination(page, Offset(100, 100));
childBookmark2.destination = PdfDestination(page, Offset(100, 400));

//Sets the bookmark color(RGB)
childBookmark1.color = PdfColor(0, 255, 0);
childBookmark2.color = PdfColor(0, 0, 255);

//Saves the bookmark
File('Output.pdf').writeAsBytes(await document.save());

//Dispose the document
document.dispose();
	
{% endhighlight %}

## Adding bookmarks in an existing PDF document

To add [`bookmarks`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocument/bookmarks.html) in an existing PDF document, use the following code example.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('').readAsBytesSync());

//Creates a document bookmark
PdfBookmark bookmark = document.bookmarks.add('Page 1');

//Sets the destination page and location
bookmark.destination = PdfDestination(document.pages[0], Offset(20, 20));

//Sets the bookmark color
bookmark.color = PdfColor(255, 0, 0);

//Sets the text style
bookmark.textStyle = [PdfTextStyle.bold];

//Saves the document
File('output.pdf').writeAsBytes(await document.save());
  
//Disposes the document
document.dispose();

{% endhighlight %}

## Inserting bookmarks in an existing PDF

When loading an existing document, the Syncfusion Flutter PDF loads all bookmarks of the document.

Each loaded bookmark is represented by the [`PdfBookmark`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfBookmark-class.html) object. The following code example explains how to [`insert`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfBookmarkBase/insert.html) new bookmarks in the existing PDF document.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Creates a document bookmark
PdfBookmark bookmark = document.bookmarks.insert(1, 'New Bookmark');

//Sets the destination page and location
bookmark.destination = PdfDestination(document.pages[0], Offset(40, 40));

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();
  
{% endhighlight %}

## Removing bookmarks from an existing PDF

You can also remove [`bookmarks`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocument/bookmarks.html) from the existing PDF document by using the [`remove`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfBookmarkBase/remove.html) method. Please refer to the following code example.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Gets all the bookmarks
PdfBookmarkBase bookmark = document.bookmarks;

//Removes bookmark by index
bookmark.removeAt(1);

//Removes bookmark by bookmark name
bookmark.remove('Page 1');

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

## Modifying bookmarks in an existing PDF

The Syncfusion Flutter PDF allows you to modify the [`bookmarks`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocument/bookmarks.html) in the existing PDF document. The following modifications can be done to bookmarks in an existing document.

* Modify the bookmark style, color, title, and destination.
* Add or insert new bookmarks into the root collection.
* Add or insert new bookmarks as a child of another bookmark.
* Assign the destination of the added bookmarks to a loaded page or a new page of the document.

The following code example shows how to modify the [`destination`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfBookmark/destination.html), [`color`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfBookmark/color.html), [`textStyle`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfBookmark/textStyle.html) and [`title`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfBookmark/title.html) of the existing bookmark collection.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Loads an existing PDF page
PdfPage page = document.pages[1];

//Gets all the bookmarks
PdfBookmarkBase collection = document.bookmarks;

//Gets the first bookmark and changes the properties of the bookmark
PdfBookmark bookmark = collection[0];
bookmark.color = PdfColor(0, 0, 255);
bookmark.destination = PdfDestination(page, Offset(20, 20));
bookmark.textStyle = [PdfTextStyle.italic];
bookmark.title = 'Changed Title';

//Adds a child to the existing bookmark
PdfBookmark childBookmark = bookmark.add('Child Bookmark');
childBookmark.destination = PdfDestination(page, Offset(100, 100));

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}
