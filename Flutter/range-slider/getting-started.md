---
layout: post
title: Getting Started for Syncfusion Flutter Range Slider | Syncfusion
description: A quick tour for initial users on Syncfusion SfRangeSlider for flutter platform
platform: flutter
control: SfRangeSlider
documentation: ug
---

# Getting Started
This section explains the steps required to add the range slider widget and its elements such as thumb, overlay, tick, numeric and date time labels. This section covers only basic features needed to get started with Syncfusion range slider widget.

## Add flutter range slider to an application
Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://flutter.dev/docs/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion flutter range slider dependency to your pubspec.yaml file.

{% highlight dart %}

dependencies:

syncfusion_flutter_sliders: ^18.1.36-beta

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

After importing the package, initialize the range slider widget as a child of any widget. Here, the range slider widget is added as a child of the Container widget.

{% tabs %}
{% highlight Dart %}

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

## Add numeric labels

Add range slider with ticks, numeric labels and minimum and maximum values to restrict slider range.

{% tabs %}
{% highlight Dart %}

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

## Add date time labels

Add range slider with tick and date time labels.

{% tabs %}
{% highlight Dart %}

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
