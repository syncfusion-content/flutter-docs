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


{% highlight dart %} 

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
            final Color? color;
    }

{% endhighlight %}

![Doughnut chart](circular-chart-types-images/doughnut.jpg)

## Rounded corners

The [`cornerStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/cornerStyle.html) property specifies the corner type for doughnut chart. The corners can be customized using the [`bothFlat`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CornerStyle-class.html), [`bothCurve`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CornerStyle-class.html), [`startCurve`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CornerStyle-class.html), and [`endCurve`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CornerStyle-class.html) options. The default value of this property is [`bothFlat`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CornerStyle-class.html).

{% highlight dart %} 

    final List<ChartData> chartData = [
    ChartData('David', 25),
    ChartData('Steve', 38),
    ChartData('Jack', 34),
    ChartData('Others', 52)
    ];

    @override
    Widget build(BuildContext context) {
    return Scaffold(
        body: Center(
            child: Container(
                child: SfCircularChart(series: <CircularSeries>[
      DoughnutSeries<ChartData, String>(
          dataSource: chartData,
          xValueMapper: (ChartData data, _) => data.x,
          yValueMapper: (ChartData data, _) => data.y,
          // Corner style of doughnut segment
          cornerStyle: CornerStyle.bothCurve)
            ]))));
        }
    }

    class ChartData {
    ChartData(this.x, this.y);
    final String x;
    final double y;
    }

{% endhighlight %}

![Doughnut corner style](circular-chart-types-images/doughnut_roundCorner.jpg)

## Doughnut with center elevation

You can use the Annotations property in charts, to provide center elevation text in doughnut charts as shown below:

{% highlight dart %} 

    final List<ChartData> chartData = [
    ChartData('David', 25),
    ChartData('Steve', 38),
    ChartData('Jack', 34),
    ChartData('Others', 52)
    ];

    @override
    Widget build(BuildContext context) {
    return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(
                        annotations: <CircularChartAnnotation>[
                         CircularChartAnnotation(
                           child: Container(
                             child: PhysicalModel(
                              child: Container(),
                                shape: BoxShape.circle,
                                elevation: 10,
                                shadowColor: Colors.black,
                                color: const Color.fromRGBO(230, 230, 230, 1)))),
                                CircularChartAnnotation(
                                  child: Container(
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
    }

    class ChartData {
    ChartData(this.x, this.y);
    final String x;
    final double y;
    }


{% endhighlight %}

![Doughnut elevation](circular-chart-types-images/doughnut_elevation.png)

## Doughnut with color mapping

You can use the [`pointColorMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartSeries/pointColorMapper.html) property to provide different color mappings to the doughnut charts as shown below:

{% highlight dart %} 

    final List<ChartData> chartData = <ChartData>[
      ChartData(
          'A', 10,  const Color.fromRGBO(255, 4, 0, 1)),
      ChartData(
          'B', 10,  const Color.fromRGBO(255, 15, 0, 1)),
      ChartData(
          'C', 10,  const Color.fromRGBO(255, 31, 0, 1)),
      ChartData(
          'D', 10,  const Color.fromRGBO(255, 60, 0, 1)),
      ChartData(
          'E', 10,  const Color.fromRGBO(255, 90, 0, 1)),
      ChartData(
          'F', 10,  const Color.fromRGBO(255, 115, 0, 1)),
      ChartData(
          'G', 10,  const Color.fromRGBO(255, 135, 0, 1)),
      ChartData(
          'H', 10,  const Color.fromRGBO(255, 155, 0, 1)),
      ChartData(
          'I', 10,  const Color.fromRGBO(255, 175, 0, 1)),
      ChartData(
          'J', 10,  const Color.fromRGBO(255, 188, 0, 1)),
      ChartData(
          'K', 10,  const Color.fromRGBO(255, 188, 0, 1)),
      ChartData(
          'L', 10,  const Color.fromRGBO(251, 188, 2, 1)),
      ChartData(
          'M', 10,  const Color.fromRGBO(245, 188, 6, 1)),
      ChartData(
          'N', 10,  const Color.fromRGBO(233, 188, 12, 1)),
      ChartData(
          'O', 10,  const Color.fromRGBO(220, 187, 19, 1)),
      ChartData(
          'P', 10,  const Color.fromRGBO(208, 187, 26, 1)),
      ChartData(
          'Q', 10,  const Color.fromRGBO(193, 187, 34, 1)),
      ChartData(
          'R', 10,  const Color.fromRGBO(177, 186, 43, 1)),
      ChartData(
          'S', 10,  const Color.fromRGBO(230, 230, 230, 1)),
      ChartData(
          'T', 10,  const Color.fromRGBO(230, 230, 230, 1))
    ];
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
                                pointColorMapper: (ChartData data, _) => data.color,
                                // Radius of doughnut
                                radius: '50%',
                                strokeColor: Colors.white,
                                strokeWidth: 2,
                                )
                            ]
                        )
                    )
                )
            );
        }
    }

    class ChartData {
    ChartData(this.x, this.y, [this.color]);
    final String x;
    final double y;
    final Color? color;
    }

