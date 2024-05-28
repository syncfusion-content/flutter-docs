---
layout: post
title: Technical indicators in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about Technical indicators feature of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Technical indicators in Flutter Cartesian Charts (SfCartesianChart)


The different types of technical indicators available in chart are follows:

* [`Accumulation distribution indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AccumulationDistributionIndicator-class.html) - AD
*	[`Average true range indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AtrIndicator-class.html) - ATR
*	[`Bollinger band indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BollingerBandIndicator-class.html)
*	[`Exponential moving average indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmaIndicator-class.html) - EMA
* [`Moving average convergence divergence`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MacdIndicator-class.html) - MACD
*	[`Momentum indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MomentumIndicator-class.html)
*	[`Relative strength index indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/RsiIndicator-class.html) - RSI 
*	[`Simple moving average indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SmaIndicator-class.html) - SMA 
*	[`Stochastic indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StochasticIndicator-class.html)
*	[`Triangular moving average indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TmaIndicator-class.html) - TMA 
*	[`Rate Of Change indicator`]() - ROC 
*	[`Weighted Moving Average indicator`]() - WMA 

## Adding Technical indicator into Chart
 
To render any indicator, add it to the [`TechnicalIndicators`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator-class.html) collection using the indicators in [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html).The following properties can be used to customize the appearance:

* [`isVisible`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/isVisible.html) - To check the visibility of the indicator.
* [`period`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AtrIndicator/period.html)- Used to indicates the moving average period.
* [`signalLineColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/signalLineColor.html)- Used to defines the color for the respective indicator line.
* [`signalLineWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/signalLineWidth.html) - Used to change the signal line width.
* [`seriesName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/seriesName.html) - Used to bind the data source of chart series to technical indicators, including x and y axis.
* [`xAxisName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/xAxisName.html),[`yAxisName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/yAxisName.html) - Used to set the x and y axes 
* [`animationDuration`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/animationDuration.html) - To control the duration of animation.
* [`animationDelay`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/animationDelay.html) - Used to specify the delay duration of the indicator animation. This takes a millisecond value as input. By default, the indicator will get animated for the specified duration. If `animationDelay` is specified, then the indicator will begin to animate after the specified duration.
* [`dataSource`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/dataSource.html) - Directly bind the values such as [`xValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/xValueMapper.html),[`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/lowValueMapper.html),[`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/highValueMapper.html),[`openValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/openValueMapper.html),[`closeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/closeValueMapper.html)
* [`isVisibleInLegend`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/isVisibleInLegend.html),[`legendItemText`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/legendItemText.html),[`legendIconType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/legendIconType.html) - Used to change the legend visibility,text and Icon type
* [`name`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/name.html) - Used to define the label for corresponding indicators.
* [`dashArray`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/dashArray.html) - Used to render the indicators with dashes.


>**Note**: If you giving series and indicator in the chart, you can add the same [`seriesName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/seriesName.html) to the series and indicator, otherwise you can directly bind the [`dataSource`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/dataSource.html) to the [`indicators`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/indicators.html) property.

## Indicator Types

###  Accumulation distribution indicator (AD)

Accumulation distribution indicator is a volume-based indicator designed to measure the accumulative flow of money into and out of a security. It requires [`volumeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/volumeValueMapper.html) property additionally with the data source to calculate the signal line.

Refer the following example,

{% tabs %}
{% highlight dart %}

     @override
     Widget build(BuildContext context) {
       return Scaffold(
        body: Center(
          child: SfCartesianChart(
            primaryXAxis: DateTimeAxis(),
            legend: Legend(isVisible: true),
            indicators: [AccumulationDistributionIndicator<ChartData, DateTime>(
                  seriesName: 'HiloOpenClose')],
            series: <CartesianSeries<ChartData, DateTime>>[
              HiloOpenCloseSeries<ChartData, DateTime>(
              dataSource: ChartData,
              xValueMapper: (ChartData data, _) => data.x,
              lowValueMapper: (ChartData data, _) => data.low,
              highValueMapper: (ChartData data, _) => data.high,
              openValueMapper: (ChartData data, _) => data.open,
              closeValueMapper: (ChartData data, _) => data.close,
              name: 'HiloOpenClose'),
              ]
            )
          )
        );
      }

      class ChartData {
        ChartData(this.x, this.low, this.high, this.open, this.close);
        final DateTime x;
        final double? low;
        final double? high;
        final double? open;
        final double? close;
      }

{% endhighlight %}
{% endtabs %}

