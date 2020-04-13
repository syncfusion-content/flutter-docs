---
layout: post
title: RTL feature in Syncfusion Flutter Range Slider | Syncfusion
description: This section helps to learn about how to change the layout direction in the right to left direction in range slider for Flutter platform
platform: Flutter
control: SfRangeSlider
documentation: ug
---

# Right to Left (RTL) in range slider

The SfRangeSlider supports changing the layout direction of the widget in the right-to-left direction by setting the [`textDirection`](https://api.flutter.dev/flutter/widgets/Directionality/textDirection.html) property to `rtl` in the [`Directionality`](https://api.flutter.dev/flutter/widgets/Directionality-class.html) widget.

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = SfRangeValues(40.0, 60.0);

@override
Widget build(BuildContext context) {
    return MaterialApp(
        home: Scaffold(
            body: Directionality(
              textDirection: TextDirection.rtl,
              child: Center(
                child: SfRangeSlider(
                  min: 0.0,
                  max: 100.0,
                  values: _values,
                  interval: 20,
                  showTicks: true,
                  showLabels: true,
                  onChanged: (SfRangeValues newValues){
                    setState(() {
                      _values = newValues;
                    });
                  },
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

SfRangeValues _values = SfRangeValues(40.0, 60.0);

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
      locale: const Locale('he'),
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: Scaffold(
        appBar: AppBar(
          title: Text('locale'),
        ),
        body: Center(
          child: SfRangeSlider(
            min: 0.0,
            max: 100.0,
            values: _values,
            interval: 20,
            showTicks: true,
            showLabels: true,
            onChanged: (SfRangeValues newValues){
              setState(() {
                _values = newValues;
              });
            },
          ),
        )
      ),
   );
}

{% endhighlight %}
{% endtabs %}

![RTL localization support](images/right-to-left/right-to-left-localization.png)
