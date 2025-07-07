---
layout: post
title: Text search in Flutter PDF Viewer widget | Syncfusion
description: Learn here all about text search feature of Syncfusion® Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Text Search in Flutter PDF Viewer (SfPdfViewer)

The [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) allows you to find text in the PDF document and navigate to all its occurrences.

## Initiate Text Search and Retrieve Results

The [searchText](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfViewerController/searchText.html) controller method is used to initiate the text search and it takes the text to be searched and [TextSearchOption](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/TextSearchOption.html) as parameters. This method searches for the text, highlights all the instances of the text in the document, and returns the [PdfTextSearchResult](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSearchResult-class.html) object holding the result values such as total instance count, current highlighted instance index, and more. The [PdfTextSearchResult](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSearchResult-class.html) object will also help you navigate to the different searched text instances available and cancel the search operation.

On mobile and desktop platforms, the search will be performed asynchronously, so the results will be returned periodically on a page-by-page basis, which can be retrieved using the `PdfTextSearchResult.addListener` method in the application.

Whereas on the web platform, the search will be performed synchronously, so the result will be returned only after completing the search on all the pages. This is because `isolate` is not supported for the web platform yet.

To differentiate the highlighted texts, the current text instance highlight color will be dark, while the rest of the instances will be light. The following code example explains how to perform the text search and retrieve the results.

N> Import **'package:syncfusion_flutter_pdf/pdf.dart'** in the Dart code if you use the [TextSearchOption](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/TextSearchOption.html) parameter.

{% tabs %}
{% highlight dart hl_lines="23 24 25 26 27 28 29 30 31 32 33 34 35 36" %}

late PdfViewerController _pdfViewerController;
late PdfTextSearchResult _searchResult;

@override
void initState() {
    _pdfViewerController = PdfViewerController();
    _searchResult = PdfTextSearchResult();
    super.initState();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: Text('Flutter PDF Viewer'),
          actions: <Widget>[
            IconButton(
              icon: Icon(
                Icons.search,
                color: Colors.white,
              ),
              onPressed: () {
                _searchResult = _pdfViewerController.searchText('the',
                    searchOption: TextSearchOption.caseSensitive);
                if (kIsWeb) {
                  print(
                      'Total instance count: ${_searchResult.totalInstanceCount}');
                } else {
                  _searchResult.addListener(() {
                    if (_searchResult.hasResult &&
                        _searchResult.isSearchCompleted) {
                      print(
                          'Total instance count: ${_searchResult.totalInstanceCount}');
                    }
                  });
                }
              },
            ),
          ],
        ),
        body: SfPdfViewer.network(
            'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
            controller: _pdfViewerController));
  }

{% endhighlight %}
{% endtabs %}

## Navigate to the Next and Previous Instance

The [nextInstance](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSearchResult/nextInstance.html) and [previousInstance](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSearchResult/previousInstance.html) methods in the [PdfTextSearchResult](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSearchResult-class.html) class help you to navigate to the next and previous search text instances in the PDF document. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="44 56" %}

late PdfViewerController _pdfViewerController;
late PdfTextSearchResult _searchResult;

@override
void initState() {
    _pdfViewerController = PdfViewerController();
    _searchResult = PdfTextSearchResult();
    super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
      appBar: AppBar(
        title: Text('Flutter PDF Viewer'),
        actions: <Widget>[
          IconButton(
            icon: Icon(
              Icons.search,
              color: Colors.white,
            ),
            onPressed: () {
              _searchResult = _pdfViewerController.searchText('the',
                  searchOption: TextSearchOption.caseSensitive);
              if (kIsWeb) {
                setState(() {});
              } else {
                _searchResult.addListener(() {
                  if (_searchResult.hasResult) {
                    setState(() {});
                  }
                });
              }
            },
          ),          
          Visibility(
            visible: _searchResult.hasResult,
            child: IconButton(
              icon: Icon(
                Icons.keyboard_arrow_up,
                color: Colors.white,
              ),
              onPressed: () {
                  _searchResult.previousInstance();
              },
            ),
          ),
          Visibility(
            visible: _searchResult.hasResult,
            child: IconButton(
              icon: Icon(
                Icons.keyboard_arrow_down,
                color: Colors.white,
              ),
              onPressed: () {
                _searchResult.nextInstance();
              },
            ),
          ),
        ],
      ),
      body: SfPdfViewer.network(
          'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
          controller:_pdfViewerController));
}

{% endhighlight %}
{% endtabs %}

## Cancel Text Search

The [clear](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSearchResult/clear.html) method in the [PdfTextSearchResult](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSearchResult-class.html) class is used to cancel the text search operation. When the text search is in progress, this method can be used to cancel the same and clear all the highlighted texts in the `SfPdfViewer`. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="45" %}

late PdfViewerController _pdfViewerController;
late PdfTextSearchResult _searchResult;

@override
void initState() {
    _pdfViewerController = PdfViewerController();
    _searchResult = PdfTextSearchResult();
    super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
      appBar: AppBar(
        title: Text('Flutter PDF Viewer'),
        actions: <Widget>[
          IconButton(
            icon: Icon(
              Icons.search,
              color: Colors.white,
            ),
            onPressed: () {
              _searchResult = _pdfViewerController.searchText('the',
                  searchOption: TextSearchOption.caseSensitive);
              if (kIsWeb) {
                setState(() {});
              } else {
                _searchResult.addListener(() {
                  if (_searchResult.hasResult) {
                    setState(() {});
                  }
                });
              }
            },
          ),
          Visibility(
            visible: _searchResult.hasResult,
            child: IconButton(
              icon: Icon(
                Icons.clear,
                color: Colors.white,
              ),
              onPressed: () {
                setState(() {
                  _searchResult.clear();
                });
              },
            ),
          ),          
        ],
      ),
      body: SfPdfViewer.network(
          'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
          controller:_pdfViewerController));
}

