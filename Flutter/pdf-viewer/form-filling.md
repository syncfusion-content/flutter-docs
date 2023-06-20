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
