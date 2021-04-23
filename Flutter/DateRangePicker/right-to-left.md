---
layout: post
title: Right to Left in Flutter Date Range Picker widget | Syncfusion
description: Learn here all about Right to Left feature in Syncfusion Flutter Date Range Picker (SfDateRangePicker) widget and more.
platform: flutter
control: SfDateRangePicker
documentation: ug
---

# Right to Left (RTL) in Flutter Date Range Picker (SfDateRangePicker)

The `SfDateRangePicker` supports changing the layout direction of the widget in the right-to-left direction by using the `Directionality` widget `textDirection` property to rtl.

You can also change the right to left direction by specifying locale, that supports RTL language such as (Arabic ,Persian ,Hebrew, Pashto and Urdu) by specifying the `MaterialApp` properties and adding the `flutter_localizations` package to your application.

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

![RTL Date Range Picker](images/rtl/right_to_left.png)