{% endhighlight %}
{% endtabs %}

## Customize the Search Text Highlight Color

The colors in which the current instance and other instances are highlighted can be customized with the help of [currentSearchTextHighlightColor](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/currentSearchTextHighlightColor.html) and [otherSearchTextHighlightColor](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/otherSearchTextHighlightColor.html) property. The default highlight color is **Orange** [Color(0xFFE56E00)] and the current instance highlight color opacity (with respect to this property) will be higher than the other instances. By default, the current instance highlight color opacity will be 60% and the other instances color opacity will be 30%.

The following code example explains how to customize the search text highlight color.

{% tabs %}
{% highlight dart hl_lines="41 42" %}

late PdfViewerController _pdfViewerController;
late PdfTextSearchResult _searchResult;

@override
void initState() {
   _pdfViewerController = PdfViewerController();
   _searchResult = PdfTextSearchResult();
   super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
      appBar: AppBar(
        title: Text('Flutter PDF Viewer'),
          actions: <Widget>[
            IconButton(
              icon: Icon(
                Icons.search,
                color: Colors.white,
              ),
              onPressed: () {
                _searchResult = _pdfViewerController.searchText('the',
                    searchOption: TextSearchOption.caseSensitive);
                if (kIsWeb) {
                  setState(() {});
                } else {
                  _searchResult.addListener(() {
                    if (_searchResult.hasResult) {
                      setState(() {});
                    }
                  });
                }
              },
            ),
          ],
        ),
        body: SfPdfViewer.network(
          'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
          controller: _pdfViewerController,
          currentSearchTextHighlightColor: Colors.blue,
          otherSearchTextHighlightColor: Colors.yellow,
        ));
}

{% endhighlight %}
{% endtabs %}

## How to Identify if There is No Instance Found for the Text Being Searched?

The [totalInstanceCount](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSearchResult/totalInstanceCount.html) property in the [PdfTextSearchResult](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSearchResult-class.html) object can be used to identify if no instance of the searched text is found in the PDF document. That is, if [totalInstanceCount](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSearchResult/totalInstanceCount.html) returns value 0, then there is no matching instance found for the searched text. The following code explains the same.

{% tabs %}
{% highlight dart hl_lines="25 26 27 28 29 30 31 32 33 34 35 36" %}

late PdfViewerController _pdfViewerController;
late PdfTextSearchResult _searchResult;

@override
void initState() {
    _pdfViewerController = PdfViewerController();
    _searchResult = PdfTextSearchResult();
    super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
      appBar: AppBar(
        title: Text('Flutter PDF Viewer'),
        actions: <Widget>[
          IconButton(
            icon: Icon(
              Icons.search,
              color: Colors.white,
            ),
            onPressed: () {
              _searchResult = _pdfViewerController.searchText('pdf',
                  searchOption: TextSearchOption.caseSensitive);
              if (kIsWeb) {
                if (_searchResult.totalInstanceCount == 0) {
                  print('No matches found.');
                }
              } else {
                _searchResult.addListener(() {
                  if (_searchResult.isSearchCompleted &&
                      _searchResult.totalInstanceCount == 0) {
                    print('No matches found.');
                  }
                });
              }
            },
          ),
        ],
      ),
      body: SfPdfViewer.network(
          'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
          controller: _pdfViewerController));
}

{% endhighlight %}
{% endtabs %}

## How to Identify if a Complete Cycle of Text Search is Completed?

The [totalInstanceCount](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSearchResult/totalInstanceCount.html) and [currentInstanceIndex](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSearchResult/currentInstanceIndex.html) properties in the [PdfTextSearchResult](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSearchResult-class.html) object can be used to identify if a complete cycle of text search is completed in the PDF document. That is, when the [nextInstance](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/PdfTextSearchResult/nextInstance.html) method is called, you can check if the `currentInstanceIndex` equals the `totalInstanceCount`, then it can be considered that a complete cycle of text search is completed. The following code example explains the same.

{% tabs %}
{% highlight dart hl_lines="71 72 73 74 75" %}

late PdfViewerController _pdfViewerController;
late PdfTextSearchResult _searchResult;

@override
void initState() {
    _pdfViewerController = PdfViewerController();
    _searchResult = PdfTextSearchResult();
    super.initState();
}

