---
layout: post
title: Doughnut Chart in Flutter Circular Charts widget | Syncfusion 
description: Learn here all about doughnut chart of Syncfusion Flutter Circular Charts (SfCircularChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Doughnut Chart in Flutter Circular Charts (SfCircularChart)

To create a Flutter doughnut chart quickly, you can check this video.

<style>#flutterDoughnutChartTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='flutterDoughnutChartTutorial' src='https://www.youtube.com/embed/VJxPp7-2nGk'></iframe>

To render a doughnut chart, create an instance of [`DoughnutSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DoughnutSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/series.html) collection property of [`SfCircularChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart-class.html). The following properties can be used to customize the appearance of doughnut segment:

* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/opacity.html) - controls the transparency of the chart series.
* [`strokeWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPoint/strokeWidth.html) - changes the stroke width of the series.
* [`strokeColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPoint/strokeColor.html) - changes the stroke color of the series.
* [`pointColorMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/pointColorMapper.html) - maps the color for individual points from the data source.
* [`pointShaderMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/pointShaderMapper.html) - maps the shader (gradient or image shader) for individual points from the data source.
* [`pointRenderMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/pointRenderMode.html) - defines the painting mode for the data points either as segment or gradient.


{% tabs %}
{% highlight Dart %} 

    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = [
            ChartData('David', 25, Color.fromRGBO(9,0,136,1)),
            ChartData('Steve', 38, Color.fromRGBO(147,0,119,1)),
            ChartData('Jack', 34, Color.fromRGBO(228,0,124,1)),
            ChartData('Others', 52, Color.fromRGBO(255,189,57,1))
        ];
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(
                        series: <CircularSeries>[
                            // Renders doughnut chart
                            DoughnutSeries<ChartData, String>(
                                dataSource: chartData,
                                pointColorMapper:(ChartData data,  _) => data.color,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y
                            )
                        ]
                    )
                )
            )
        );
    }

    class ChartData {
        ChartData(this.x, this.y, [this.color]);
            final String x;
            final double y;
            final Color color;
    }

{% endhighlight %}
{% endtabs %}

![Doughnut chart](circular-chart-types-images/doughnut.jpg)

## Rounded corners

The [`cornerStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/cornerStyle.html) property specifies the corner type for doughnut chart. The corners can be customized using the [`CornerStyle.bothFlat`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CornerStyle.html), [`CornerStyle.bothCurve`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CornerStyle.html), [`CornerStyle.startCurve`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CornerStyle.html), and [`CornerStyle.endCurve`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CornerStyle.html) options. The default value of this property is [`CornerStyle.bothFlat`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CornerStyle.html).

{% highlight dart hl_lines="13" %}

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(
                        series: <CircularSeries>[
                            DoughnutSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                // Corner style of doughnut segment
                                cornerStyle: CornerStyle.bothCurve
                            )
                        ]
                    )
                )
            )
        );  
    }

{% endhighlight %}
{% endtabs %}

![Doughnut corner style](circular-chart-types-images/doughnut_roundCorner.jpg)

## Doughnut with center elevation

You can use the Annotations property in charts, to provide center elevation text in doughnut charts as shown below:

{% tabs %}
{% highlight Dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(
                        annotations: <CircularChartAnnotation>[
                         CircularChartAnnotation(
                           widget: Container(
                             child: PhysicalModel(
                              child: Container(),
                                shape: BoxShape.circle,
                                elevation: 10,
                                shadowColor: Colors.black,
                                color: const Color.fromRGBO(230, 230, 230, 1)))),
                                CircularChartAnnotation(
                                  widget: Container(
                                  child: const Text('62%',
                                 style: TextStyle(
                                color: Color.fromRGBO(0, 0, 0, 0.5), fontSize: 25))))
                                   ],
                        series: <CircularSeries>[
                            DoughnutSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                // Radius of doughnut
                                radius: '50%'
                            )
                        ]
                    )
                )
            )
        );
    }


{% endhighlight %}
{% endtabs %}

![Doughnut elevation](circular-chart-types-images/doughnut_elevation.png)

## Doughnut with color mapping

You can use the [`pointColorMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeries/pointColorMapper.html) property to provide different color mappings to the doughnut charts as shown below:

{% tabs %}
{% highlight Dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(
                        series: <CircularSeries>[
                            DoughnutSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                pointColorMapper: (ChartSampleData data, _) => data.pointColor,
                                // Radius of doughnut
                                radius: '50%'
                            )
                        ]
                    )
                )
            )
        );
    }


{% endhighlight %}
{% endtabs %}

![Doughnut color mapping](circular-chart-types-images/doughnut_colormapping.png)

## Changing the doughnut size

You can use the [`radius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/radius.html) property to change the diameter of the doughnut chart with respect to the plot area. The default value of this property is 80%.

