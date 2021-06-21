---
layout: post
title: Accessibility in Flutter PDF Viewer widget | Syncfusion
description: Learn here all about the accessibility feature of the Syncfusion Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: Flutter
control: SfPdfViewer
documentation: ug
---

# Accessibility in Flutter PDF Viewer (SfPdfViewer)

## Sufficient contrast

The `SfPdfViewer` [theming](https://help.syncfusion.com/flutter/themes/themes) support provides a consistent and standardized appearance, as well as the ability to set the colors for all UI elements.

The following APIs allow you to customize the colors of the following elements.
* [searchTextHighlightColor](https://help.syncfusion.com/flutter/pdf-viewer/text-search#customize-the-search-text-highlight-color)
* [selectionColor and selectionHandleColor](https://help.syncfusion.com/flutter/pdf-viewer/text-selection#customize-the-text-selection-and-its-handle-color)

## Large fonts

The font size of the [`SfPdfViewer`](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) will be automatically scaled based on the device settings. 

Also, you can change the font size of the [`SfPdfViewer`](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) elements using the following APIs:

* [`Pagination dialog style`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfPdfViewerThemeData/paginationDialogStyle.html)
* [`Bookmark view style`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfPdfViewerThemeData/bookmarkViewStyle.html)
* [`Scroll head style`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfPdfViewerThemeData/scrollHeadStyle.html)
* [`Scroll status style`](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfPdfViewerThemeData/scrollStatusStyle.html)

## Keyboard navigation

The `SfPdfViewer` supports the following keyboard interactions.

<table>
  <tr>
  <tr>
    <th  style="text-align:left" colspan="2">Key</th>
    <th>Description</th>
    </tr>
     <tr>
    <th style="text-align:left">Windows</th>
    <th style="text-align:left">macOs</th>
  </tr>
     <tr>
  <th style="text-align:left" colspan="3">Shortcuts for page navigation</th>
  </tr>
  <tr>
    <td>Home</td>
    <td>fn+Left arrow</td>
    <td>Navigate to the first page</td>
  </tr>
  <tr>
    <td>End</td>
    <td>fn+Right arrow</td>
    <td>Navigate to the last page</td>
  </tr>
  <tr>
    <td>Left arrow</td>
    <td>Left arrow</td>
    <td>Navigate to the previous page</td>
  </tr>
  <tr>
    <td>Right arrow</td>
    <td>Right arrow</td>
    <td>Navigate to the next page</td>
  </tr>
   <tr>
    <th style="text-align:left" colspan="3">Shortcuts for Zooming</th>
  </tr>
   <tr>
    <td>Ctrl + =</td>
     <td>command + =</td>
    <td>Perform zoom in operation</td>
  </tr>
  <tr>
  </tr>
   <tr>
    <td>Ctrl + -</td>
    <td>command + -</td>
    <td>Perform zoom out operation</td>
  </tr>
  <tr>
    <td>Ctrl + 0</td>
    <td>command + 0</td>
    <td>Retain the zoom level to 1</td>
  </tr>
   <tr>
    <th style="text-align:left" colspan="3">Shortcut for Text Search</th>
  </tr>
  <tr>
    <td>Ctrl + f</td>
     <td>command + f</td>
    <td>Open the search toolbar</td>
  </tr>
   <tr>
    <th style="text-align:left" colspan="3">Shortcut for Text Selection</th>
  </tr>
  <tr>
    <td>Ctrl + c</td>
    <td>command + c</td>
    <td>Copy the selected text</td>
  </tr>
</table>