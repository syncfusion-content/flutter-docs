---
layout: post
title: Forms in Flutter PDF library | Syncfusion
description: Learn here all about different types of Forms feature of Syncfusion Flutter PDF non-UI library and more.
platform: flutter
control: PDF
documentation: UG
---

# Forms in Flutter PDF

An interactive form sometimes referred to as an AcroForm is a collection of fields for gathering information. A PDF document can contain any number of fields appearing on any combination of pages, all that makes a single, globally interactive form spanning the entire document.

## Creating a new PDF form

Flutter PDF allows you to create and manage the form (AcroForm) in PDF documents by using the PdfForm class. The PdfFormFieldCollection class represents the entire field collection of the form.

### Adding the text box field

The [`PdfTextBoxField `](#) class is used to create a text box field in PDF forms.

The following code sample explains how to add a textbox field to a new PDF document.

{% highlight dart %}

//Create a new PDF document.
final PdfDocument document = PdfDocument();

// Create a text box form field and add it to the document.
document.form.fields.add(PdfTextBoxField(
    document.pages.add(), 'TextBox', Rect.fromLTWH(100, 20, 200, 20),
    text: 'toType',
    font: PdfStandardFont(PdfFontFamily.courier, 12),
    isPassword: false,
    spellCheck: true,
    backColor: PdfColor(0, 255, 0),
    borderColor: PdfColor(255, 0, 0),
    foreColor: PdfColor(0, 0, 255)));

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

The following code sample explains how to add the textbox to an existing PDF document.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

// Create a text box form field and add it to the existing document.
document.form.fields.add(PdfTextBoxField(
    document.pages[0], 'TextBox', Rect.fromLTWH(100, 20, 200, 20),
    text: 'toType',
    font: PdfStandardFont(PdfFontFamily.courier, 12),
    isPassword: false,
    spellCheck: true,
    backColor: PdfColor(0, 255, 0),
    borderColor: PdfColor(255, 0, 0),
    foreColor: PdfColor(0, 0, 255)));

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

### Adding the combo box field

The PdfComboBoxField class is used to create a combo box field in PDF forms. You can add a list of items to the combo box by using the PdfListFieldItem class.

Please refer to the following code sample for adding the combo box in a new PDF document.

{% highlight dart %}

//Create a new PDF document.
final PdfDocument document = PdfDocument();

// Create a combo box form field and add it to the document.
document.form.fields.add(PdfComboBoxField(
    document.pages.add(), 'comboBox', Rect.fromLTWH(100, 100, 200, 20),
    font: PdfStandardFont(PdfFontFamily.helvetica, 12),
    alignment: PdfTextAlignment.right,
    editable: true,
    selectedValue: 'Language 2',
    items: [
    PdfListFieldItem('Tamil', 'Language 1'),
    PdfListFieldItem('English', 'Language 2'),
    PdfListFieldItem('French', 'Language 3')
    ]));

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

Please refer to the following code sample for adding the combo box in an existing PDF document.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

// Create a combo box form field and add it to the existing document.
document.form.fields.add(PdfComboBoxField(
    document.pages[0], 'comboBox', Rect.fromLTWH(100, 100, 200, 20),
    font: PdfStandardFont(PdfFontFamily.helvetica, 12),
    alignment: PdfTextAlignment.right,
    editable: true,
    selectedValue: 'Language 2',
    items: [
    PdfListFieldItem('Tamil', 'Language 1'),
    PdfListFieldItem('English', 'Language 2'),
    PdfListFieldItem('French', 'Language 3')
    ]));

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

### Adding the radio button field

To create the radio button in the PDF forms, you can use the PdfRadioButtonListField class and you can create the radio button list items by using the PdfRadioButtonListItem class.

Please refer to the following code sample for adding the radio button in a new PDF document.

{% highlight dart %}

//Create a new PDF document.
final PdfDocument document = PdfDocument();

// Create a radio button form field and add it to the document.
document.form.fields.add(PdfRadioButtonListField(
document.pages.add(),
'Gender',
items: <PdfRadioButtonListItem>[
    PdfRadioButtonListItem('Male', Rect.fromLTWH(100, 150, 35, 35),
        style: PdfCheckBoxStyle.diamond,
        highlightMode: PdfHighlightMode.push,
        foreColor: PdfColor(0, 255, 0),
        borderWidth: 3),
    PdfRadioButtonListItem('Female', Rect.fromLTWH(100, 200, 35, 35),
        highlightMode: PdfHighlightMode.outline,
        backColor: PdfColor(153, 12, 102),
        foreColor: PdfColor(0, 255, 0),
        borderWidth: 2),
    PdfRadioButtonListItem('Others', Rect.fromLTWH(100, 250, 35, 35),
        highlightMode: PdfHighlightMode.outline,
        borderStyle: PdfBorderStyle.dot,
        borderColor: PdfColor(230, 0, 172),
        foreColor: PdfColor(0, 255, 0),
        borderWidth: 1)
],
selectedIndex: 0,
));

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

The following code sample shows how to add the radio button in an existing PDF document.

{% highlight dart %}

//Loads an existing PDF document.  
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

// Create a radio button form field and add it to the existing document.
document.form.fields.add(PdfRadioButtonListField(
document.pages[0],
'Gender',
items: <PdfRadioButtonListItem>[
    PdfRadioButtonListItem('Male', Rect.fromLTWH(100, 150, 35, 35),
        style: PdfCheckBoxStyle.diamond,
        highlightMode: PdfHighlightMode.push,
        foreColor: PdfColor(0, 255, 0),
        borderWidth: 3),
    PdfRadioButtonListItem('Female', Rect.fromLTWH(100, 200, 35, 35),
        highlightMode: PdfHighlightMode.outline,
        backColor: PdfColor(153, 12, 102),
        foreColor: PdfColor(0, 255, 0),
        borderWidth: 2),
    PdfRadioButtonListItem('Others', Rect.fromLTWH(100, 250, 35, 35),
        highlightMode: PdfHighlightMode.outline,
        borderStyle: PdfBorderStyle.dot,
        borderColor: PdfColor(230, 0, 172),
        foreColor: PdfColor(0, 255, 0),
        borderWidth: 1)
],
selectedIndex: 0,
));

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

### Retrieving option values from the acroform radio button

The Flutter PDF supports retrieving values from the acroform radio button. The value property is used to get values of the PdfRadioButtonListItem instance.

The following code example shows how to get values from the acroform radio button.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

// Get a radio button and select the item.
final PdfField radioButtonListField = document.form.fields[0];
if (radioButtonListField is PdfRadioButtonListField &&
    radioButtonListField.selectedIndex != 1) {
  radioButtonListField.selectedValue = radioButtonListField.items[1].value;
}

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

### Adding the list box field

You can create the list box field in PDF forms using the PdfListBoxField class.

Please refer to the following code sample for adding the list box field in a new PDF document.

{% highlight dart %}

//Create a new PDF document.
final PdfDocument document = PdfDocument();

// Create a list form field and add it to the document.
document.form.fields.add(PdfListBoxField(
    document.pages.add(), 'listBox', Rect.fromLTWH(100, 100, 100, 50),
    alignment: PdfTextAlignment.center,
    items: [
    PdfListFieldItem('Tamil', 'Language 1'),
    PdfListFieldItem('English', 'Language 2'),
    PdfListFieldItem('French', 'Language 3')
    ],
    selectedValues: [
    'Tamil'
    ]));
document.form.setDefaultAppearance(true);

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

Please refer to the following code sample for adding the list box field in an existing PDF document.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

// Create a list form field and add it to the existing document.
document.form.fields.add(PdfListBoxField(
    document.pages[0], 'listBox', Rect.fromLTWH(100, 100, 100, 50),
    alignment: PdfTextAlignment.center,
    items: [
    PdfListFieldItem('Tamil', 'Language 1'),
    PdfListFieldItem('English', 'Language 2'),
    PdfListFieldItem('French', 'Language 3')
    ],
    selectedValues: [
    'Tamil'
    ]));
document.form.setDefaultAppearance(true);

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

### Adding the check Box field

You can create the check box field in PDF forms using the PdfCheckBoxField class.

Please refer to the following code sample for adding the check box field in a new PDF document.

{% highlight dart %}

//Create a new PDF document.
final PdfDocument document = PdfDocument();

// Create a list form field and add it to the document.
document.form.fields.add(PdfCheckBoxField(
    document.pages.add(), 'CheckBox', Rect.fromLTWH(100, 200, 70, 45),
    highlightMode: PdfHighlightMode.push,
    borderStyle: PdfBorderStyle.dot,
    borderColor: PdfColor(230, 0, 172),
    backColor: PdfColor(153, 255, 102),
    foreColor: PdfColor(255, 153, 0),
    borderWidth: 1,
    style: PdfCheckBoxStyle.diamond,
    isChecked: true));

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

Please refer to the following code sample for adding the check box field in an existing PDF document.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

// Create a check box form field and add it to the existing document.
document.form.fields.add(PdfCheckBoxField(
    document.pages.add(), 'CheckBox', Rect.fromLTWH(100, 200, 70, 45),
    highlightMode: PdfHighlightMode.push,
    borderStyle: PdfBorderStyle.dot,
    borderColor: PdfColor(230, 0, 172),
    backColor: PdfColor(153, 255, 102),
    foreColor: PdfColor(255, 153, 0),
    borderWidth: 1,
    style: PdfCheckBoxStyle.diamond,
    isChecked: true));

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

### Adding the signature field

You can add the signature field in PDF forms using the PdfSignatureField class.

Please refer to the following code sample for adding the signature field in a new PDF document.

{% highlight dart %}

//Create a new PDF document.
final PdfDocument document = PdfDocument();

// Create a signature form field and add it to the document.
document.form.fields.add(PdfSignatureField(document.pages.add(), 'Sign',
    bounds: Rect.fromLTWH(100, 100, 100, 50)));

//Save the PDF document.
File('output.pdf').writeAsBytesSync(document.save());

{% endhighlight %}

Please refer to the following code sample for adding the signature field in an existing PDF document.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

// Create a signature form field and add it to the existing document.
document.form.fields.add(PdfSignatureField(document.pages[0], 'Sign',
    bounds: Rect.fromLTWH(100, 100, 100, 50)));

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

### Adding the button field

To create button fields in PDF forms, you can use the PdfButtonField class.

The following code explains how to add the button field in a new PDF document.

{% highlight dart %}

//Create a new PDF document.
final PdfDocument document = PdfDocument();

// Create a list form field and add it to the document.
document.form.fields.add(PdfButtonField(
    document.pages.add(), 'Button field', Rect.fromLTWH(10, 10, 130, 40),
    text: 'submit',
    font: PdfStandardFont(PdfFontFamily.timesRoman, 14),
    backColor: PdfColor(0, 255, 120),
    borderColor: PdfColor(255, 131, 0),
    foreColor: PdfColor(201, 130, 255),
    highlightMode: PdfHighlightMode.push,
    borderWidth: 5,
    borderStyle: PdfBorderStyle.dashed)
..addPrintAction());

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

Please refer to the following code sample for adding the button field in an existing PDF document.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

// Create a PDF button form field and add it to the existing document.
document.form.fields.add(PdfButtonField(
    document.pages[0], 'Button field', Rect.fromLTWH(10, 10, 130, 40),
    text: 'submit',
    font: PdfStandardFont(PdfFontFamily.timesRoman, 14),
    backColor: PdfColor(0, 255, 120),
    borderColor: PdfColor(255, 131, 0),
    foreColor: PdfColor(201, 130, 255),
    highlightMode: PdfHighlightMode.push,
    borderWidth: 5,
    borderStyle: PdfBorderStyle.dashed)
..addPrintAction());

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

## Set appearance to the PDF form fields

After filling the form fields in the PDF document, it may appear empty due to the absence of the appearance dictionary. By setting the setDefaultAppearance method in PdfForm class to false, you can create the appearance dictionary. By this, the text will be visible in all PDF Viewers. 

The following code sample explains how to set appearance to the PDF form fields.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Set the default appearance.
document.form.setDefaultAppearance(true);

//Get the loaded form field and update text.
(document.form.fields[0] as PdfTextBoxField).text = 'Updated';

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

## Modifying the existing form field in a PDF document

You can modify an existing form field by getting the field from the PdfFormFieldCollection. You can retrieve a field from the field collection by index.

The following code sample explains how to modify an existing form field in a PDF document.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Get the loaded form field and modify the properties.
final PdfField field = document.form.fields[0];
if (field is PdfTextBoxField) {
  field.multiline = false;
  field.isPassword = false;
  field.text = 'new Text';
  field.maxLength = 0;
  field.spellCheck = false;
  field.defaultValue = 'new defaultValue';
  field.scrollable = false;
}

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());
{% endhighlight %}