@override
Widget build(BuildContext context) {
  return Scaffold(
      appBar: AppBar(
        title: Text('Flutter PDF Viewer'),
        actions: <Widget>[
          IconButton(
            icon: Icon(
              Icons.search,
              color: Colors.white,
            ),
            onPressed: () {
              _searchResult = _pdfViewerController.searchText('the',
                  searchOption: TextSearchOption.caseSensitive);
              if (kIsWeb) {
                setState(() {});
              } else {
                _searchResult.addListener(() {
                  if (_searchResult.hasResult) {
                    setState(() {});
                  }
                });
              }
            },
          ),
          Visibility(
            visible: _searchResult.hasResult,
            child: IconButton(
              icon: Icon(
                Icons.clear,
                color: Colors.white,
              ),
              onPressed: () {
                setState(() {
                  _searchResult.clear();
                });
              },
            ),
          ),
          Visibility(
            visible: _searchResult.hasResult,
            child: IconButton(
              icon: Icon(
                Icons.keyboard_arrow_up,
                color: Colors.white,
              ),
              onPressed: () {
                _searchResult.previousInstance();
              },
            ),
          ),
          Visibility(
            visible: _searchResult.hasResult,
            child: IconButton(
              icon: Icon(
                Icons.keyboard_arrow_down,
                color: Colors.white,
              ),
              onPressed: () {
                _searchResult.nextInstance();				
                if (_searchResult.currentInstanceIndex ==
                        _searchResult.totalInstanceCount &&
                    _searchResult.isSearchCompleted) {
                  print('No more occurrences found.');
                }
              },
            ),
          ),
        ],
      ),
      body: SfPdfViewer.network(
          'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
          controller:_pdfViewerController));
}

{% endhighlight %}
{% endtabs %}

## How to Create and Display a Custom Search Toolbar with the Search Features?

With the options available in the `SfPdfViewer` text search, you can easily create and display a custom search toolbar with the search features. The following code example explains the same.

In this example, initially the main toolbar or AppBar will be displayed with a search button, and on pressing that, a custom search toolbar will be displayed with the following options:

* **Back button** - To close the search toolbar.
* **Text field entry** - To enter the text to be searched in the document.
* **Close button** - To cancel the search progress.
* **Busy indicator** - To indicate that the search is in progress. This will be visible only on mobile and desktop platforms.
* **Instances information text** - Displays the current instance index and total instances count of the searched text.
* **Previous instance search navigation button** - To navigate to the previous match instance.
* **Next instance search navigation button** - To navigate to the next match instance.

{% tabs %}
{% highlight Dart %}

import 'package:flutter/foundation.dart';
import 'package:flutter/material.dart';
import 'package:syncfusion_flutter_pdf/pdf.dart';
import 'package:syncfusion_flutter_pdfviewer/pdfviewer.dart';

void main() {
  runApp(MaterialApp(
    debugShowCheckedModeBanner: false,
    home: HomePage(),
  ));
}

/// Represents the Homepage for Navigation
class HomePage extends StatefulWidget {
  @override
  _HomePage createState() => _HomePage();
}

class _HomePage extends State<HomePage> {
  final PdfViewerController _pdfViewerController = PdfViewerController();
  final GlobalKey<SearchToolbarState> _textSearchKey = GlobalKey();
  late bool _showToolbar;
  late bool _showScrollHead;

  /// Ensure the entry history of Text search.
  LocalHistoryEntry? _historyEntry;

  /// Indicates whether the device is desktop or not.
  bool _isDesktop = false;

  /// Overlay entry for text search.
  OverlayEntry? _textSearchOverlayEntry;
  final GlobalKey<TextSearchOverlayState> _textSearchOverlayKey = GlobalKey();
  final GlobalKey _searchKey = GlobalKey();

  @override
  void initState() {
    _showToolbar = false;
    _showScrollHead = true;
    super.initState();
  }

  /// Ensure the entry history of text search.
  void _ensureHistoryEntry() {
    if (_historyEntry == null) {
      final ModalRoute<dynamic>? route = ModalRoute.of(context);
      if (route != null) {
        _historyEntry = LocalHistoryEntry(onRemove: _handleHistoryEntryRemoved);
        route.addLocalHistoryEntry(_historyEntry!);
      }
    }
  }
  
