---
layout: post
title: Plotband for Syncfusion Flutter Sparkline
description: Learn how to customize the plot band, color, borderColor, borderWidth of the Syncfusion Flutter Sparkline Chart.
platform: flutter
control: Sparkline
documentation: ug
---

# Syncfusion Flutter Sparkline Plot Band 

This feature is used to highlight a particular region in the sparkline along Y axis.

The following properties are used to customize the appearances:
* [`start`]() - used to configure the start plot band value in Y axis.
* [`end`]() - used to configure the end plot band values in Y axis.
* [`color`]() - used to change the color for plot band.
* [`borderColor`]() - used to change the border color of plot band.
* [`borderWidth`]() - used to change the border width of plot band.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Center(
          child:  SfSparkLineChart(
                    plotBand: SparkChartPlotBand(start: 7, end: 8),
                  data: <double>[
                        5,
                        6,
                        5,
                        7,
                        4,
                        3,
                        9,
                        5,
                        6,
                        5,
                        7,
                        8,
                        4,
                        5,
                        3,
                        4,
                        11,
                        10,
                        2,
                        12,
                        4,
                        7,
                        6,
                        8
                      ],
               )
             )
           );
         }

    class SalesData {
    SalesData(this.month, this.sales);
    final String month;
    final double sales;
    }

{% endhighlight %}

![Sparkline plot band](images/plotband/spark-plotband.png)