Retrieving or Modifying the fore, border, and back color of an existing form field

You can retrieve or modify the fore, border, and background color of existing form fields in a PDF document by using the foreColor, borderColor, and backColor properties of the respective form fields. The following code sample explains this.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Get the loaded form field.
final PdfField field = document.form.fields[0];

if (field is PdfTextBoxField) {
  //Get colors from the loaded field.
  PdfColor fColor = field.foreColor;
  PdfColor brColor = field.borderColor;
  PdfColor bColor = field.backColor;

  //Set colors for the loaded field.
  field.foreColor = brColor;
  field.borderColor = bColor;
  field.backColor = fColor;
}
//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

## Retrieving Actions from a Form Field

In PDF documents, form fields can have associated actions that dictate behavior when a user interacts with the field. You can retrieve these actions from a form field using the PdfFieldActions property. This property is read-only and provides the actions currently associated with a field.

The following code sample demonstrates how to retrieve actions from an existing form field in a PDF document.

{% highlight dart %}
// Load an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

// Get the form field from which you want to retrieve actions.
final PdfButtonField buttonField = document.form.fields[0] as PdfButtonField;

// Retrieve and process the actions of the form field.
final PdfFieldActions actions = buttonField.actions;
// Check if actions are not null and perform a test.
if (actions != null) {
// Check for specific known action properties or behaviors.
  print('Actions are present for the field.');
} else {
  print('No actions associated with the field.');
}