  /// Remove history entry for text search.
  void _handleHistoryEntryRemoved() {
    _textSearchKey.currentState?.clearSearch();
    setState(() {
      _showToolbar = false;
    });
    _historyEntry = null;
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: _showToolbar && !_isDesktop
          ? AppBar(
              flexibleSpace: SafeArea(
                child: SearchToolbar(
                  key: _textSearchKey,
                  showTooltip: true,
                  controller: _pdfViewerController,
                  onTap: (Object toolbarItem) async {
                    if (toolbarItem.toString() == 'Cancel Search') {
                      setState(() {
                        _showToolbar = false;
                        _showScrollHead = true;
                        if (Navigator.canPop(context)) {
                          Navigator.maybePop(context);
                        }
                      });
                    }
                    if (toolbarItem.toString() == 'noResultFound') {
                      setState(() {
                        _textSearchKey.currentState?._showToast = true;
                      });
                      await Future.delayed(Duration(seconds: 1));
                      setState(() {
                        _textSearchKey.currentState?._showToast = false;
                      });
                    }
                  },
                ),
              ),
              automaticallyImplyLeading: false,
              backgroundColor: Color(0xFFFAFAFA),
            )
          : AppBar(
              title: Text(
                'Flutter PDF Viewer',
                style: TextStyle(color: Colors.black87),
              ),
              actions: [
                IconButton(
                  key: _searchKey,
                  icon: Icon(
                    Icons.search,
                    color: Colors.black87,
                  ),
                  onPressed: () {
                    if (_isDesktop) {
                      if (_textSearchOverlayEntry == null) {
                        _showTextSearchMenu();
                      } else {
                        _closeSearchMenu();
                      }
                    } else {
                      setState(() {
                        _showScrollHead = false;
                        _showToolbar = true;
                        _ensureHistoryEntry();
                      });
                    }
                  },
                ),
              ],
              automaticallyImplyLeading: false,
              backgroundColor: Color(0xFFFAFAFA),
            ),
      body: LayoutBuilder(builder: (context, constraints) {
        _isDesktop = constraints.biggest.width > 768;
        return Stack(
          children: [
            SfPdfViewer.network(
              'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
              controller: _pdfViewerController,
              canShowScrollHead: _showScrollHead,
            ),
            Visibility(
              visible: _textSearchKey.currentState?._showToast ?? false,
              child: Align(
                alignment: Alignment.center,
                child: Flex(
                  direction: Axis.horizontal,
                  mainAxisAlignment: MainAxisAlignment.center,
                  children: <Widget>[
                    Container(
                      padding: EdgeInsets.only(
                          left: 15, top: 7, right: 15, bottom: 7),
                      decoration: BoxDecoration(
                        color: Colors.grey[600],
                        borderRadius: BorderRadius.all(
                          Radius.circular(16.0),
                        ),
                      ),
                      child: Text(
                        'No result',
                        textAlign: TextAlign.center,
                        style: TextStyle(
                            fontFamily: 'Roboto',
                            fontSize: 16,
                            color: Colors.white),
                      ),
                    ),
                  ],
                ),
              ),
            ),
          ],
        );
      }),
    );
  }

  void _showTextSearchMenu() {
    if (_textSearchOverlayEntry == null) {
      final RenderBox? searchRenderBox =
          (_searchKey.currentContext?.findRenderObject()) as RenderBox?;
      if (searchRenderBox != null) {
        final Offset position = searchRenderBox.localToGlobal(Offset.zero);
        final OverlayState overlayState =
            Overlay.of(context, rootOverlay: true);
        overlayState.insert(_textSearchOverlayEntry = OverlayEntry(
          builder: (BuildContext context) {
            return Positioned(
              top: position.dy + 40.0,
              left: (MediaQuery.of(context).size.width - 8) - 412,
              child: TextSearchOverlay(
                key: _textSearchOverlayKey,
                controller: _pdfViewerController,
                textSearchOverlayEntry: _textSearchOverlayEntry,
                onClose: _closeSearchMenu,
              ),
            );
          },
        ));
      }
    }
  }

  /// Close search menu for web platform.
  void _closeSearchMenu() {
    if (_textSearchOverlayEntry != null) {
      _textSearchOverlayKey.currentState?.clearSearchResult();
      _textSearchOverlayEntry?.remove();
      _textSearchOverlayEntry = null;
    }
  }
}

/// Signature for the [SearchToolbar.onTap] callback.
typedef SearchTapCallback = void Function(Object item);

/// SearchToolbar widget
class SearchToolbar extends StatefulWidget {
  ///it describe the search toolbar constructor
  SearchToolbar({
    this.controller,
    this.onTap,
    this.showTooltip = true,
    Key? key,
  }) : super(key: key);

  /// Indicates whether the tooltip for the search toolbar items need to be shown or not.
  final bool showTooltip;

  /// An object that is used to control the [SfPdfViewer].
  final PdfViewerController? controller;

  /// Called when the search toolbar item is selected.
  final SearchTapCallback? onTap;

  @override
  SearchToolbarState createState() => SearchToolbarState();
}

/// State for the SearchToolbar widget
class SearchToolbarState extends State<SearchToolbar> {
  /// Indicates whether search is initiated or not.
  bool _isSearchInitiated = false;

  /// Indicates whether search toast need to be shown or not.
  bool _showToast = false;

  ///An object that is used to retrieve the current value of the TextField.
  final TextEditingController _editingController = TextEditingController();

  /// An object that is used to retrieve the text search result.
  PdfTextSearchResult _pdfTextSearchResult = PdfTextSearchResult();

  ///An object that is used to obtain keyboard focus and to handle keyboard events.
  FocusNode? focusNode;

  @override
  void initState() {
    super.initState();
    focusNode = FocusNode();
    focusNode?.requestFocus();
  }

  @override
  void dispose() {
    // Clean up the focus node when the Form is disposed.
    focusNode?.dispose();
    _pdfTextSearchResult.removeListener(() {});
    super.dispose();
  }

  ///Clear the text search result
  void clearSearch() {
    _isSearchInitiated = false;
    _pdfTextSearchResult.clear();
  }

  ///Display the Alert dialog to search from the beginning
  void _showSearchAlertDialog(BuildContext context) {
    showDialog(
      context: context,
      builder: (BuildContext context) {
        return AlertDialog(
          insetPadding: EdgeInsets.all(0),
          title: Text('Search Result'),
          content: Container(
              width: 328.0,
              child: Text(
                  'No more occurrences found. Would you like to continue to search from the beginning?')),
          actions: <Widget>[
            TextButton(
              onPressed: () {
                setState(() {
                  _pdfTextSearchResult.nextInstance();
                });
                Navigator.of(context).pop();
              },
              child: Text(
                'YES',
                style: TextStyle(
                    color: Color(0x00000000).withOpacity(0.87),
                    fontFamily: 'Roboto',
                    fontStyle: FontStyle.normal,
                    fontWeight: FontWeight.w500,
                    decoration: TextDecoration.none),
              ),
            ),
            TextButton(
              onPressed: () {
                setState(() {
                  _pdfTextSearchResult.clear();
                  _editingController.clear();
                  _isSearchInitiated = false;
                  focusNode?.requestFocus();
                });
                Navigator.of(context).pop();
              },
              child: Text(
                'NO',
                style: TextStyle(
                    color: Color(0x00000000).withOpacity(0.87),
                    fontFamily: 'Roboto',
                    fontStyle: FontStyle.normal,
                    fontWeight: FontWeight.w500,
                    decoration: TextDecoration.none),
              ),
            ),
          ],
        );
      },
    );
  }

