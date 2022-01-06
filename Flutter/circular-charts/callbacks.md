---
layout: post
title: Callbacks in Flutter Circular Charts widget | Syncfusion 
description: Learn here all about available Callbacks feature of Syncfusion Flutter Circular Charts (SfCircularChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Callbacks in Flutter Circular Charts (SfCircularChart)

Circular chart contains the below listed callbacks

## onLegendItemRender

Triggers when the legend item is rendering. Here, you can customize the legend’s text, and shape.  The [`onLegendItemRender`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/onLegendItemRender.html) Callback contains the following arguments.

* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendRenderArgs/text.html) - specifies the content of the legend.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendRenderArgs/pointIndex.html) - specifies the current point index that is applicable for circular chart type alone.
* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendRenderArgs/seriesIndex.html) - specifies the current series index.
* [`legendIconType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendRenderArgs/legendIconType.html) - specifies the shape of the legend.
* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendRenderArgs/color.html) - to get and set the color of the legend icon.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
      return Scaffold(
        body: Center(
          child: SfCircularChart(
            legend: Legend(isVisible: true),
            onLegendItemRender: (LegendRenderArgs args){
              args.text = 'Legend Text';
              args.legendIconType = LegendIconType.diamond;
            }
          )
        )
      );
    }

{% endhighlight %}

## onTooltipRender

Triggers while tooltip is rendering. Here, you can customize the text, header, x and y-positions. The [`onTooltipRender`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/onTooltipRender.html) Callback contains the following arguments.

* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/text.html) - specifies the content of the tooltip.
* [`header`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/header.html) - specifies the header content of the tooltip.
* [`locationX`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/locationX.html) - specifies the x position of tooltip.
* [`locationY`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/locationY.html) - specifies the y position of tooltip.
* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/seriesIndex.html) - specifies the current series index.
* [`dataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/dataPoints.html) - holds the data point collection.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/pointIndex.html) - specifies the current point index.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/viewportPointIndex.html) - to get the viewport index value of the tapped data label.

{% highlight dart %}
    
    late TooltipBehavior _tooltipBehavior;

    @override
    void initState(){
      _tooltipBehavior = TooltipBehavior(enable: true);
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
    
      return Scaffold(
        body: Center(
          child: SfCircularChart(
            onTooltipRender: (TooltipArgs args){
              args.text = 'Custom Text';
            },
            tooltipBehavior:_tooltipBehavior,
          )
        )
      );
    }

{% endhighlight %}

## onDataLabelRender

Triggers when data label is rendering. Text and text styles such as color, font size, and font weight can be customized. The [`onDataLabelRender`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/onDataLabelRender.html) Callback contains the following arguments.

* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/text.html) - specifies the content of the data label.
* [`textStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/textStyle.html) - used to change the text color, size, font family, font style, and font weight.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/pointIndex.html) - specifies the current point index.
* [`seriesRenderer`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/seriesRenderer.html) - specifies current series.
* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/color.html) - to get and set the color of data label.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/viewportPointIndex.html) - to get the viewport index value of the tapped data label.
* [`dataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelRenderArgs/dataPoints.html) - to get the data points of the series.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
      return Scaffold(
        body: Center(
          child: SfCircularChart(
            onDataLabelRender:(DataLabelRenderArgs args){
              args.text = 'Data label';
            },
            series: <CircularSeries>[
              PieSeries<ChartData, String>(
              dataLabelSettings: DataLabelSettings(
                  isVisible: true
              )
              )
            ]
          )
        )
      );
    }

{% endhighlight %}

## onPointTap

Triggers when tapping on the series point. The [`onPointTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/onPointTap.html) callback contains the following arguments.

* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/seriesIndex.html) - specifies the current series index.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/pointIndex.html) - specifies the current point index.
* [`dataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/dataPoints.html) - holds the data point collection.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/viewportPointIndex.html) - specifies the viewport index value of the tapped data point.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfCircularChart(
             series: <CircularSeries>[
              PieSeries<ChartData, String>(
                onPointTap: (ChartPointDetails details) {
                  print(details.pointIndex);
                  print(details.seriesIndex);
                }
              )
            ],
          )
        )
      );
    }

{% endhighlight %}

## onPointDoubleTap

Triggers when double-tap the series point. The [`onPointDoubleTap`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/onPointDoubleTap.html) callback contains the following arguments.

* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/seriesIndex.html) - specifies the current series index.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/pointIndex.html) - specifies the current point index.
* [`dataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/dataPoints.html) - holds the data point collection.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/viewportPointIndex.html) - specifies the viewport index value of the double-tapped data point.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfCircularChart(
             series: <CircularSeries>[
              PieSeries<ChartData, String>(
                onPointDoubleTap: (ChartPointDetails details) {
                  print(details.pointIndex);
                  print(details.seriesIndex);
                }
              )
            ],
          )
        )
      );
    }

{% endhighlight %}

## onPointLongPress

Triggers when long press on the series point. The [`onPointLongPress`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/onPointLongPress.html) callback contains the following arguments.

* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/seriesIndex.html) - specifies the current series index.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/pointIndex.html) - specifies the current point index.
* [`dataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/dataPoints.html) - holds the data point collection.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartPointDetails/viewportPointIndex.html) - specifies the viewport index value of the long pressed data point.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfCircularChart(
             series: <CircularSeries>[
              PieSeries<ChartData, String>(
                onPointLongPress: (ChartPointDetails details) {
                  print(details.pointIndex);
                  print(details.seriesIndex);
                }
              )
            ],
          )
        )
      );
    }
{% endhighlight %}

## onLegendTapped

Triggers when tapping the legend item. The [`onLegendTapped`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/onLegendTapped.html) Callback contains the following arguments.

* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendTapArgs/seriesIndex.html) - specifies the current series index.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendTapArgs/pointIndex.html) - specifies the current point index that is applicable for circular series.
* [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LegendTapArgs/series.html) - specifies the current series.


{% highlight dart %}

    @override
    Widget build(BuildContext context) {
    
      return Scaffold(
        body: Center(
          child: SfCircularChart(
            onLegendTapped: (LegendTapArgs args) {
              print(args.seriesIndex);
            },
            legend: Legend(isVisible: true)
          )
        )
      );
    }

{% endhighlight %}

## onSelectionChanged

Triggers while selection changes. Here you can customize the selectedColor, unselectedColor, selectedBorderColor, selectedBorderWidth, unselectedBorderColor, and unselectedBorderWidth properties. The [`onSelectionChanged`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/onSelectionChanged.html) Callback contains the following arguments.

* [`seriesRenderer`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/seriesRenderer.html) - specifies current series.
* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/seriesIndex.html) - specifies the current series index.
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/pointIndex.html) - specifies the current point index.
* [`selectedColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/selectedColor.html) - specifies color of the selected data points or series.
* [`unselectedColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/unselectedColor.html) - specifies color of the unselected data points or series.
* [`selectedBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/selectedBorderColor.html) - specifies border color of the selected data points or series.
* [`selectedBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/selectedBorderWidth.html) - specifies border width of the selected data points or series.
* [`unselectedBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/unselectedBorderColor.html) - specifies border color of the unselected data points or series.
* [`unselectedBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/unselectedBorderWidth.html) - specifies border width of the unselected data points or series.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionArgs/viewportPointIndex.html) - to get the overall point index.

{% highlight dart %}
    
    late SelectionBehavior _selectionBehavior;

    @override
    void initState(){
      _selectionBehavior = SelectionBehavior(
                enable: true);
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
    
      return Scaffold(
        body: Center(
          child: SfCircularChart(
          onSelectionChanged: (SelectionArgs args){
              args.selectedColor = Colors.red;
              args.unselectedColor = Colors.lightGreen;
            },
            series: <CircularSeries>[
              PieSeries<ChartData, String>(
                selectionBehavior: _selectionBehavior
              )
            ]
          )
        )
      );
    }

{% endhighlight %}

## onDataLabelTapped

Triggers when tapping on the data label of the data point in the series. The [`onDataLabelTapped`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/onDataLabelTapped.html) Callback contains the following arguments.

* [`position`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/position.html) - specifies the position of the tapped data label in logical pixels.
* [`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/seriesIndex.html) - Specifies the series index of the tapped data label
* [`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/pointIndex.html) - Specifies the point index of the tapped data label.
* [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/text.html) - Specifies the content of the tapped data label.
* [`dataLabelSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/dataLabelSettings.html) - to get the data label customization options specified in that particular series.
* [`viewportPointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelTapDetails/viewportPointIndex.html) - to get the viewport index value of the tapped data label.

>**NOTE**: This callback will not be called, when the builder is specified for data label (data label template). For this case, custom widget specified in the [`DataLabelSettings.builder`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/builder.html) property can be wrapped using the [`GestureDetector`](https://api.flutter.dev/flutter/widgets/GestureDetector-class.html) and this functionality can be achieved in the application level.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Container(
        child: SfCircularChart(
          onDatalabelTapped: (DataLabelTapArgs args) {
            print(args.seriesIndex);                 
          },
          series: <CircularSeries<Sample, DateTime>>[
            PieSeries<Sample, DateTime>(
                dataSource: sample,
                xValueMapper: (Sample sales, _) => sales.x,
                yValueMapper: (Sample sales, _) => sales.y,
                dataLabelSettings: DataLabelSettings(
                  isVisible: true),
            )
          ]
        )
      );
    }

