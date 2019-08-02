---
layout: post
title: Multiple series in Syncfusion Flutter chart
description: Learn how to render different types of series in a chart.
platform: flutter
control: Chart
documentation: ug
---

# Series customization

## Multiple series

You can add multiple series to [`series`]() property of [`SfCartesianChart`]() class. By default, all the series rendered based on the [`PrimaryXAxis`]() and [`PrimaryYAxis`]() of [`SfCartesianChart`](). But if you want to plot different unit or value that is specific to particular series, you can specify the separate axis for that series using [`xAxisName`]() and [`yAxisName`]() properties of series.

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
            ])
            )
        ));
    }

{% endhighlight %}

![Multiple series](images/getting-started/livechart.png)

## Combination series

[`SfCartesianChart`]() allows you to render the combination of different types of series.

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
            ])
            )
        ));
    }

{% endhighlight %}

![Combination series](images/getting-started/livechart.png)

**Limitation of Combination Chart**

* Cartesian type series cannot be combined with Circular series (pie, doughnut, and radial bar).

## Animation

[`SfCartesianChart`]() provides animation support for data series. Series will be animated whenever the items source changes. Animation is enabled by default, you can also control the duration of the animation using [`animationDuration`]() property.

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
            ])
            )
        ));
    }

{% endhighlight %}

## Transpose the series

The [`isTransposed`]() property of [`CartesianSeries`]() is used to plot the chart vertically and view the data in a different perspective.

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
                    animationDuration: 1000
                )])
            )
        ));
    }

{% endhighlight %}

![Transposed chart](images/getting-started/livechart.png)

## Color palette

The [`palette`]() property is used to define the colors for each series.

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
            ])
            )
        ));
    }

{% endhighlight %}

![Palette](images/getting-started/livechart.png)

## Color mapping for data points   

The [`pointColorMapper`]() property is used to map the color field from data source. 

The [`palette`]() property is used to define the colors for each series.

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
              ),
            ])
            )
        ));
    }

    class ChartData {
        ChartData(this.x, this.y, this.color);
            final String x;
            final double y;
            final Color color;
    }

{% endhighlight %}

![Point color mapping](images/getting-started/livechart.png)

## Gradient fill

The [`gradient`]() property is used to define the gradient colors. The colors from this property is used for series.

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
            ])
            )
        ));
    }

{% endhighlight %}

![Gradient color](images/getting-started/livechart.png)

## Empty points

The data points that uses the null as value are considered as empty points. Empty data points are ignored and not plotted in the Chart when the data is provided by using the points property. By using [`emptyPointSettings`]() property in series, you can customize the empty point. Available [`mode`]() types are [`gap`](), [`zero`](), [`drop`]() and [`average`]().Default mode of the empty point is [`gap`]().

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
                  emptyPointSettings: EmptyPointSettings(
                    mode: EmptyPointMode.average
                  )),
            ])
            )
        ));
    }

{% endhighlight %}

![Empty points](images/getting-started/livechart.png)

### Empty point customization

Specific color for empty point can be set by [`color`]() property in [`emptyPointSettings`](). The [`borderWidth`]() property is used to change the stroke width of the empty point and [`borderColor`]() is used to change the stroke color of the empty point.

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
                  )),
            ])
            )
        ));
    }

{% endhighlight %}

![Empty points customization](images/getting-started/livechart.png)

## Sorting

The chart’s data source can be sorted using the [`sortingOrder`]() and [`sortFieldValueMapper`]() properties of series. The [`sortingOrder`]() property specifies the data points in the series can be sorted in [`ascending`]() or [`descending`]() order. The data points will be rendered in the specified order if [`sortingOrder`]() is set to [`none`](). The [`sortFieldValueMapper`]() specifies the field in the data source, which is considered for sorting the data points.

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
            ])
            )
        ));
    }

{% endhighlight %}

![Sorting](images/getting-started/livechart.png)