  @override
  Widget build(BuildContext context) {
    return Row(
      children: <Widget>[
        Material(
          color: Colors.transparent,
          child: IconButton(
            icon: Icon(
              Icons.arrow_back,
              color: Color(0x00000000).withOpacity(0.54),
              size: 24,
            ),
            onPressed: () {
              widget.onTap?.call('Cancel Search');
              _isSearchInitiated = false;
              _editingController.clear();
              _pdfTextSearchResult.clear();
            },
          ),
        ),
        Flexible(
          child: TextFormField(
            style: TextStyle(
                color: Color(0x00000000).withOpacity(0.87), fontSize: 16),
            enableInteractiveSelection: false,
            focusNode: focusNode,
            keyboardType: TextInputType.text,
            textInputAction: TextInputAction.search,
            controller: _editingController,
            decoration: InputDecoration(
              border: InputBorder.none,
              hintText: 'Find...',
              hintStyle: TextStyle(color: Color(0x00000000).withOpacity(0.34)),
            ),
            onChanged: (text) {
              if (_editingController.text.isNotEmpty) {
                setState(() {});
              }
            },
            onFieldSubmitted: (String value) {
              if (kIsWeb) {
                _pdfTextSearchResult =
                    widget.controller!.searchText(_editingController.text);
                if (_pdfTextSearchResult.totalInstanceCount == 0) {
                  widget.onTap?.call('noResultFound');
                }
                setState(() {});
              } else {
                _isSearchInitiated = true;
                _pdfTextSearchResult =
                    widget.controller!.searchText(_editingController.text);
                _pdfTextSearchResult.addListener(() {
                  if (super.mounted) {
                    setState(() {});
                  }
                  if (!_pdfTextSearchResult.hasResult &&
                      _pdfTextSearchResult.isSearchCompleted) {
                    widget.onTap?.call('noResultFound');
                  }
                });
              }
            },
          ),
        ),
        Visibility(
          visible: _editingController.text.isNotEmpty,
          child: Material(
            color: Colors.transparent,
            child: IconButton(
              icon: Icon(
                Icons.clear,
                color: Color.fromRGBO(0, 0, 0, 0.54),
                size: 24,
              ),
              onPressed: () {
                setState(() {
                  _editingController.clear();
                  _pdfTextSearchResult.clear();
                  widget.controller!.clearSelection();
                  _isSearchInitiated = false;
                  focusNode!.requestFocus();
                });
                widget.onTap!.call('Clear Text');
              },
              tooltip: widget.showTooltip ? 'Clear Text' : null,
            ),
          ),
        ),
        Visibility(
          visible:
              !_pdfTextSearchResult.isSearchCompleted && _isSearchInitiated,
          child: Padding(
            padding: const EdgeInsets.only(right: 10),
            child: SizedBox(
              width: 24,
              height: 24,
              child: CircularProgressIndicator(
                color: Theme.of(context).primaryColor,
              ),
            ),
          ),
        ),
        Visibility(
          visible: _pdfTextSearchResult.hasResult,
          child: Row(
            children: [
              Text(
                '${_pdfTextSearchResult.currentInstanceIndex}',
                style: TextStyle(
                    color: Color.fromRGBO(0, 0, 0, 0.54).withOpacity(0.87),
                    fontSize: 16),
              ),
              Text(
                ' of ',
                style: TextStyle(
                    color: Color.fromRGBO(0, 0, 0, 0.54).withOpacity(0.87),
                    fontSize: 16),
              ),
              Text(
                '${_pdfTextSearchResult.totalInstanceCount}',
                style: TextStyle(
                    color: Color.fromRGBO(0, 0, 0, 0.54).withOpacity(0.87),
                    fontSize: 16),
              ),
              Material(
                color: Colors.transparent,
                child: IconButton(
                  icon: Icon(
                    Icons.navigate_before,
                    color: Color.fromRGBO(0, 0, 0, 0.54),
                    size: 24,
                  ),
                  onPressed: () {
                    setState(() {
                      _pdfTextSearchResult.previousInstance();
                    });
                    widget.onTap!.call('Previous Instance');
                  },
                  tooltip: widget.showTooltip ? 'Previous' : null,
                ),
              ),
              Material(
                color: Colors.transparent,
                child: IconButton(
                  icon: Icon(
                    Icons.navigate_next,
                    color: Color.fromRGBO(0, 0, 0, 0.54),
                    size: 24,
                  ),
                  onPressed: () {
                    setState(() {
                      if (_pdfTextSearchResult.currentInstanceIndex ==
                              _pdfTextSearchResult.totalInstanceCount &&
                          _pdfTextSearchResult.currentInstanceIndex != 0 &&
                          _pdfTextSearchResult.totalInstanceCount != 0 &&
                          _pdfTextSearchResult.isSearchCompleted) {
                        _showSearchAlertDialog(context);
                      } else {
                        widget.controller!.clearSelection();
                        _pdfTextSearchResult.nextInstance();
                      }
                    });
                    widget.onTap!.call('Next Instance');
                  },
                  tooltip: widget.showTooltip ? 'Next' : null,
                ),
              ),
            ],
          ),
        ),
      ],
    );
  }
}

