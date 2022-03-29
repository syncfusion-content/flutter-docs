---
layout: post
title: Data label in Flutter Pyramid Chart widget | Syncfusion 
description: Learn here all about Data label feature of Syncfusion Flutter Pyramid Chart (SfPyramidChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Data label in Flutter Pyramid Chart (SfPyramidChart)

Data label can be added to a chart series by enabling the [`isVisible`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/isVisible.html) option in the [`dataLabelSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries/dataLabelSettings.html). You can use the following properties to customize the appearance.

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/color.html) - used to change the background color of the data label shape.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/borderWidth.html) - used to change the stroke width of the data label shape.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/borderColor.html) - used to change the stroke color of the data label shape.
* [`alignment`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/alignment.html) - aligns the data label text to [`ChartAlignment.near`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAlignment.html), [`ChartAlignment.center`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAlignment.html) and [`ChartAlignment.far`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAlignment.html).
* [`textStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/textStyle.html) - used to change the data label text color, size, font family, font style, and font weight.
* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/color.html) - used to change the color of the data label.
* [`fontFamily`](https://api.flutter.dev/flutter/painting/TextStyle/fontFamily.html) - used to change the font family for the data label.
* [`fontStyle`](https://api.flutter.dev/flutter/painting/TextStyle/fontStyle.html) - used to change the font style for the data label.
* [`fontWeight`](https://api.flutter.dev/flutter/painting/TextStyle/fontWeight.html) - used to change the font weight for the data label.
* [`fontSize`](https://api.flutter.dev/flutter/painting/TextStyle/fontSize.html) - used to change the font size for the data label.
* [`margin`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/margin.html) - used to change the margin size for data labels.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/opacity.html) - used to control the transparency of the data label.
* [`labelAlignment`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelAlignment.html) - used to align the Pyramid data label positions. The available options to customize the positions are [`ChartDataLabelAlignment.outer`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment.html), [`ChartDataLabelAlignment.auto`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment.html), [`ChartDataLabelAlignment.top`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment.html), [`ChartDataLabelAlignment.bottom`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment.html) and [`ChartDataLabelAlignment.middle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment.html).
* [`borderRadius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/borderRadius.html) - used to add the rounded corners to the data label shape.
* [`angle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/angle.html) - used to rotate the labels.
* [`offset`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/offset.html) - used to move the data label vertically or horizontally from its position.
* [`showCumulativeValues`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/showCumulativeValues.html) - to show the cumulative values in stacked type series charts.
* [`labelIntersectAction`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelIntersectAction.html) - action on data labels intersection. The intersecting data labels can be hidden.


{% tabs %}
{% highlight dart hl_lines="8" %}  

    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = [
            ChartData('Jan', 35),
            ChartData('Feb', 28),
            ChartData('Mar', 38),
            ChartData('Apr', 32),
            ChartData('May', 40)
        ];

        return Scaffold(
            body: Center(
                child: Container(
                    child: SfPyramidChart(
                        series: PyramidSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                dataLabelSettings: DataLabelSettings(
                                    // Renders the data label
                                    isVisible: true
                                )
                            )
                    )
                )
            )
        );
    }
    class ChartData {
        ChartData(this.x, this.y);
        final String x;
        final double? y;
    }

{% endhighlight %}
{% endtabs %}

![DataLabel](images/datalabel/default_datalabel.png)

## Connector line

This feature is used to connect label and data point using a line. It can be enabled for [`PyramidSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries-class.html) chart type. The [`connectorLineSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/connectorLineSettings.html) property used to customize the connector line.

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ConnectorLineSettings/color.html) - used to change the color of the line
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ConnectorLineSettings/width.html) - used to change the stroke thickness of the line
* [`length`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ConnectorLineSettings/length.html) - specifies the length of the connector line.
* [`type`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ConnectorLineSettings/type.html) - specifies the shape of connector line either [`ConnectorType.curve`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ConnectorType.html) or [`ConnectorType.line`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ConnectorType.html). 

{% tabs %}
{% highlight dart hl_lines="18" %}  

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfPyramidChart(
                        series: <PyramidSeries>[
                            PyramidSeries<ChartData, double>(
                                enableSmartLabels: true,
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    labelPosition: ChartDataLabelPosition.outside,
                                    connectorLineSettings: ConnectorLineSettings(
                                        // Type of the connector line
                                        type: ConnectorType.curve
                                    )
                                )
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}
{% endtabs %}

## Positioning the labels

The [`labelAlignment`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment.html) property is used to position the Pyramid chart type data labels at [`ChartDataLabelAlignment.top`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment.html), [`ChartDataLabelAlignment.bottom`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment.html), [`ChartDataLabelAlignment.auto`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment.html), [`ChartDataLabelAlignment.outer`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment.html) and [`ChartDataLabelAlignment.middle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment.html) position of the actual data point position. By default, labels are [`ChartDataLabelAlignment.auto`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelAlignment.html) positioned. You can move the labels horizontally and vertically using OffsetX and OffsetY properties respectively.

The [`labelPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelPosition.html) property is used to place the Pyramid series data labels either [`ChartDataLabelPosition.inside`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelPosition.html) or [`ChartDataLabelPosition.outside`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelPosition.html). By default the label of Pyramid chart is placed [`ChartDataLabelPosition.inside`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartDataLabelPosition.html) the series.

{% tabs %}
{% highlight dart hl_lines="14" %}  

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfPyramidChart(
                        series: PyramidSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    // Positioning the data label
                                    labelPosition: ChartDataLabelPosition.outside
                                )
                            )
                    )
                )
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![Data label position](images/datalabel/datalabel_position.png)

>**Note**: The [`labelAlignment`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelAlignment.html) property is used to position the Cartesian chart labels whereas [`labelPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelPosition.html) property is used to position the Pyramid chart labels.

## Apply series color

The [`useSeriesColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/useSeriesColor.html) property is used to apply the series color to background color of the data labels. The default value of this property is false.

{% tabs %}
{% highlight dart hl_lines="16" %}  

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfPyramidChart(
                        series: PyramidSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    // Positioning the data label
                                    labelPosition: ChartDataLabelPosition.outside,
                                    // Renders background rectangle and fills it with series color
                                    useSeriesColor: true
                                )
                            )
                    )
                )
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![Series color](images/datalabel/use_series_color.png)

## Templating the labels

You can customize the appearance of the data label with your own template using the [`builder`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/builder.html) property of [`dataLabelSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PyramidSeries/dataLabelSettings.html).

{% tabs %}
{% highlight Dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfPyramidChart(
                        series: PyramidSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    // Templating the data label
                                    builder: (dynamic data, dynamic point, dynamic series, int pointIndex, int seriesIndex) {
                                        return Container(
                                        height: 30,
                                        width: 30,
                                        child: Image.asset('images/livechart.png')
                                        );
                                    }
                                )
                            )
                    )
                )
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![Label template](images/datalabel/datalabel_template.png)

## Hide data label for 0 value

Data label and its connector line in the Pyramid charts for the point value 0 can be hidden using the [`showZeroValue`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/showZeroValue.html) property. This defaults to `true`.

{% tabs %}
{% highlight dart hl_lines="17" %}  

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                    child:SfPyramidChart(
                        series: PyramidSeries<ChartData, num>(
                            dataSource: [
                                ChartData(11, 35),
                                ChartData(12, 28),
                                ChartData(13, 0),
                                ChartData(14, 32),
                                ChartData(15, 40)
                            ],
                            xValueMapper: (ChartData data, _) => data.xValue,
                            yValueMapper: (ChartData data, _) => data.yValue,
                            dataLabelSettings: DataLabelSettings(
                                showZeroValue: false, 
                                isVisible: true
                            ),
                        )
                    )
            )
        );
    }

