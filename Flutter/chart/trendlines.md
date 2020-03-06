---
layout: post
title: Syncfusion Flutter Charts Trendlines
description: Learn how to enable and customize the trendlines available in the Syncfusion Flutter Chart widget.
platform: flutter
control: Chart
documentation: ug
---

# Trendlines

Trendlines are used to show the direction and speed of price.

Trendlines can be generated for Cartesian type series (Line, Column, Scatter, Area, Candle, HiLo etc.) except bar type series. You can add more than one trendline to a series.

You can use the following properties to customize the behavior and appearance of trendlines.

* [`type`]() - Specifies the type of trendline the must be added to the series.
* [`isVisible`]() -Used to toggle the visibility of trendlines in a series.
* [`width`]() -Used to determine the width of trendline.
* [`backwardForecast`]() -Used to specify the range of backward forecast for the trendline.
* [`forwardForecast`]() -Used to specify the range of forward forecast for the trendline.
* [`intercept`]() - Used to provide the trendline intercept values
* [`period`]() -Used to determine the starting point for the trendline.
* [`polynomialOrder`]() -used to provide the polynomial order for polynomial type trendlines.
* [ ` animationDuration` ]() -Used to animate the trendlines . By default animationDuration has a value of 1500.When animationDuration is set to zero no animation takes place.


## Types of trendlines

Chart supports 6 types of trendlines.

### Linear

A linear trendline is a best fit straight line that is used with simpler data sets. To render a linear trendline, use trendline type as Linear.

{ % highlight dart % }

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders spline chart
                            SplineSeries<SalesData, double>(
                                dataSource: chartData,
                                trendlines:<Trendline>[
                                 Trendline(
                                type: TrendlineType.linear, 
                                color: Colors.blue)
                             ]
                        ]
                    )
                )
            )
        );
    }
{ % end highlight %}

![linear trendline](images/trendline/linear.png)

### Exponential

An exponential trendline is a curved line that is most useful when data values rise or fall at increasingly higher rates. You cannot create an exponential trendline, if your data contains zero or negative values.

To render an exponential trendline, use trendline type as Exponential .

{ % highlight dart % }

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders spline chart
                            SplineSeries<SalesData, double>(
                                dataSource: chartData,
                                trendlines:<Trendline>[
                                 Trendline(
                                type: TrendlineType.exponential, 
                                color: Colors.blue)
                             ],
                        ]
                    )
                )
            )
        );
    }
{ % end highlight %}

![exponential trendline](images/trendline/exponential.png)

### Logarithmic

A logarithmic trendline is a best-fit curved line that is most useful when the rate of change in the data increases or decreases quickly and then levels out. A logarithmic trendline can use negative and/or positive values.

To render a logarithmic trendline, use trendline type as Logarithmic 

{ % highlight dart % }

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders spline chart
                            SplineSeries<SalesData, double>(
                                dataSource: chartData,
                                trendlines:<Trendline>[
                                 Trendline(
                                type: TrendlineType.logarithmic, 
                                color: Colors.blue)
                             ],
                        ]
                    )
                )
            )
        );
    }
{ % end highlight %}
 
![logarithmic trendline](images/trendline/logarithmic.png)


### Polynomial
A polynomial trendline is a curved line that is used when data fluctuates.

To render a polynomial trendline, use trendline type as Polynomial.

{ % highlight dart % }

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders spline chart
                            SplineSeries<SalesData, double>(
                                dataSource: chartData,
                                trendlines:<Trendline>[
                                 Trendline(
                                type: TrendlineType.polynomial, 
                                color: Colors.blue)
                             ],
                        ]
                    )
                )
            )
        );
    }
{ % end highlight %}


![polynomial trendline](images/trendline/polynomial.png)

### Power
A power trendline is a curved line that is best used with data sets that compare measurements that increase at a specific rate.

To render a power trendline, use trendline type as Power

{ % highlight dart % }

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders spline chart
                            SplineSeries<SalesData, double>(
                                dataSource: chartData,
                                trendlines:<Trendline>[
                                 Trendline(
                                type: TrendlineType.power, 
                                color: Colors.blue)
                             ],
                        ]
                    )
                )
            )
        );
    }
{ % end highlight %}