{% highlight dart hl_lines="13" %}

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(
                        series: <CircularSeries>[
                            DoughnutSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                // Radius of doughnut
                                radius: '50%'
                            )
                        ]
                    )
                )
            )
        );
    }


{% endhighlight %}
{% endtabs %}

![Doughnut size](circular-chart-types-images/doughnut_size.jpg)

## Changing doughnut inner radius

You can change the inner radius of doughnut chart using the [`innerRadius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/innerRadius.html) property with respect to the plot area. The value ranges from 0% to 100%.

{% highlight dart hl_lines="13" %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(
                        series: <CircularSeries>[
                            DoughnutSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                // Radius of doughnut's inner circle
                                innerRadius: '80%'
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![Doughnut innner radius](circular-chart-types-images/doughnut_innerRadius.jpg)

## Exploding a segment

You can explode a doughnut segment by enabling the [`explode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/explode.html) property. The following properties are used to customize the explode options:

* [`explodeIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/explodeIndex.html) - specifies the index of the slice to explode it at the initial rendering.
* [`explodeOffset`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/explodeOffset.html) - specifies the offset of exploded slice. The value ranges from 0% to 100%.
* [`explodeGesture`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/explodeGesture.html) - gesture for activating the explode. Explode can be activated in single tap, double tap, and long press. The available gesture types are [`ActivationMode.singleTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode.html), [`ActivationMode.doubleTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode.html), [`ActivationMode.longPress`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode.html), and [`ActivationMode.none`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode.html). The default value is [`ActivationMode.singleTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode.html).

{% highlight dart hl_lines="13 14" %}  

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(
                        series: <CircularSeries>[
                            DoughnutSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                // Explode the segments on tap
                                explode: true,
                                explodeIndex: 1
                            )
                        ]
                    )
                )
            )
        );
    }


{% endhighlight %}
{% endtabs %}

![Doughnut explode](circular-chart-types-images/doughnut_explode.jpg)

## Exploding all the segments

Using the [`explodeAll`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/explodeAll.html) property of [`DoughnutSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DoughnutSeries-class.html), you can explode all the doughnut segments.

{% highlight dart hl_lines="14" %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(
                        series: <CircularSeries>[
                            DoughnutSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                explode: true,
                                // Explode all the segments
                                explodeAll: true
                            )
                        ]
                    )
                )
            )
        );
    }


{% endhighlight %}
{% endtabs %}

![Pie explode all](circular-chart-types-images/doughnut_explodeAll.jpg)

## Angle of doughnut

[`SfCircularChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart-class.html) allows you to render all the data points or segments in semi-pie, quarter-pie, or in any sector using the [`startAngle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/startAngle.html) and [`endAngle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/endAngle.html) properties.

{% highlight dart hl_lines="13 15" %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(
                        series: <CircularSeries>[
                            DoughnutSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                // Starting angle of doughnut
                                startAngle: 270, 
                                // Ending angle of doughnut
                                endAngle: 90 
                            )
                        ]
                    )
                )
            )
        );
    }


{% endhighlight %}
{% endtabs %}

![Doughnut angle](circular-chart-types-images/doughnut_angle.jpg)

## Grouping data points

The small segments in the doughnut chart can be grouped into **others** category using the [`groupTo`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/groupTo.html) and [`groupMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/groupMode.html) properties of [`DoughnutSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DoughnutSeries-class.html). The [`groupMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/groupMode.html) property is used to specify the grouping type based on the actual data point value or by points length, and the [`groupTo`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/groupTo.html) property is used to set the limit to group data points into a single slice. The grouped segment is labeled as **Others** in legend and toggled as any other segment. The default value of the [`groupTo`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/groupTo.html) property is null, and the default value of [`groupMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/groupMode.html) property is [`CircularChartGroupMode.point`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularChartGroupMode.html).

{% highlight dart hl_lines="13 14" %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(
                        series: <CircularSeries>[
                            DoughnutSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                // Mode of grouping
                                groupMode: CircularChartGroupMode.point,
                                groupTo: 2
                            )
                        ]
                    )
                )
            )
        );
    }


{% endhighlight %}
{% endtabs %}

![Doughnut grouping](circular-chart-types-images/doughnut_grouping.jpg)

>**Note**: You can refer to our [Flutter Doughnut Chart](https://www.syncfusion.com/flutter-widgets/flutter-charts/chart-types/doughnut-chart) feature tour page for its groundbreaking feature representations.