{% endhighlight %}
{% endtabs %}

![hide_0_value](images/datalabel/dataLabel_0_value.png)

## Data label saturation color

If the user didn’t provide text color to the data label, then by default, the saturation color is applied to the data label text. i.e., if the data points background color intensity is dark, then the data label will render in white color (#FFFFFF) and if the data points background color intensity is light, data label will render in black color (#000000).

![label_saturation](images/datalabel/pyramid_saturation.png)

## Overflow mode

Action on data labels when it’s overflowing from its region area. The overflowing data label rendering behavior can be changed based on this. If [`overflowMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/overflowMode.html) property is set to [`OverflowMode.none`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/overflowMode.html) then the [`labelIntersectAction`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelIntersectAction.html) takes the priority, else [`overflowMode`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/overflowMode.html) takes the priority.
  
Defaults to [`OverflowMode.none`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/overflowMode.html).

>**Note**: This is applicable for pie, doughnut, pyramid, and funnel series types alone.

{% tabs %}
{% highlight dart hl_lines="7" %} 

    Widget build(BuildContext context) {
        return Container(
            child: SfPyramidChart(
             series: PyramidSeries<ChartData, String>(
             dataLabelSettings: DataLabelSettings(
               isVisible: true,
               overflowMode: OverflowMode.trim
            ),
          ),
        )
      );
    }

{% endhighlight %}
{% endtabs %}
![label_overflow](images/datalabel/pyramid_overflow.jpg)

## Smart labels

This feature is used to arrange the data labels smartly and avoid the intersection when there is overlapping of labels. The enum property called the [`LabelIntersectAction.shift`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LabelIntersectAction.html) in [`labelIntersectAction`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelIntersectAction.html) is used to arrange the data labels smartly when labels get intersect. By default, the label intersection action property is [`LabelIntersectAction.shift`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LabelIntersectAction.html).

If the [`labelPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelPosition.html) is [`ChartDataLabelPosition.inside`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelPosition.html) and the [`labelIntersectAction`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelIntersectAction.html) is [`LabelIntersectAction.shift`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LabelIntersectAction.html), then the overlapped labels will shift to outside the slices and arrange smartly. If the [`labelPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelPosition.html) is [`ChartDataLabelPosition.inside`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelPosition.html) and the [`labelIntersectAction`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelIntersectAction.html) is [`LabelIntersectAction.hide`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LabelIntersectAction.html), then the overlapped labels will be hidden.

If the [`labelPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelPosition.html) is [`ChartDataLabelPosition.outside`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelPosition.html) and the [`labelIntersectAction`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelIntersectAction.html) is [`LabelIntersectAction.shift`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LabelIntersectAction.html), then the overlapped labels arrange smartly. If the [`labelPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelPosition.html) is [`ChartDataLabelPosition.outside`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelPosition.html) and the [`labelIntersectAction`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelIntersectAction.html) is [`LabelIntersectAction.hide`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LabelIntersectAction.html), then the overlapped labels will be hidden.

If the [`labelIntersectAction`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelIntersectAction.html) is [`LabelIntersectAction.none`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LabelIntersectAction.html), then the overlapped labels will be visible irrespective of [`labelPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelPosition.html).

When the [`labelIntersectAction`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelIntersectAction.html) is [`LabelIntersectAction.shift`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LabelIntersectAction.html), and if the data label goes out of the chart area, then the labels got trimmed and the tooltip is shown when clicking/tapping the data label. The values of the [`labelIntersectAction`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelIntersectAction.html) are listed below.
* [`LabelIntersectAction.hide`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LabelIntersectAction.html) - hides the intersected data labels.
* [`LabelIntersectAction.none`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LabelIntersectAction.html) - intersected data labels will be visible.
* [`LabelIntersectAction.shift`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LabelIntersectAction.html) - smartly arranges the overlapped data labels.

{% tabs %}
{% highlight dart hl_lines="34" %} 

    @override
    Widget build(BuildContext context) {
      final List<ChartData> chartData = <ChartData>[
        ChartData('USA', 46),
        ChartData('Great Britain', 27),
        ChartData('China', 26),
        ChartData('Russia', 19),
        ChartData('Germany', 17),
        ChartData('Japan', 12),
        ChartData('France', 10),
        ChartData('Korea', 9),
        ChartData('Italy', 8),
        ChartData('Australia', 8),
        ChartData('Netherlands', 8),
        ChartData('Hungary', 8),
        ChartData('Brazil', 7),
        ChartData('Spain', 7),
        ChartData('Kenya', 6),
        ChartData('Jamaica', 6),
        ChartData('Croatia', 5),
        ChartData('Cuba', 5),
        ChartData('New Zealand', 4)
    ];
      return SfPyramidChart(
        series: PyramidSeries<ChartData, String>(
            dataSource: chartData,
            xValueMapper: (ChartData data, _) => data.x,
            yValueMapper: (ChartData data, _) => data.y,
            dataLabelMapper: (ChartData data, _) => data.x,
            radius: '60%',
            dataLabelSettings: DataLabelSettings(
              isVisible: true,
              // Avoid labels intersection
              labelIntersectAction: LabelIntersectAction.shift,
              labelPosition: ChartDataLabelPosition.outside,
              connectorLineSettings: ConnectorLineSettings(
                type: ConnectorType.curve, length: '25%')
              )
          )
        ]);
    }

    class ChartData {
      ChartData({this.x, this.y});
      final String? x;
      final num? y;
    }

{% endhighlight %}
{% endtabs %}

![Smart labels](images/datalabel/smart_datalabel.png)