/// TextSearchOverlay widget for search operation.This is for web platform.
class TextSearchOverlay extends StatefulWidget {
  /// Constructor for TextSearchOverlay.
  const TextSearchOverlay({
    Key? key,
    this.controller,
    this.textSearchOverlayEntry,
    this.onClose,
    this.textDirection = TextDirection.ltr,
  }) : super(key: key);

  /// An object that is used to control the [SfPdfViewer].
  final PdfViewerController? controller;

  /// An object that is used to insert text search overlay.
  final OverlayEntry? textSearchOverlayEntry;

  /// Callback which triggers when closing the search overlay.
  final VoidCallback? onClose;

  /// The text direction
  final TextDirection textDirection;

  @override
  TextSearchOverlayState createState() => TextSearchOverlayState();
}

/// State class of TextSearchOverlay widget.This is for web platform.
class TextSearchOverlayState extends State<TextSearchOverlay> {
  Color? _color;

  /// Indicates whether search toolbar items need to be shown or not.
  bool showItem = false;

  /// Indicates whether enter key is pressed or not.
  bool isEnterKeyPressed = false;

  /// An object that is used to retrieve the text search result.
  PdfTextSearchResult _pdfTextSearchResult = PdfTextSearchResult();

  /// Indicates whether search is initiated or not.
  bool _isSearchInitiated = false;

  /// An object that is used to retrieve the current value of the TextField.
  final TextEditingController _editingController = TextEditingController();

  ///Indicates whether text search option is match case
  bool isMatchCaseChecked = false;

  ///Indicates whether text search option is whole word
  bool isWholeWordChecked = false;

  /// Focus node for search overlay entry.
  final FocusNode _focusNode = FocusNode();

  late bool _isLight;

  @override
  void initState() {
    _focusNode.requestFocus();
    super.initState();
  }

  @override
  void dispose() {
    _focusNode.dispose();
    _pdfTextSearchResult.removeListener(() {});
    super.dispose();
  }

  @override
  void didChangeDependencies() {
    _isLight = Theme.of(context).brightness == Brightness.light;
    _color = _isLight
        ? const Color(0x00000000).withOpacity(0.87)
        : const Color(0x00ffffff).withOpacity(0.87);
    super.didChangeDependencies();
  }