{% endhighlight %}

## onChartTouchInteractionUp

Triggers when tapped or clicked on the chart area. You can get the tapped region using the [`position`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTouchInteractionArgs/position.html) argument.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Container(
            child: SfCircularChart(
                onChartTouchInteractionUp: (ChartTouchInteractionArgs args){
                  print(args.position.dx.toString());
                  print(args.position.dy.toString());
                }
            )
        );
    }

{% endhighlight %}

## onChartTouchInteractionMove

Triggers when tapped or clicked and moved on the chart area. You can get the tapped region using the [`position`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTouchInteractionArgs/position.html) argument.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
        return Container(
            child: SfCircularChart(
                onChartTouchInteractionMove: (ChartTouchInteractionArgs args){
                  print(args.position.dx.toString());
                  print(args.position.dy.toString());
                }
            )
        );
    }

{% endhighlight %}

## onChartTouchInteractionDown

Triggers when touched or clicked on the chart area. You can get the tapped region using the [`position`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTouchInteractionArgs/position.html) argument.

{% highlight dart %}

    @override
    Widget build(BuildContext context) {
        return Container(
          child: SfCircularChart(
                onChartTouchInteractionDown: (ChartTouchInteractionArgs args){
                  print(args.position.dx.toString());
                  print(args.position.dy.toString());
                }
            )
        );
    }

{% endhighlight %}

## onRendererCreated

Triggers when the series renderer is created. This callback can be used to obtain the [`CircularSeriesController`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeriesController-class.html) instance, which is used to access the the public methods in the series.

{% highlight dart %}

        //Initialize the series controller
    CircularSeriesController? circularSeriesController;

    return Column(children: <Widget>[
      Container(
          child: SfCircularChart(
        series: <CircularSeries<ChartData, dynamic>>[
          DoughnutSeries<ChartData, dynamic>(
            dataSource: chartData,
            xValueMapper: (ChartData data, _) => data.x,
            yValueMapper: (ChartData data, _) => data.y,
            onRendererCreated: (CircularSeriesController controller) {
              circularSeriesController = controller;
            },
          ),
        ],
      )),
      Container(
          child: ElevatedButton(
              onPressed: () {
                //Removed a point from data source
                chartData.removeAt(0);
                //Added a point to the data source
                chartData.add(ChartData(3, 23));
                //Here accessed the public method of the series.
                circularSeriesController!.updateDataSource(
                  addedDataIndexes: <int>[chartData.length - 1],
                  removedDataIndexes: <int>[0],
                );
              },
              child: Container(
                child: Text('Add a point'),
                )
              )
            )
          ]
        );
      }
    }

    class ChartData {
      ChartData(this.x, this.y);
      final num x;
      final double? y;
    }

{% endhighlight %}

## onCreateShader

The [`onCreateShader`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/onCreateShader.html) provides options to get the outer rect, inner rect, and render type (either series or legend) using [`ChartShaderDetails`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartShaderDetails-class.html)  class.

The onCreateShader callback is called once while rendering
the data points and legend. For further reference on this callback, check the [`Gradient and ImageShader`](./circular-series-customization#Gradient-fill-and-shader) section.

{% highlight dart %}

    Widget build(BuildContext context) {
    final List<ChartData> chartData = <ChartData>[
      ChartData('IND', 24),
      ChartData('AUS', 20),
      ChartData('USA', 27),
      ChartData('DEU', 57),
      ChartData('ITA', 30),
      ChartData('UK', 41),
    ];
    final List<Color> colors = <Color>[
      const Color.fromRGBO(75, 135, 185, 1),
      const Color.fromRGBO(192, 108, 132, 1),
      const Color.fromRGBO(246, 114, 128, 1),
      const Color.fromRGBO(248, 177, 149, 1),
      const Color.fromRGBO(116, 180, 155, 1)
    ];
    final List<double> stops = <double>[
      0.2,
      0.4,
      0.6,
      0.8,
      1,
    ];

    return Scaffold(
        body: Center(
            child: Container(
          child: SfCircularChart(
              onCreateShader: (ChartShaderDetails chartShaderDetails) {
                return ui.Gradient.linear(chartShaderDetails.outerRect.topRight,
                    chartShaderDetails.outerRect.centerLeft, colors, stops);
              },
              series: <PieSeries<ChartData, String>>[
                PieSeries<ChartData, String>(
                  dataSource: chartData,
                  xValueMapper: (ChartData data, _) => data.x,
                  yValueMapper: (ChartData data, _) => data.y),
                ]
              ),
            )
          )
        );
      }
    }

    class ChartData {
      ChartData(this.x, this.y);
      final String x;
      final double? y;
    }

{% endhighlight %}