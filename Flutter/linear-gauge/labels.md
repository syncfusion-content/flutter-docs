---
layout: post
title: Customize labels in a linear gauge | Linear Gauge widget| Syncfusion
description: Tutorial about the available styles of labels on Linear Gauge Flutter widget.| Flutter Linear Gauge widget|
platform: flutter
control: SfLinearGauge
documentation: ug
---

# Default Linear Gauge Labels

The default style of axis labels are as below.

![Initialize linear gauge for axis](images/getting-started/default_linear_gauge.png)

## Customize Linear Gauge label styles

Axis labels can be customized using the `axisLabelStyle` property of `SfLinearGauge`. The `axisLabelStyle` property have the below properties to customize the axis labels.

* `color` – Allows to customize the color of the labels.
* `fontFamily` – Allows to specify the font family for labels.
* `fontStyle` – Allows to specify the font style for labels.
* `fontWeight` – Allows to specify the font weight for labels.
* `fontSize` – Allows to specify the font size for labels.

{% highlight dart %} 

 @override
  Widget build(BuildContext context) {
    return MaterialApp(
        home: Scaffold(
            body: Center(
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
    );
  }

{% endhighlight %}

![Customize linear gauge axis label style](images/axis-labels/customize_label_style.png)

## Switch Linear Gauge label visibility

The `showLabels` property of `SfLinearGauge` allows to show or hide the visibility of axis labels. The default value of the property is true.

{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center( 
                  child: SfLinearGauge(showLabels: false)) 
        )
    );
}

{% endhighlight %}

![Switch linear gauge axis label visibility](images/axis-labels/axis_label_visibility.png)

## Customize the interval between labels

The `interval` between labels can be customized using the interval property of `SfLinearGauge`. The major ticks are generated based on this interval property.

{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center( 
                  child: SfLinearGauge(
                   interval: 20 
                )
            )
        )
    );
}

{% endhighlight %}

![Set maximum labels interval in axis track](images/axis-labels/axis_label_interval.png)

## Change the label position

The linear axis allows to position the labels either `inside` or `outside` the axis track using the `labelsPosition` property. By default, labels are positioned `inside` the axis track.

{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center( 
                child: SfLinearGauge(
                    tickPosition: LinearElementPosition.outside,
                    labelPosition: LinearLabelPosition.outside
                ), 
            )
        )
    );
}

{% endhighlight %}

![Set linear gauge label placement](images/axis-labels/label-placement.png)


## Change the label offset

The `labelOffset` property allows to adjust the distance between the tick-end and the labels. 

{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center( 
                child: SfLinearGauge(
                  labelOffset:20
                ),             
            )
        )
    );
}

{% endhighlight %}

![Set linear gauge label offset](images/axis-labels/label_offset.png)

##  Customize the maximum number of visible labels

By default, a maximum of three labels are displayed for each 100 logical pixels in an axis. The maximum number of labels that should present within 100 logical pixels length can be customized using the `maximumLabels` property of the axis. 

{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center( 
                  child: SfLinearGauge(
                    maximumLabels: 5
                ) 
            )
        )
    );
}

{% endhighlight %}

![Set maximum number of labels in axis track](images/axis-labels/axis_label_visibility.png)

## Customize Label Text

You can format or change the whole numeric label text using the labelFormatterCallback.

{% highlight dart %}

SfLinearGauge(
    labelFormatterCallback: (label) {
      if (label == '0') {
        return 'Start';
      }

      if (label == '50') {
        return 'Mid';
      }

      if (label == '100') {
        return 'End';
      }

      return label;
    }
)

{% endhighlight %}

![Customize Label Text in axis track](images/axis-labels/custom_label_text.png)

## Number Format

The numberFormat property is used to format the numeric labels. The default value of numberFormat property is null.

{% highlight dart %} 

    NOTE: You must import intl package for formatting numeric slider using the NumberFormat class.

{% endhighlight %}

{% highlight dart %}

SfLinearGauge(
  numberFormat: NumberFormat("\$")
),

{% endhighlight %}

![Customize Label Format in Axis Label](images/axis-labels/axis_label_number_format.png)