---
layout: post
title: Circular series customization in Syncfusion Flutter charts
description: Learn how to customize the series features like animation, color palette, gradient, etc., in SfCircular chart
platform: flutter
control: Chart
documentation: ug
---

# Series customization in Circular charts 

## Animation

[`SfCircularChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart-class.html) provides animation support for the series. Series will be animated while rendering. Animation is enabled by default, you can also control the duration of the animation using [`animationDuration`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/animationDuration.html) property. You can disable the animation by setting 0 value to that property.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(series: <CircularSeries<ChartData,dynamic>>[
                        // Render pie chart
                        PieSeries<ChartData, String>(
                            dataSource: chartData,
                            pointColorMapper:(ChartData data,  _) => data.color,
                            xValueMapper: (ChartData data, _) => data.x,
                            yValueMapper: (ChartData data, _) => data.y,
                            animationDuration: 1000
                        )
                    ]
                )
            )
        )
    );
    }}

{% endhighlight %}

## Color Palette

[`SfCircularChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart-class.html) provides Color Palette property called [`palette`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/palette.html) for the data points in the chart series. If the series color is not specified, then the series will be rendered with appropriate palette color. Ten colors are available by default.


{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(
                        palette: <Color>[Colors.amber, Colors.brown, Colors.green, Colors.redAccent, Colors.blueAccent, Colors.teal],
                        series: <CircularSeries<ChartData,dynamic>>[
                        // Render pie chart
                        PieSeries<ChartData, String>(
                            dataSource: chartData,
                            pointColorMapper:(ChartData data,  _) => data.color,
                            xValueMapper: (ChartData data, _) => data.x,
                            yValueMapper: (ChartData data, _) => data.y,
                        )
                    ]
                )
            )
        )
    );
    }}

{% endhighlight %}

![Color Palette](images/circular-customization/color_palette.jpg)

## Dynamic animation

[`SfCircularChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart-class.html) also provide the dynamic animation support for the series.The series can be dynamically added to the charts, it will animated by setting the timer value. when you set the [`animationDuration`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/animationDuration.html) value to 0, the series won't be animated. 


## Empty points

The data points that has null value are considered as empty points. Empty data points are ignored and not plotted in the chart. By using [`emptyPointSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/emptyPointSettings.html) property in series, you can decide the action taken for empty points. Available [`modes`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode-class.html) are [`gap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode-class.html), [`zero`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode-class.html), [`drop`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode-class.html) and [`average`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode-class.html). Default mode of the empty point is [`gap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointMode-class.html).

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        
         final List<ChartData> chartData = [
            ChartData('David', null),
            ChartData('Steve', 38),
            ChartData('Jack', 34),
            ChartData('Others', 52)
        ];
        return Scaffold(
            body: Center(
                child: SfCircularChart(
                    series: <CircularSeries<ChartData,dynamic>>[
                        // Render pie chart
                        PieSeries<ChartData, String>(
                            dataSource: chartData,
                            dataLabelSettings: DataLabelSettings(isVisible:true),
                            emptyPointSettings:
                      EmptyPointSettings(mode: EmptyPointMode.average),
                            pointColorMapper:(ChartData data,  _) => data.color,
                            xValueMapper: (ChartData data, _) => data.x,
                            yValueMapper: (ChartData data, _) => data.y,)])));
    }}

{% endhighlight %}

![Empty points](images/circular-customization/emptyPoints.jpg)

### Empty point customization

Specific color for empty point can be set by [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointSettings/color.html) property in [`emptyPointSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/emptyPointSettings.html). The [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointSettings/borderWidth.html) property is used to change the stroke width of the empty point and [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmptyPointSettings/borderColor.html) is used to change the stroke color of the empty point.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
     final List<ChartData> chartData = [
      ChartData('David', null),
      ChartData('Steve', 38),
      ChartData('Jack', 34),
      ChartData('Others', 52)
    ];
    return Scaffold(
        body: Center(
            child: Container(
                child: SfCircularChart(
                    series: <CircularSeries<ChartData, dynamic>>[
          PieSeries<ChartData, String>(
              dataSource: chartData,
              dataLabelSettings: DataLabelSettings(isVisible: true),
              emptyPointSettings: EmptyPointSettings(
                  mode: EmptyPointMode.average,
                  color: Colors.red,
                  borderColor: Colors.black,
                  borderWidth: 2),
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y)
        ]))));
      }}

{% endhighlight %}

![Empty points customization](images/circular-customization/emptyPointcustomization.jpg)

## Sorting

The chart’s data source can be sorted using the [`sortingOrder`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/sortingOrder.html) and [`sortFieldValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/sortFieldValueMapper.html) properties of series. The [`sortingOrder`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SortingOrder-class.html) property specifies the data points in the series can be sorted in [`ascending`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SortingOrder-class.html) or [`descending`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SortingOrder-class.html) order. The data points will be rendered in the specified order if [`sortingOrder`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/sortingOrder.html) is set to [`none`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SortingOrder-class.html). The [`sortFieldValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/sortFieldValueMapper.html) specifies the field in the data source, which is considered for sorting the data points.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        
         final List<ChartData> chartData = [
            ChartData('David', 25),
            ChartData('Steve', 38),
            ChartData('Jack', 34),
            ChartData('Others', 52)
        ];

        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(
                      
                      series: <CircularSeries<ChartData,dynamic>>[
                        // Render pie chart
                        PieSeries<ChartData, String>(
                            dataSource: chartData,
                            dataLabelSettings: DataLabelSettings(isVisible:true),
                            sortingOrder: SortingOrder.ascending,
                            sortFieldValueMapper: (ChartData data, _) => data.x,
                            pointColorMapper:(ChartData data,  _) => data.color,
                            xValueMapper: (ChartData data, _) => data.x,
                            yValueMapper: (ChartData data, _) => data.y,
                            animationDuration: 1000
                        )]))));
    }}

{% endhighlight %}

![Sorting](images/circular-customization/sortings.jpg)

## Color mapping for data points   

The [`pointColorMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/pointColorMapper.html) property is used to map the color field from the data source. 

{% highlight dart %} 

    @override
     Widget build(BuildContext context) {
    static dynamic chartData = <SalesData>[
    SalesData('Rent', 1000,Colors.teal),
    SalesData('Food', 2500,Colors.lightBlue),
    SalesData('Savings', 760,Colors.brown),
    SalesData('Tax', 1897,Colors.grey),
    SalesData('Others', 2987,Colors.blueGrey)
     ];
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(
                        primaryXAxis: CategoryAxis(),
                        series: <PieSeries<SalesData, String>>[
                            PieSeries<SalesData, String>(
                                dataSource: chartData,
              xValueMapper: (SalesData sales, _) => sales.year,
              yValueMapper: (SalesData sales, _) => sales.sales,
              //map Color for each dataPoint datasource.
              pointColorMapper: (SalesData sales,_) => sales.color,
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![mapcolor](images/circular-customization/color-mapping.jpg)
