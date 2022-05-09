---
layout: post
title: Right to Left in Flutter Date Range Picker widget | Syncfusion
description: Learn here all about Right to Left feature in Syncfusion Flutter Date Range Picker (SfDateRangePicker) widget and more.
platform: flutter
control: SfDateRangePicker
documentation: ug
---

# Right to Left (RTL) in Flutter Date Range Picker (SfDateRangePicker)
`SfDateRangePicker` supports Right to left rendering and all the date picker elements rendering direction will be changed.

## RTL rendering ways
Right to left rendering can be switched in the following ways:

### Wrapping the SfDateRangePicker with Directionality widget
The `SfDateRangePicker` supports changing the layout direction of the widget in the right-to-left direction by using the `Directionality` widget and set the `textDirection` property as [TextDirection.rtl](https://api.flutter.dev/flutter/dart-ui/TextDirection.html).

{% tabs %}
{% highlight dart hl_lines="7" %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: Text('Right to Left'),
    ),
    body: Directionality(
      textDirection: TextDirection.rtl,
      child: SfDateRangePicker(
        view: DateRangePickerView.month,
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![RTL Date Range Picker](images/rtl/right_to_left.png)

### Changing the locale to RTL languages
To change the date range picker rendering direction from right to left, change the locale to any of the RTL languages such as Arabic, Persian, Hebrew, Pashto, and Urdu.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
      localizationsDelegates: [
        GlobalMaterialLocalizations.delegate,
        GlobalWidgetsLocalizations.delegate,
      ],
      supportedLocales: <Locale>[
        Locale('en'),
        Locale('ar'),
        // ... other locales the app supports
      ],
      locale: Locale('ar'),
      home: Scaffold(
        body: SfDateRangePicker(
            //...
            ),
      ));
}
	
{% endhighlight %}
{% endtabs %}

## RTL supported date range picker elements
Right to left rendering is supported for all the elements in the `SfDateRangePicker`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: Text('Right to Left'),
    ),
    body: Directionality(
      textDirection: TextDirection.rtl,
      child: SfDateRangePicker(
        view: DateRangePickerView.month,
      ),
    ),
  );
}

   
{% endhighlight %}
{% endtabs %}