![power trendline](images/trendline/power.png)

### Moving Average
A moving average trendline smoothen out fluctuations in data to show a pattern or trend more clearly.

To render a moving average trendline, use trendline type as MovingAverage 

{ % highlight dart % }

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders spline chart
                            SplineSeries<SalesData, double>(
                                dataSource: chartData,
                                trendlines:<Trendline>[
                                 Trendline(
                                type: TrendlineType.MovingAverage,
                                color: Colors.blue)
                             ],
                        ]
                    )
                )
            )
        );
    }
{ % end highlight %}

![linear trendline](images/trendline/movingaverage.png)

## Forecasting

Trendline forecasting is the prediction of future/past situations.

Forward Forecasting and Backward Forecasting are the two types of forecasting.

### Forward Forecasting

The value set for forwardForecast is used to determine the distance moving towards the future trend.

{ % highlight dart % }

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders spline chart
                            SplineSeries<SalesData, double>(
                                dataSource: chartData,
                                trendlines:<Trendline>[
                                 Trendline(
                                type: TrendlineType.linear, 
                                forwardForecast:10,
                                color: Colors.blue),
                             ],
                        ]
                    )
                )
            )
        );
    }
{ % end highlight %}

![forward forecast](images/trendline/forwardforecast.png)

### Backward Forecasting

The value set for the backwardForecast is used to determine the past trends.

{ % highlight dart % }

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders spline chart
                            SplineSeries<SalesData, double>(
                                dataSource: chartData,
                                trendlines:<Trendline>[
                                 Trendline(
                                type: TrendlineType.linear, 
                                backwardForecast:10,
                                color: Colors.blue)
                             ],
                        ]
                    )
                )
            )
        );
    }
{ % end highlight %}

![forward forecast](images/trendline/backwardforecast.png)

## Legend

Legend provides information about the series rendered in the chart.Legend for trendline gets rendered  together  with the series legend when the legend is set to be visible.Also when the  [ `name` ]()  property is assigned to a trendline,the name of the legend is changed based on the name of the trendlines.[`legendItemText`]()  can also be provided for changing the name of the legend.In default  rendering the [`legendIconShape`]()  will be a horizontal line.

{ % highlight dart % }

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders spline chart
                            SplineSeries<SalesData, double>(
                                dataSource: chartData,
                                trendlines:<Trendline>[
                                 Trendline(
                                type: TrendlineType.linear, 
                                name:'trendline-name',
                                color: Colors.blue)
                             ],
                        ]
                    )
                )
            )
        );
    }
{ % end highlight %}

![forward forecast](images/trendline/legend.png)


## Markers

Data markers are used to provide information about the data points in the series. You can add a shape to adorn each data point.Trendlines support markers that can be enabled using the property [`markerSettings`]() .

{ % highlight dart % }

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders spline chart
                            SplineSeries<SalesData, double>(
                                dataSource: chartData,
                                trendlines:<Trendline>[
                                 Trendline(
                                type: TrendlineType.linear, 
                                name:'trendline-name',
                                 markerSettings: MarkerSettings(isVisible:true),
                                color: Colors.blue)
                             ],
                        ]
                    )
                )
            )
        );
    }
{ % end highlight %}

![backward forecast](images/trendline/marker.png)

## Tooltip

Chart will display details about the points through tooltip, when user interaction is done over the point.Trendline Tooltip has the same [`ActivationMode`]()  that has been given in the [`TooltipBehavior`]()  of the series.

{ % highlight dart % }

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders spline chart
                            SplineSeries<SalesData, double>(
                                dataSource: chartData,
                                trendlines:<Trendline>[
                                 Trendline(
                                type: TrendlineType.linear, 
                                name:'trendline-name',
                                 enableTooltip: true,
                                 markerSettings: MarkerSettings(isVisible:true),
                                color: Colors.blue)
                             ],
                        ]
                    )
                )
            )
        );
    }
{ % end highlight %}


![tooltip](images/trendline/tooltip.png)





