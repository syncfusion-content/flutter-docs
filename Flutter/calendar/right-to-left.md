---
layout: post
title: Right to Left in Flutter Event Calendar widget | Syncfusion
description: Learn here all about Right to Left feature of Syncfusion Flutter Event Calendar (SfCalendar) widget and more.
platform: flutter
control: SfCalendar
documentation: ug
---

# Right to left (RTL) in Flutter Event Calendar (SfCalendar)
`SfCalendar` supports changing the layout direction of the widget in the right-to-left direction by using the `Directionality` widget `textDirection` property to rtl.

You can also change the right to left direction by specifying locale, which support RTL language such as (Arabic ,Persian ,Hebrew, Pashto, Urdu) by specifying the `MaterialApp` properties and adding the `flutter_localizations` package to your application.

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
               child: SfCalendar(
               view: CalendarView.month,
           ),
       ),
   );
}
   
{% endhighlight %}
{% endtabs %}

