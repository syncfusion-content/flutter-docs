---
layout: post
title: Markers and data labels in Syncfusion Flutter Spark charts
description: Learn how to add the markers and data point labels to the series available in the Syncfusion Flutter Spark charts widget.
platform: flutter
control: Sparkline
documentation: ug
---

# Marker and data label

## Marker

Markers are used to provide information about the exact point location. You can add a shape to adorn each data point. Using the [`marker`]() property, add the markers to [`SfSparkLineChart`](), and [`SfSparkAreaChart`]() widgets.

You can use the following properties to customize the appearance:

* [`displayMode`]() - Toggles the visibility of the marker. Defaults to `none`
* [`borderWidth`]() - Represents the border width of the marker.
* [`color`]() - Represents the color of the marker.
* [`borderColor`]() - Represents the border color of the marker.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfSparkLineChart(
              marker: SparkChartMarker(
                borderColor: Colors.orange,
                borderWidth: 2,
                displayMode: SparkChartMarkerDisplayMode.all
              ),
              data: <double>[
                    5, 6, 5, 7, 4, 3, 9, 5, 6, 5, 7, 8, 4, 5, 3, 4, 11, 10, 2, 12, 4, 7, 6, 8
              ],
          )
        )
      );
    }

{% endhighlight %}

![Sparkline marker](images/marker/spark-marker-circle.png)

### Customizing marker shapes

Markers can be assigned with different shapes using the [`shape`]() property. By default, markers are rendered with circle shape. The shapes of markers are listed below.

* circle,
* diamond,
* square,
* triangle,
* invertedTriangle

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfSparkLineChart(
            marker: SparkChartMarker(
              shape: MarkerShape.square,
              displayMode: SparkChartMarkerDisplayMode.all
            ),
            data: <double>[
              5, 6, 5, 7, 4, 3, 9, 5, 6, 5, 7, 8, 4, 5, 3, 4, 11, 10, 2, 12, 4, 7, 6, 8
            ],
          )
        )
      );
    }

{% endhighlight %}

![Sparkline marker shape](images/marker/spark-marker-square.png)

## Data label

Data labels are used to display values of data points to improve the readability.

### Enable data label

To enable data label for spark charts, use the [`labelDisplayMode`]() property in spark charts widgets.

Following possible values are available in spark charts to render data label:

* [`none`]() - Does not allow to display data points on any side.
* [`all`]() - Allows to display data labels on all points.
* [`high`]() - Allows to display data labels on the high point.
* [`low`]() - Allows to display data labels on the low point.
* [`last`]() - Allows to display data labels on the last point.
* [`first`]() - Allows to display data labels on the first point.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfSparkLineChart(
              labelDisplayMode: LabelDisplayMode.all,
              data: <double>[
                  5, 6, 5, 7, 4, 3, 9, 5, 6, 5, 7, 8, 4, 5, 3, 4, 11, 10, 2, 12, 4, 7, 6, 8
              ],
          )
        )
      );
    }

{% endhighlight %}

![Sparkline datalabel](images/marker/spark-datalabel.png)

N> The [`SfSparkWinLossChart`]() widget doesn't provide data label support.