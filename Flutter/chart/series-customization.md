---
layout: post
title: Series customization in Syncfusion Flutter charts
description: Learn how to customize the appearance of the series in a chart.
platform: flutter
control: Chart
documentation: ug
---

# Series customization

## Multiple series

You can add multiple series to [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html) class. By default, all the series rendered based on the [`PrimaryXAxis`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/primaryXAxis.html) and [`PrimaryYAxis`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/primaryYAxis.html) in [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). But if you want to plot different unit or value that is specific to particular series, you can specify separate axis for that series using [`xAxisName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/xAxisName.html) and [`yAxisName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/yAxisName.html) properties of series.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                primaryXAxis: CategoryAxis(),
                series: <CartesianSeries>[
              ColumnSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y,
              ),
              ColumnSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y2,
              ),
              ColumnSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y3,
                        ),
                    ]
                )
            )
        )
    );
}

{% endhighlight %}

![Multiple series](images/series-customization/multipleSeries.jpg)

## Combination series

[`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html) allows you to render the combination of different types of series.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                primaryXAxis: CategoryAxis(),
                series: <CartesianSeries>[
              ColumnSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y,
              ),
              LineSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y2,
                        ),
                    ]
                )
            )
        )
    );
}

{% endhighlight %}

![Combination series](images/series-customization/combination_series.jpg)

**Limitation of Combination Chart**

* Cartesian type series cannot be combined with Circular series (pie, doughnut, and radial bar).

## Animation

[`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html) provides animation support for the series. Series will be animated while rendering. Animation is enabled by default, you can also control the duration of the animation using [`animationDuration`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/animationDuration.html) property. You can disable the animation by setting 0 value to that property.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                primaryXAxis: CategoryAxis(),
                series: <CartesianSeries>[
              ColumnSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y,
                animationDuration: 1000
                        )
                    ]
                )
            )
        )
    );
}

{% endhighlight %}

## Transpose the series

The [`isTransposed`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/isTransposed.html) property of [`CartesianSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries-class.html) is used to transpose the horizontal and vertical axes, to view the data in a different perspective. Using this feature, you can render vertical charts.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                    isTransposed: true,
                    primaryXAxis: CategoryAxis(),
                    series: <CartesianSeries>[
                ColumnSeries<ChartData, String>(
                    dataSource: chartData,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y,
                        )
                    ]
                )
            )
        )
    );
}

{% endhighlight %}

![Transposed chart](images/series-customization/transpose.jpg)

## Color palette

The [`palette`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/palette.html) property is used to define the colors for the series available in chart. By default, a set of 10 colors are predefined for applying it to the series. If the colors specified in the series are less than the number of series, than the remaining series are filled with the specified palette colors rotationally.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                primaryXAxis: CategoryAxis(),
                palette: <Color>[
                    Colors.teal,
                    Colors.orange,
                    Colors.brown
                  ],
                series: <CartesianSeries>[
              ColumnSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y,
              ),
              ColumnSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y2,
              ),
              ColumnSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y3,
                        ),
                    ]
                )
            )
        )
    );
}

{% endhighlight %}

![Palette](images/series-customization/palette.jpg)

## Color mapping for data points   

The [`pointColorMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/pointColorMapper.html) property is used to map the color field from the data source. 

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = [
            ChartData('Germany', 118, Colors.teal),
            ChartData('Russia', 123, Colors.orange),
            ChartData('Norway', 107, Colors.brown),
            ChartData('USA', 87, Colors.deepOrange),
        ];
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                primaryXAxis: CategoryAxis(),
                series: <CartesianSeries>[
              ColumnSeries<ChartData, String>(
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                yValueMapper: (ChartData data, _) => data.y,
                pointColorMapper: (ChartData data, _) => data.color
                        )
                    ]
                )
            )
        )
    );
}

    class ChartData {
        ChartData(this.x, this.y, this.color);
            final String x;
            final double y;
            final Color color;
    }

{% endhighlight %}

![Point color mapping](images/series-customization/color_mapping.jpg)

## Gradient fill

