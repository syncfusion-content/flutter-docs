---
layout: post
title: Text selection in Flutter PDF Viewer widget | Syncfusion
description: Learn here all about text selection feature of Syncfusion Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: Flutter
control: SfPdfViewer
documentation: ug
---

# Viewing password-protected PDF's in Flutter PDF Viewer (SfPdfViewer)

When loading a password-protected document without a password or with an invalid password in [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) using the [password](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/password.html) property. The default password dialogue will be displayed.

![Password dialog](images/password-dialog.png)

## Customize the visibility of password dialogue

The password-protected document can be loaded by providing the password in the [password](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/password.html) property of SfPdfViewer. The [canShowPasswordDialog](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/canShowPasswordDialog.html) property allows the user to customize the password dialogue visibility. The following code example explains the same.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Container(
          child: SfPdfViewer.asset(
              'assets/encrypted_document.pdf',
            password:'syncfusion',
            canShowPasswordDialog: false,)));
}

{% endhighlight %}
{% endtabs %}