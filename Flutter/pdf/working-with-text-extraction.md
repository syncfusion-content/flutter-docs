---
layout: post
title: Text extraction in Flutter PDF library | Syncfusion
description: Learn here all about different types of fonts and draw Text feature of Syncfusion Flutter PDF non-UI library and more.
platform: flutter
control: PDF
documentation: ug
---

# Text Extraction in Flutter PDF

The Syncfusion<sup>&reg;</sup> Flutter PDF allows you to extract or find the text from a particular page or the entire PDF document.

## Working with the basic text extraction

You can extract the text from pages using the extractText method in the PdfTextExtractor class.

The following code explains how to extract the text from the entire PDF document:

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Extracts the text from all the pages
String text = PdfTextExtractor(document).extractText();
  
//Dispose the document
document.dispose();

{% endhighlight %}

The following code sample explains how to extract the texts from a  specific page:

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Extracts the text from page 1
String text = PdfTextExtractor(document).extractText(startPageIndex: 0);

//Dispose the document
document.dispose();

{% endhighlight %}

The following code sample explains how to extract the texts from a particular page range:

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Extracts the text from pages 1 to 3
String text = PdfTextExtractor(document)
    .extractText(startPageIndex: 0, endPageIndex: 2);

//Dispose the document
document.dispose();

{% endhighlight %}

## Text Extraction with Bounds

### Working with Lines

You can get the line and its properties that contains texts by using the TextLine. Refer to the following code sample.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Extracts the text line collection from the document
final List<TextLine> textLine =
    PdfTextExtractor(document).extractTextLines();

//Gets specific line from the collection
TextLine line = textLine[0];

//Gets bounds of the line
Rect bounds = line.bounds;

//Gets font name of the line
String fontName = line.fontName;

//Gets size of the line
double fontSize = line.fontSize;

//Gets font style of the line
List<PdfFontStyle> fontStyle = line.fontStyle;

//Gets text in the line
String text = line.text;

//Gets a collection of the words in the line
List<TextWord> textWordCollection = line.wordCollection;

//Dispose the document
document.dispose();

{% endhighlight %}

### Working with words

You can get a single word and its properties by using the TextWord. Refer to the following code sample.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Extracts the text line collection from the page 2
final List<TextLine> textLine =
    PdfTextExtractor(document).extractTextLines(startPageIndex: 1);

//Gets the specific line from the collection
TextLine line = textLine[0];

//Gets a collection of the words in the line
List<TextWord> textWordCollection = line.wordCollection;

//Gets word from the collection using index
TextWord textWord = textWordCollection[0];

//Gets bounds of the word
Rect wordBounds = textWord.bounds;

//Gets font name of the word
String wordFontName = textWord.fontName;

//Gets size of the word
double wordFontSize = textWord.fontSize;

//Gets font style of the word
List<PdfFontStyle> wordFontStyle = textWord.fontStyle;

//Gets the word
String wordText = textWord.text;

//Gets Glyph details of the word
List<TextGlyph> textGlyphCollection = textWord.glyphs;

//Dispose the document
document.dispose();

{% endhighlight %}

### Working with characters

You can get a single character and its properties by using the TextGlyph. Refer to the following code sample.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Extracts the text line collection from the pages 2 to 3
final List<TextLine> textLine = PdfTextExtractor(document)
    .extractTextLines(startPageIndex: 1, endPageIndex: 2);

//Gets the specific line from the collection
TextLine line = textLine[0];

//Gets a collection of the words in the line
List<TextWord> textWordCollection = line.wordCollection;

//Gets word from the collection using index
TextWord textWord = textWordCollection[0];

//Gets Glyph details of the word
List<TextGlyph> textGlyphCollection = textWord.glyphs;

//Gets character of the word
TextGlyph textGlyph = textGlyphCollection[0];

//Gets bounds of the character
Rect glyphBounds = textGlyph.bounds;

//Gets font name of the character
String glyphFontName = textGlyph.fontName;

//Gets font size of the character
double glyphFontSize = textGlyph.fontSize;

//Gets font style of the character
List<PdfFontStyle> glyphFontStyle = textGlyph.fontStyle;

//Gets character in the word
String glyphText = textGlyph.text;

//Dispose the document
document.dispose();

{% endhighlight %}

## Working with find text

You can find a collection of text from pages using the findText method in the PdfTextExtractor class. You can get the text and its properties using the MatchedItem.

The following code sample explains how to find the text from an entire PDF document:

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Find the text and get matched items
List<MatchedItem> textCollection =
    PdfTextExtractor(document).findText(['text1', 'text2']);
 
//Gets the matched item in the collection using index
MatchedItem matchedText = textCollection[0];

//Gets the text bounds
Rect textBounds = matchedText.bounds;
  
//Gets the page index
int pageIndex = matchedText.pageIndex;
 
//Gets the text
String text = matchedText.text;

//Dispose the document
document.dispose();

{% endhighlight %}

The following code sample explains how to find the text from a specific page.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Find the text and get matched items from the page 1
List<MatchedItem> textCollection = PdfTextExtractor(document)
    .findText(['text1', 'text2'], startPageIndex: 0);

//Dispose the document
document.dispose();

{% endhighlight %}

The TextSearchOption is used to specify the option for text search. The following code snippet explains how to find text using the search option from a particular page range.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Find the text and get matched items from the pages 1 to 3
List<MatchedItem> textCollection = PdfTextExtractor(document).findText(
    ['text1', 'text2'],
    startPageIndex: 0,
    endPageIndex: 2,
    searchOption: TextSearchOption.caseSensitive);

//Dispose the document
document.dispose();

{% endhighlight %}