![ADIndicator](images/technical-indicators/ad.jpg)

### Average true range indicator(ATR)

ATR indicator is a technical analysis volatility indicator. This indicator does not indicate the price trend. simply the degree of price volatility. The average true range is an N-day smoothed moving average (SMMA) of the true range values.

Refer the following example,

{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
     return Scaffold(
        body: Center(
         child: SfCartesianChart(
          primaryXAxis: DateTimeAxis(),
          legend: Legend(isVisible: true),
          indicators:[
          AtrIndicator<dynamic, dynamic>(
            period: 3,
            seriesName: 'HiloOpenClose')],
    series: <CartesianSeries<ChartData, DateTime>>[
            HiloOpenCloseSeries<ChartData, DateTime>(
              dataSource: ChartData,
              xValueMapper: (ChartData data, _) => data.x,
              lowValueMapper: (ChartData data, _) => data.low,
              highValueMapper: (ChartData data, _) => data.high,
              openValueMapper: (ChartData data, _) => data.open,
              closeValueMapper: (ChartData data, _) => data.close,
              name: 'HiloOpenClose')
              ]
            )
          )
        );
      }
      class ChartData {
        ChartData(this.x, this.low, this.high, this.open, this.close);
        final DateTime x;
        final double? low;
        final double? high;
        final double? open;
        final double? close;
      }

{% endhighlight %}
{% endtabs %}

![ATRIndicator](images/technical-indicators/atr.jpg)

### Bollinger band Indicator

This indicator also has [`upperLineColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BollingerBandIndicator/upperLineColor.html) and [`lowerLineColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BollingerBandIndicator/lowerLineColor.html) properties that can be used to define the brushes for the indicator lines.

Also, we can specify standard deviation values for the BollingerBand indicator using [`standardDeviation`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BollingerBandIndicator/standardDeviation.html) property.

Refer the following example,

{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
     return Scaffold(
       body: Center(
         child: SfCartesianChart(
           primaryXAxis: DateTimeAxis(),
           legend: Legend(isVisible: true),
           indicators: [ BollingerBandIndicator<dynamic, dynamic>(
                  period: 3,
                  seriesName: 'HiloOpenClose')],
           series: <CartesianSeries<ChartData, DateTime>>[
              HiloOpenCloseSeries<ChartData, DateTime>(name: 'HiloOpenClose')
              ]
            )
          )
        );         
      }

      class ChartData {
        ChartData(this.x, this.low, this.high, this.open, this.close);
        final DateTime x;
        final double? low;
        final double? high;
        final double? open;
        final double? close;
      }

{% endhighlight %}
{% endtabs %}

![BollingerBand](images/technical-indicators/bollinger.jpg)

### Exponential moving average indicator (EMA)

An EMA indicator is a simple, arithmetic moving average that is calculated by adding the closing price for the number of time periods and dividing the total value by the number of periods.

It also has a [`valueField`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmaIndicator/valueField.html) property. Based on this property Indicator will render.

Refer the following example,

{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            primaryXAxis: DateTimeAxis(),
            legend: Legend(isVisible: true),
            indicators: [
        EmaIndicator<dynamic, dynamic>(
            seriesName: 'HiloOpenClose',
            valueField: 'high',)],
            series: <CartesianSeries<ChartData, DateTime>>[
        HiloOpenCloseSeries<ChartData, DateTime>(
            name: 'HiloOpenClose')
            ]
          )
        )
      );
    }

    class ChartData {
        ChartData(this.x, this.low, this.high, this.open, this.close);
        final DateTime x;
        final double? low;
        final double? high;
        final double? open;
        final double? close;
      }

{% endhighlight %}
{% endtabs %}

![EMAIndicator](images/technical-indicators/ema.jpg)

### Moving average convergence divergence (MACD)

This is mostly using indicator having [`shortPeriod`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MacdIndicator/shortPeriod.html) and [`longPeriod`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MacdIndicator/longPeriod.html) for defining the motion of the indicator.

Also you can draw [`MacdType.line`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MacdType.html), [`MacdType.histogram`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MacdType.html) MACD or [`MacdType.both`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MacdType.html) types using the  [`macdType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MacdIndicator/macdType.html) property,

The [`macdLineColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MacdIndicator/macdLineColor.html) property is used to define the color for the MACD line and the [`histogramNegativeColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MacdIndicator/histogramNegativeColor.html) and [`histogramPositiveColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MacdIndicator/histogramPositiveColor.html) property is used to define the color for the MACD histogram.

