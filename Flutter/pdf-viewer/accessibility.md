---
layout: post
title: Accessibility in Flutter PDF Viewer widget | Syncfusion
description: Learn here all about the accessibility feature of the Syncfusion® Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Accessibility in Flutter PDF Viewer (SfPdfViewer)

## Screen Reader

The [`SfPdfViewer`](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) can be accessed by screen readers by wrapping the [`SfPdfViewer`](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) widget with the [`Semantics`](https://api.flutter.dev/flutter/widgets/Semantics-class.html) widget.

{% tabs %}
{% highlight dart hl_lines="4 5 6 7 8 9" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Semantics(
      label: 'Flutter PDF Viewer',
      child:
         SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf'),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Sufficient Contrast

The `SfPdfViewer` [theming](https://help.syncfusion.com/flutter/themes) support provides a consistent and standardized appearance, as well as the ability to set the colors for all UI elements.

The following APIs allow you to customize the colors of the following elements:
* [searchTextHighlightColor](https://help.syncfusion.com/flutter/pdf-viewer/text-search#customize-the-search-text-highlight-color)
* [selectionColor and selectionHandleColor](https://help.syncfusion.com/flutter/pdf-viewer/text-selection#customize-the-text-selection-and-its-handle-color)

## Large Fonts

The font size of the [`SfPdfViewer`](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) will be automatically scaled based on the device settings. 

Also, you can change the font size of the [`SfPdfViewer`](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) elements using the following APIs:

* [`Pagination dialog style`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfPdfViewerThemeData/paginationDialogStyle.html)
* [`Bookmark view style`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfPdfViewerThemeData/bookmarkViewStyle.html)
* [`Scroll head style`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfPdfViewerThemeData/scrollHeadStyle.html)
* [`Scroll status style`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfPdfViewerThemeData/scrollStatusStyle.html)

## Keyboard Navigation

The `SfPdfViewer` supports the following keyboard interactions:

<table>
  <tr>
    <th style="text-align:left" colspan="1">Action</th>
    <th>Windows</th>
    <th>Macintosh</th>
    <th>Linux</th>
  </tr>
  <tr>
    <th style="text-align:left" colspan="4">Shortcuts for Page Navigation</th>
  </tr>
  <tr>
    <td>Navigate to the first page</td>
    <td>Home</td>
    <td>Function+Left arrow</td>
    <td>Home</td>
  </tr>
  <tr>
    <td>Navigate to the last page</td>
    <td>End</td>
    <td>Function+Right arrow</td>
    <td>End</td>
  </tr>
  <tr>
    <td>Navigate to the previous page</td>
    <td>Left arrow</td>
    <td>Left arrow</td>
    <td>Left arrow</td>
  </tr>
  <tr>
    <td>Navigate to the next page</td>
    <td>Right arrow</td>
    <td>Right arrow</td>
    <td>Right arrow</td>
  </tr>
  <tr>
    <th style="text-align:left" colspan="4">Shortcuts for Zooming</th>
  </tr>
  <tr>
    <td>Perform zoom in operation</td>
    <td>CONTROL + =</td>
    <td>COMMAND + =</td> 
    <td>CONTROL + =</td>
  </tr>
  <tr>
    <td>Perform zoom out operation</td>
    <td>CONTROL + -</td>
    <td>COMMAND + -</td>
    <td>CONTROL + -</td>
  </tr>
  <tr>
    <td>Reset the zoom level to 1</td>
    <td>CONTROL + 0</td>
    <td>COMMAND + 0</td>
    <td>CONTROL + 0</td>
  </tr>
  <tr>
    <th style="text-align:left" colspan="4">Shortcut for Text Search</th>
  </tr>
  <tr>
    <td>Open the search toolbar</td>
    <td>CONTROL + F</td>
    <td>COMMAND + F</td>
    <td>CONTROL + F</td>
  </tr>
  <tr>
    <th style="text-align:left" colspan="4">Shortcut for Text Selection</th>
  </tr>
  <tr>
    <td>Copy the selected text</td>
    <td>CONTROL + C</td>
    <td>COMMAND + C</td>
    <td>CONTROL + C</td>
  </tr>
</table>

## Easier Touch Targets

The [`SfPdfViewer`](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) has a touch target of 48 x 48, as per the standard for all elements.