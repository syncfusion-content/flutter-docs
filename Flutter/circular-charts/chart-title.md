---
layout: post
title: Chart title in Flutter Circular Charts widget | Syncfusion 
description: Learn here all about Chart title feature of Syncfusion Flutter Circular Charts (SfCircularChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Chart title in Flutter Circular Charts (SfCircularChart)

You can define and customize the chart title using [`title`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/title.html) property of [`SfCircularChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart-class.html). The [`text`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTitle/text.html) property of [`ChartTitle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTitle-class.html) is used to set the text for the title. 

Following properties can be used to customize its appearance.

* [`backgroundColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTitle/backgroundColor.html) - used to change the background color.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTitle/borderColor.html) - used to change the border color.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTitle/borderWidth.html) - used to change the border width.
* [`textStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTitle/textStyle.html) - used to change the text color, size, font family, fontStyle, and font weight.
* [`color`](https://api.flutter.dev/flutter/painting/TextStyle/color.html) - used to change the color of the text.
* [`fontFamily`](https://api.flutter.dev/flutter/painting/TextStyle/fontFamily.html) - used to change the font family for chart title. 
* [`fontStyle`](https://api.flutter.dev/flutter/painting/TextStyle/fontStyle.html) - used to change the font style for the chart title.
* [`fontSize`](https://api.flutter.dev/flutter/painting/TextStyle/fontSize.html) - used to change the font size for the chart title.


### Text Alignment

You can align the title text content horizontally to the near, center or far of the chart using the [`alignment`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTitle/alignment.html) property of the [`title`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCircularChart/title.html).

{% highlight dart %} 

      @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: Center(
            child: Container(
              child: SfCircularChart(
                title: ChartTitle(
                  text: 'Half yearly sales analysis',
                  backgroundColor: Colors.lightGreen,
                  borderColor: Colors.blue,
                  borderWidth: 2,
                  // Aligns the chart title to left
                  alignment: ChartAlignment.near,
                  textStyle: TextStyle(
                    color: Colors.red,
                    fontFamily: 'Roboto',
                    fontStyle: FontStyle.italic,
                    fontSize: 14,
                  )
                ),
                series: <ChartSeries>[
                  // Initialize line series
                  PieSeries<ChartData, String>(
                    dataSource: [
                      // Bind data source
                      ChartData('Jan', 35),
                      ChartData('Feb', 28),
                      ChartData('Mar', 34),
                      ChartData('Apr', 32),
                      ChartData('May', 40)
                    ],
                    pointColorMapper: (ChartData data, _) => data.color,
                    xValueMapper: (ChartData data, _) =>   data.x,
                    yValueMapper: (ChartData data, _) => data.y
                  )
                ]
              )
            )
          )
        );
      }

{% endhighlight %}

![Chart title](images/chart-title/chart_title.jpg)