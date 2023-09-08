---
layout: post
title: Form filling in Flutter PDF Viewer widget | Syncfusion
description: Learn here all about form filling feature of Syncfusion Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: Flutter
control: SfPdfViewer
documentation: ug
---

# Form filling in Flutter PDF Viewer (SfPdfViewer)

The [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) allows you to fill, edit, save, export, and import the AcroForm fields in a PDF document.

## Supported form fields

You can load and fill in the following form fields in a PDF document using the Flutter PDF Viewer. 

* Text box. 
* Checkbox. 
* Radio button. 
* Combo box. 
* Signature. 
* List box.

## Adding or Editing the form data programmatically

Programmatically add or edit the form data in the document using the [getFormFields](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/getFormFields.html) method, which retrieves the form field collection.

### Adding or Editing text box data

Programmatically add or edit the text of the text box by changing the [text](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextFormField/text.html) property.

{% tabs %}
{% highlight dart hl_lines="17 18 19 20" %}

final PdfViewerController _pdfViewerController = PdfViewerController(); 
 
@override 
Widget build(BuildContext context) { 
  return Scaffold( 
    appBar: AppBar( 
      title: const Text('Syncfusion Flutter PDF Viewer'), 
      actions: <Widget>[ 
        IconButton( 
          icon: const Icon( 
            Icons.edit, 
            color: Colors.white, 
          ), 
          onPressed: () { 
            final List<PdfFormField> formFields = 
            _pdfViewerController.getFormFields();            
            final PdfTextFormField textbox = formFields.singleWhere(
                  (PdfFormField formField) => formField.name == 'name')
              as PdfTextFormField;
            textbox.text = 'John';          
          }, 
        ), 
      ], 
    ), 
    body: SfPdfViewer.asset( 
      'assets/form_document.pdf', 
      controller: _pdfViewerController, 
    ), 
  ); 
}

{% endhighlight %}
{% endtabs %}

### Adding or Editing checkbox data

Programmatically check or uncheck the checkbox by changing the [isChecked](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfCheckboxFormField/isChecked.html) property.

{% tabs %}
{% highlight dart hl_lines="17 18 19 20" %}

final PdfViewerController _pdfViewerController = PdfViewerController(); 
 
@override 
Widget build(BuildContext context) { 
  return Scaffold( 
    appBar: AppBar( 
      title: const Text('Syncfusion Flutter PDF Viewer'), 
      actions: <Widget>[ 
        IconButton( 
          icon: const Icon( 
            Icons.edit, 
            color: Colors.white, 
          ), 
          onPressed: () { 
            final List<PdfFormField> formFields = 
            _pdfViewerController.getFormFields();            
            final PdfCheckboxFormField checkbox = formFields.singleWhere(
                  (PdfFormField formField) => formField.name == 'newsletter')
              as PdfCheckboxFormField;
            checkbox.isChecked = true;          
          }, 
        ), 
      ], 
    ), 
    body: SfPdfViewer.asset( 
      'assets/form_document.pdf', 
      controller: _pdfViewerController, 
    ), 
  ); 
}

{% endhighlight %}
{% endtabs %}

### Editing combo box data

Programmatically select an item from the combo box using the [selectedItem](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfComboBoxFormField/selectedItem.html) property.

{% tabs %}
{% highlight dart hl_lines="17 18 19 20" %}

final PdfViewerController _pdfViewerController = PdfViewerController(); 
 
@override 
Widget build(BuildContext context) { 
  return Scaffold( 
    appBar: AppBar( 
      title: const Text('Syncfusion Flutter PDF Viewer'), 
      actions: <Widget>[ 
        IconButton( 
          icon: const Icon( 
            Icons.edit, 
            color: Colors.white, 
          ), 
          onPressed: () { 
            final List<PdfFormField> formFields = 
            _pdfViewerController.getFormFields();            
            final PdfComboBoxFormField combobox = formFields.singleWhere(
                  (PdfFormField formField) => formField.name == 'state')
              as PdfComboBoxFormField;
            combobox.selectedItem = combobox.items[4];         
          }, 
        ), 
      ], 
    ), 
    body: SfPdfViewer.asset( 
      'assets/form_document.pdf', 
      controller: _pdfViewerController, 
    ), 
  ); 
}

