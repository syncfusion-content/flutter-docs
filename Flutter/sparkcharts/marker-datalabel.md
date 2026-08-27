---
layout: post
title: Marker and Data label in Flutter Spark Chart | Syncfusion®
description: The marker and data label support in Flutter Spark Chart offers clear data point value display, improving chart readability and data interpretation.
platform: flutter
control: Sparkline
documentation: ug
---

# Marker and Data label in Flutter Spark Chart

## Marker

Markers provide information about the exact point location. You can add a shape to each data point by using the [`marker`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SparkChartMarker-class.html) property with [`SfSparkLineChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart-class.html) and [`SfSparkAreaChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkAreaChart-class.html) widgets.

You can use the following properties to customize the appearance:

* [`displayMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SparkChartMarker/displayMode.html) - Toggles the visibility of the marker. Defaults to [`SparkChartMarkerDisplayMode.none`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SparkChartMarkerDisplayMode.html).
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SparkChartMarker/borderWidth.html) - Represents the border width of the marker.
* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SparkChartMarker/color.html) - Represents the color of the marker.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SparkChartMarker/borderColor.html) - Represents the border color of the marker.

{% tabs %}
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfSparkLineChart(
            axisLineWidth: 0,
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
{% endtabs %}

![Sparkline marker](images/marker/spark-marker-circle.png)

### Customizing marker shapes

Markers can be assigned with different shapes using the [`shape`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SparkChartMarker/shape.html) property. By default, markers are rendered with circle shape. The shapes of markers are listed below.

* circle,
* diamond,
* square,
* triangle,
* invertedTriangle

{% tabs %}
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfSparkLineChart(
            axisLineWidth: 0,
            marker: SparkChartMarker(
              shape: SparkChartMarkerShape.square,
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
{% endtabs %}

![Sparkline marker shape](images/marker/spark-marker-square.png)

## Data label

Data labels display data point values to improve readability.

### Enable data labels

To enable data labels for spark charts, use the [`labelDisplayMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkLineChart/labelDisplayMode.html) property in Flutter Spark Chart widgets.

The following values are available in spark charts to render data labels:

* [`SparkChartLabelDisplayMode.none`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SparkChartLabelDisplayMode.html) - Does not allow to display data points on any side.
* [`SparkChartLabelDisplayMode.all`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SparkChartLabelDisplayMode.html) - Allows to display data labels on all points.
* [`SparkChartLabelDisplayMode.high`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SparkChartLabelDisplayMode.html) - Allows to display data labels on the high point.
* [`SparkChartLabelDisplayMode.low`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SparkChartLabelDisplayMode.html) - Allows to display data labels on the low point.
* [`SparkChartLabelDisplayMode.last`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SparkChartLabelDisplayMode.html) - Allows to display data labels on the last point.
* [`SparkChartLabelDisplayMode.first`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SparkChartLabelDisplayMode.html) - Allows to display data labels on the first point.

{% tabs %}
{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfSparkLineChart(
              axisLineWidth: 0,
              labelDisplayMode: SparkChartLabelDisplayMode.all,
              data: <double>[
                  5, 6, 5, 7, 4, 3, 9, 5, 6, 5, 7, 8, 4, 5, 3, 4, 11, 10, 2, 12, 4, 7, 6, 8
              ],
          )
        )
      );
    }

{% endhighlight %}
{% endtabs %}

![Sparkline datalabel](images/marker/spark-datalabel.png)

> **Note**: The [`SfSparkWinLossChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/sparkcharts/SfSparkWinLossChart-class.html) widget doesn't support data labels.