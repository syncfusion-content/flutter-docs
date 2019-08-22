---
layout: post
title: Markers and data labels in Syncfusion Flutter Charts
description: Learn how to add markers and data point labels to the Flutter Chart series.
platform: flutter
control: Chart
documentation: ug
---

# Marker and data label

## Marker

Markers are used to provide information about the exact point location. You can add a shape to adorn each data point. Markers can be enabled by using the [`isVisible`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/isVisible.html) property of [`markerSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/markerSettings.html). You can use the following properties to customize the appearance.

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/color.html) – used to change the color of the marker shape.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/borderWidth.html) – used to change the stroke width of the marker shape.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/borderColor.html) – used to change the stroke color of the marker shape.
* [`height`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/height.html) - used to change the height of the marker shape.
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/width.html) - used to change the width of the marker shape.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <CartesianSeries>[
                            LineSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                markerSettings: MarkerSettings(
                                    isVisible: true
                                )
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Marker](images/marker-datalabel/default_marker.jpg)

### Customizing marker shapes

Markers can be assigned with different shapes using the [`shape`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/shape.html) property. By default, markers are rendered with [`circle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataMarkerType-class.html) shape. The shapes of markers are listed below.

* circle
* rectangle
* image
* pentagon
* verticalLine
* horizontalLine
* diamond
* triangle
* invertedTriangle

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <CartesianSeries>[
                            LineSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                markerSettings: MarkerSettings(
                                    isVisible: true,
                                    shape: DataMarkerType.diamond
                                )
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Marker Shapes](images/marker-datalabel/marker_shape.jpg)

### Image marker

The markers can be rendered with desired image as shape. For this you have to specify the [`shape`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/shape.html) as [`image`]() and refer the image path using [`imageUrl`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/MarkerSettings/imageUrl.html) property.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <CartesianSeries>[
                            LineSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                markerSettings: MarkerSettings(
                                    isVisible: true,
                                    shape: DataMarkerType.image,
                                    imageUrl: 'images/livechart.png'
                                )
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Image Marker](images/marker-datalabel/image_marker.jpg)

## Data label

Data label can be added to a chart series by enabling the [`isVisible`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/isVisible.html) option in the [`dataLabelSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/dataLabelSettings.html). You can use the following properties to customize the appearance.

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/color.html) – used to change the background color of the data label shape.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/borderWidth.html) – used to change the stroke width of the data label shape.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/borderColor.html) – used to change the stroke color of the data label shape.
* [`alignment`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/alignment.html) - aligns the data label text to [`near`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAlignment-class.html), [`center`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAlignment-class.html) and [`far`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartAlignment-class.html).
* [`textStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/textStyle.html) – used to change the data label text color, size, font family, font style, and font weight.
* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/color.html) – used to change the color of the data label.
* [`fontFamily`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/fontFamily.html) - used to change the font family for the data label.
* [`fontStyle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/fontStyle.html) - used to change the font style for the data label.
* [`fontWeight`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/fontWeight.html) - used to change the font weight for the data label.
* [`fontSize`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ChartTextStyle/fontSize.html) - used to change the font size for the data label.
* [`margin`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/margin.html) - used to change the margin size for data labels.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/opacity.html) - used to control the transparency of the data label.
* [`position`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/position.html) - used to align the data label to positions. The available options to customize the positions are [`outer`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianLabelPosition-class.html), [`auto`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianLabelPosition-class.html), [`top`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianLabelPosition-class.html), [`bottom`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianLabelPosition-class.html) and [`middle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianLabelPosition-class.html).
* [`borderRadius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/borderRadius.html) - used to add the rounded corners to the data label shape.
* [`angle`]() - used to rotate the labels.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <CartesianSeries>[
                            LineSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true
                                )
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![DataLabel](images/marker-datalabel/default_datalabel.jpg)

### Formatting label content

Data label considers the format used in the vertical axis by default. In the below code snippet, we have specified format to y-axis and you can see the same format is applied to data label.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryYAxis: NumericAxis(numberFormat: NumberFormat.simpleCurrency()),
                        series: <CartesianSeries>[
                            LineSeries<ChartData, double>(
                                dataSource: chartData,
                                color: Colors.red,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true
                                )
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![DataLabel format](images/marker-datalabel/datalabel_format.jpg)

### Label position

The [`position`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianLabelPosition-class.html) property is used to position the Cartesian chart type data labels at [`top`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianLabelPosition-class.html), [`bottom`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianLabelPosition-class.html), [`auto`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianLabelPosition-class.html), [`outer`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianLabelPosition-class.html) and [`middle`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianLabelPosition-class.html) position of the actual data point position. By default, labels are [`auto`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianLabelPosition-class.html) positioned. You can move the labels horizontally and vertically using OffsetX and OffsetY properties respectively.

The [`labelPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelPosition.html) property is used to place the circular series data labels either [`inside`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LabelPosition-class.html) or [`outside`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LabelPosition-class.html). By default the label of circular chart is placed [`inside`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/LabelPosition-class.html) the series.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(
                        series: <CircularSeries>[
                            PieSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    labelPosition: LabelPosition.outside
                                )
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Data label position](images/marker-datalabel/datalabel_position.jpg)