{% endhighlight %}
{% endtabs %}

### Editing radio button data

Programmatically select an item from the radio buttons using the [selectedItem](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfRadioFormField/selectedItem.html) property.

{% tabs %}
{% highlight dart hl_lines="17 18 19 20" %}

final PdfViewerController _pdfViewerController = PdfViewerController(); 
 
@override 
Widget build(BuildContext context) { 
  return Scaffold( 
    appBar: AppBar( 
      title: const Text('Syncfusion Flutter PDF Viewer'), 
      actions: <Widget>[ 
        IconButton( 
          icon: const Icon( 
            Icons.edit, 
            color: Colors.white, 
          ), 
          onPressed: () { 
            final List<PdfFormField> formFields = 
            _pdfViewerController.getFormFields();            
            final PdfRadioFormField radiobutton = formFields.singleWhere(
                  (PdfFormField formField) => formField.name == 'gender')
              as PdfRadioFormField;
            radiobutton.selectedItem = radiobutton.items[2];         
          }, 
        ), 
      ], 
    ), 
    body: SfPdfViewer.asset( 
      'assets/form_document.pdf', 
      controller: _pdfViewerController, 
    ), 
  ); 
}

{% endhighlight %}
{% endtabs %}

### Editing list box data

Programmatically select an item or more from the list box using the [selectedItems](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfListBoxFormField/selectedItems.html) property.

{% tabs %}
{% highlight dart hl_lines="17 18 19 20" %}

final PdfViewerController _pdfViewerController = PdfViewerController(); 
 
@override 
Widget build(BuildContext context) { 
  return Scaffold( 
    appBar: AppBar( 
      title: const Text('Syncfusion Flutter PDF Viewer'), 
      actions: <Widget>[ 
        IconButton( 
          icon: const Icon( 
            Icons.edit, 
            color: Colors.white, 
          ), 
          onPressed: () { 
            final List<PdfFormField> formFields = 
            _pdfViewerController.getFormFields();            
            final PdfListBoxFormField listbox = formFields.singleWhere(
                  (PdfFormField formField) => formField.name == 'list')
              as PdfListBoxFormField;
            listbox.selectedItems = listbox.items.sublist(0, 2);          
          }, 
        ), 
      ], 
    ), 
    body: SfPdfViewer.asset( 
      'assets/form_document.pdf', 
      controller: _pdfViewerController, 
    ), 
  ); 
}

{% endhighlight %}
{% endtabs %}

### Adding or Editing signature data

Programmatically add or remove the signature in a signature form field by assigning the image bytes or `null` to the [signature](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfSignatureFormField/signature.html) property.

{% tabs %}
{% highlight dart hl_lines="17 18 19 20 21 22" %}

final PdfViewerController _pdfViewerController = PdfViewerController(); 
 
@override 
Widget build(BuildContext context) { 
  return Scaffold( 
    appBar: AppBar( 
      title: const Text('Syncfusion Flutter PDF Viewer'), 
      actions: <Widget>[ 
        IconButton( 
          icon: const Icon( 
            Icons.edit, 
            color: Colors.white, 
          ), 
          onPressed: () async { 
            final List<PdfFormField> formFields = 
            _pdfViewerController.getFormFields();            
            final PdfSignatureFormField signature = formFields.singleWhere(
                  (PdfFormField formField) => formField.name == 'signature')
              as PdfSignatureFormField;
            final ByteData bytedata =
              await rootBundle.load('assets/signature.png');
            signature.signature = bytedata.buffer.asUint8List();        
          }, 
        ), 
      ], 
    ), 
    body: SfPdfViewer.asset( 
      'assets/form_document.pdf', 
      controller: _pdfViewerController, 
    ), 
  ); 
}

{% endhighlight %}
{% endtabs %}

## Customize the visibility of built-in Signature pad

By default, the `SfPdfViewer` displays the signature pad when tapped on the signature form field. You can customize the visibility of the built-in signature pad using the [canShowSignaturePad](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/canShowSignaturePadDialog.html) property. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="9" %}
 
@override 
Widget build(BuildContext context) { 
  return Scaffold( 
    appBar: AppBar( 
      title: const Text('Syncfusion Flutter PDF Viewer'),
    ), 
    body: SfPdfViewer.asset( 
      'assets/form_document.pdf', 
      canShowSignaturePadDialog: false, 
    ), 
  ); 
}

