---
layout: post
title: Text selection in Flutter PDF Viewer widget | Syncfusion<sup>&reg;</sup>
description: Learn here all about text selection feature of Syncfusion<sup>&reg;</sup> Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Text selection in Flutter PDF Viewer (SfPdfViewer)

On a touch device, the [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) allows you to select a text in the PDF page by long pressing on it, which in turn displays the selection handles or bubbles at the top-left and bottom-right corners of its bounds. Then, you can use the left handle to select the text at the left and top, and the right handle to select the text at the right and bottom directions.

And on a desktop web browser, the text selection can also be performed using mouse dragging with the [`selection`](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfInteractionMode.html) interaction mode enabled.

N> The images in the document will not be selected and, the multiple-page text selection is not supported for now. 

## Enable or disable text selection

You can enable or disable the text selection in the PDF page using the [enableTextSelection](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/enableTextSelection.html) property. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="6" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
              enableTextSelection: false));
}

{% endhighlight %}
{% endtabs %}

N> On a desktop web browser, this `enableTextSelection` property will have no effect on the [`pan`](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfInteractionMode.html) interaction mode.

## Customize the text selection and its handle color

The [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) allows you to customize the color used for text selection and its handle based on your requirements. The properties [selectionColor](https://api.flutter.dev/flutter/material/TextSelectionThemeData/selectionColor.html) and [selectionHandleColor](https://api.flutter.dev/flutter/material/TextSelectionThemeData/selectionHandleColor.html) of the [TextSelectionThemeData](https://api.flutter.dev/flutter/material/TextSelectionThemeData-class.html) class can be used to customize them. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="3 4 5 6" %}

void main() => runApp(MaterialApp(
      title: 'Syncfusion PDF Viewer Demo',
      theme: ThemeData(
        textSelectionTheme: TextSelectionThemeData(
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
          title: Text('Syncfusion Flutter PDF Viewer'),
        ),
        body: Container(
            child: SfPdfViewer.network(
          'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
        )));
  }
}

{% endhighlight %}
{% endtabs %}

## Customize the visibility of the text selection context menu

The `canShowTextSelectionMenu` property allows the user to customize the visibility of the built-in text selection context menu. You can assign `false` to this property to disable the text selection context menu. The following code example explains how to disable the built-in text selection context menu in the PDF viewer.

{% tabs %}
{% highlight dart hl_lines="7" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Container(
      child: SfPdfViewer.network(
        'https://cdn.syncfusion.com/content/PDFViewer/encrypted.pdf',
        canShowTextSelectionMenu: false,
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Callbacks

The `SfPdfViewer` text selection supports the [PdfTextSelectionChangedCallback](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSelectionChangedCallback.html) to notify the text selection changes.

### Text selection changed callback

The [onTextSelectionChanged](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onTextSelectionChanged.html) callback triggers when the text is selected or deselected in the SfPdfViewer. The [PdfTextSelectionChangedDetails](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSelectionChangedDetails-class.html) will hold the [globalSelectedRegion](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSelectionChangedDetails/globalSelectedRegion.html) representing the global bounds information of the selected text region and the [selectedText](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSelectionChangedDetails/selectedText.html) representing the selected text value. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="9 10 11 12 13" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      appBar: AppBar(
        title: Text('Syncfusion Flutter PDF Viewer'),
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

## How to get the selected text lines in the PDF viewer?

Using the [getSelectedTextLines](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewerState/getSelectedTextLines.html) method, you can get the selected text lines in the PDF viewer. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="10 11" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: const Text('Syncfusion Flutter PDF Viewer'),
      actions: <Widget>[
        IconButton(
          icon: const Icon(Icons.add),
          onPressed: () async {
            final List<PdfTextLine>? selectedTextLines =
                _pdfViewerKey.currentState?.getSelectedTextLines();

            if (selectedTextLines != null && selectedTextLines.isNotEmpty) {
              // Creates a highlight annotation with the selected text lines.
              final HighlightAnnotation highlightAnnotation =
                  HighlightAnnotation(
                textBoundsCollection: selectedTextLines,
              );
              // Adds the highlight annotation to the PDF document.
              _pdfViewerController.addAnnotation(highlightAnnotation);
            }
          },
        ),
      ],
    ),
    body: SfPdfViewer.asset(
      'assets/sample.pdf',
      key: _pdfViewerKey,
      controller: _pdfViewerController,
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## How to create and display a customized text selection context menu with copy and text markup options to retrieve the selected text?

With the options available in `SfPdfViewer` text selection, you can easily create and display a customized text selection context menu with various options such as **Copy, Highlight, Underline, Strikethrough, and Squiggly**, and perform operations with them. The following code example explains how to implement this functionality.

In this example, we use the [OverlayEntry](https://api.flutter.dev/flutter/widgets/OverlayEntry-class.html) widget to create the customized context menu and add buttons for various options, such as Copy, Highlight, Underline, Strikethrough, and Squiggly. We are calling the method to display the customized context menu in the [onTextSelectionChanged](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onTextSelectionChanged.html) callback. Whenever one of these options is pressed, the corresponding action is performed on the selected text.

* For the copy operation, the selected text value is retrieved from the'selectedText` property of the [onTextSelectionChanged](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/onTextSelectionChanged.html) callback details. We then copy the text to the clipboard using the [Clipboard.setData](https://api.flutter.dev/flutter/services/Clipboard/setData.html) method.
The text selection is cleared after the Copy operation by calling the [clearSelection](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/clearSelection.html) controller method.

* For the text markup options, we retrieve the selected text lines using the [getSelectedTextLines](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewerState/getSelectedTextLines.html) method and add the respective annotations using the [addAnnotation](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/addAnnotation.html) method on the `PdfViewerController`.

{% tabs %}
{% highlight Dart %}

import 'package:flutter/material.dart';
import 'package:flutter/services.dart';
import 'package:syncfusion_flutter_pdfviewer/pdfviewer.dart';

void main() => runApp(const MaterialApp(
      title: 'Syncfusion PDF Viewer Demo',
      home: HomePage(),
    ));

/// Represents Homepage for Navigation
class HomePage extends StatefulWidget {
  const HomePage({super.key});

  @override
  State<HomePage> createState() => _HomePageState();
}

class _HomePageState extends State<HomePage> {
  late PdfViewerController _pdfViewerController;
  OverlayEntry? _overlayEntry;
  final GlobalKey<SfPdfViewerState> _pdfViewerKey = GlobalKey();

  @override
  void initState() {
    _pdfViewerController = PdfViewerController();
    super.initState();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Syncfusion Flutter PDF Viewer'),
      ),
      body: SfPdfViewer.network(
        'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
        onTextSelectionChanged: (PdfTextSelectionChangedDetails details) {
          if (details.selectedText == null && _overlayEntry != null) {
            _overlayEntry!.remove();
            _overlayEntry = null;
          } else if (details.selectedText != null && _overlayEntry == null) {
            _showContextMenu(context, details);
          }
        },
        key: _pdfViewerKey,
        controller: _pdfViewerController,
        canShowTextSelectionMenu: false,
      ),
    );
  }

  void _showContextMenu(
      BuildContext context, PdfTextSelectionChangedDetails details) {
    const double height = 250;
    const double width = 150;
    final OverlayState overlayState = Overlay.of(context);
    final Size screenSize = MediaQuery.of(context).size;

    double top = details.globalSelectedRegion!.top >= screenSize.height / 2
        ? details.globalSelectedRegion!.top - height - 10
        : details.globalSelectedRegion!.bottom + 20;
    top = top < 0 ? 20 : top;
    top = top + height > screenSize.height
        ? screenSize.height - height - 10
        : top;

    double left = details.globalSelectedRegion!.bottomLeft.dx;
    left = left < 0 ? 10 : left;
    left =
        left + width > screenSize.width ? screenSize.width - width - 10 : left;
    _overlayEntry = OverlayEntry(
      builder: (BuildContext context) => Positioned(
        top: top,
        left: left,
        child: Container(
          decoration: BoxDecoration(
            color: Colors.white,
            borderRadius: BorderRadius.circular(4),
            boxShadow: const <BoxShadow>[
              BoxShadow(
                color: Colors.black26,
                blurRadius: 4,
                offset: Offset(2, 2),
              ),
            ],
          ),
          constraints:
              const BoxConstraints.tightFor(width: width, height: height),
          child: Column(
            mainAxisAlignment: MainAxisAlignment.spaceEvenly,
            children: <Widget>[
              TextButton(
                onPressed: () {
                  if (details.selectedText != null) {
                    Clipboard.setData(
                        ClipboardData(text: details.selectedText!));
                    print('Text copied to clipboard: ${details.selectedText}');
                    _pdfViewerController.clearSelection();
                  }
                },
                child: const Text('Copy', style: TextStyle(fontSize: 15)),
              ),
              TextButton(
                onPressed: () {
                  final List<PdfTextLine>? textLines =
                      _pdfViewerKey.currentState?.getSelectedTextLines();
                  if (textLines != null && textLines.isNotEmpty) {
                    final HighlightAnnotation highlightAnnotation =
                        HighlightAnnotation(
                      textBoundsCollection: textLines,
                    );
                    _pdfViewerController.addAnnotation(highlightAnnotation);
                  }
                },
                child: const Text('Highlight', style: TextStyle(fontSize: 15)),
              ),
              TextButton(
                onPressed: () {
                  final List<PdfTextLine>? textLines =
                      _pdfViewerKey.currentState?.getSelectedTextLines();
                  if (textLines != null && textLines.isNotEmpty) {
                    final UnderlineAnnotation underLineAnnotation =
                        UnderlineAnnotation(
                      textBoundsCollection: textLines,
                    );
                    _pdfViewerController.addAnnotation(underLineAnnotation);
                  }
                },
                child: const Text('Underline', style: TextStyle(fontSize: 15)),
              ),
              TextButton(
                onPressed: () {
                  final List<PdfTextLine>? textLines =
                      _pdfViewerKey.currentState?.getSelectedTextLines();
                  if (textLines != null && textLines.isNotEmpty) {
                    final StrikethroughAnnotation strikethroughAnnotation =
                        StrikethroughAnnotation(
                      textBoundsCollection: textLines,
                    );
                    _pdfViewerController.addAnnotation(strikethroughAnnotation);
                  }
                },
                child:
                    const Text('Strikethrough', style: TextStyle(fontSize: 15)),
              ),
              TextButton(
                onPressed: () {
                  final List<PdfTextLine>? textLines =
                      _pdfViewerKey.currentState?.getSelectedTextLines();
                  if (textLines != null && textLines.isNotEmpty) {
                    final SquigglyAnnotation squigglyAnnotation =
                        SquigglyAnnotation(
                      textBoundsCollection: textLines,
                    );
                    _pdfViewerController.addAnnotation(squigglyAnnotation);
                  }
                },
                child: const Text('Squiggly', style: TextStyle(fontSize: 15)),
              ),
            ],
          ),
        ),
      ),
    );
    overlayState.insert(_overlayEntry!);
  }
}

{% endhighlight %}
{% endtabs %}