Refer the following example,

{% tabs %}
{% highlight dart %}
    
    @override
    Widget build(BuildContext context) {
     return Scaffold(
       body: Center(
          child: SfCartesianChart(
            primaryXAxis: DateTimeAxis(),
            legend: Legend(isVisible: true),
            indicators: [
          MacdIndicator<dynamic, dynamic>(
              longPeriod: 5,
              shortPeriod: 2,
              seriesName: 'HiloOpenClose')],
            series: <CartesianSeries<ChartData, DateTime>>[
          HiloOpenCloseSeries<ChartData, DateTime>(
            name: 'HiloOpenClose')
           ]
          )
        )
      );
    }

     class ChartData {
        ChartData(this.x, this.low, this.high, this.open, this.close);
        final DateTime x;
        final double? low;
        final double? high;
        final double? open;
        final double? close;
      }

{% endhighlight %}
{% endtabs %}

![MACDIndicator](images/technical-indicators/macd.jpg)

### Momentum Indicator

This indicator also has a centerline. The [`centerLineColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MomentumIndicator/centerLineColor.html) and [`centerLineWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MomentumIndicator/centerLineWidth.html) properties are used to define center line.

Refer the following example,

{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            primaryXAxis: DateTimeAxis(),
            legend: Legend(isVisible: true),
            indicators: [
          MomentumIndicator<dynamic, dynamic>(
            period: 3,
            seriesName: 'HiloOpenClose',)],
           series: <CartesianSeries<ChartData, DateTime>>[
          HiloOpenCloseSeries<ChartData, DateTime>(name: 'HiloOpenClose')
            ]
          )
        )
      );
    }

     class ChartData {
        ChartData(this.x, this.low, this.high, this.open, this.close);
        final DateTime x;
        final double? low;
        final double? high;
        final double? open;
        final double? close;
      }

{% endhighlight %}
{% endtabs %}

![MomentumIndicator](images/technical-indicators/momentum.jpg)

### Relative strength index Indicator(RSI)
The RSI indicator has an additional two lines other than the signal line.They indicate the [`overBought`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/RsiIndicator/overbought.html) and [`overSold`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/RsiIndicator/oversold.html) region.

The [`upperLineColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/RsiIndicator/upperLineColor.html) property is used to define the color for the line that indicates [`overBought`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/RsiIndicator/overbought.html) region, and the [`lowerLineColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/RsiIndicator/lowerLineColor.html) property is used to define the color for the line that indicates [`overSold`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/RsiIndicator/oversold.html) region.

Refer the following example,

{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            primaryXAxis: DateTimeAxis(),
            legend: Legend(isVisible: true),
             indicators: [
          RsiIndicator<dynamic, dynamic>(
            period: 3,
            seriesName: 'HiloOpenClose',
            overbought: 70,
            oversold: 30)],
            series: <CartesianSeries<ChartData, DateTime>>[
          HiloOpenCloseSeries<ChartData, DateTime>(name: 'HiloOpenClose')
            ]
          )
        )
      );
     }

      class ChartData {
        ChartData(this.x, this.low, this.high, this.open, this.close);
        final DateTime x;
        final double? low;
        final double? high;
        final double? open;
        final double? close;
      }

{% endhighlight %}
{% endtabs %}

![RSIIndicator](images/technical-indicators/rsi.jpg)

### Simple moving average indicator(SMA)

The [`Simple moving average indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SmaIndicator-class.html) is similar to [`Exponential moving average indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmaIndicator-class.html) and this can be defined using the following code examples.

{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            primaryXAxis: DateTimeAxis(),
            legend: Legend(isVisible: true),
            indicators: [
          SmaIndicator<dynamic, dynamic>(
            seriesName: 'HiloOpenClose',
            valueField: 'close')],
           series: <CartesianSeries<ChartData, DateTime>>[
          HiloOpenCloseSeries<ChartData, DateTime>(
            name: 'HiloOpenClose')
            ]
          )
        )
      );
    }

     class ChartData {
        ChartData(this.x, this.low, this.high, this.open, this.close);
        final DateTime x;
        final double? low;
        final double? high;
        final double? open;
        final double? close;
      }

{% endhighlight %}
{% endtabs %}

![SMAIndicator](images/technical-indicators/sma.jpg)

### Stochastic indicator

This indicator is used to measure the range and momentum of price movements. It contains [`kPeriod`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StochasticIndicator/kPeriod.html) and [`dPeriod`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StochasticIndicator/dPeriod.html) property defining the ‘k’ percentage and ‘d’ percentage respectively.

