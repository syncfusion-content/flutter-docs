---
layout: post
title: RTL in Flutter Range Selector widget | Syncfusion
description: Learn here all about the RTL rendering in Syncfusion Flutter Range Selector (SfRangeSelector) widget.
platform: Flutter
control: SfRangeSelector
documentation: ug
---

# Right to Left (RTL) in Flutter Range Selector (SfRangeSelector)

### Using locale

You can change the right to left direction by specifying locale, which support RTL language such as (Arabic ,Persian ,Hebrew, Pashto, Urdu) by specifying the MaterialApp properties such as `localizationsDelegates`, `supportedLocales`, `locale` and adding the flutter_localizations package to your pubspec.yaml file.

{% tabs %}
{% highlight Dart %}

dependencies:
  flutter_localizations:
    sdk: flutter

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight Dart %}

SfRangeValues _initialValues = SfRangeValues(4.0, 8.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
    theme: ThemeData(
      primarySwatch: Colors.blue,
    ),
    localizationsDelegates: [
      GlobalCupertinoLocalizations.delegate,
      GlobalMaterialLocalizations.delegate,
      GlobalWidgetsLocalizations.delegate,
    ],
    supportedLocales: [
      Locale("fa", "IR"),
    ],
    locale: Locale("fa", "IR"),
    home: Scaffold(
      backgroundColor: Colors.white,
      body: SfRangeSelector(
        min: 2.0,
        max: 10.0,
        interval: 1,
        showLabels: true,
        showTicks: true,
        initialValues: _initialValues,
        child: Container(
          color: Colors.pink[200],
          height: 150,
        ),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

### Using Directionality widget

The SfRangeSelector supports changing the layout direction of the widget in the right-to-left direction by setting the [`textDirection`](https://api.flutter.dev/flutter/widgets/Directionality/textDirection.html) property to `rtl` in the [`Directionality`](https://api.flutter.dev/flutter/widgets/Directionality-class.html) widget.

{% tabs %}
{% highlight Dart %}

SfRangeValues _initialValues = SfRangeValues(4.0, 8.0);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Directionality(
            textDirection: TextDirection.rtl,
            child: Center(
              child: SfRangeSelector(
                min: 2.0,
                max: 10.0,
                interval: 1,
                showLabels: true,
                showTicks: true,
                initialValues: _initialValues,
                child: Container(
                    color: Colors.pink[200],
                    height: 150,
                 ),
              ),
            )
         ),
      )
  );
}

{% endhighlight %}
{% endtabs %}

![RTL support](images/right-to-left/right-to-left-support.png)
