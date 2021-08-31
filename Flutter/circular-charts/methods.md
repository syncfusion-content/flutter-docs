---
layout: post
title: Methods in Flutter Circular Charts widget | Syncfusion 
description: Learn here all about available Methods of Syncfusion Flutter Circular Charts (SfCircularChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Methods in Flutter Circular Charts (SfCircularChart)

## Methods in tooltipBehavior

### Show method in tooltipBehavior

The [`show`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/show.html) method is used to activate the tooltip at the specified x and y point values.

{% highlight dart %} 

    late SfCircularChart chart;
    late TooltipBehavior _tooltipBehavior;

    @override
    void initState() {
    _tooltipBehavior = TooltipBehavior(enable: true);
    super.initState();
    }

    @override
    Widget build(BuildContext context) {
    final List<ChartData> chartData = [
      ChartData(10, 17),
      ChartData(20, 34),
      // Add the required data
    ];

    chart = SfCircularChart(
        tooltipBehavior: _tooltipBehavior,
        series: <CircularSeries>[
          PieSeries<ChartData, double>(
              enableTooltip: true,
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y)
        ]);

    return Scaffold(
        body: Center(
            child: Column(children: <Widget>[
      Container(child: chart),
      TextButton(child: Text('Show'), onPressed: show),
      ])));
    }

    void show() {
    _tooltipBehavior.show(10, 17);
      }
    }

    class ChartData {
    ChartData(this.x, this.y);
    final double x;
    final double y;
    }
  
{% endhighlight %}

### showByIndex method in tooltipBehavior

The [`showByIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/showByIndex.html) method is used to display the tooltip at the specified series and point index.

The below mentioned arguments are given to the [`showByIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/showByIndex.html) method:

[`seriesIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/seriesIndex.html) - index of the series for which the pointIndex is specified.

[`pointIndex`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipArgs/pointIndex.html)  - index of the point for which the tooltip should be shown.


{% highlight dart %} 

    late SfCircularChart chart;
    late TooltipBehavior _tooltipBehavior;

    @override
    void initState(){
      _tooltipBehavior = TooltipBehavior(enable: true);
      super.initState();
    }

    @override
    Widget build(BuildContext context) {

      final List<ChartData> chartData = [
          ChartData(10, 17),
          ChartData(20, 34),
          // Add the required data
      ];

      chart = SfCircularChart(
        tooltipBehavior: _tooltipBehavior,
          series: <CircularSeries>[
            PieSeries<ChartData, double>(
              enableTooltip: true,
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y)
        ]
      );

      return Scaffold(
        body: Center(
          child: Column(
            children: <Widget>[
              Container(child: chart),
              TextButton(
                child: Text('Show'),
                onPressed:(){
                    _tooltipBehavior.showByIndex(0,1);
                  }
                ),
              ]
            )
          )
        );
      }
    }

    class ChartData {
    ChartData(this.x, this.y);
    final double x;
    final double y;
    }

{% endhighlight %}

### showByPixel method in tooltipBehavior

The [`showByPixel`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/showByPixel.html) method is used to display the tooltip at the specified x and y-positions.

x & y - logical pixel values to position the tooltip.

{% highlight dart %} 

    late SfCircularChart chart;
    late TooltipBehavior _tooltipBehavior;

    @override
    void initState(){
      _tooltipBehavior = TooltipBehavior(enable: true);
      super.initState();
    }

    @override
    Widget build(BuildContext context) {

      final List<ChartData> chartData = [
          ChartData(10, 17),
          ChartData(20, 34),
          // Add the required data
      ];

      chart = SfCircularChart(
        tooltipBehavior: _tooltipBehavior,
          series: <CircularSeries>[
            PieSeries<ChartData, double>(
              enableTooltip: true,
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y)
        ]
      );

      return Scaffold(
        body: Center(
          child: Column(
            children: <Widget>[
              Container(child: chart),
              TextButton(
                child: Text('Show'),
                onPressed:(){
                  _tooltipBehavior.showByPixel(230.0,470.0);
                  }
                ),
              ]
            )
          )
        );
      }
    }

    class ChartData {
    ChartData(this.x, this.y);
    final double x;
    final double y;
    }

{% endhighlight %}

### Hide method in tooltipBehavior

The [`hide`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/hide.html) method is used to hide the displaying tooltip programmatically.

{% highlight dart %} 

    late SfCircularChart chart;
    late TooltipBehavior _tooltipBehavior;

    @override
    void initState(){
      _tooltipBehavior = TooltipBehavior(enable: true);
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
      final List<ChartData> chartData = [
          ChartData(10, 17),
          ChartData(20, 34)
      // Add the required data  
      ];

      chart = SfCircularChart(
        tooltipBehavior: _tooltipBehavior,
        series: <CircularSeries>[
          PieSeries<ChartData, double>(
              enableTooltip: true,
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y)
          ]
      );

      return Scaffold(
        body: Center(
          child: Column(
            children: <Widget>[
              Container(child: chart),
              TextButton(
                child: Text('Hide'),
                onPressed: hide
              ),
            ]
          )
        )
      );
    }

    void hide(){
        _tooltipBehavior.hide();
      }
    }

    class ChartData {
    ChartData(this.x, this.y);
    final double x;
    final double y;
    }

{% endhighlight %}

## Methods in selectionBehavior

### SelectDataPoints method in selectionBehavior

The [`selectDataPoints`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SelectionBehavior/selectDataPoints.html) method is used to select the data point programmatically. The required arguments are listed below.

* `pointIndex` - index of the point which needs to be selected.
* `seriesIndex` - index of the series for which the pointIndex is specified and this is an optional parameter. By default it will be considered as 0.

N> The [`enableMultiSelection`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/enableMultiSelection.html) is also applicable for this but, it is based on the API values specified in the chart.

{% highlight dart %}

    late SfCircularChart chart;
    late SelectionBehavior _selectionBehavior;

    @override
    void initState(){
      _selectionBehavior = SelectionBehavior(enable: true);
      super.initState();
    }

    @override
    Widget build(BuildContext context) {
      
      final List<ChartData> chartData = [
        ChartData(10, 17),
        ChartData(20, 34)
        // Add the required data
      ];
      chart = SfCircularChart(
        series: <CircularSeries>[
          PieSeries<ChartData, double>(
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y,
              selectionBehavior: _selectionBehavior
          )
        ]
      );
      
      return Scaffold(
        body: Center(
          child: Column(
            children: <Widget>[
              Container(child: chart),
              TextButton(
                child: Text('Select'),
                onPressed: select
              ),
            ]
          )
        )
      );
    }

    void select() {
        _selectionBehavior.selectDataPoints(1, 0);
      }
    }

    class ChartData {
    ChartData(this.x, this.y);
    final double x;
    final double y;
    }


{% endhighlight %}