  @override
  Widget build(BuildContext context) {
    const List<BoxShadow> boxShadows = <BoxShadow>[
      BoxShadow(
        color: Color.fromRGBO(0, 0, 0, 0.26),
        blurRadius: 8,
        offset: Offset(0, 3),
      ),
    ];
    return Material(
      child: Directionality(
        textDirection: widget.textDirection,
        child: Container(
          height: 146,
          width: 412,
          decoration: BoxDecoration(
            color: _isLight ? const Color(0xFFFFFFFF) : const Color(0xFF424242),
            boxShadow: boxShadows,
          ),
          child: Column(
            children: <Widget>[
              Row(
                mainAxisAlignment: MainAxisAlignment.spaceBetween,
                children: <Widget>[
                  // Search label for overlay
                  Padding(
                    padding: widget.textDirection == TextDirection.rtl
                        ? const EdgeInsets.only(right: 16, top: 15)
                        : const EdgeInsets.only(
                            left: 16,
                            top: 15,
                          ),
                    child: SizedBox(
                      height: 23,
                      width: 66,
                      child: Text(
                        'Search',
                        style: TextStyle(
                            color: _color,
                            fontFamily: 'Roboto',
                            fontStyle: FontStyle.normal,
                            fontWeight: FontWeight.w500,
                            fontSize: 20,
                            letterSpacing: -0.2,
                            decoration: TextDecoration.none),
                      ),
                    ),
                  ),
                  // Close button for search overlay
                  Padding(
                    padding: widget.textDirection == TextDirection.rtl
                        ? const EdgeInsets.only(right: 8, top: 8)
                        : const EdgeInsets.only(left: 8, top: 8),
                    child: SizedBox(
                      height: 36,
                      width: 36,
                      child: RawMaterialButton(
                        onPressed: () {
                          _closeSearchMenu();
                        },
                        child: Icon(
                          Icons.clear,
                          color: _isLight
                              ? const Color.fromRGBO(0, 0, 0, 0.54)
                              : const Color.fromRGBO(255, 255, 255, 0.65),
                          size: 20,
                        ),
                      ),
                    ),
                  ),
                ],
              ),
              Row(
                children: <Widget>[
                  // Search input field.
                  Flexible(
                    child: Padding(
                      padding: widget.textDirection == TextDirection.rtl
                          ? const EdgeInsets.only(right: 16)
                          : const EdgeInsets.only(left: 16),
                      child: TextFormField(
                        focusNode: _focusNode,
                        controller: _editingController,
                        textInputAction: TextInputAction.none,
                        style: TextStyle(
                          fontSize: 15,
                          fontFamily: 'Roboto',
                          fontStyle: FontStyle.normal,
                          fontWeight: FontWeight.normal,
                          color: _color,
                        ),
                        decoration: InputDecoration(
                          contentPadding: const EdgeInsets.only(top: 20),
                          border: const UnderlineInputBorder(),
                          enabledBorder: const UnderlineInputBorder(
                              borderSide:
                                  BorderSide(color: Colors.grey, width: 2.0)),
                          hintStyle: TextStyle(
                              color: _isLight
                                  ? const Color(0x00000000).withOpacity(0.34)
                                  : const Color(0xFF949494),
                              fontSize: 15,
                              fontFamily: 'Roboto',
                              fontStyle: FontStyle.normal,
                              fontWeight: FontWeight.w400,
                              decoration: TextDecoration.none),
                          suffixIcon: !showItem
                              ? Padding(
                                  padding: const EdgeInsets.only(
                                      left: 8, right: 8, bottom: 6, top: 15),
                                  child: SizedBox(
                                    height: 14.57,
                                    width: 14.57,
                                    child: RawMaterialButton(
                                      onPressed: () {
                                        if (_editingController
                                            .text.isNotEmpty) {
                                          _handleSearch();
                                        }
                                      },
                                      child: Icon(
                                        Icons.search,
                                        color: _isLight
                                            ? Colors.black.withOpacity(0.54)
                                            : Colors.white.withOpacity(0.65),
                                        size: 18,
                                      ),
                                    ),
                                  ),
                                )
                              : Padding(
                                  padding: const EdgeInsets.only(
                                      left: 8, right: 8, bottom: 6, top: 18),
                                  child: SizedBox(
                                    height: 14.57,
                                    width: 14.57,
                                    child: RawMaterialButton(
                                      onPressed: () {
                                        setState(() {
                                          _pdfTextSearchResult.clear();
                                          _editingController.clear();
                                          _focusNode.requestFocus();
                                          _isSearchInitiated = false;
                                          showItem = false;
                                        });
                                      },
                                      child: Icon(
                                        Icons.clear,
                                        color: _isLight
                                            ? Colors.black.withOpacity(0.54)
                                            : Colors.white.withOpacity(0.65),
                                        size: 18,
                                      ),
                                    ),
                                  ),
                                ),
                        ),
                        onChanged: (String value) {
                          isEnterKeyPressed = false;
                        },
                        onFieldSubmitted: (String value) {
                          setState(() {
                            _handleSearch();
                          });
                        },
                      ),
                    ),
                  ),
                  Visibility(
                    visible: !_pdfTextSearchResult.isSearchCompleted &&
                        _isSearchInitiated &&
                        !kIsWeb,
                    child: Padding(
                      padding:
                          const EdgeInsets.only(left: 6, right: 6, top: 15),
                      child: SizedBox(
                        width: 20,
                        height: 20,
                        child: CircularProgressIndicator(
                          backgroundColor: Colors.grey.withOpacity(0.4),
                          strokeWidth: 3,
                        ),
                      ),
                    ),
                  ),
                  // Search result status
                  Visibility(
                    visible: showItem,
                    child: Padding(
                      padding: const EdgeInsets.only(top: 10, left: 8),
                      child: Row(
                        children: <Widget>[
                          // Current search instance
                          Text(
                            _pdfTextSearchResult.currentInstanceIndex
                                .toString(),
                            style: TextStyle(
                                color: _color,
                                fontSize: 15,
                                fontFamily: 'Roboto',
                                fontStyle: FontStyle.normal,
                                fontWeight: FontWeight.normal,
                                decoration: TextDecoration.none),
                          ),
                          Text(
                            '/',
                            style: TextStyle(
                                color: _color,
                                fontSize: 15,
                                fontFamily: 'Roboto',
                                fontStyle: FontStyle.normal,
                                fontWeight: FontWeight.normal,
                                decoration: TextDecoration.none),
                          ),
                          // Total search count
                          Text(
                            _pdfTextSearchResult.totalInstanceCount.toString(),
                            style: TextStyle(
                                color: _color,
                                fontSize: 15,
                                fontFamily: 'Roboto',
                                fontStyle: FontStyle.normal,
                                fontWeight: FontWeight.normal,
                                decoration: TextDecoration.none),
                          ),
                        ],
                      ),
                    ),
                  ),
                  // Group divider
                  Padding(
                      padding: const EdgeInsets.only(top: 10),
                      child: SizedBox(
                        height: 24,
                        child: VerticalDivider(
                          width: 24.0,
                          thickness: 1.0,
                          color: _isLight
                              ? Colors.black.withOpacity(0.24)
                              : Colors.white.withOpacity(0.26),
                        ),
                      )),
                  // Previous search instance button
                  Padding(
                    padding: const EdgeInsets.only(top: 10),
                    child: SizedBox(
                      height: 36,
                      width: 36,
                      child: RawMaterialButton(
                        shape: RoundedRectangleBorder(
                          borderRadius: BorderRadius.circular(2.0),
                        ),
                        onPressed: _pdfTextSearchResult.hasResult
                            ? () {
                                setState(() {
                                  _pdfTextSearchResult.previousInstance();
                                });
                              }
                            : null,
                        child: Icon(
                          Icons.keyboard_arrow_left,
                          color: _isLight
                              ? _pdfTextSearchResult.hasResult
                                  ? const Color.fromRGBO(0, 0, 0, 0.54)
                                  : Colors.black.withOpacity(0.28)
                              : _pdfTextSearchResult.hasResult
                                  ? const Color.fromRGBO(255, 255, 255, 0.65)
                                  : Colors.white12,
                          size: 20,
                        ),
                      ),
                    ),
                  ),
                  // Next search instance button
                  Padding(
                    padding: const EdgeInsets.only(
                      top: 10,
                      right: 8,
                    ),
                    child: SizedBox(
                      height: 36,
                      width: 36,
                      child: RawMaterialButton(
                        shape: RoundedRectangleBorder(
                          borderRadius: BorderRadius.circular(2.0),
                        ),
                        onPressed: _pdfTextSearchResult.hasResult
                            ? () {
                                setState(() {
                                  _pdfTextSearchResult.nextInstance();
                                });
                              }
                            : null,
                        child: Icon(
                          Icons.keyboard_arrow_right,
                          color: _isLight
                              ? _pdfTextSearchResult.hasResult
                                  ? const Color.fromRGBO(0, 0, 0, 0.54)
                                  : Colors.black.withOpacity(0.28)
                              : _pdfTextSearchResult.hasResult
                                  ? const Color.fromRGBO(255, 255, 255, 0.65)
                                  : Colors.white12,
                          size: 20,
                        ),
                      ),
                    ),
                  ),
                ],
              ),
              Row(
                children: <Widget>[
                  // Check box for case sensitive search.
                  Padding(
                    padding: widget.textDirection == TextDirection.rtl
                        ? const EdgeInsets.only(right: 16, top: 16, bottom: 16)
                        : const EdgeInsets.only(left: 16, top: 16, bottom: 16),
                    child: SizedBox(
                      height: 18,
                      width: 18,
                      child: Theme(
                        data: ThemeData(
                          useMaterial3: false,
                          unselectedWidgetColor: _isLight
                              ? const Color.fromRGBO(0, 0, 0, 0.54)
                              : const Color.fromRGBO(255, 255, 255, 0.54),
                        ),
                        child: Checkbox(
                          value: isMatchCaseChecked,
                          checkColor: Colors.white,
                          onChanged: (bool? value) {
                            setState(() {
                              isEnterKeyPressed = false;
                              isMatchCaseChecked = value ?? false;
                            });
                          },
                        ),
                      ),
                    ),
                  ),
                  // Label for case sensitive search.
                  Padding(
                    padding: widget.textDirection == TextDirection.rtl
                        ? const EdgeInsets.only(right: 8, top: 16, bottom: 16)
                        : const EdgeInsets.only(left: 8, top: 16, bottom: 16),
                    child: Text(
                      'Match case',
                      style: TextStyle(
                          color: _color,
                          fontFamily: 'Roboto',
                          fontStyle: FontStyle.normal,
                          fontWeight: FontWeight.normal,
                          fontSize: 15,
                          decoration: TextDecoration.none),
                    ),
                  ),
                  // Check box for whole word search.
                  Padding(
                    padding: widget.textDirection == TextDirection.rtl
                        ? const EdgeInsets.only(right: 16, top: 16, bottom: 16)
                        : const EdgeInsets.only(left: 16, top: 16, bottom: 16),
                    child: SizedBox(
                      height: 18,
                      width: 18,
                      child: Theme(
                        data: ThemeData(
                          useMaterial3: false,
                          unselectedWidgetColor: _isLight
                              ? const Color.fromRGBO(0, 0, 0, 0.54)
                              : const Color.fromRGBO(255, 255, 255, 0.54),
                        ),
                        child: Checkbox(
                          checkColor: Colors.white,
                          value: isWholeWordChecked,
                          onChanged: (bool? value) {
                            setState(() {
                              isEnterKeyPressed = false;
                              isWholeWordChecked = value ?? false;
                            });
                          },
                        ),
                      ),
                    ),
                  ),
                  // Label for whole word search.
                  Padding(
                    padding: widget.textDirection == TextDirection.rtl
                        ? const EdgeInsets.only(right: 8, top: 16, bottom: 16)
                        : const EdgeInsets.only(left: 8, top: 16, bottom: 16),
                    child: Text(
                      'Whole word',
                      style: TextStyle(
                          color: _color,
                          fontFamily: 'Roboto',
                          fontStyle: FontStyle.normal,
                          fontWeight: FontWeight.normal,
                          fontSize: 15,
                          decoration: TextDecoration.none),
                    ),
                  ),
                ],
              ),
            ],
          ),
        ),
      ),
    );
  }