{% endhighlight %}

## Filling form fields in an existing PDF Document

Flutter PDF allows you to fill the form fields using the PdfField class.

### Filling the text box field

You can fill a text box field using the text property of PdfTextBoxField class. The following code sample explains this.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Get the loaded form field and update text.
(document.form.fields[0] as PdfTextBoxField).text = 'Updated';

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

### Filling the combo box field

You can fill a combo box field using the selectedValue or selectedIndex properties of PdfLoadedComboBoxField class. Please refer to the following code sample to fill the combo box field in an existing PDF document.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

// Get a combo box field and select the item.
final PdfField comboBox = document.form.fields[0];
if (comboBox is PdfComboBoxField && comboBox.selectedIndex != 1) {
  comboBox.selectedValue = comboBox.items[1].value;
}

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

### Filling the radio button field

You can fill a radio button field using the selectedValue or selectedIndex properties of PdfRadioButtonListField class. Please refer to the following code sample to fill the radio button field in an existing PDF document.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

// Get a radio button and select the item.
final PdfField radioButtonListField = document.form.fields[0];
if (radioButtonListField is PdfRadioButtonListField &&
    radioButtonListField.selectedIndex != 1) {
  radioButtonListField.selectedValue = radioButtonListField.items[1].value;
}

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

### Filling the list box field

