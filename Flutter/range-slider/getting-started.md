---
layout: post
title: Getting Started for Syncfusion Flutter Range Slider | Syncfusion
description: This section explains the steps required to add the range slider widget and its elements such as numeric and date values, ticks, labels and tooltips 
platform: flutter
control: SfRangeSlider
documentation: ug
---

# Getting Started for Range Slider
This section explains the steps required to add the range slider widget and ts elements such as numeric and date values, ticks, labels and tooltips. This section covers only basic features needed to know to get started with Syncfusion range slider.

## Add flutter range slider to an application
Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://flutter.dev/docs/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion flutter range slider dependency to your pubspec.yaml file.

{% highlight dart %}

dependencies:

syncfusion_flutter_sliders: ^18.1.0.36-beta

{% endhighlight %}

**Get packages** 

Run the following command to get the required packages.

{% highlight dart %}

$ flutter pub get

{% endhighlight %}

**Import package**

Import the following package in your Dart code.

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_sliders/sliders.dart';

{% endhighlight %}
{% endtabs %}

## Initialize range slider

After importing the package, initialize the range slider widget as a child of any widget. Here, the range slider widget is added as a child of the Container widget. The default value of the `min` and `max` property of the SfRangeSlider is 0.0 and 1.0 respectively. So, the `values` property must be given within the range.

N> You must update the `values` property inside the `setState` function for the movement of the thumb in the range slider.

{% tabs %}
{% highlight Dart %}

SfRangeValues _values = const SfRangeValues(0.3, 0.7);

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: Container(
                  child: SfRangeSlider(
                    values: _values,
                    onChanged: (dynamic values){
                      setState(() {
                        _values = values;
                      });
                    },
                  )
              )
          )
      )
  );
}
	
{% endhighlight %}
{% endtabs %}

![Default range slider](images/getting-started/default_range_slider.png)

## Add tick with numeric labels

Add the range slider with ticks, numeric labels, minimum and maximum values to restrict the slider range.

N> The label type like numeric or date time can be determined based on the `min` and `max` properties.

{% tabs %}
{% highlight Dart %}

final double _min = 0;
final double _max = 100;
SfRangeValues _values = const SfRangeValues(40.0, 60.0);

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
      child: Container(
        child: SfRangeSlider(
          min: _min,
          max: _max,
          values: _values,
          interval: 20,
          showTicks: true,
          showLabels: true,
          minorTicksPerInterval: 1,
          onChanged: (SfRangeValues value) {
            setState(() {
              _values = value;
            });
          },
        ),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Numeric range slider](images/getting-started/numeric_range_slider.png)

## Add tick with date labels

Add the range slider with ticks and date labels.

N> You must import the 'package:intl/intl.dart' show DateFormat` package to add the date format in the range slider.

{% tabs %}
{% highlight Dart %}

DateTime _min = DateTime(2008, 01, 01);
DateTime _max = DateTime(2018, 01, 01);
SfRangeValues _values = SfRangeValues(DateTime(2012, 01, 01), DateTime(2014, 01, 01));

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Center(
      child: Container(
        child: SfRangeSlider(
          min: _min,
          max: _max,
          values: _values,
          interval: 2,
          showTicks: true,
          showLabels: true,
          minorTicksPerInterval: 1,
          dateIntervalType: DateIntervalType.years,
          dateFormat: DateFormat.y(),
          onChanged: (SfRangeValues value) {
            setState(() {
              _values = value;
            });
          },
        ),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![DateTime range slider](images/getting-started/date_range_slider.png)
