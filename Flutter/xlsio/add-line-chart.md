---
layout: post
title: Adding a Line Chart | Syncfusion Flutter XlsIO
description: Learn how to create, add, and manipulate a line chart in an Excel worksheet using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Adding a Line Chart to an Excel Worksheet

A line chart displays information as a series of data points connected by straight line segments. It is most effective for showing trends over a continuous range, such as time series. A plain line chart connects the points with lines; the `lineMarkers` variant adds a visible marker on each data point.

For prerequisites and installation steps, see the [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview). For background on charts and the chart package, see [Working with Excel Charts](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-charts).

N> The code samples in this document use `await workbook.save()`. Always call `workbook.dispose()` after saving to release the XlsIO DOM memory, ideally inside a `try/finally` block.

## Create a line chart

A line chart is created in three steps: build the data, add a `Chart` to the worksheet's `ChartCollection`, and set the `chartType` and `dataRange`. The first column of the data range supplies the category labels, and the second column supplies the values.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';
import 'package:syncfusion_officechart/officechart.dart';

Future<void> createLineChart() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Sample data: a list of cities and their temperatures.
  sheet.getRangeByName('A1').setText('City Name');
  sheet.getRangeByName('A2').setText('Chennai');
  sheet.getRangeByName('A3').setText('Mumbai');
  sheet.getRangeByName('A4').setText('Delhi');
  sheet.getRangeByName('A5').setText('Hyderabad');
  sheet.getRangeByName('A6').setText('Kolkata');
  sheet.getRangeByName('B1').setText('Temp in C');
  sheet.getRangeByName('B2').setNumber(34);
  sheet.getRangeByName('B3').setNumber(40);
  sheet.getRangeByName('B4').setNumber(47);
  sheet.getRangeByName('B5').setNumber(20);
  sheet.getRangeByName('B6').setNumber(66);

  // Create a chart collection and add a line chart.
  final ChartCollection charts = ChartCollection(sheet);
  final Chart chart = charts.add();
  chart.chartType = ExcelChartType.line;
  chart.dataRange = sheet.getRangeByName('A1:B6');
  chart.isSeriesInRows = false;

  // Bind the chart collection to the worksheet.
  sheet.charts = charts;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Customize a line chart

The `Chart` class exposes properties for the most common chart elements: chart title, data labels, legend, and line patterns. The samples below build on the same data setup.

### Sample data setup

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';
import 'package:syncfusion_officechart/officechart.dart';

void populateLineChartData(Worksheet sheet) {
  sheet.getRangeByName('A1').setText('Month');
  sheet.getRangeByName('A2').setText('January');
  sheet.getRangeByName('A3').setText('February');
  sheet.getRangeByName('A4').setText('March');
  sheet.getRangeByName('A5').setText('April');
  sheet.getRangeByName('A6').setText('May');

  sheet.getRangeByName('B1').setText('Laptop');
  sheet.getRangeByName('B2').setNumber(1200);
  sheet.getRangeByName('B3').setNumber(1100);
  sheet.getRangeByName('B4').setNumber(1300);
  sheet.getRangeByName('B5').setNumber(1250);
  sheet.getRangeByName('B6').setNumber(1400);

  sheet.getRangeByName('C1').setText('SmartPhone');
  sheet.getRangeByName('C2').setNumber(1500);
  sheet.getRangeByName('C3').setNumber(1300);
  sheet.getRangeByName('C4').setNumber(1780);
  sheet.getRangeByName('C5').setNumber(1890);
  sheet.getRangeByName('C6').setNumber(1600);

  sheet.getRangeByName('D1').setText('Tablets');
  sheet.getRangeByName('D2').setNumber(800);
  sheet.getRangeByName('D3').setNumber(900);
  sheet.getRangeByName('D4').setNumber(850);
  sheet.getRangeByName('D5').setNumber(950);
  sheet.getRangeByName('D6').setNumber(1000);
}
{% endhighlight %}

### Chart title

