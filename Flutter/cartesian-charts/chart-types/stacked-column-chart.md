---
layout: post
title: Stacked column Chart in Flutter Cartesian Charts | Syncfusion 
description: Learn here all about stacked column chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Stacked column Chart in Flutter Cartesian Charts (SfCartesianChart)

To create a Flutter stacked column chart quickly, you can check this video.

<style>#flutterstackedcolumnChartTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='flutterstackedcolumnChartTutorial' src='https://www.youtube.com/embed/NCUDBD_ClHo'></iframe>

To render a stacked column chart, create an instance of [`StackedColumnSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedColumnSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). The following properties can be used to customize the appearance of stacked line series:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) - changes the color of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) - changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) - changes the stroke color of the series.


{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = [
          ChartData('China', 12, 10, 14, 20),
          ChartData('USA', 14, 11, 18, 23),
          ChartData('UK', 16, 10, 15, 20),
          ChartData('Brazil', 18, 16, 18, 24)
        ];

         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            StackedColumnSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedColumnSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                             StackedColumnSeries<ChartData,String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                            StackedColumnSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y4
                            )
                        ]
                    )
                )   
            )
        );
    }

    class ChartData{
        ChartData(this.x, this.y1, this.y2, this.y3, this.y4);
        final String x;
        final String y1;
        final String y2;
        final String y3;
        final String y4;
    }

{% endhighlight %}

![Stacked column](cartesian-chart-types-images/stacked_column.jpg)

## Grouping series

You can group and stack the similar stacked series types using the [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedColumnSeries/groupName.html) property of stacked series. The stacked series that contains the same [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedColumnSeries/groupName.html) will be stacked in a single group.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            StackedColumnSeries<ChartData, String>(
                                groupName: 'Group A',
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedColumnSeries<ChartData, String>(
                                groupName: 'Group B',
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedColumnSeries<ChartData, String>(
                                groupName: 'Group A',
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                            StackedColumnSeries<ChartData, String>(
                                groupName: 'Group B',
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y4
                            )
                        ]
                    )
                )   
            )
        );
    }

    class ChartData{
        ChartData(this.x, this.y1, this.y2, this.y3, this.y4);
        final String x;
        final String y1;
        final String y2;
        final String y3;
        final String y4;
    }

{% endhighlight %}

![Stacked column grouping](cartesian-chart-types-images/stacked_column_grouping.jpg)

## Display cumulative values

You can show the cumulative data label values using the [`showCumulativeValues`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/showCumulativeValues.html) property. If the series are grouped using [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedColumnSeries/groupName.html), then cumulative values will be shown based on grouping.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            StackedColumnSeries<ChartData, String>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(isVisible:true, showCumulativeValues: true),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedColumnSeries<ChartData, String>(
                                groupName: 'Group B',
                                dataLabelSettings: DataLabelSettings(isVisible:true, showCumulativeValues: true),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedColumnSeries<ChartData, String>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(isVisible:true, showCumulativeValues: true),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                            StackedColumnSeries<ChartData, String>(
                                groupName: 'Group B',
                                dataLabelSettings: DataLabelSettings(isVisible:true, showCumulativeValues: true),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y4
                            )
                        ]
                    )
                )   
            )
        );
    }

    class ChartData{
        ChartData(this.x, this.y1, this.y2, this.y3, this.y4);
        final String x;
        final String y1;
        final String y2;
        final String y3;
        final String y4;
    }

{% endhighlight %}

![Stacked column cumulative](cartesian-chart-types-images/stacked_column_cumulative.jpg)

#### See Also

* [Color palette](./series-customization#color-palette) 
* [Color mapping](./series-customization#color-mapping-for-data-points)
* [Animation](./series-customization#animation)
* [Gradient](./series-customization#gradient-fill)
* [Empty points](./series-customization#empty-points)  
* [Sorting](./series-customization##sorting) 