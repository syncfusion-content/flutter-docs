---
layout: post
title: Right to Left in Flutter Event Calendar widget | Syncfusion
description: Learn here all about Right to Left feature of Syncfusion Flutter Event Calendar (SfCalendar) widget and more.
platform: flutter
control: SfCalendar
documentation: ug
---

# Right to left (RTL) in Flutter Event Calendar (SfCalendar)
Event calendar supports Right to left rendering and all the calendar elements rendering direction will be changed.

## RTL rendering ways
Right to left rendering can be switched in the following ways:

### Wrapping the SfCalendar with Directionality widget
`SfCalendar` supports changing the layout direction of the widget in the right-to-left direction by using the `Directionality` widget and set the `textDirection` property as [TextDirection.rtl](https://api.flutter.dev/flutter/dart-ui/TextDirection.html).

{% tabs %}
{% highlight dart hl_lines="7 8" %}

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

### Changing the locale to RTL languages
To change the event calendar rendering direction from right to left, change the locale to any of the RTL languages such as Arabic, Persian, Hebrew, Pashto, and Urdu.

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
	  body: SfCalendar(
		  //...
		  ),
	));
}

	
{% endhighlight %}
{% endtabs %}


## RTL supported calendar element
Right to left rendering is supported for all the elements in the `SfCalendar`.


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
        allowedViews: [
          CalendarView.day,
          CalendarView.week,
          CalendarView.workWeek,
          CalendarView.month,
          CalendarView.schedule,
          CalendarView.timelineDay,
          CalendarView.timelineWeek,
          CalendarView.timelineWorkWeek,
          CalendarView.timelineMonth
        ],
      ),
    ),
  );
}

   
{% endhighlight %}
{% endtabs %}
