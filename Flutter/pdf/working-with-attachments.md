---
layout: post
title: Attachments in Flutter PDF library | Syncfusion
description: Learn here all about add, remove, and load the properties of file Attachments feature of Syncfusion Flutter PDF non-UI library and more.
platform: flutter
control: PDF
documentation: ug
---

# Attachments in Flutter PDF

The Syncfusion Flutter PDF provides support for file attachments in PDF documents.

Attachments can contain any kind of file with detailed information.

## Adding an attachment to a PDF document

You can add a file attachment to a PDF document using the PdfAttachment class. The following code example shows this.

{% highlight dart %}

//Creates a new PDF document
PdfDocument document = PdfDocument();

//Create and add attachment to the PDF document
document.attachments.add(PdfAttachment(
    'input.txt', File('input.txt').readAsBytesSync(),
    description: 'Text File', mimeType: 'application/txt'));

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

You can also add file attachment as a base 64 string using the PdfAttachment class. The following code example shows this.

{% highlight dart %}

//Creates a new PDF document
PdfDocument document = PdfDocument();

//Create and add attachment to the PDF document
document.attachments.add(PdfAttachment.fromBase64String(
    'input.txt', 'SGVsbG8gV29ybGQ=',
    description: 'Text File', mimeType: 'application/txt'));

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

The Syncfusion Flutter PDF also provides support for adding the attachments to an existing PDF document. The following code example shows the same.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Create and add attachment to the PDF document
document.attachments.add(PdfAttachment(
    'input.txt', File('input.txt').readAsBytesSync(),
    description: 'Text File', mimeType: 'application/txt'));

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

## Removing attachments from an existing PDF

You can remove the attachments from the existing document by using the remove method, as shown in the following code example.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Gets the attachment from the loaded document
PdfAttachment attachment = document.attachments[0];

//Removes the attachment
document.attachments.remove(attachment);

//Removes the attachment from a specific index
document.attachments.removeAt(1);

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}

## Extracting and saving an attachment to the disc

The Syncfusion Flutter PDF provides support for extracting the attachments and saving them to the disk. The following code example explains how to extract and save an attachment.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Gets the attachment collection
PdfAttachmentCollection attachmentCollection = document.attachments;

//Iterates the attachments
for (int i = 0; i < attachmentCollection.count; i++) {
  //Extracts the attachment and saves it to the disk
  File(attachmentCollection[i].fileName)
      .writeAsBytesSync(attachmentCollection[i].data);
}

//Saves the document
File('output.pdf').writeAsBytes(await document.save());

//Disposes the document
document.dispose();

{% endhighlight %}