The following code sample explains how to fill the list box field in an existing PDF document using the selectedIndex property of PdfListBoxField class.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

// Get a list box field and select the items.
(document.form.fields[0] as PdfListBoxField).selectedIndexes = [1,3];

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

### Filling the check box field

You can fill a check box field by enabling the checked property of PdfCheckBoxField class. Please refer to the following code sample to fill the check box field.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

// Get and fill the check box field.
(document.form.fields[0] as PdfCheckBoxField).isChecked = true;

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

### Enumerate the form fields

All the form fields are maintained in the PdfFormFieldCollection class. You can enumerate the fields from this form field collection and fill them.

The following code example explains this.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Enumerates the form fields.
for (int i = 0; i < document.form.fields.count; i++) {
  PdfField field = document.form.fields[i];
  if (field is PdfTextBoxField) {
    field.text = 'Updated';
  }
}

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

## Removing editing capability of form fields

The form field editing or filling capabilities can be removed by either flattening the PDF document or marking the form or field as read-only.

Flutter PDF provides the support to flatten a form field by removing the existing form field and replacing it with graphical objects that would resemble the form field and cannot be edited.

Please refer to the sample for flattening the form fields in a new PDF document.

{% highlight dart %}

//Create a new PDF document.
final PdfDocument document = PdfDocument();

