---
layout: post
title: Security in Flutter PDF library | Syncfusion
description: Learn here all about add encryption and set permission by Security feature of Syncfusion Flutter PDF non-UI library and more.
platform: flutter
control: PDF
documentation: ug
---

# Security in Flutter PDF

Flutter PDF allows you to protect the PDF document using encryption and set permission to the PDF document operations like printing, editing, copy content etc. using user password and owner password. Two types of encryption algorithms are available

* Rivest Cipher 4 (RC4)
* Advanced Encryption Standard (AES)

## Working with RC4 Encryption

You can encrypt PDF document using RC4 algorithm with 40bit or 128bit key size. The following code snippet illustrates how to encrypt the PDF document with the [`userPassword`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfSecurity/userPassword.html).

User password: Prevents people from opening or viewing a PDF document. Once the User Password is set, to open the PDF document, Adobe Acrobat/Reader will prompt a user to enter this password. If it is not correct, the document will not open. By setting a PDF User password, you can secure the PDF document.

{% highlight dart %}

//Create a new PDF documentation
PdfDocument document = PdfDocument();

//Document security
PdfSecurity security = document.security;

//Specifies encryption algorithm and key size
security.algorithm = PdfEncryptionAlgorithm.rc4x128Bit;

//Set user password
security.userPassword = 'password';

//Draw the text by adding page to the document
document.pages.add().graphics.drawString(
    'Encrypted with RC4 128bit', PdfStandardFont(PdfFontFamily.helvetica, 27),
    brush: PdfBrushes.mediumVioletRed,
    bounds: const Rect.fromLTWH(10, 10, 500, 50));

//Save and dispose the PDF document
File('Output.pdf').writeAsBytes(await document.save());
document.dispose();

{% endhighlight %}

N> While using both user and owner passwords, please specify different user and owner password while encrypting the PDF document for better security.

You can protect the PDF document from printing, editing, copying with the [`ownerPassword`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfSecurity/ownerPassword.html) by using the following code snippet.

Owner password: Sets PDF document restrictions, which can include printing, content copying, editing, page extracting, commenting, and more. Once the owner password is set, Acrobat will require this password to make any changes to the PDF document. It further secures the PDF document to set a PDF Owner Password.

{% highlight dart %}

//Create a new PDF documentation
PdfDocument document = PdfDocument();

//Document security
PdfSecurity security = document.security;

//Specifies encryption algorithm and key size
security.algorithm = PdfEncryptionAlgorithm.rc4x128Bit;

//Set owner password
security.ownerPassword = 'password';

//It allows printing and accessibility copy content
security.permissions.addAll(<PdfPermissionsFlags>[
    PdfPermissionsFlags.print,
    PdfPermissionsFlags.accessibilityCopyContent
]);

//Draw the text by adding page to the document
document.pages.add().graphics.drawString(
    'This document is protected with owner password',
    PdfStandardFont(PdfFontFamily.helvetica, 27),
    brush: PdfBrushes.mediumVioletRed,
    bounds: const Rect.fromLTWH(10, 10, 500, 50));

//Save and dispose the PDF document
File('Output.pdf').writeAsBytes(await document.save());
document.dispose();

{% endhighlight %}

## Working with AES Encryption

You can encrypt PDF document using AES algorithm with 128bit or 256bit or 256bit Revision 6 key size. The following code snippet illustrates how to encrypt the PDF document with the [`userPassword`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfSecurity/userPassword.html).

{% highlight dart %}

//Create a new PDF documentation
PdfDocument document = PdfDocument();

//Document security
PdfSecurity security = document.security;

//Specifies encryption algorithm and key size
security.algorithm = PdfEncryptionAlgorithm.aesx256Bit;

//Set user password
security.userPassword = 'password';

//Draw the text by adding page to the document
document.pages.add().graphics.drawString(
    'Encrypted with AES 256bit', PdfStandardFont(PdfFontFamily.helvetica, 27),
    brush: PdfBrushes.mediumVioletRed,
    bounds: const Rect.fromLTWH(10, 10, 500, 50));

//Save and dispose the PDF document
File('Output.pdf').writeAsBytes(await document.save());
document.dispose();

{% endhighlight %}

You can protect the PDF document from printing, editing, copying with the [`ownerPassword`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfSecurity/ownerPassword.html) by using the following code snippet.

{% highlight dart %}

//Create a new PDF document
PdfDocument document = PdfDocument();

//Document security
PdfSecurity security = document.security;