{% endhighlight %}

![Doughnut color mapping](circular-chart-types-images/doughnut_colormapping.png)

## Changing the doughnut size

You can use the [`radius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/radius.html) property to change the diameter of the doughnut chart with respect to the plot area. The default value of this property is 80%.

{% highlight dart %} 

    final List<ChartData> chartData = [
    ChartData('Jan', 35),
    ChartData('Feb', 28),
    ChartData('Mar', 34),
    ChartData('May', 40)
    ];
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
                                radius: '50%',
                                )
                            ]
                        )
                    )
                )
            );
        }
    }

    class ChartData {
    ChartData(this.x, this.y);
    final String x;
    final double y;
    }


{% endhighlight %}

![Doughnut size](circular-chart-types-images/doughnut_size.jpg)

## Changing doughnut inner radius

You can change the inner radius of doughnut chart using the [`innerRadius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/innerRadius.html) property with respect to the plot area. The value ranges from 0% to 100%.

{% highlight dart %} 

    final List<ChartData> chartData = [
    ChartData('Jan', 35),
    ChartData('Feb', 28),
    ChartData('Mar', 34),
    ChartData('May', 40)
    ];
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
                                innerRadius: '80%'
                                )
                            ]
                        )
                    )
                )
            );
        }
    }

    class ChartData {
    ChartData(this.x, this.y);
    final String x;
    final double y;
    }

{% endhighlight %}

![Doughnut innner radius](circular-chart-types-images/doughnut_innerRadius.jpg)

## Exploding a segment

You can explode a doughnut segment by enabling the [`explode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/explode.html) property. The following properties are used to customize the explode options:

* [`explodeIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/explodeIndex.html) - specifies the index of the slice to explode it at the initial rendering.
* [`explodeOffset`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/explodeOffset.html) - specifies the offset of exploded slice. The value ranges from 0% to 100%.
* [`explodeGesture`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/explodeGesture.html) - gesture for activating the explode. Explode can be activated in single tap, double tap, and long press. The available gesture types are [`singleTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode-class.html), [`doubleTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode-class.html), [`longPress`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode-class.html), and [`none`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode-class.html). The default value is [`singleTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ActivationMode-class.html).

{% highlight dart %} 

    final List<ChartData> chartData = [
    ChartData('Jan', 35),
    ChartData('Feb', 28),
    ChartData('Mar', 34),
    ChartData('May', 40)
    ];
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
    }

    class ChartData {
    ChartData(this.x, this.y);
    final String x;
    final double y;
    }



{% endhighlight %}

![Doughnut explode](circular-chart-types-images/doughnut_explode.jpg)

## Exploding all the segments

Using the [`explodeAll`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/explodeAll.html) property of [`DoughnutSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DoughnutSeries-class.html), you can explode all the doughnut segments.

{% highlight dart %} 

    final List<ChartData> chartData = [
    ChartData('Jan', 35),
    ChartData('Feb', 28),
    ChartData('Mar', 34),
    ChartData('May', 40)
    ];
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
    }

    class ChartData {
    ChartData(this.x, this.y);
    final String x;
    final double y;
    }


{% endhighlight %}

![Pie explode all](circular-chart-types-images/doughnut_explodeAll.jpg)

## Angle of doughnut

[`SfCircularChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart-class.html) allows you to render all the data points or segments in semi-pie, quarter-pie, or in any sector using the [`startAngle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/startAngle.html) and [`endAngle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/endAngle.html) properties.

{% highlight dart %} 

    final List<ChartData> chartData = [
    ChartData('Jan', 35),
    ChartData('Feb', 28),
    ChartData('Mar', 34),
    ChartData('May', 40)
    ];
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
                                startAngle: 270, // Starting angle of doughnut
                                endAngle: 90 // Ending angle of doughnut
                                )
                            ]
                        )
                    )
                )
            );
        }
    }

    class ChartData {
    ChartData(this.x, this.y);
    final String x;
    final double y;
    }


{% endhighlight %}

![Doughnut angle](circular-chart-types-images/doughnut_angle.jpg)

## Grouping data points

The small segments in the doughnut chart can be grouped into **others** category using the [`groupTo`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/groupTo.html) and [`groupMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/groupMode.html) properties of [`DoughnutSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DoughnutSeries-class.html). The [`groupMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/groupMode.html) property is used to specify the grouping type based on the actual data point value or by points length, and the [`groupTo`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/groupTo.html) property is used to set the limit to group data points into a single slice. The grouped segment is labeled as **Others** in legend and toggled as any other segment. The default value of the [`groupTo`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/groupTo.html) property is null, and the default value of [`groupMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/groupMode.html) property is [`point`]().

{% highlight dart %} 

    final List<ChartData> chartData = [
    ChartData('Jan', 35),
    ChartData('Feb', 28),
    ChartData('Mar', 34),
    ChartData('May', 40)
    ];
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
    }

    class ChartData {
    ChartData(this.x, this.y);
    final String x;
    final double y;
    }


{% endhighlight %}

![Doughnut grouping](circular-chart-types-images/doughnut_grouping.jpg)