{% endhighlight %}
{% endtabs %}

### How to create and display a custom signature pad?

With the above option available in the `SfPdfViewer`, you can easily hide the built-in signature pad and create and display a custom signature pad to draw and add personalised signatures to the signature form field. The following code example explains the same.

In this example, the custom signature pad using `SfSignaturePad` will be displayed when tapping on the signature field with the following options:

* **Clear** - Clears all the signature strokes in the `SfSignaturePad`.
* **Save** - Saves the signature strokes in the `SfSignaturePad` to the signature form field as an image.

{% tabs %}
{% highlight dart %}

import 'dart:typed_data';
import 'dart:ui' as ui;

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_pdfviewer/pdfviewer.dart';
import 'package:syncfusion_flutter_signaturepad/signaturepad.dart';

void main() {
  runApp(MaterialApp(
    title: 'Syncfusion PDF Viewer Demo',
    home: HomePage(),
  ));
}

class HomePage extends StatefulWidget {
  @override
  _HomePage createState() => _HomePage();
}

class _HomePage extends State<HomePage> {
  final GlobalKey<SfPdfViewerState> _pdfViewerKey = GlobalKey();
  final GlobalKey<SfSignaturePadState> _signaturePadKey = GlobalKey();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SfPdfViewer.asset(
        'assets/form_document.pdf',
        key: _pdfViewerKey,
        canShowSignaturePadDialog: false,
        onFormFieldFocusChange: (PdfFormFieldFocusChangeDetails details) {
          if (details.formField is PdfSignatureFormField && details.hasFocus) {
            final PdfSignatureFormField signatureFormField =
                details.formField as PdfSignatureFormField;
            _showCustomSignaturePadDialog(signatureFormField);
          }
        },
      ),
    );
  }

  /// Displays the custom signature pad dialog.
  Future<void> _showCustomSignaturePadDialog(
      PdfSignatureFormField formField) async {
    await showDialog(
      context: context,
      builder: (BuildContext context) {
        return AlertDialog(
          title: const Text(
            'Draw your Signature',
            textAlign: TextAlign.center,
          ),
          titlePadding: const EdgeInsets.all(8),
          contentPadding: const EdgeInsets.all(12),
          content: Container(
            height: 200,
            width: 300,
            decoration: BoxDecoration(
              border: Border.all(color: Colors.grey),
            ),
            child: SfSignaturePad(
              key: _signaturePadKey,
            ),
          ),
          actions: [
            TextButton(
              onPressed: () {
                // Clears the strokes in the signature pad.
                _signaturePadKey.currentState!.clear();
              },
              child: const Text('Clear'),
            ),
            TextButton(
              onPressed: () async {
                Navigator.pop(context);
                await _saveSignature(formField);
              },
              child: const Text('Save'),
            ),
          ],
        );
      },
    );
  }

  /// Saves the image from the signature pad to the form field.
  Future<void> _saveSignature(PdfSignatureFormField formField) async {
    final ui.Image image =
        await _signaturePadKey.currentState!.toImage(pixelRatio: 3.0);
    final ByteData? imageBytes =
        await image.toByteData(format: ui.ImageByteFormat.png);
    if (imageBytes != null) {
      final Uint8List data = imageBytes.buffer.asUint8List();
      formField.signature = data;
    }
  }
}

{% endhighlight %}
{% endtabs %}

## Restrict the editing of form fields

To prevent editing the values of the form fields in the PDF document, set the `readOnly` property of the respective form field to `true`.

{% tabs %}
{% highlight dart hl_lines="17" %}

final PdfViewerController _pdfViewerController = PdfViewerController(); 
 
@override 
Widget build(BuildContext context) { 
  return Scaffold( 
    appBar: AppBar( 
      title: const Text('Syncfusion Flutter PDF Viewer'), 
      actions: <Widget>[ 
        IconButton( 
          icon: const Icon( 
            Icons.edit, 
            color: Colors.white, 
          ), 
          onPressed: () { 
            final List<PdfFormField> formFields = 
              _pdfViewerController.getFormFields();            
            formFields[0].readOnly = true;
          }, 
        ), 
      ], 
    ), 
    body: SfPdfViewer.asset( 
      'assets/form_document.pdf', 
      controller: _pdfViewerController, 
    ), 
  ); 
}