N> The [`position`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/position.html) property is used to position the Cartesian chart labels whereas [`labelPosition`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/labelPosition.html) property is used to position the circular chart labels.

### Smart labels

This feature is used to arrange the data labels smartly and avoid the intersection when there is overlapping of labels. The property [`enableSmartLabels`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/enableSmartLabels.html) in [`CircularSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries-class.html) is used to arrange the data labels smartly. By default, this property is *true*.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child:SfCircularChart(
                        series: <CircularSeries>[
                            PieSeries<ChartData, double>(
                                enableSmartLabels: true,
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) =>  data.y,
                                dataLabelMapper: (ChartData data, _) => data.x,
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    labelPosition: LabelPosition.inside
                                )   
                            )
                        ]   
                    )
                )
            )
        );
    }

{% endhighlight %}

![Smart labels](images/marker-datalabel/smart_label.jpg)

### Apply series color

The [`useSeriesColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/useSeriesColor.html) property is used to apply the series color to background color of the data labels. The default value of this property is *false*.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child:SfCircularChart(
                        series: <CircularSeries>[
                            PieSeries<ChartData, double>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                dataLabelMapper: (ChartData data, _) => data.x,
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true, 
                                    labelPosition: LabelPosition.outside,
                                    useSeriesColor: true
                                )
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Series color](images/marker-datalabel/use_series_color.jpg)

### Connector line

This feature is used to connect label and data point using a line. It can be enabled for [`Pie`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/PieSeries-class.html) and [`Doughnut`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DoughnutSeries-class.html) chart types. The [`connectorLineSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/connectorLineSettings.html) property used to customize the connector line.

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ConnectorLineSettings/color.html) – used to change the color of the line
* [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ConnectorLineSettings/width.html) – used to change the stroke thickness of the line
* [`length`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ConnectorLineSettings/length.html) – specifies the length of the connector line.
* [`type`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ConnectorLineSettings/type.html) - specifies the shape of connector line either [`curve`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ConnectorType-class.html) or [`line`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ConnectorType-class.html). 

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCircularChart(
                        series: <CircularSeries>[
                            PieSeries<ChartData, double>(
                                enableSmartLabels: true,
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    labelPosition: LabelPosition.outside,
                                    connectorLineSettings: ConnectorLineSettings(
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

![Connector line](images/marker-datalabel/connector_line.jpg)

### Point text mapping

The [`dataLabelMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/dataLabelMapper.html) property is used to map the text from data source. 

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        final List<ChartData> chartData = [
            ChartData('USA', 17, '17%'),
            ChartData('China', 34, '34%'),
            ChartData('Japan', 24, '24%'),
            ChartData('Africa', 30, '30%'),
            ChartData('UK', 10, '10%')
        ];

        return Scaffold(
            body: Center(
                child: Container(
                    child:SfCircularChart(
                        series: <CircularSeries>[
                            PieSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                dataLabelMapper: (ChartData data, _) => data.text,
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true
                                )
                            )
                        ]
                    )
                )
            )
        );
    }

    class ChartData {
        ChartData(this.x, this.y, this.text);
        final String x;
        final double y;
        final String text;
    }

{% endhighlight %}

![Data label mapper](images/marker-datalabel/value_mapper.jpg)

### Label template

You can customize the appearance of the data label with your own template using the [`builder`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/builder.html) property of [`dataLabelSettings`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CircularSeries/dataLabelSettings.html).

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child:SfCircularChart(
                        series: <CircularSeries>[
                            PieSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData data, _) => data.x,
                                yValueMapper: (ChartData data, _) => data.y,
                                dataLabelMapper: (ChartData data, _) => data.text,
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    builder: (dynamic data, dynamic point, dynamic series, int pointIndex, int seriesIndex) {
                                        return Container(
                                        height: 30,
                                        width: 30,
                                        child: Image.asset('images/livechart.png')
                                        );
                                    }
                                )
                            )
                        ]
                    )
                )
            )
        );
    }

{% endhighlight %}

![Label template](images/marker-datalabel/datalabel_template.jpg)