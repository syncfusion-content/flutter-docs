---
layout: post
title: Bookmarks of Syncfusion Flutter PDF
description: Learn how to add bookmarks to navigate interactively from one part of the document to another in the Flutter PDF.
platform: flutter
control: PDF
documentation: ug
---

# Working with PDF Bookmarks

The Syncfusion Flutter PDF provides support to add bookmarks to a PDF document to navigate interactively from one part of the document to another. It provides customization such as title font, color, size and more. 

## Adding bookmarks to a PDF

The PdfBookmarkBase collection represents the bookmarks in a PDF document. You can add a bookmark to a new PDF document using PdfBookmark class. Refer to the following code example.

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
File('Output.pdf').writeAsBytes(document.save());

//Dispose the document
document.dispose();
  
{% endhighlight %}

## Adding a child to the bookmarks

You can add a child bookmark by using the insert or add method. Refer to the following code example.

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
File('Output.pdf').writeAsBytes(document.save());

//Dispose the document
document.dispose();
	
{% endhighlight %}