{% endhighlight %}
{% endtabs %}

## Clear form data

The [clearFormData](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/clearFormData.html) method clears all the form field data in the PDF document. The optional `pageNumber` parameter can be used to clear the form field data on a specific page. By default, the `pageNumber` parameter is 0. Refer to the following code example.

{% tabs %}
{% highlight dart hl_lines="16 26" %}

final PdfViewerController _pdfViewerController = PdfViewerController(); 
 
@override 
Widget build(BuildContext context) { 
  return Scaffold( 
    appBar: AppBar( 
      title: const Text('Syncfusion Flutter PDF Viewer'), 
      actions: <Widget>[
        IconButton( 
          icon: const Icon( 
            Icons.clear, 
            color: Colors.white, 
          ), 
          onPressed: () {  
            // Clears all the form field data on the 2nd page.
            _pdfViewerController.clearFormData(pageNumber: 2);         
          }, 
        ),
        IconButton( 
          icon: const Icon( 
            Icons.clear, 
            color: Colors.white, 
          ), 
          onPressed: () { 
            // Clears all the form field data in the pdf document.
            _pdfViewerController.clearFormData();        
          }, 
        ), 
      ], 
    ), 
    body: SfPdfViewer.asset( 
      'assets/form_document.pdf', 
      controller: _pdfViewerController, 
    ), 
  ); 
}

{% endhighlight %}
{% endtabs %}

## Save form data 

You can save the modified form field data by calling the [saveDocument](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/saveDocument.html) method. Refer to the following code example. 

{% tabs %}
{% highlight dart hl_lines="15 16" %}

final PdfViewerController _pdfViewerController = PdfViewerController(); 
 
@override 
Widget build(BuildContext context) { 
  return Scaffold( 
    appBar: AppBar( 
      title: const Text('Syncfusion Flutter PDF Viewer'), 
      actions: <Widget>[ 
        IconButton( 
          icon: const Icon( 
            Icons.save, 
            color: Colors.white, 
          ), 
          onPressed: () async { 
            final List<int> savedBytes = 
                await _pdfViewerController.saveDocument(); 
          }, 
        ), 
      ], 
    ), 
    body: SfPdfViewer.asset( 
      'assets/form_document.pdf', 
      controller: _pdfViewerController, 
    ), 
  ); 
}

{% endhighlight %}
{% endtabs %}

N> When the `saveDocument` method is called, the document will be automatically reloaded after the save in the viewer. Also, the signature field will be flattened on save irrespective of the `PdfFlattenOption` provided.   

### Flattening the form data on save 

Flattening PDF form is a process of removing the form fields in the PDF document, thereby rendering the form fields appearance and content in the page graphics. This will avoid the PDF form being edited on any device. Flutter PDF Viewer supports flattening the PDF form when saving. You can perform this action by setting the [PdfFlattenOption](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfFlattenOption.html) to `PdfFlattenOption.formFields` in the `saveDocument` method.  

By default, the `PdfFlattenOption` will be `PdfFlattenOption.none`, which means the form fields (except signature fields) can be edited after saving.  

Refer to the following code example. 

{% tabs %}
{% highlight dart hl_lines="15 16" %}

final PdfViewerController _pdfViewerController = PdfViewerController(); 
 
@override 
Widget build(BuildContext context) { 
  return Scaffold( 
    appBar: AppBar( 
      title: const Text('Syncfusion Flutter PDF Viewer'), 
      actions: <Widget>[ 
        IconButton( 
          icon: const Icon( 
            Icons.save, 
            color: Colors.white, 
          ), 
          onPressed: () async { 
            final List<int> savedBytes = await _pdfViewerController 
                .saveDocument(flattenOption: PdfFlattenOption.formFields); 
          }, 
        ), 
      ], 
    ), 
    body: SfPdfViewer.asset( 
      'assets/form_document.pdf', 
      controller: _pdfViewerController, 
    ), 
  ); 
}

{% endhighlight %}
{% endtabs %}

## Importing and Exporting form data 

The Flutter PDF viewer allows users to import and export form data to and from PDF documents. The import and export of form data support the following extensions. 

* fdf 
* xfdf 
* json 
* xml 

