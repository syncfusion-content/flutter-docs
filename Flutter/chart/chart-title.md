---
layout: post
title: Chart Title
description: How to add chart title and customize the appearance of the chart title in the Essential Flutter Charts.
platform: flutter
control: Chart
documentation: ug
---

# Title

You can define and customize the Chart title using [`title`]() property of [`SfCartesianChart`](). The [`text`]() property of [`ChartTitle`]() is used to set the text for the title. 

Following properties are used to customize its appearance.


* [`backgroundColor`]() – used to change the background color.
* [`borderColor`]() – used to change the border color.
* [`borderWidth`]() – used to change the border width.
* [`textStyle`]() – used to change the text color, size, font family, fontStyle, and font weight.
* [`color`]() – used to change the color of the text.
* [`fontFamily`]() - used to change the font family for chart title. 
* [`fontStyle`]() – used to change the font style for the chart title.
* [`fontSize`]() - used to change the font size for the chart title.

### Text Alignment

You can align the title text content to the near, center or far of the title using the [`alignment`]() property of the [`title`]().

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child: SfCartesianChart(
                   title: ChartTitle(
                      text: 'Half yearly sales analysis',
                      backgroundColor: Colors.lightGreen,
                      borderColor: Colors.blue,
                      borderWidth: 2,
                      alignment: ChartAlignment.near,
                      textStyle: ChartTextStyle(
                        color: Colors.red,
                        fontFamily: 'Roboto',
                        fontStyle: FontStyle.italic,
                        fontSize: 14,
                      )),
                   primaryXAxis: CategoryAxis(), // Initialize category axis.
                  series: <ChartSeries>[
                  // Initialize line series.
                  LineSeries<SalesData, String>(
                    dataSource: [
                      // Bind data source.
                      SalesData('Jan', 35),
                      SalesData('Feb', 28),
                      SalesData('Mar', 34),
                      SalesData('Apr', 32),
                      SalesData('May', 40)
                    ],
                    xValueMapper: (SalesData sales, _) => sales.year,
                    yValueMapper: (SalesData sales, _) => sales.sales)
              ])
            )
        ),
        );
    }

{% endhighlight %}

![Chart title](images/getting-started/livechart.png)
