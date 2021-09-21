---
layout: post
title: Text selection in Flutter PDF Viewer widget | Syncfusion
description: Learn here all about text selection feature of Syncfusion Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: Flutter
control: SfPdfViewer
documentation: ug
---

# Text selection in Flutter PDF Viewer (SfPdfViewer)

On a touch device, the [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) allows you to select a text in the PDF page by long pressing on it, which in turn displays the selection handles or bubbles at the top-left and bottom-right corners of its bounds. Then, you can use the left handle to select the text at the left and top, and the right handle to select the text at the right and bottom directions.

And on a desktop web browser, the text selection can also be performed using mouse dragging with the [`selection`](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfInteractionMode-class.html) interaction mode enabled.

N> The images in the document will not be selected and, the multiple-page text selection is not supported for now. 

## Enable or disable text selection

You can enable or disable the text selection in the PDF page using the [enableTextSelection](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/enableTextSelection.html) property. The following code example explains the same.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
              enableTextSelection: false));
}

{% endhighlight %}
{% endtabs %}

N> On a desktop web browser, this `enableTextSelection` property will have no effect on the [`pan`](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfInteractionMode-class.html) interaction mode.

## Customize the text selection and its handle color

The [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) allows you to customize the color used for text selection and its handle based on your requirements. The properties [selectionColor](https://api.flutter.dev/flutter/material/TextSelectionThemeData/selectionColor.html) and [selectionHandleColor](https://api.flutter.dev/flutter/material/TextSelectionThemeData/selectionHandleColor.html) of the [TextSelectionThemeData](https://api.flutter.dev/flutter/material/TextSelectionThemeData-class.html) class can be used to customize them. The following code example explains the same.

{% tabs %}
{% highlight Dart %}

import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_pdfviewer/pdfviewer.dart';

void main() => runApp(MaterialApp(
      title: 'Syncfusion PDF Viewer Demo',
      theme: ThemeData(
        textSelectionTheme: const TextSelectionThemeData(
            selectionColor: Colors.red, selectionHandleColor: Colors.blue),
      ),
      home: HomePage(),
    ));

/// Represents Homepage for Navigation
class HomePage extends StatefulWidget {
  @override
  _HomePageState createState() => _HomePageState();
}

class _HomePageState extends State<HomePage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: const Text('Syncfusion Flutter PDF Viewer'),
        ),
        body: Container(
            child: SfPdfViewer.network(
          'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
        )));
  }
}

{% endhighlight %}
{% endtabs %}

## Callbacks

The `SfPdfViewer` text selection supports the [PdfTextSelectionChangedCallback](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSelectionChangedCallback.html) to notify the text selection changes.

### Text selection changed callback

The [onTextSelectionChanged](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onTextSelectionChanged.html) callback triggers when the text is selected or deselected in the SfPdfViewer. The [PdfTextSelectionChangedDetails](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSelectionChangedDetails-class.html) will hold the [globalSelectedRegion](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSelectionChangedDetails/globalSelectedRegion.html) representing the global bounds information of the selected text region and the [selectedText](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSelectionChangedDetails/selectedText.html) representing the selected text value. The following code example explains the same.

{% tabs %}
{% highlight Dart %}

 @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: const Text('Syncfusion Flutter PDF Viewer'),
        ),
        body: SfPdfViewer.network(
          'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
          onTextSelectionChanged: (PdfTextSelectionChangedDetails details) {
            if (details.selectedText != null) {
              print(details.selectedText);
            }
          },
        ));
}

{% endhighlight %}
{% endtabs %}

## How to create and display a customized text selection context menu with a Copy option to retrieve the selected text?

With the options available in the `SfPdfViewer` text selection, you can easily create and display a customized text selection context menu with the **Copy** option and perform an operation for the same. The following code example explains the same.

In this example, we have used the [OverlayEntry](https://api.flutter.dev/flutter/widgets/OverlayEntry-class.html) widget to create the customized context menu and have added a simple button (for the Copy option) as a child to it. Whenever this Copy option is pressed, the selected text will be copied to the clipboard and the selection will be cleared. The selected text value is retrieved from the [onTextSelectionChanged](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onTextSelectionChanged.html) callback details and we have called the context menu displaying method within this callback implementation. The text selection gets cleared after the Copy operation by calling the [clearSelection](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/clearSelection.html) controller method.

{% tabs %}
{% highlight Dart %}

import 'package:flutter/material.dart';
import 'package:flutter/services.dart';
import 'package:syncfusion_flutter_pdfviewer/pdfviewer.dart';

void main() => runApp(MaterialApp(
      title: 'Syncfusion PDF Viewer Demo',
      home: HomePage(),
    ));

/// Represents Homepage for Navigation
class HomePage extends StatefulWidget {
  @override
  _HomePageState createState() => _HomePageState();
}

class _HomePageState extends State<HomePage> {
  late PdfViewerController _pdfViewerController;
  OverlayEntry? _overlayEntry;
  @override
  void initState() {
    _pdfViewerController = PdfViewerController();
    super.initState();
  }

  void _showContextMenu(
      BuildContext context, PdfTextSelectionChangedDetails details) {
    final OverlayState _overlayState = Overlay.of(context)!;
    _overlayEntry = OverlayEntry(
      builder: (BuildContext context) => Positioned(
        top: details.globalSelectedRegion!.center.dy - 55,
        left: details.globalSelectedRegion!.bottomLeft.dx,
        child: ElevatedButton(
          onPressed: () {
            Clipboard.setData(ClipboardData(text: details.selectedText));
            print(
                'Text copied to clipboard: ' + details.selectedText.toString());
            _pdfViewerController.clearSelection();
          },
          style: ButtonStyle(
            backgroundColor: MaterialStateProperty.all(Colors.white),
          ),
          child: const Text('Copy',
              style: TextStyle(fontSize: 17, color: Colors.black)),
        ),
      ),
    );
    _overlayState.insert(_overlayEntry!);
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: const Text('Syncfusion Flutter PDF Viewer'),
        ),
        body: Container(
            child: SfPdfViewer.network(
          'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
          onTextSelectionChanged: (PdfTextSelectionChangedDetails details) {
            if (details.selectedText == null && _overlayEntry != null) {
              _overlayEntry!.remove();
              _overlayEntry = null;
            } else if (details.selectedText != null && _overlayEntry == null) {
              _showContextMenu(context, details);
            }
          },
          controller: _pdfViewerController,
        )));
  }
}
{% endhighlight %}
{% endtabs %}