//Flatten the whole form fields.
document.form.flattenAllFields();

// Create a textbox form field and add it to the document.
document.form.fields.add(PdfTextBoxField(
    document.pages.add(), 'TextBox', Rect.fromLTWH(100, 20, 200, 20),
    text: 'toType', isPassword: true, spellCheck: true));

//Save the PDF document.
File('output.pdf').writeAsBytesSync(document.save());

{% endhighlight %}

Please refer to the sample for flattening the form fields in an existing PDF document.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

// Get and fill the text box field.
(document.form.fields[0] as PdfTextBoxField).text = 'Updated';

//Flatten the whole existing form fields. 
document.form.flattenAllFields();

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

To prevent the user from changing the form field content, you can also use the readOnly property.

The following code sample explains how to set the readOnly property to a new PDF document.

{% highlight dart %}

//Create a new PDF document.
final PdfDocument document = PdfDocument();

//Set the form as read-only.
document.form.readOnly = true;

// Create a text box form field and add it to the document.
document.form.fields.add(PdfTextBoxField(
    document.pages.add(), 'TextBox', Rect.fromLTWH(100, 20, 200, 20),
    text: 'toType', isPassword: true, spellCheck: true));

//Save the PDF document.
File('output.pdf').writeAsBytesSync(document.save());

{% endhighlight %}

The following code sample explains how to set the ReadOnly property to an existing PDF document.

{% highlight dart %}

//Loads an existing PDF document and set the form as read-only.
PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync())
    ..form.readOnly = true;

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

## Removing the form fields from the existing PDF document

You can remove the form fields from an existing PDF document using the remove or removeAt methods of PdfFormFieldCollection class.

The following code explains how to remove the form fields from the existing PDF document.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Get the loaded form.
PdfFormFieldCollection collection = document.form.fields;

//Remove the field at index 1.
collection.removeAt(1);

//Remove the field.
collection.remove(collection[0]);

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

## Auto naming of form fields

Flutter PDF supports auto naming of form fields in a PDF document while creating form fields with the same name. The fieldAutoNaming property of PdfForm is used to enable or disable auto naming of a form field.

While enabling this property, the field names are auto naming. If the fields are created using the same or common name, the created fields will act as an individual.

While disabling this property, the field names are not auto naming, and the created fields are saved in a single group. The same value will be referred in all the same name fields.

By default, the value is set to true. This is explained in the following code sample.

{% highlight dart %}

//Create a new PDF document.
final PdfDocument document = PdfDocument();

//Enable the field auto naming.
document.form.fieldAutoNaming = true;

// Create a text box form field and add it to the document.
document.form.fields.add(PdfTextBoxField(
    document.pages.add(), 'TextBox', Rect.fromLTWH(100, 20, 200, 20),
    text: 'First name', spellCheck: true));

// Create a text box form field and add it to the document.
document.form.fields.add(PdfTextBoxField(
    document.pages[0], 'TextBox', Rect.fromLTWH(100, 50, 200, 20),
    text: 'Last name', spellCheck: true));

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

## Adding an action to the form field

Flutter PDF provides support to add various actions to the form fields. The PdfFieldActions class is used to create the form field actions.

The following code example explains this.

{% highlight dart %}

//Create a new PDF document.
final PdfDocument document = PdfDocument();

//Create a button field with the filed actions and added to the form fields.
document.form.fields.add(PdfButtonField(document.pages.add(),
    'Submit with actions', Rect.fromLTWH(100, 60, 50, 20),
    actions: PdfFieldActions(
    PdfAnnotationActions(
        mouseEnter: PdfSubmitAction('https://www.google.co.in/',
            dataFormat: SubmitDataFormat.pdf, submitCoordinates: true)),
    keyPressed: PdfJavaScriptAction(
        'app.alert(\"You are looking at Java script action of PDF \")'),
    )));

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

## Importing FDF file to PDF