{% highlight dart %}
Future<void> configureLineChartTitle() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateLineChartData(sheet);

  final ChartCollection charts = ChartCollection(sheet);
  final Chart chart = charts.add();
  chart.chartType = ExcelChartType.line;
  chart.dataRange = sheet.getRangeByName('A1:D6');
  chart.isSeriesInRows = false;

  // Set the chart title with formatting.
  chart.chartTitle = 'Monthly Sales Data';
  chart.chartTitleArea.bold = true;
  chart.chartTitleArea.size = 10;
  chart.chartTitleArea.color = '#0000FF';

  sheet.charts = charts;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Data labels

{% highlight dart %}
Future<void> configureLineChartDataLabels() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateLineChartData(sheet);

  final ChartCollection charts = ChartCollection(sheet);
  final Chart chart = charts.add();
  chart.chartType = ExcelChartType.line;
  chart.dataRange = sheet.getRangeByName('A1:D6');
  chart.isSeriesInRows = false;

  // Configure data labels on every series.
  for (final ChartSerie serie in chart.series) {
    serie.dataLabels.isValue = true;
    serie.dataLabels.textArea.bold = true;
    serie.dataLabels.textArea.size = 10;
    serie.dataLabels.textArea.fontName = 'Arial';
    serie.dataLabels.textArea.color = '#27A6EA';
  }

  sheet.charts = charts;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

The `dataLabels` flags control which parts of a data point are displayed:

| Flag | Description |
|------|-------------|
| `isValue` | Display the numeric value of the data point. |
| `isCategoryName` | Display the category name (for example, the month). |
| `isSeriesName` | Display the name of the series. |

### Per-series line patterns

{% highlight dart %}
Future<void> configureLineChartSeriesPatterns() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateLineChartData(sheet);

  final ChartCollection charts = ChartCollection(sheet);
  final Chart chart = charts.add();
  chart.chartType = ExcelChartType.line;
  chart.dataRange = sheet.getRangeByName('A1:D6');
  chart.isSeriesInRows = false;

  // Apply a different line pattern to each series.
  final List<ExcelChartLinePattern> patterns = <ExcelChartLinePattern>[
    ExcelChartLinePattern.longDash,
    ExcelChartLinePattern.roundDot,
    ExcelChartLinePattern.squareDot,
  ];
  for (int i = 0; i < chart.series.length; i++) {
    chart.series[i].linePattern = patterns[i];
    chart.series[i].linePatternColor = '#EE2828';
  }

  sheet.charts = charts;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Legend and chart borders

{% highlight dart %}
Future<void> configureLineChartLegendAndBorders() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateLineChartData(sheet);

  final ChartCollection charts = ChartCollection(sheet);
  final Chart chart = charts.add();
  chart.chartType = ExcelChartType.line;
  chart.dataRange = sheet.getRangeByName('A1:D6');
  chart.isSeriesInRows = false;

  // Set the legend position. The `legend` property is nullable; it is null
  // until a legend is first accessed, after which it is created automatically.
  chart.legend!.position = ExcelLegendPosition.right;

  // Set the chart border (the line around the entire chart).
  chart.linePattern = ExcelChartLinePattern.solid;
  chart.linePatternColor = '#2F4F4F';

  // Set the plot area border (the line around the plot area only).
  chart.plotArea.linePattern = ExcelChartLinePattern.roundDot;
  chart.plotArea.linePatternColor = '#36DCE9';

  sheet.charts = charts;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

The following Excel document is generated by combining the samples above:

![Customizing a line chart](images/LineChart.png)

## See also

* [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview)
* [Working with Excel Charts](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-charts)
* [Add a column chart](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/add-column-chart)
* [Add a bar chart](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/add-bar-chart)
* [Add a pie chart](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/add-pie-chart)
* [Chart API reference](https://pub.dev/documentation/syncfusion_officechart/latest/officechart/Chart-class.html)
* [Release notes](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/release-notes)
