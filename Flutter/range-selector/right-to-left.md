---
layout: post
title: RTL feature in Syncfusion Flutter Range Selector | Syncfusion
description: This section helps to learn about how to change the layout direction in the right to left direction in range selector for Flutter platform
platform: Flutter
control: SfRangeSelector
documentation: ug
---

# Right to Left (RTL) in range selector

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

You can also change the right to left direction by specifying locale, that supports RTL language such as (Arabic ,Persian ,Hebrew, Pashto and Urdu) by specifying the MaterialApp properties and adding the flutter_localizations package to your application.

{% highlight dart %}

dependencies:

  flutter_localizations:
    sdk: flutter

{% endhighlight %}

{% tabs %}
{% highlight Dart %}

SfRangeValues _initialValues = SfRangeValues(4.0, 8.0);

@override
Widget build(BuildContext context) {
    return MaterialApp(
      localizationsDelegates: [
        // ... app-specific localization delegate[s] here
        GlobalMaterialLocalizations.delegate,
        GlobalWidgetsLocalizations.delegate,
      ],
      supportedLocales: [
        const Locale('es'),
        const Locale('he'), //french
        const Locale('ar') //spanish
      ],
      locale: const Locale('ar'),
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: Scaffold(
        appBar: AppBar(
          title: Text('locale'),
        ),
        body: Center(
          child:Center(
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
           ),
        )
      ),
    );
 }

{% endhighlight %}
{% endtabs %}

![RTL support](images/right-to-left/right-to-left-localization.png)
