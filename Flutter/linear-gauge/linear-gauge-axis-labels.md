---
layout: post
title: Documentation about the Axis labels in Flutter linear gauge | Tutorials Flutter Linear Gauge widget| Syncfusion
description: Overview about the available styles of Axis labels on Linear Gauge  Flutter widget.
platform: flutter
control: Overview
documentation: ug
---

# Default Linear Gauge Labels

The default style of axis labels are as below.

![Initialize linear gauge for axis](images/getting-started/default_linear_gauge.png)

## Customize Linear Gauge label styles

Axis labels can be customized using the axisLabelStyle property of SfLinearGauge. The axisLabelStyle property have the below properties to customize the axis labels.

* color – Allows to customize the color of the labels.
* fontFamily – Allows to specify the font family for labels.
* fontStyle – Allows to specify the font style for labels.
* fontWeight – Allows to specify the font weight for labels.
* fontSize – Allows to specify the font size for labels.

{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: Container(
                  child: SfLinearGauge(
                    axisLabelStyle: TextStyle(
                        color: Colors.red,
                        fontSize: 15,
                        fontStyle: FontStyle.italic,
                        fontWeight: FontWeight.bold,
                        fontFamily: 'Times')
                  )
              )
          )
      )
  );
}

{% endhighlight %}

![Customize linear gauge axis label style](images/axis-labels/customize_label_style.png)

## Switch Linear Gauge label visibility

The showLabels property of SfLinearGauge allows to show or hide the visibility of axis labels. The default value of the property is true.

{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: Container(
                  child: SfLinearGauge(
                   showLabels: false)))
      )
  );
}

{% endhighlight %}

![switch linear gauge axis label visibility](images/axis-labels/axis_label_visibility.png)

## Customize the interval between labels

The interval between labels can be customized using the interval property of SfLinearGauge. The major ticks are generated based on this interval property.

{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: Container(
                  child: SfLinearGauge(
                   interval: 20,
                  )
              )
          )
      )
  );
}

{% endhighlight %}

![set maximum labels interval in axis track](images/axis-labels/axis_label_interval.png)

## Label placement customization

The linear axis allows to position the labels either inside or outside the axis track using the labelsPosition properties. By default, labels are positioned inside the axis track.

{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: Container(
                child: SfLinearGauge(
                    tickPosition: LinearElementPosition.outside,
                    labelPosition: LinearLabelPosition.outside
                ),
              )
          )
      )
  );
}

{% endhighlight %}

![flutter linear gauge label placement](images/axis-labels/label-placement.png)


## Label position customization with offset

The labelOffset property allows to adjust the distance between the tick end and the labels. By default, the value of the label offset is 15.

{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: Container(
                child: SfLinearGauge(
                  labelOffset:20,
                ),
              )
          )
      )
  );
}

{% endhighlight %}

![set maximum labels position in axis track](images/axis-labels/label_offset.png)

##  Maximum number of labels per 100 logical pixels

By default, a maximum of three labels are displayed for each 100 logical pixels in an axis. The maximum number of labels that should present within 100 logical pixels length can be customized using the maximumLabels property of the axis. 

{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center(
              child: Container(
                  child: SfLinearGauge(
                    maximumLabels: 5
                  )
              )
          )
      )
  );
}

{% endhighlight %}

![set maximum labels interval in axis track](images/axis-labels/axis_label_visibility.png)