---
layout: post
title: Digital Signature in Flutter PDF library | Syncfusion
description: Learn here all about internal and external Digital Signature feature of Syncfusion Flutter PDF non-UI library and more.
platform: flutter
control: PDF
documentation: ug
---

# Digital Signature in Flutter PDF

Flutter PDF allows you to add a digital signature to the PDF document. You can sign the PDF document internally by using a certificate with private keys or externally by using the digital signature created from various sources such as cloud services like DigitalSign.

## Adding a digital signature

To add a digital signature, you need a certificate with private keys. The following code example explains how to add a digital signature to the PDF document.

{% highlight dart %}

//Creates a new PDF document
PdfDocument document = PdfDocument();

//Adds a new page
PdfPage page = document.pages.add();

//Creates a digital signature and sets signature information
PdfSignatureField field = PdfSignatureField(page, 'signature',
    bounds: Rect.fromLTWH(0, 0, 200, 100),
    signature: PdfSignature(
        //Creates a certificate instance from the PFX file with a private key
        certificate:
            PdfCertificate(File('PDF.pfx').readAsBytesSync(), 'password123'),
        contactInfo: 'johndoe@owned.us',
        locationInfo: 'Honolulu, Hawaii',
        reason: 'I am author of this document.',
        digestAlgorithm: DigestAlgorithm.sha256,
        cryptographicStandard: CryptographicStandard.cms));

//Add a signature field to the form
document.form.fields.add(field);

//Save and dispose the PDF document
File('Output.pdf').writeAsBytes(await document.save());
document.dispose();

{% endhighlight %}

## Signing an existing document

You can load the signature field from the existing PDF document and add a certificate to the document as follows,

{% highlight dart %}

//Loads an existing PDF document.
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Gets the first signature field of the PDF document.
PdfSignatureField field = document.form.fields[0] as PdfSignatureField;

//Creates a digital signature and sets the signature information.
field.signature = PdfSignature(
    //Creates a certificate instance from the PFX file with a private key.
    certificate:
        PdfCertificate(File('PDF.pfx').readAsBytesSync(), 'password123'),
    contactInfo: 'johndoe@owned.us',
    locationInfo: 'Honolulu, Hawaii',
    reason: 'I am author of this document.',
    digestAlgorithm: DigestAlgorithm.sha512,
    cryptographicStandard: CryptographicStandard.cades);

//Save and dispose the PDF document.
File('Output.pdf').writeAsBytes(await document.save());
document.dispose();

{% endhighlight %}

## Adding a signature appearance

You can customize the appearance of the signature field by using the [`appearance`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfSignatureField/appearance.html) property in [`PdfSignatureField`](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfSignatureField-class.html) as follows,

{% highlight dart %}

//Loads an existing PDF document.
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Gets the first signature field of the PDF document.
PdfSignatureField field = document.form.fields[0] as PdfSignatureField;

//Creates a digital signature.
field.signature = PdfSignature(
    //Creates a certificate instance from the PFX file with a private key.
    certificate:
        PdfCertificate(File('PDF.pfx').readAsBytesSync(), 'password123'));

//Gets the signature field appearance graphics.
PdfGraphics graphics = field.appearance.normal.graphics;

//Draws the signature image.
graphics!.drawImage(
    PdfBitmap(File('image.jpg').readAsBytesSync()), Rect.fromLTWH(0, 0, field.bounds.width, field.bounds.height));

//Save and dispose the PDF document.
File('Output.pdf').writeAsBytes(await document.save());
document.dispose();

{% endhighlight %}

## Externally sign a PDF document

You can sign the PDF document from an external digital signature created from various sources such as cloud services like DigitalSign.

The following code example shows how to sign the PDF document from an external signature.

{% highlight dart %}

//Loads an existing PDF document.
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Gets the first signature field of the PDF document.
PdfSignatureField field = document.form.fields[0] as PdfSignatureField;

//Creates a digital signature.
field.signature = PdfSignature()
    ..addExternalSigner(
        //Creates an external signer.
        PdfExternalSigner(),
        //Loads a public certificate to generate message digest for signing.
        [File('certificate.cer').readAsBytesSync()]);

//Save and dispose the PDF document.
File('Output.pdf').writeAsBytes(await document.save());
document.dispose();

{% endhighlight %}

You can create an external digital signature with the [`x509`](https://pub.dev/packages/x509) package by using the following steps:

**Add dependency**

Add this to your package's pubspec.yaml file.

{% highlight dart %}

dependencies:
  x509: ^0.1.4

{% endhighlight %}

**Import package**

{% highlight dart %}

import 'package:x509/x509.dart' as x509;

{% endhighlight %}

You can compute the signed message digest by using the x509 package with a corresponding private key of the public certificate.

{% highlight dart %}

//Class for singing a PDF document externally.
class PdfExternalSigner implements IPdfExternalSigner {
  //Hash algorithm.
  @override
  String get hashAlgorithm => 'SHA-256';

  //Sign message digest.
  @override
  SignerResult sign(List<int> message) {
    final pem = File('privatekey.pem').readAsBytesSync();
    final x509.KeyPair keyPair =
        x509.parsePem(String.fromCharCodes(pem)).single;
    final privateKey = keyPair.privateKey as x509.RsaPrivateKey;
    final signer = privateKey.createSigner(x509.algorithms.signing.rsa.sha256);
    final x509.Signature signed = signer.sign(message);
    return SignerResult(signed.data.toList());
  }
}

{% endhighlight %}

## Adding multiple digital signature

You can apply one or more digital signatures to a PDF document. The following code example shows how to add multiple signatures to the PDF document.
 
{% highlight dart %}

//Loads an existing PDF document.
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Gets the first signature field of the PDF document.
PdfSignatureField field = document.form.fields[0] as PdfSignatureField;

//Creates a digital signature and sets signature information.
field.signature = PdfSignature(
    //Creates a certificate instance from the PFX file with a private key.
    certificate:
        PdfCertificate(File('PDF.pfx').readAsBytesSync(), 'password123'),
    contactInfo: 'johndoe@owned.us',
    locationInfo: 'Honolulu, Hawaii',
    reason: 'I am author of this document.',
    digestAlgorithm: DigestAlgorithm.sha512,
    cryptographicStandard: CryptographicStandard.cades);

//Save and load the PDF document.
document = PdfDocument(inputBytes: await document.save());

//Gets the second signature field of the PDF document.
field = document.form.fields[1] as PdfSignatureField;

//Creates a digital signature and sets signature information.
field.signature = PdfSignature(
    //Creates a certificate instance from the PFX file with a private key.
    certificate: PdfCertificate(
        File('Certificate.pfx').readAsBytesSync(), 'password123'),
    contactInfo: 'johndoe@owned.us',
    locationInfo: 'Honolulu, Hawaii',
    reason: 'I am author of this document.',
    digestAlgorithm: DigestAlgorithm.sha256,
    cryptographicStandard: CryptographicStandard.cms);

//Save and dispose the PDF document.
File('Output.pdf').writeAsBytes(await document.save());
document.dispose();

{% endhighlight %}
