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

## Save form data 

You can save the modified form field data by calling the `saveDocument` method. Refer to the following code example. 

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

Flattening PDF form is a process of removing the form fields in the PDF document, thereby rendering the form fields appearance and content in the page graphics. This will avoid the PDF form being edited on any device. Flutter PDF Viewer supports flattening the PDF form when saving. You can perform this action by setting the `PdfFlattenOption` to `PdfFlattenOption.formFields` in the `saveDocument` method.  

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

The `exportFormData` method exports the current data filled in the form fields into a bytes list in the specified data format. Refer to the following code example.

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

The `importFormData` method imports the data from a file of a specified type and fills the saved data into the form fields. 

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

## Modifying the form field data programmatically

Programmatically modify the form field data in the pdf document using the `formFields` collection. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="13 14" %}

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
          onPressed: () {
            final List<PdfFormField> formFields = 
              _pdfViewerController.getFormFields(); 
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

### Modify text box data

Programmatically modify the text of text box by changing the `text` property.

{% tabs %}
{% highlight dart hl_lines="18 19 20 21" %}

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
            
            final PdfTextFormField textbox = formfields.singleWhere(
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

### Modify checkbox data

Programmatically check or uncheck the checkbox by changing the `isChecked` property.

{% tabs %}
{% highlight dart hl_lines="18 19 20 21" %}

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
            
            final PdfCheckboxFormField checkbox = formfields.singleWhere(
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

### Modify combo box data

Programmatically select an item from the combo box using the `selectedItem` property.

{% tabs %}
{% highlight dart hl_lines="18 19 20 21" %}

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
            
            final PdfComboBoxFormField combobox = formfields.singleWhere(
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

### Modify radio button data

Programmatically select an item from the radio buttons using the `selectedItem` property.

{% tabs %}
{% highlight dart hl_lines="18 19 20 21" %}

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
            
            final PdfRadioFormField radiobutton = formfields.singleWhere(
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

### Modify list box data

Programmatically select an item from the list box using the `selectedItems` property.

{% tabs %}
{% highlight dart hl_lines="18 19 20 21" %}

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
            
            final PdfListBoxFormField listbox = formfields.singleWhere(
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

### Modify signature data

Programmatically add a signature in a signature form field by assigning the image bytes to the `signature` property. Programmatically remove the signature in a signature form field by assigning null to the `signature` property.

{% tabs %}
{% highlight dart hl_lines="18 19 20 21 22 23" %}

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
            
            final PdfSignatureFormField signature = formfields.singleWhere(
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

## Clear form data

You can clear the form field data by calling the `clearFormData` method. Refer to the following code example.
The `pageNumber` parameter can be used to clear the form field data in a aparticular page. By default, the `pageNumber` argument is 0 by which all the form fields in the odf document wil be cleared.

{% tabs %}
{% highlight dart hl_lines="16" %}

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
          onPressed: () async { 
            // Clears all the form field data in the pdf document.
            _pdfViewerController.clearFormData();   
            // Clears all the form field data on the 2nd page.
            // _pdfViewerController.clearFormData(2);         
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

By default, the `SfPdfViewer` displays the signature pad when tapped on the signature form field. You can customize the visibility of the built-in signauture pad using the `canShowSignaturePad` property. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="15" %}

final PdfViewerController _pdfViewerController = PdfViewerController(); 
 
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

## Restrict the editing of form fields

To prevent editing the values of the form field in the PDF document, set the `readOnly` property of the `PdfFormField` to true.

{% tabs %}
{% highlight dart hl_lines="18" %}

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

## Callbacks

The `SfPdfViewer` supports the `PdfFormFieldFocusChangeCallback` to notify the interaction with the form fields and the `PdfFormFieldValueChangedCallback` to notify the values changes in the form fields.

### PdfFormFieldFocusChangeCallback

The `onFormFieldFocusChange` callback triggers when the user taps on the form field. The `PdfFormFieldFocusChangeDetails` will return the `PdfFormField` instance and `hasFocus` property. The following code example explains the same.

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

### PdfFormFieldValueChangedCallback

The `onFormFieldValueChanged` callback triggers when the user taps on the form field. The `PdfFormFieldValueChangedDetails` the `PdfFormField` instance, `oldValue` and `newValue` properties. The following code example explains the same.

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
      onFormFieldValueChanged:( PdfFormFieldValueChangedDetails details) {
        // Handle form field value changed here.       
      },
    ), 
  ); 
}

{% endhighlight %}
{% endtabs %}