//Specifies encryption algorithm and key size
security.algorithm = PdfEncryptionAlgorithm.aesx256Bit;

//Set owner password
security.ownerPassword = 'password';

//It allows printing and accessibility copy content
security.permissions.addAll(<PdfPermissionsFlags>[
    PdfPermissionsFlags.print,
    PdfPermissionsFlags.accessibilityCopyContent]);

//Draw the text by adding page to the document
document.pages.add().graphics.drawString(
    'This document is protected with owner password',
    PdfStandardFont(PdfFontFamily.helvetica, 27),
    brush: PdfBrushes.mediumVioletRed,
    bounds: const Rect.fromLTWH(10, 10, 500, 50));

//Save and dispose the PDF document
File('Output.pdf').writeAsBytes(await document.save());
document.dispose();

{% endhighlight %}

## Protect an existing document

You can protect an existing PDF document with both [`userPassword`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfSecurity/userPassword.html) and [`ownerPassword`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfSecurity/ownerPassword.html) by using the following code snippet.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Document security
PdfSecurity security = document.security;

//Specifies encryption algorithm and key size
security.algorithm = PdfEncryptionAlgorithm.aesx256Bit;

//Set owner and user password
security.ownerPassword = 'ownerPassword';
security.userPassword = 'userPassword';

//Save and dispose the PDF document
File('Output.pdf').writeAsBytes(await document.save());
document.dispose();

{% endhighlight %}

## Changing the password of the PDF document

You can change the [`userPassword`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfSecurity/userPassword.html) of the existing PDF document by using following code snippet.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document = PdfDocument(
    inputBytes: File('input.pdf').readAsBytesSync(), password: 'password');

//Change the user password
document.security.userPassword = 'NewPassword';

//Save and dispose the PDF document
File('Output.pdf').writeAsBytes(await document.save());
document.dispose();

{% endhighlight %}

## Remove password from the user password PDF document

You can remove the [`userPassword`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfSecurity/userPassword.html) from the encrypted PDF document by using the following code snippet.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document = PdfDocument(
    inputBytes: File('input.pdf').readAsBytesSync(), password: 'password');

//Change the user password as empty string
document.security.userPassword = '';

//Save and dispose the PDF document
File('Output.pdf').writeAsBytes(await document.save());
document.dispose();

{% endhighlight %}

## Change the permission of the PDF document

You can change the permission of the PDF document using the [`permissions`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPermissions-class.html). The following code snippet illustrates the same.

{% highlight dart %}

//Loads an existing PDF document
PdfDocument document = PdfDocument(
    inputBytes: File('input.pdf').readAsBytesSync(), password: 'password');

//Remove the permissions
document.security.permissions.remove(PdfPermissionsFlags.print);

//Add the new permissions
document.security.permissions.addAll(<PdfPermissionsFlags>[
    PdfPermissionsFlags.editContent,
    PdfPermissionsFlags.copyContent,
    PdfPermissionsFlags.editAnnotations,
    PdfPermissionsFlags.fillFields,
    PdfPermissionsFlags.assembleDocument,
    PdfPermissionsFlags.fullQualityPrint]);

//Save and dispose the PDF document
File('Output.pdf').writeAsBytes(await document.save());
document.dispose();

{% endhighlight %}

## How to determine whether the PDF document is protected by user or owner password?

Flutter PDF supports identifying the document whether it is protected by user or owner.

The following table shows the various combination for loading the secured document with user or owner password:

<table>
<thead>
<tr>
<th>
Document type
</th>
<th>
Open with
</th>
<th>
User password
</th>
<th>
Owner password
</th>
</tr>
</thead>
<tbody>
<tr>
<td>
PDF document secured with both the owner and user passwords
</td>
<td>
User password
</td>
<td>
Returns user password
</td>
<td>
Returns empty string
</td>
</tr>
<tr>
<td>
PDF document secured with both the owner and user passwords
</td>
<td>
Owner password
</td>
<td>
Returns user password (Returns null for AES 256 and AES 256 Revision 6 encryptions)
</td>
<td>
Returns owner password
</td>
</tr>
<tr>
<td>
PDF document secured with owner password alone
</td>
<td>
Owner password
</td>
<td>
Returns empty string
</td>
<td>
Returns owner password
</td>
</tr>
<tr>
<td>
PDF document secured with user password alone
</td>
<td>
User Password
</td>
<td>
Returns user password
</td>
<td>
Returns owner Password (owner password is same as the user password; it allows full permission to users)
</td>
</tr>
</tbody>
</table>