  /// Close search menu for web platform.
  void _closeSearchMenu() {
    setState(() {
      widget.onClose?.call();
      _isSearchInitiated = false;
      _pdfTextSearchResult.clear();
    });
  }

  ///Handle text search result
  void _handleSearch() {
    if (!isEnterKeyPressed) {
      _getSearchResult();
      showItem = true;
    } else {
      _pdfTextSearchResult.nextInstance();
    }
    _focusNode.requestFocus();
  }

  ///Get the text search result
  void _getSearchResult() {
    isEnterKeyPressed = true;
    TextSearchOption? searchOption;
    if (isMatchCaseChecked && isWholeWordChecked) {
      searchOption = TextSearchOption.both;
    } else if (isMatchCaseChecked) {
      searchOption = TextSearchOption.caseSensitive;
    } else if (isWholeWordChecked) {
      searchOption = TextSearchOption.wholeWords;
    }
    if (kIsWeb) {
      _pdfTextSearchResult = widget.controller!
          .searchText(_editingController.text, searchOption: searchOption);
    } else {
      _isSearchInitiated = true;
      _pdfTextSearchResult = widget.controller!
          .searchText(_editingController.text, searchOption: searchOption);
      _pdfTextSearchResult.addListener(_rebuild);
    }
  }

  void _rebuild() {
    if (super.mounted) {
      setState(() {});
    }
  }

  /// Clears the search result.
  void clearSearchResult() {
    _pdfTextSearchResult.removeListener(_rebuild);
    _isSearchInitiated = false;
    _pdfTextSearchResult.clear();
  }
}

{% endhighlight %}
{% endtabs %}