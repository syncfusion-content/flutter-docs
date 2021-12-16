---
layout: post
title: Loading password protected PDF's in Flutter PDF Viewer | Syncfusion
description: Learn here all about Loading password protected PDF's feature of Syncfusion Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: Flutter
control: SfPdfViewer
documentation: ug
---

# Loading password protected PDF's in Flutter PDF Viewer (SfPdfViewer)

The password protected document can be loaded by passing the password in constructor of SfPdfViewer. The following code example explains the loading encrypted document in SfPdfViewer.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Container(
          child: SfPdfViewer.asset(
              'assets/encrypted_document.pdf',
              password: 'syncfusion',)));
}

{% endhighlight %}
{% endtabs %}

## Customize the visibility of password dialogue

By default,the password dialog will be alerted when user doesn’t provide a password for encrypted document or incorrect password is passed in constructor.
You can customize the visibility of the password dialogue using the canShowPasswordDialog property.The following code example explain the same.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Container(
          child: SfPdfViewer.asset(
              'assets/encrypted_document.pdf',
            canShowPasswordDialog: false,)));
}

{% endhighlight %}
{% endtabs %}

![Password dialog](images/password-dialog.png)