The required file type can be chosen from the [DataFormat](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/DataFormat.html) enumeration. In the following sections, only the `xfdf` file type is explained for brevity. 

N> Import ‘package:syncfusion_flutter_pdf/pdf.dart’ in the Dart code to use the [DartFormat](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/DataFormat.html) parameter. 

### Exporting form data 

The [exportFormData](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/exportFormData.html) method exports the current data filled in the form fields into a bytes list in the specified data format. Refer to the following code example.

{% tabs %}
{% highlight dart hl_lines="15 16" %}

final PdfViewerController _pdfViewerController = PdfViewerController(); 
 
@override 
Widget build(BuildContext context) { 
  return Scaffold( 
    appBar: AppBar( 
      title: const Text('Syncfusion Flutter PDF Viewer'), 
      actions: <Widget>[ 
        IconButton( 
          icon: const Icon( 
            Icons.outbox, 
            color: Colors.white, 
          ), 
          onPressed: () async { 
            final List<int> formDataBytes = _pdfViewerController 
                .exportFormData(dataFormat: DataFormat.xfdf); 
          }, 
        ), 
      ], 
    ), 
    body: SfPdfViewer.asset( 
      'assets/form_document.pdf', 
      controller: _pdfViewerController, 
    ), 
  ); 
} 

{% endhighlight %}
{% endtabs %}

N> When exporting, the signature form field data will not be exported.  
 
### Importing form data 

The [importFormData](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/importFormData.html) method imports the data from a file of a specified type and fills the saved data into the form fields. 

{% tabs %}
{% highlight dart hl_lines="15 16 17 18" %}

final PdfViewerController _pdfViewerController = PdfViewerController(); 
 
@override 
Widget build(BuildContext context) { 
  return Scaffold( 
    appBar: AppBar( 
      title: const Text('Syncfusion Flutter PDF Viewer'), 
      actions: <Widget>[ 
        IconButton( 
          icon: const Icon( 
            Icons.inbox, 
            color: Colors.white, 
          ), 
          onPressed: () async { 
            final ByteData data = await DefaultAssetBundle.of(context) 
                .load('assets/form_data.xfdf'); 
            final List<int> formDataBytes = data.buffer.asUint8List(); 
            _pdfViewerController.importFormData(formDataBytes, DataFormat.xfdf); 
          }, 
        ), 
      ], 
    ), 
    body: SfPdfViewer.asset( 
      'assets/form_document.pdf', 
      controller: _pdfViewerController, 
    ), 
  ); 
}

{% endhighlight %}
{% endtabs %}

## Callbacks

The `SfPdfViewer` supports the [PdfFormFieldFocusChangeCallback](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfFormFieldFocusChangeCallback.html) to notify the interaction with the form fields and the [PdfFormFieldValueChangedCallback](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfFormFieldValueChangedCallback.html) to notify the values changes in the form fields.

### Form field focus change callback

The [onFormFieldFocusChange](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onFormFieldFocusChange.html) callback triggers when the focus changes in or out of the form field. The [PdfFormFieldFocusChangeDetails](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfFormFieldFocusChangeDetails-class.html) will return the `formField` instance and its focus change value in the `hasFocus` property. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="9 10 11" %}
 
@override 
Widget build(BuildContext context) { 
  return Scaffold( 
    appBar: AppBar( 
      title: const Text('Syncfusion Flutter PDF Viewer'), 
    ), 
    body: SfPdfViewer.asset( 
      'assets/form_document.pdf', 
      onFormFieldFocusChange: (PdfFormFieldFocusChangeDetails details) {
        print('${details.formField.name} - ${details.hasFocus}');
      },
    ), 
  ); 
}

{% endhighlight %}
{% endtabs %}

N> The `PdfFormFieldFocusChangeCallback` only triggers for text boxes and signature form fields.

### Form field value changed callback

The [onFormFieldValueChanged](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onFormFieldValueChanged.html) callback triggers when the value is changed in the form field. The [PdfFormFieldValueChangedDetails](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfFormFieldValueChangedDetails-class.html) the `formField` instance along with its `oldValue` and `newValue`. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="9 10 11 12" %}
 