In this indicator [`upperLineColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StochasticIndicator/upperLineColor.html),[`lowerLineColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StochasticIndicator/lowerLineColor.html) and [`periodLineColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StochasticIndicator/periodLineColor.html) property are used to define the color for the Stochastic indicator lines.

Refer the following example,

{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            primaryXAxis: DateTimeAxis(),
            legend: Legend(isVisible: true),
            indicators: [
          StochasticIndicator<dynamic, dynamic>(   
              seriesName: 'HiloOpenClose',,
              kPeriod: 2,
              dPeriod: 3)],
             series: <CartesianSeries<ChartData, DateTime>>[
          HiloOpenCloseSeries<ChartData, DateTime>(name: 'HiloOpenClose')
            ]
          )
        )
      );
    }

     class ChartData {
        ChartData(this.x, this.low, this.high, this.open, this.close);
        final DateTime x;
        final double? low;
        final double? high;
        final double? open;
        final double? close;
      }

{% endhighlight %}
{% endtabs %}

![StochasticIndicator](images/technical-indicators/stochastic.jpg)

### Triangular moving average indicator (TMA)

A TMA indicator is simply a double-smoothed simple moving average of data calculated over a period where the middle portion of the data has more weight.

Refer the following example,

{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            primaryXAxis: DateTimeAxis(),
            legend: Legend(isVisible: true),
            indicators: [
          TmaIndicator<ChartData, dynamic>(
              seriesName: 'HiloOpenClose',
              valueField: 'low')],
            series: <CartesianSeries<ChartData, DateTime>>[
          HiloOpenCloseSeries<ChartData, DateTime>(
            name: 'HiloOpenClose')
            ]
          )
        )
      );
    }

     class ChartData {
        ChartData(this.x, this.low, this.high, this.open, this.close);
        final DateTime x;
        final double? low;
        final double? high;
        final double? open;
        final double? close;
      }
{% endhighlight %}
{% endtabs %}

![TMAIndicator](images/technical-indicators/tma.jpg)

### Rate of Change Indicator (ROC)

The ROC Indicator (Rate of Change) is a momentum oscillator used in technical analysis to measure the percentage change in price over a specified period of time.

  * Positive values indicate an upward momentum, suggesting price increases over the specified period.

  * Negative values indicate a downward momentum, suggesting price decreases over the specified period.

This indicator also has a centerline. The [`centerLineColor`]() and [`centerLineWidth`]() properties are used to define center line.

Refer the following example,

{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            primaryXAxis: DateTimeAxis(),
            legend: Legend(isVisible: true),
            indicators: [
              ROcIndicator<dynamic, dynamic>(
                period: 3,
                seriesName: 'HiloOpenClose',
              ),
            ],
            series: <CartesianSeries<ChartData, DateTime>>[
              HiloOpenCloseSeries<ChartData, DateTime>(
                xValueMapper: (ChartData data, _) => data.x,
                highValueMapper: (ChartData data, _) => data.high,
                lowValueMapper: (ChartData data, _) => data.low,
                openValueMapper: (ChartData data, _) => data.open,
                closeValueMapper: (ChartData data, _) => data.close,  
                name: 'HiloOpenClose',
              ),
            ],
          ),
        ),
      );
    }

     class ChartData {
        ChartData(this.x, this.low, this.high, this.open, this.close);

        final DateTime x;
        final double? low;
        final double? high;
        final double? open;
        final double? close;
      }

{% endhighlight %}
{% endtabs %}

![RocIndicator](images/technical-indicators/roc.jpg)

### Weighted moving average indicator (WMA)

The [`Weighted moving average indicator`]() is unlike a [`Simple moving average indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SmaIndicator-class.html), where each data point has an equal weight, the WMA assigns different weights to each data point.

This means that recent data points are given more weight in the calculation, making the WMA more responsive to recent price changes.

Refer the following example,

{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            primaryXAxis: DateTimeAxis(),
            legend: Legend(isVisible: true),
            indicators: [
              WmaIndicator<dynamic, dynamic>(
                seriesName: 'HiloOpenClose',
                valueField: 'close',
              ),
            ],
            series: <CartesianSeries<ChartData, DateTime>>[
              HiloOpenCloseSeries<ChartData, DateTime>(
                xValueMapper: (ChartData data, _) => data.x,
                highValueMapper: (ChartData data, _) => data.high,
                lowValueMapper: (ChartData data, _) => data.low,
                openValueMapper: (ChartData data, _) => data.open,
                closeValueMapper: (ChartData data, _) => data.close,  
                name: 'HiloOpenClose',
              ),
            ],
          ),
        ),
      );
    }

     class ChartData {
        ChartData(this.x, this.low, this.high, this.open, this.close);
        final DateTime x;
        final double? low;
        final double? high;
        final double? open;
        final double? close;
      }

