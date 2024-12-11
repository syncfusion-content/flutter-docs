---
layout: post
title: RTL support in Flutter PDF Viewer widget | Syncfusion<sup>&reg;</sup> 
description: Learn here all about the Right to Left (RTL) support in Syncfusion<sup>&reg;</sup> Flutter PDF Viewer (SfPdfViewer) widget and more.
platform: flutter
control: SfPdfViewer
documentation: ug
---

# Right to Left (RTL) in Flutter PDF Viewer (SfPdfViewer)

The [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) supports right-to-left rendering. All the user interface elements will be rendered based on LTR and RTL direction, and the functionalities like text search and copying text also support RTL languages.

## RTL rendering ways

Right to left rendering can be switched in the following ways:

### Wrapping the SfPdfViewer with Directionality widget

To change the rendering direction from right to left, wrap the [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) widget inside the [Directionality](https://api.flutter.dev/flutter/widgets/Directionality-class.html) widget and set the [textDirection](https://api.flutter.dev/flutter/widgets/Directionality/textDirection.html) property as [TextDirection.rtl](https://api.flutter.dev/flutter/widgets/Directionality/textDirection.html).

{% tabs %}
{% highlight dart hl_lines="26 27 28 29 30 31 32" %}

  final GlobalKey<SfPdfViewerState> _pdfViewerKey = GlobalKey();

  @override
  void initState() {
    super.initState();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Syncfusion Flutter PDF Viewer'),
        actions: <Widget>[
          IconButton(
            icon: const Icon(
              Icons.bookmark,
              color: Colors.white,
              semanticLabel: 'Bookmark',
            ),
            onPressed: () {
              _pdfViewerKey.currentState?.openBookmarkView();
            },
          ),
        ],
      ),
      body: Directionality(
        textDirection: TextDirection.rtl,
        child: SfPdfViewer.network(
          'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
          key: _pdfViewerKey,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

### Changing the locale to RTL languages

To change the [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) rendering direction from right to left, change the [locale](https://api.flutter.dev/flutter/material/MaterialApp/locale.html) to any of the RTL languages such as Arabic, Persian, Hebrew, Pashto, and Urdu.

To use `flutter_localizations`, add the package as dependency to `pubspec.yaml` file.

{% highlight dart %}

dependencies:
flutter_localizations:
  sdk: flutter

{% endhighlight %}

Then, import the `flutter_localizations` library, specify [localizationsDelegates](https://api.flutter.dev/flutter/widgets/LocalizationsDelegate-class.html) and `supportedLocales` for `MaterialApp`.

{% tabs %}
{% highlight dart %}

  final GlobalKey<SfPdfViewerState> _pdfViewerKey = GlobalKey();

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      localizationsDelegates: const [
        GlobalMaterialLocalizations.delegate,
        GlobalWidgetsLocalizations.delegate,
        GlobalCupertinoLocalizations.delegate,
      ],
      supportedLocales: const <Locale>[
        Locale('en'),
        Locale('ar'),
        // ... other locales the app supports
      ],
      locale: const Locale('ar'),
      home: Scaffold(
        appBar: AppBar(
          title: const Text('Syncfusion Flutter PDF Viewer'),
          actions: <Widget>[
            IconButton(
              icon: const Icon(
                Icons.bookmark,
                color: Colors.white,
                semanticLabel: 'Bookmark',
              ),
              onPressed: () {
                _pdfViewerKey.currentState?.openBookmarkView();
              },
            ),
          ],
        ),
        body: SfPdfViewer.network(
          'https://cdn.syncfusion.com/content/PDFViewer/flutter-succinctly.pdf',
          key: _pdfViewerKey,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

N> RTL scrolling is not supported in single page layout mode when the [scrollDirection](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/scrollDirection.html) property is set to `PdfScrollDirection.horizontal`.