@override 
Widget build(BuildContext context) { 
  return Scaffold( 
    appBar: AppBar( 
      title: const Text('Syncfusion Flutter PDF Viewer'), 
    ), 
    body: SfPdfViewer.asset( 
      'assets/form_document.pdf', 
      onFormFieldValueChanged:(PdfFormFieldValueChangedDetails details) {
        print('${details.oldValue}');     
        print('${details.newValue}');     
      },
    ), 
  ); 
}

{% endhighlight %}
{% endtabs %}

## How to synchronize text form field data with the text entry widget periodically for each character change?

With the help of the [onFormFieldValueChanged](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onFormFieldValueChanged.html) callback, we can synchronize text form field data with the text entry widget periodically for each character change. The following code example explains the same.

{% tabs %}
{% highlight %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_pdfviewer/pdfviewer.dart';

void main() {
  runApp(MaterialApp(
    title: 'Syncfusion PDF Viewer Demo',
    home: HomePage(),
  ));
}

/// Represents Homepage for Navigation
class HomePage extends StatefulWidget {
  @override
  _HomePage createState() => _HomePage();
}

class _HomePage extends State<HomePage> {
  final GlobalKey<SfPdfViewerState> _pdfViewerKey = GlobalKey();

  final TextEditingController _nameController = TextEditingController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Column(
        children: [
          SizedBox(
            width: 200,
            child: TextField(
              controller: _nameController,
              decoration: InputDecoration(
                labelText: 'Name',
                fillColor: Colors.grey[100],
              ),
            ),
          ),
          Expanded(
            flex: 5,
            child: SfPdfViewer.asset(
              'assets/form_document.pdf',
              key: _pdfViewerKey,
              onFormFieldValueChanged:
                  (PdfFormFieldValueChangedDetails details) {
                final PdfFormField field = details.formField;
                if (field is PdfTextFormField && field.name == 'name') {
                  _nameController.value = TextEditingValue(text: field.text);
                }
              },
            ),
          ),
        ],
      ),
    );
  }
}

{% endhighlight %}
{% endtabs %}

## How to synchronize text form field data with the text entry widget after filling it out completely?

With the help of the [onFormFieldFocusChange](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onFormFieldFocusChange.html) callback, we can synchronize text form field data with the text entry widget after filling it out completely. The following code example explains the same.

{% tabs %}
{% highlight dart %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_pdfviewer/pdfviewer.dart';

void main() {
  runApp(MaterialApp(
    title: 'Syncfusion PDF Viewer Demo',
    home: HomePage(),
  ));
}

/// Represents Homepage for Navigation
class HomePage extends StatefulWidget {
  @override
  _HomePage createState() => _HomePage();
}

class _HomePage extends State<HomePage> {
  final GlobalKey<SfPdfViewerState> _pdfViewerKey = GlobalKey();

  final TextEditingController _nameController = TextEditingController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Column(
        children: [
          SizedBox(
            width: 200,
            child: TextField(
              controller: _nameController,
              decoration: InputDecoration(
                labelText: 'Name',
                fillColor: Colors.grey[100],
              ),
            ),
          ),
          Expanded(
            flex: 5,
            child: SfPdfViewer.asset(
              'assets/form_document.pdf',
              key: _pdfViewerKey,
              onFormFieldFocusChange:
                  (PdfFormFieldFocusChangeDetails details) async {
                final PdfFormField field = details.formField;
                if (field is PdfTextFormField && field.name == 'name') {
                  if (details.hasFocus) {
                    _nameController.value = TextEditingValue.empty;
                  }
                }
              },
            ),
          ),
        ],
      ),
    );
  }
}

{% endhighlight %}
{% endtabs %}

## How to perform validation over the form field data?

With the help of the [onFormFieldFocusChange](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onFormFieldFocusChange.html) and [onFormFieldValueChanged](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onFormFieldValueChanged.html) callbacks and the form field programmatic options available in `SfPdfViewer`, we can validate the form field data. The following code examples explain the same.

In this example, we are validating the form field data in a registration form when saving. The validation includes,