{% endhighlight %}
{% endtabs %}

![WmaIndicator](images/technical-indicators/wma.jpg)

## Legend for technical indicators


Legend provides information about the series rendered in the chart. Legend for the indicator is rendered along with the series legend when the legend is set to be visible. Also when the  [ `name` ](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/name.html) property is given to an indicator, the legend name is changed based on the indicator name.[`legendItemText`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/legendItemText.html) can also be provided for changing the name of the legend. In default rendering the [`legendIconType`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/legendIconType.html) will be a horizontal line.

The following code example can define the legend.

{% tabs %}
{% highlight dart hl_lines="10 11" %}

    @override
    Widget build(BuildContext context){
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            primaryXAxis: DateTimeAxis(),
            indicators: [
              MomentumIndicator<dynamic, dynamic>(
                  seriesName: 'HiloOpenClose',
                  legendIconType: LegendIconType.diamond,
                  legendItemText: 'Indicator')],
            series: <CartesianSeries<ChartData, DateTime>>[
              HiloOpenCloseSeries<ChartData, DateTime>(
                  name: 'HiloOpenClose')
                  ]
                )
              )
            );
          }

      class ChartData {
        ChartData(this.x, this.low, this.high, this.open, this.close);
        final DateTime x;
        final double? low;
        final double? high;
        final double? open;
        final double? close;
      }

{% endhighlight %}
{% endtabs %}

![Legend](images/technical-indicators/legend.jpg)


Also refer [`technical indicators event`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/IndicatorRenderArgs-class.html) for customizing the tooltip further.

## Tooltip for technical indicators

The chart will display the segment information through the tooltip. It is used to show information about the segment when you tap on the segment. The technical indicator tooltip has the same [`ActivationMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior/activationMode.html) that has been given in the [`TooltipBehavior`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TooltipBehavior-class.html) of the series.

{% tabs %}
{% highlight dart hl_lines="5" %}
   
   late TooltipBehavior _tooltipBehavior;
    
    @override
    void initState(){
      _tooltipBehavior = TooltipBehavior(enable: true, shared: true);
    super.initState();
    }

    @override
    Widget build(BuildContext context){
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            primaryXAxis: DateTimeAxis(),
            tooltipBehavior: _tooltipBehavior,
            indicators: [
              ATRIndicator<dynamic, dynamic>(
                  seriesName: 'HiloOpenClose',
                  )
                ],
            series: <CartesianSeries<ChartData, DateTime>>[
              HiloOpenCloseSeries<ChartData, DateTime>(
                  enableTooltip: true,
                  name: 'HiloOpenClose')
              ]
            )
          )
        );
      }

       class ChartData {
        ChartData(this.x, this.low, this.high, this.open, this.close);
        final DateTime x;
        final double? low;
        final double? high;
        final double? open;
        final double? close;
      }

{% endhighlight %}
{% endtabs %}

![tooltip](images/technical-indicators/tooltip.jpg)

## Binding data source to indicators

In order to use [`TechnicalIndicators`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator-class.html) for line, area chart etc., you need to bind the data source of the chart to indicator's [`xValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/xValueMapper.html), [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/lowValueMapper.html), [`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/highValueMapper.html), [`openValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/openValueMapper.html), [`closeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/closeValueMapper.html) respectively. 

Refer the following example below

{% tabs %}
{% highlight dart %}

    @override
    Widget build(BuildContext context){
      return Scaffold(
        body: Center(
          child: SfCartesianChart(
            indicators: <TechnicalIndicators>[
            MomentumIndicator<ChartData, num>(
                period: 5,
                dataSource: chartData,
                xValueMapper: (ChartData data, _) => data.x,
                highValueMapper: (ChartData data, _) => data.high,
                lowValueMapper: (ChartData data, _) => data.low,
                openValueMapper: (ChartData data, _) => data.open,
                closeValueMapper: (ChartData data, _) => data.close,
              )
            ], 
            series: <CartesianSeries<ChartData, num>>[
              LineSeries<ChartData, num>(
                  color: Colors.purple,
                  dataSource: chartData,
                  xValueMapper: (ChartData1 data, _) => data.x,
                  yValueMapper: (ChartData1 data, _) => data.y,
              )
            ]
          )
        )
      );
    }

     class ChartData {
        ChartData(this.x, this.low, this.high, this.open, this.close);
        final num x;
        final double? low;
        final double? high;
        final double? open;
        final double? close;
      }

      class ChartData1{
        ChartData1(this.x, this.y);
        final num x;
        final double y;
      }

{% endhighlight %}
{% endtabs %}

![Binding data source to Indicators](images/technical-indicators/indicator_binding.jpg)

#### See Also

* [Refer this link for technical indicators callback](https://help.syncfusion.com/flutter/cartesian-charts/callbacks#onrenderdetailsupdate).

* [Bind data source to technical indicators in Flutter Cartesian chart](https://support.syncfusion.com/kb/article/11420/bind-data-source-to-technical-indicators-in-flutter-cartesian-chart).

>**Note**: Each indicators has their own number of value mappers available,
* [`Accumulation distribution indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AccumulationDistributionIndicator-class.html) (AD) - can be rendered with five value mappers ([`xValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/xValueMapper.html), [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/lowValueMapper.html), [`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/highValueMapper.html), [`closeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/closeValueMapper.html), [`volumeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/volumeValueMapper.html)).

