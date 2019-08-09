---
layout: post
title: Markers and data labels in Essential Syncfusion Flutter Chart
description: Learn how to add markers and data point labels, connector lines, formatting label content, configure the data label template to the Chart series.
platform: flutter
control: Chart
documentation: ug
---

# Marker and data label

## Marker

Markers are used to provide information about the exact point location. You can add a shape to adorn each data point. Markers can be enabled by using the [`isVisible`]() property of [`markerSettings`](). You can use the following properties to customize the appearance.

* [`color`]() – used to change the color of the marker shape.
* [`borderWidth`]() – used to change the stroke width of the marker shape.
* [`borderColor`]() – used to change the stroke color of the marker shape.
* [`height`]() - used to change the height of the marker shape.
* [`width`]() - used to change the width of the marker shape.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(series: <CartesianSeries>[
                LineSeries<ChartData, double>(
                    dataSource: chartData,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y,
                    markerSettings: MarkerSettings(
                        isVisible: true
                    )
                ),
            ]))
        ));
    }

{% endhighlight %}

![Marker](images/marker-datalabel/default_marker.jpg)

### Customizing marker shapes

Markers can be assigned with different shapes using the [`shape`]() property. By default, markers are rendered with [`circle`]() shape. The shapes of markers are listed below.

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
                child:SfCartesianChart(series: <CartesianSeries>[
                LineSeries<ChartData, double>(
                    dataSource: chartData,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y,
                    markerSettings: MarkerSettings(
                        isVisible: true,
                        shape: DataMarkerType.diamond,
                    )
                ),
            ]))
        ));
    }

{% endhighlight %}

![Marker Shapes](images/marker-datalabel/marker_shape.jpg)

### Image marker

The markers can be rendered with desired image as shape. For this you specify the [`shape`]() as [`image`]() and refer the path using [`imageUrl`]() property.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(series: <CartesianSeries>[
                LineSeries<ChartData, double>(
                    dataSource: chartData,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y,
                    markerSettings: MarkerSettings(
                        isVisible: true,
                        shape: DataMarkerType.image,
                        imageUrl: 'images/livechart.png'
                    )
                ),
            ]))
        ));
    }

{% endhighlight %}

![Image Marker](images/marker-datalabel/image_marker.jpg)

## Data label

Data label can be added to a chart series by enabling the [`isVisible`]() option in the [`dataLabelSettings`](). You can use the following properties to customize the appearance.

* [`color`]() – used to change the background color of the data label shape.
* [`borderWidth`]() – used to change the stroke width of the data label shape.
* [`borderColor`]() – used to change the stroke color of the data label shape.
* [`alignment`]() - aligns the data label text to [`near`](), [`center`]() and [`far`]().
* [`textStyle`]() – used to change the data label text color, size, font family, font style, and font weight.
* [`color`]() – used to change the color of the data label.
* [`fontFamily`]() - used to change the font family for the data label.
* [`fontStyle`]() - used to change the font style for the data label.
* [`fontWeight`]() - used to change the font weight for the data label.
* [`fontSize`]() - used to change the font size for the data label.
* [`margin`]() - used to change the margin size for data labels.
* [`opacity`]() - used to control the transparency of the data label.
* [`position`]() - used to align the data label to positions. The available options to customize the psotions are [`outer`](), [`auto`](), [`top`](), [`bottom`]() and [`middle`]().
* [`borderRadius`]() - used to add the rounded corners to the data label shape.
* [`angle`]() - used to rotate the labels.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(series: <CartesianSeries>[
                LineSeries<ChartData, double>(
                    dataSource: chartData,
                    xValueMapper: (ChartData data, _) => data.x,
                    yValueMapper: (ChartData data, _) => data.y,
                    dataLabelSettings: DataLabelSettings(
                        isVisible: true,
                    )
                ),
            ])
        )));
    }

{% endhighlight %}

![DataLabel](images/marker-datalabel/default_datalabel.jpg)

### Formatting label content

Data label considers the format used in vertical axis by default.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCartesianChart(
              primaryYAxis: NumericAxis(numberFormat: NumberFormat.simpleCurrency()),
              series: <CartesianSeries>[
          LineSeries<ChartData, double>(
              dataSource: chartData,
              color: Colors.red,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y,
              dataLabelSettings: DataLabelSettings(
                isVisible: true,
              )),
        ])
        )));
    }