<table>
<tr>
<td>
<b>Field name</b>
</td>
<td>
<b>Validation messages</b>
</td>
</tr>
<tr>
<td>
Name
</td>
<td>
* Name is required.<br>
* Name should have at least 3 characters.<br>
* Name should not exceed 30 characters.<br>
* Name should not contain numbers.<br>
* Name should not contain special characters.<br>
</td>
</tr>
<tr>
<td>
Email
</td>
<td>
* Email is required.<br>
* Email should be in correct format.<br>
</td>
</tr>
<tr>
<td>
Date of birth
</td>
<td>
* Date of birth is required.<br>
* Date of birth should be in dd/mm/yyyy format.<br>
</td>
</tr>
<tr>
<td>
Course
</td>
<td>
* Atleast one course should be selected.
</td>
</tr>
<tr>
<td>
Signature
</td>
<td>
* Signature is required.
</td>
</tr>
</table>

{% tabs %}
{% highlight %}

final PdfViewerController _pdfViewerController = PdfViewerController();
List<PdfFormField>? _formFields;

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      actions: <Widget>[
        IconButton(
          icon: const Icon(Icons.save),
          onPressed: _validateAndSaveForm,
        ),
      ],
    ),
    body: SfPdfViewer.asset(
      'assets/form_document.pdf',
      controller: _pdfViewerController,
      onDocumentLoaded: (PdfDocumentLoadedDetails details) {
        _formFields = _pdfViewerController.getFormFields();
      },
    ),
  );
}

/// Validates the form field data.
Future<void> _validateAndSaveForm() async {
  if (_formFields == null) {
    return;
  } else if (_formFields!.isEmpty) {
    return;
  }
  final List<String> errors = <String>[];
  for (final PdfFormField formField in _formFields!) {
    if (formField is PdfTextFormField) {
      if (formField.name == 'name') {
        if (formField.text == null || formField.text.isEmpty) {
          errors.add('Name is required.');
        } else if (formField.text.length < 3) {
          errors.add('Name should have atleast 3 characters.');
        } else if (formField.text.length > 30) {
          errors.add('Name should not exceed 30 characters.');
        } else if (formField.text.contains(RegExp(r'[0-9]'))) {
          errors.add('Name should not contain numbers.');
        } else if (formField.text
            .contains(RegExp(r'[!@#$%^&*(),.?":{}|<>]'))) {
          errors.add('Name should not contain special characters.');
        }
      } else if (formField.name == 'dob') {
        if (formField.text == null || formField.text.isEmpty) {
          errors.add('Date of birth is required.');
        } else if (!RegExp(r'^\d{1,2}\/\d{1,2}\/\d{4}$')
            .hasMatch(formField.text)) {
          errors.add('Date of birth should be in dd/mm/yyyy format.');
        }
      } else if (formField.name == 'email') {
        if (formField.text == null || formField.text.isEmpty) {
          errors.add('Email is required.');
        } else if (!RegExp(r'^[\w-\.]+@([\w-]+\.)+[\w-]{2,4}$')
            .hasMatch(formField.text)) {
          errors.add('Email should be in correct format.');
        }
      }
    } else if (formField is PdfListBoxFormField) {
      if (formField.selectedItems == null ||
          formField.selectedItems!.isEmpty) {
        errors.add('Please select atleast one course.');
      }
    } else if (formField is PdfSignatureFormField) {
      if (formField.signature == null) {
        errors.add('Please sign the document.');
      }
    }
  }
  if (errors.isNotEmpty) {
    await showDialog(
      context: context,
      builder: (BuildContext context) {
        return AlertDialog(
          title: const Text('Errors'),
          content: SizedBox(
            height: 200,
            width: 100,
            child: ListView.builder(
              itemCount: errors.length,
              itemBuilder: (_, int index) {
                return Padding(
                  padding: const EdgeInsets.all(8.0),
                  child: Text(errors[index]),
                );
              },
            ),
          ),
          actions: <Widget>[
            TextButton(
              onPressed: () {
                Navigator.pop(context);
              },
              child: const Text('Try Again'),
            ),
          ],
        );
      },
    );
  } else {
    _pdfViewerController.saveDocument(
        flattenOption: PdfFlattenOption.formFields);
    showDialog(
      context: context,
      builder: (BuildContext context) {
        return AlertDialog(
          title: const Text('Success'),
          content: const Text('Form submitted successfully.'),
          actions: <Widget>[
            TextButton(
              onPressed: () {
                Navigator.pop(context);
              },
              child: const Text('OK'),
            ),
          ],
        );
      },
    );
  }
}

{% endhighlight %}
{% endtabs %}