The [`gradient`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/gradient.html) property is used to define the gradient colors. The colors from this property is used for series.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        final List<Color> color = <Color>[];
        color.add(Colors.deepOrange[50]);
        color.add(Colors.deepOrange[200]);
        color.add(Colors.deepOrange);

        final List<double> stops = <double>[];
        stops.add(0.0);
        stops.add(0.5);
        stops.add(1.0);

        final LinearGradient gradientColors =
            LinearGradient(colors: color, stops: stops);

        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                series: <CartesianSeries>[
              AreaSeries<ChartData, double>(
                  dataSource: chartData,
                  xValueMapper: (ChartData data, _) => data.x,
                  yValueMapper: (ChartData data, _) => data.y,
                  gradient: gradientColors),
                    ]
                )
            )
        )
    );
}

{% endhighlight %}

![Gradient color](images/series-customization/gradient.jpg)

## Empty points

The data points that has null value are considered as empty points. Empty data points are ignored and not plotted in the chart. By using [`emptyPointSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/emptyPointSettings.html) property in series, you can decide the action taken for empty points. Available [`modes`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode-class.html) are [`gap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode-class.html), [`zero`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode-class.html), [`drop`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode-class.html) and [`average`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode-class.html). Default mode of the empty point is [`gap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode-class.html).

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        
        final List<ChartData> chartData = [
            ChartData(1, 112),
            ChartData(2, null),
            ChartData(3, 107),
            ChartData(4, 87)
        ];

        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                series: <CartesianSeries>[
              ColumnSeries<ChartData, double>(
                  dataSource: chartData,
                  xValueMapper: (ChartData data, _) => data.x,
                  yValueMapper: (ChartData data, _) => data.y,
                  emptyPointSettings: EmptyPointSettings(
                    mode: EmptyPointMode.average
                            )
                        )
                    ]
                )
            )
        )
    );
}

{% endhighlight %}

![Empty points](images/series-customization/emptyPoint.jpg)

### Empty point customization

Specific color for empty point can be set by [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointSettings/color.html) property in [`emptyPointSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/emptyPointSettings.html). The [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointSettings/borderWidth.html) property is used to change the stroke width of the empty point and [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointSettings/borderColor.html) is used to change the stroke color of the empty point.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        
        final List<ChartData> chartData = [
            ChartData(1, 112),
            ChartData(2, null),
            ChartData(3, 107),
            ChartData(4, 87),
        ];

        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
                series: <CartesianSeries>[
              ColumnSeries<ChartData, double>(
                  dataSource: chartData,
                  xValueMapper: (ChartData data, _) => data.x,
                  yValueMapper: (ChartData data, _) => data.y,
                  borderColor: Colors.blue,
                  borderWidth: 5,
                  emptyPointSettings: EmptyPointSettings(
                    mode: EmptyPointMode.average, 
                    color: Colors.red, 
                    borderColor: Colors.black,
                    borderWidth: 2
                            )
                        )
                    ]
                )
            )
        )
    );
}

{% endhighlight %}

![Empty points customization](images/series-customization/emptyPoint_customization.jpg)

## Sorting

The chart’s data source can be sorted using the [`sortingOrder`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/sortingOrder.html) and [`sortFieldValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/sortFieldValueMapper.html) properties of series. The [`sortingOrder`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/sortingOrder.html) property specifies the data points in the series can be sorted in [`ascending`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SortingOrder-class.html) or [`descending`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SortingOrder-class.html) order. The data points will be rendered in the specified order if [`sortingOrder`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/sortingOrder.html) is set to [`none`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SortingOrder-class.html). The [`sortFieldValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/sortFieldValueMapper.html) specifies the field in the data source, which is considered for sorting the data points.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        
         final List<ChartData> chartData = [
            ChartData('USA', 112),
            ChartData('China', 97),
            ChartData('Japan', 107),
            ChartData('Africa', 87),
        ];

        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
              primaryXAxis: CategoryAxis(),
                series: <CartesianSeries>[
              ColumnSeries<ChartData, String>(
                  dataSource: chartData,
                  xValueMapper: (ChartData data, _) => data.x,
                  yValueMapper: (ChartData data, _) => data.y,
                  sortingOrder: SortingOrder.descending,
                  sortFieldValueMapper: (ChartData data, _) => data.x,
                        ),
                    ]
                )
            )
        )
    );
}

{% endhighlight %}

![Sorting](images/series-customization/sorting.jpg)