FDF (Forms Data Format) is a file format for representing form data and annotations that are contained in a PDF form. You can import the FDF file to PDF using the importData method available in the ['PdfForm'](#) class.

The following code sample explains how to import the FDF file to PDF.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Import the FDF into the existing form.
document.form
  .importData(File('Import.fdf').readAsBytesSync(), DataFormat.fdf);

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

## Importing XFDF file to PDF

XFDF (XML Forms Data Format) is used to save the form data that can be imported into a PDF document. You can import the XFDF file to PDF using the importData method available in the ['PdfForm'](#) class.

The following code sample explains how to import the XFDF file to PDF.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Import the XFDF into the existing form.
document.form
  .importData(File('Import.xfdf').readAsBytesSync(), DataFormat.xfdf);

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

## Importing JSON file to PDF

JSON (JavaScript Object Notation) file is used to save the form data that can be imported into a PDF document. You can import the JSON file to PDF using the importData method available in the ['PdfForm'](#) class.

The following code sample explains how to import JSON files to PDF.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Import the JSON into the existing form.
document.form
  .importData(File('Import.json').readAsBytesSync(), DataFormat.json);

//Enable the form default appearance.
document.form.setDefaultAppearance(true);

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

## Importing XML file to PDF

XML stands for an extensible markup language. The XML file is used to save the form data that can be imported into a PDF document. You can import the JSON file to PDF using the importData method available in the ['PdfForm'](#) class.

The following code sample explains how to import XML files to PDF.

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Import the XML into the existing form.
document.form
  .importData(File('Import.xml').readAsBytesSync(), DataFormat.xml);

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}

## Export PDF file to FDF

To export the FDF file from a PDF document, you can use the exportData method available in the ['PdfForm'](#) class.

The following code sample explains how to export the FDF file from a PDF document.

{% highlight dart %}

//Load the existing PDF document.
PdfDocument document = PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Export the form data to FDF format.
File('Export.fdf').writeAsBytesSync(document.form.exportData(DataFormat.fdf));

//Dispose the PDF document.
document.dispose();

{% endhighlight %}

## Export PDF file to XFDF

To export the XFDF file from a PDF document, you can use the exportData method available in the ['PdfForm'](#) class.

The following code sample explains how to export the XFDF file from a PDF document.

{% highlight dart %}

//Load the existing PDF document.
PdfDocument document = PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Export the form data to XFDF format.
File('Export.xfdf').writeAsBytesSync(document.form.exportData(DataFormat.xfdf));

//Dispose the PDF document.
document.dispose();

{% endhighlight %}

## Export PDF file to JSON

To export the JSON file from a PDF document, you can use the exportData method available in the ['PdfForm'](#) class.

The following code sample explains how to export JSON files from a PDF document.

{% highlight dart %}
//Load the existing PDF document.
PdfDocument document = PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Export the form data to JSON format.
File('Export.json').writeAsBytesSync(document.form.exportData(DataFormat.json));

//Dispose the PDF document.
document.dispose();

{% endhighlight %}

## Export PDF file to XML

To export the XML file from a PDF document, you can use the exportData method available in the ['PdfForm'](#) class.

The following code sample explains how to export an XML file from a PDF document.

{% highlight dart %}

//Load the existing PDF document.
PdfDocument document = PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

//Export the form data to XML format.
File('Export.xml').writeAsBytesSync(document.form.exportData(DataFormat.xml));

//Dispose the PDF document.
document.dispose();

{% endhighlight %}


## Troubleshooting

Sometimes, Form fields may appear empty in an adobe reader due to the absence of the appearance dictionary. To resolve this, you need to enable the Adobe Reader default appearance by using the setDefaultAppearance method in PdfForm class.

The following code explains how to enable the default appearance in a new PDF document. 

{% highlight dart %}

//Loads an existing PDF document.
final PdfDocument document =
    PdfDocument(inputBytes: File('input.pdf').readAsBytesSync());

// Create a list form field and add it to the existing document.
document.form.fields.add(PdfListBoxField(
    document.pages[0], 'listBox', Rect.fromLTWH(100, 100, 100, 50),
    alignment: PdfTextAlignment.center,
    items: [
    PdfListFieldItem('Tamil', 'Language 1'),
    PdfListFieldItem('English', 'Language 2'),
    PdfListFieldItem('French', 'Language 3')
    ],
    selectedValues: [
    'Tamil'
    ]));
document.form.setDefaultAppearance(true);

//Save the PDF document.
File('output.pdf').writeAsBytesSync(await document.save());

{% endhighlight %}