{% endhighlight %}

![DataLabel format](images/marker-datalabel/datalabel_format.jpg)

### Label position

The [`position`]() property is used to position the cartesian chart type data marker labels at [`top`](), [`bottom`](), [`auto`](), [`outer`]() and [`middle`]() position of the actual data point position. By default, labels are [`auto`]() positioned. You can move the labels horizontally and vertically using OffsetX and OffsetY properties respectively.

The [`labelPosition`]() property is used to place the circular series data marker labels either [`inside`]() or [`outside`](). By default the label of circular chart is placed [`inside`]() the series.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCircularChart(series: <CircularSeries>[
          PieSeries<ChartData, double>(
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y,
              dataLabelSettings: DataLabelSettings(
                isVisible: true,
                labelPosition: LabelPosition.outside,
              )),
        ])
        )));
    }

{% endhighlight %}

![Data label position](images/marker-datalabel/datalabel_position.jpg)

N> The [`position`]() property is used to position the cartesian chart labels whereas [`labelPosition`]() property is used to position the circular chart labels.

### Smart labels

This feature is used to arrange the data marker labels smartly and avoid the intersection when there is overlapping of labels. The property [`enableSmartLabels`]() in [`CircularSeries`]() is used to arrange the data marker labels smartly. By default, this property is *true*.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCircularChart(series: <CircularSeries>[
          PieSeries<ChartData, double>(
              enableSmartLabels: true,
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => dataLabelMapper: (ChartData sales, _)    => sales.x
              xValueMapper: (ChartData data, _) => data.x,
              dataLabelSettings: DataLabelSettings(
                isVisible: true,
                labelPosition: LabelPosition.inside,
              )),
        ])
        )));
    }

{% endhighlight %}

![Smart labels](images/marker-datalabel/smart_label.jpg)

### Apply series color

The [`useSeriesColor`]() property is used to apply the series color to background color of data marker labels. The default value of this property is *false*.

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCircularChart(series: <CircularSeries>[
          PieSeries<ChartData, double>(
              enableSmartLabels: true,
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y,
              dataValueMapper: (ChartData data, _) => data.x,
              dataLabelSettings: DataLabelSettings(
                isVisible: true, labelPosition: LabelPosition.outside
              )),
        ])
        )));
    }

{% endhighlight %}

![Series color](images/marker-datalabel/use_series_color.jpg)

### Connector line

This feature is used to connect label and data point using a line. It can be enabled for [`PieSeries`]() and [`DoughnutSeries`]() chart types. The [`connectorLineSettings`]() property used to customize the connector line.

* [`color`]() – used to change the color of the line
* [`width`]() – used to change the stroke thickness of the line
* [`length`]() – specifies the length of the connector line.
* [`type`]() - specifies the shape of connector line either [`curve`]() or [`line`](). 

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCircularChart(series: <CircularSeries>[
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
              )),
        ])
        )));
    }

{% endhighlight %}

![Connector line](images/marker-datalabel/connector_line.jpg)

### Point text mapping

The [`dataLabelMapper`]() property is used to map the text from data source. 

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
                child:SfCircularChart(series: <CircularSeries>[
          PieSeries<ChartData, String>(
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y,
              dataLabelMapper: (ChartData data, _) => data.text,
              dataLabelSettings: DataLabelSettings(
                  isVisible: true)),
        ])
        )));
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

You can customize the appearance of the data marker label with your own template using the [`builder`]() property of [`dataLabelSettings`]().

{% highlight dart %} 

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        body: Center(
            child: Container(
                child:SfCircularChart(series: <CircularSeries>[
          PieSeries<ChartData, String>(
              dataSource: chartData,
              xValueMapper: (ChartData data, _) => data.x,
              yValueMapper: (ChartData data, _) => data.y,
              dataLabelSettings: DataLabelSettings(
                  isVisible: true,
                  builder: (dynamic data, dynamic point, dynamic series,
                    int pointIndex, int seriesIndex) {
                  return Container(
                      height: 30,
                      width: 30,
                      child: Image.asset('images/livechart.png'));
                })),
        ])
        )));
    }

{% endhighlight %}

![Label template](images/marker-datalabel/datalabel_template.jpg)