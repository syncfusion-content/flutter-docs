---
layout: post
title: Undo and redo annotations in the Flutter PDF Viewer | Syncfusion<sup>&reg;</sup>
description: Learn here all about Undo and Redo actions on the annotations in Syncfusion<sup>&reg;</sup> Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Undo and redo annotations in the Flutter PDF Viewer (Syncfusion<sup>&reg;</sup>)

If you performed any undesired actions when adding, removing, or editing annotations, you can undo and redo the action to restore the previous state. This section will go through how to undo and redo the changes made to the annotations.

For desktop platforms such as Windows, macOS, and desktop web, you can use the following shortcut keys to perform the actions.

<table>
<tr>
<th>Action & Shortcut keys</th>
<th>Windows</th>
<th>macOS</th>
</tr>
<tr>
<th>Undo</th>
<td><code>Ctrl</code> + <code>z</code></td>
<td><code>Command</code> + <code>z</code></td>
</tr>
<tr>
<th>Redo</th>
<td><code>Ctrl</code> + <code>y</code></td>
<td><code>Command</code> + <code>y</code></td>
</tr>
</table>

You can perform the undo and redo operations in the `SfPdfViewer` by assigning the `UndoHistoryController` instance to the `undoController` property of the `SfPdfViewer`. The UndoHistoryController class contains the `undo` and `redo` methods to perform the undo and redo operations, respectively. The `canUndo` and `canRedo` properties check whether the undo and redo operations can be performed, respectively. The following code example illustrates how to perform the undo and redo operations programmatically in the `SfPdfViewer` with the help of the UndoHistoryController class.

{% tabs %}
{% highlight dart hl_lines="12 13 21 22 29" %}

final UndoHistoryController _undoController = UndoHistoryController();

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      appBar: AppBar(actions: [
        ValueListenableBuilder(
            valueListenable: _undoController,
            builder: (context, value, child) {
              return IconButton(
                onPressed:
                    _undoController.value.canUndo ? _undoController.undo : null,
                icon: const Icon(Icons.undo),
              );
            }),
        ValueListenableBuilder(
            valueListenable: _undoController,
            builder: (context, value, child) {
              return IconButton(
                onPressed:
                    _undoController.value.canRedo ? _undoController.redo : null,
                icon: const Icon(Icons.redo),
              );
            }),
      ]),
      body: SfPdfViewer.network(
        'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
        undoController: _undoController,
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

N> This `undoController` is common for annotations and form fields. You do not need to create separate instances for both.