---
layout: post
title: Open a Password-Protected PDF in Flutter PDF Viewer widget (SfPdfViewer) | Syncfusion
description: Learn here about opening a password-protected document in Syncfusion Flutter PDF Viewer widget and more.
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Open a Password-Protected PDF in Flutter PDF Viewer (SfPdfViewer)
To load a password-protected document without a password or with an invalid password in [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) using the [password](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/password.html) property. The default password dialog will be displayed.

![Password dialog](images/password-dialog/password-dialog.png)

## Customize the visibility of password dialog

The password-protected document can be loaded by providing the password in the [password](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/password.html) property of SfPdfViewer. The [canShowPasswordDialog](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/canShowPasswordDialog.html) property allows the user to customize the password dialog visibility. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="7 8" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Container(
          child: SfPdfViewer.network(
            'https://cdn.syncfusion.com/content/PDFViewer/encrypted.pdf',
            password:'syncfusion',
            canShowPasswordDialog: false,)));
}

{% endhighlight %}
{% endtabs %}

## How to create and display a Customized Password Dialog?

The `SfPdfViewer` library allows you to create and display a customized password dialog. The following code example explains the same.
In this example, We have disabled the built-in password dialog by setting the false to the [canShowPasswordDialog](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/canShowPasswordDialog.html) property and creating the customized password dialog with the [AlertDialog](https://api.flutter.dev/flutter/material/AlertDialog-class.html) widget. Whenever the `password` is empty or incorrect, the [onDocumentLoadFailed](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onDocumentLoadFailed.html) callback is triggered, used this callback to display the customized password dialog.

{% tabs %}
{% highlight Dart %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_pdfviewer/pdfviewer.dart';
import 'package:flutter/foundation.dart';

void main() {
  runApp(const MaterialApp(home: CustomPasswordDialog()));
}

class CustomPasswordDialog extends StatefulWidget {
  const CustomPasswordDialog({Key? key}) : super(key: key);

  @override
  _CustomPasswordDialogState createState() => _CustomPasswordDialogState();
}

class _CustomPasswordDialogState extends State<CustomPasswordDialog> {
  String? _password;
  final GlobalKey<FormFieldState> _formKey = GlobalKey<FormFieldState>();
  final TextEditingController _textFieldController = TextEditingController();
  final FocusNode _passwordDialogFocusNode = FocusNode();
  bool _hasPasswordDialog = false;
  String _errorText = '';

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Custom password dialog'),
        toolbarHeight: 56,
      ),
      body: SfPdfViewer.network(
        'https://cdn.syncfusion.com/content/PDFViewer/encrypted.pdf',
        canShowPasswordDialog: false,
        password: _password,
        onDocumentLoaded: (details) {
          if (_hasPasswordDialog) {
            Navigator.pop(context);
            _hasPasswordDialog = false;
            _passwordDialogFocusNode.unfocus();
            _textFieldController.clear();
          }
        },
        onDocumentLoadFailed: (details) {
          if (details.description.contains('password')) {
            if (details.description.contains('password') &&
                _hasPasswordDialog) {
              _errorText = "Invalid password !!";
              _formKey.currentState?.validate();
              _textFieldController.clear();
              _passwordDialogFocusNode.requestFocus();
            } else {
              _errorText = '';
              /// Creating custom password dialog.
              _showCustomPasswordDialog();
              _passwordDialogFocusNode.requestFocus();
              _hasPasswordDialog = true;
            }
          }
        },
      ),
    );
  }

  /// Show the customized password dialog
  Future<void> _showCustomPasswordDialog() async {
    return showDialog<void>(
        context: context,
        builder: (BuildContext context) {
          final Orientation orientation = kIsWeb
              ? Orientation.portrait
              : MediaQuery.of(context).orientation;
          return AlertDialog(
            scrollable: true,
            insetPadding: EdgeInsets.zero,
            contentPadding: orientation == Orientation.portrait
                ? const EdgeInsets.all(24)
                : const EdgeInsets.only(top: 0, right: 24, left: 24, bottom: 0),
            buttonPadding: orientation == Orientation.portrait
                ? const EdgeInsets.all(8)
                : const EdgeInsets.all(4),
            title: Row(
              mainAxisAlignment: MainAxisAlignment.spaceBetween,
              children: <Widget>[
                Text(
                  'Password required',
                  style: TextStyle(
                    fontFamily: 'Roboto',
                    fontSize: 20,
                    fontWeight: FontWeight.w500,
                    color: Theme.of(context)
                        .colorScheme
                        .onSurface
                        .withOpacity(0.87),
                  ),
                ),
                SizedBox(
                  height: 36,
                  width: 36,
                  child: RawMaterialButton(
                    onPressed: () {
                      _closePasswordDialog();
                    },
                    child: Icon(
                      Icons.clear,
                      color: Theme.of(context)
                          .colorScheme
                          .onSurface
                          .withOpacity(0.6),
                      size: 24,
                    ),
                  ),
                ),
              ],
            ),
            shape: const RoundedRectangleBorder(
                borderRadius: BorderRadius.all(Radius.circular(4.0))),
            content: SingleChildScrollView(
                child: SizedBox(
                    width: 326,
                    child: Column(children: <Widget>[
                      Align(
                        alignment: Alignment.centerLeft,
                        child: Padding(
                          padding: const EdgeInsets.fromLTRB(0, 0, 0, 30),
                          child: Text(
                            'The document is password protected. Please enter a password.',
                            style: TextStyle(
                              fontFamily: 'Roboto',
                              fontSize: 16,
                              fontWeight: FontWeight.w400,
                              color: Theme.of(context)
                                  .colorScheme
                                  .onSurface
                                  .withOpacity(0.6),
                            ),
                          ),
                        ),
                      ),
                      Form(
                        child: TextFormField(
                          key: _formKey,
                          controller: _textFieldController,
                          focusNode: _passwordDialogFocusNode,
                          obscureText: true,
                          decoration: const InputDecoration(
                              hintText: 'Password hint: syncfusion',
                              border: OutlineInputBorder(
                                  borderSide: BorderSide(color: Colors.blue)),
                              focusedBorder: OutlineInputBorder(
                                  borderSide: BorderSide(color: Colors.blue))),
                          obscuringCharacter: '#',
                          onFieldSubmitted: (value) {
                            _handlePasswordValidation(value);
                          },
                          validator: (value) {
                            if (_errorText.isNotEmpty) {
                              return _errorText;
                            }
                            return null;
                          },
                          onChanged: (value) {
                            _formKey.currentState?.validate();
                            _errorText = '';
                          },
                        ),
                      )
                    ]))),
            actions: <Widget>[
              TextButton(
                onPressed: () {
                  _handlePasswordValidation(_textFieldController.text);
                },
                child: Text(
                  'OK',
                  style: TextStyle(
                    fontFamily: 'Roboto',
                    fontSize: 14,
                    fontWeight: FontWeight.w500,
                    color: Theme.of(context).colorScheme.primary,
                  ),
                ),
              ),
              Padding(
                padding: const EdgeInsets.fromLTRB(0, 0, 10, 0),
                child: TextButton(
                  onPressed: () {
                    _closePasswordDialog();
                  },
                  child: Text(
                    'CANCEL',
                    style: TextStyle(
                      fontFamily: 'Roboto',
                      fontSize: 14,
                      fontWeight: FontWeight.w500,
                      color: Theme.of(context).colorScheme.primary,
                    ),
                  ),
                ),
              )
            ],
          );
        });
  }

  ///Close the password dialog
  void _closePasswordDialog() {
    Navigator.pop(context, 'Cancel');
    _hasPasswordDialog = false;
    _passwordDialogFocusNode.unfocus();
    _textFieldController.clear();
  }

  /// Validates the password entered in text field.
  void _handlePasswordValidation(String value) {
    setState(() {
      _password = value;
      _passwordDialogFocusNode.requestFocus();
    });
  }
}

{% endhighlight %}
{% endtabs %}

![Custom Password dialog](images/password-dialog/custompassword-dialog.png)