*	[`Average true range indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/AtrIndicator-class.html) (ATR) - can be rendered with four value mappers ([`xValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/xValueMapper.html), [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/lowValueMapper.html), [`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/highValueMapper.html), [`closeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/closeValueMapper.html)).

*	[`Bollinger band indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/BollingerBandIndicator-class.html) - can be rendered with two value mappers ([`xValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/xValueMapper.html) and [`closeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/closeValueMapper.html)).

*	[`Exponential moving average indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/EmaIndicator-class.html) (EMA) - can be rendered with five value mappers ([`xValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/xValueMapper.html), [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/lowValueMapper.html), [`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/highValueMapper.html), [`openValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/openValueMapper.html), [`closeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/closeValueMapper.html)).

* [`Moving average convergence divergence`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MacdIndicator-class.html) (MACD) - can be rendered with two value mappers ([`xValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/xValueMapper.html) and [`closeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/closeValueMapper.html)).

*	[`Momentum indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MomentumIndicator-class.html) - can be rendered with five value mappers ([`xValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/xValueMapper.html), [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/lowValueMapper.html), [`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/highValueMapper.html), [`openValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/openValueMapper.html), [`closeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/closeValueMapper.html)).

*	[`Relative strength index indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/RsiIndicator-class.html) (RSI) - can be rendered with four value mappers ([`xValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/xValueMapper.html), [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/lowValueMapper.html), [`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/highValueMapper.html), [`closeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/closeValueMapper.html)).

*	[`Simple moving average indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SmaIndicator-class.html) (SMA) - can be rendered with five value mappers ([`xValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/xValueMapper.html), [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/lowValueMapper.html), [`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/highValueMapper.html), [`openValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/openValueMapper.html), [`closeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/closeValueMapper.html)).

*	[`Stochastic indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StochasticIndicator-class.html) - can be rendered with five value mappers ([`xValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/xValueMapper.html), [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/lowValueMapper.html), [`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/highValueMapper.html), [`openValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/openValueMapper.html), [`closeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/closeValueMapper.html)).

*	[`Triangular moving average indicator`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TmaIndicator-class.html) (TMA) - can be rendered with five value mappers ([`xValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/xValueMapper.html), [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/lowValueMapper.html), [`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/highValueMapper.html), [`openValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/openValueMapper.html), [`closeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/closeValueMapper.html)).

*	[`Rate Of Change indicator`]() (ROC) - can be rendered with five value mappers ([`xValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/xValueMapper.html), [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/lowValueMapper.html), [`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/highValueMapper.html), [`openValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/openValueMapper.html), [`closeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/closeValueMapper.html)).

*	[`Weighted moving average indicator`]() (WMA) - can be rendered with five value mappers ([`xValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/xValueMapper.html), [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/lowValueMapper.html), [`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/highValueMapper.html), [`openValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/openValueMapper.html), [`closeValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/TechnicalIndicator/closeValueMapper.html)).

>**Note**: `chartData` in the above code snippets is a class type list and holds the data for binding to the chart series. Refer [Bind data source](https://help.syncfusion.com/flutter/cartesian-charts/getting-started#bind-data-source) topic for more details.
