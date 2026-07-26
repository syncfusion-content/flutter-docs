---
layout: post
title: Adding a Stacked Line Chart | Syncfusion Flutter XlsIO
description: Learn how to create, add, and manipulate a stacked line chart in an Excel worksheet using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Adding a Stacked Line Chart to an Excel Worksheet

A stacked line chart is a line chart in which each series is drawn above the previous one, so the values appear stacked along the y-axis. It is most effective for showing how the contribution of each series to a total changes over a continuous range, such as time. If you want to compare the values of multiple series without stacking, use a regular line chart instead.

For prerequisites and installation steps, see the [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview). For background on charts and the chart package, see [Working with Excel Charts](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-charts).

N> The code samples in this document use `await workbook.save()`. Always call `workbook.dispose()` after saving to release the XlsIO DOM memory, ideally inside a `try/finally` block.

## Create a stacked line chart

A stacked line chart is created in three steps: build the data, add a `Chart` to the worksheet's `ChartCollection`, and set the `chartType` and `dataRange`. The first column of the data range supplies the category labels, and each remaining column supplies a series of values.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';
import 'package:syncfusion_officechart/officechart.dart';

Future<void> createStackedLineChart() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Sample data: a list of cities and two temperature series.
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
  sheet.getRangeByName('C1').setText('Temp in F');
  sheet.getRangeByName('C2').setNumber(93);
  sheet.getRangeByName('C3').setNumber(104);
  sheet.getRangeByName('C4').setNumber(120);
  sheet.getRangeByName('C5').setNumber(80);
  sheet.getRangeByName('C6').setNumber(140);

  // Create a chart collection and add a stacked line chart.
  final ChartCollection charts = ChartCollection(sheet);
  final Chart chart = charts.add();
  chart.chartType = ExcelChartType.lineStacked;
  chart.dataRange = sheet.getRangeByName('A1:C6');
  chart.isSeriesInRows = false;

  // Bind the chart collection to the worksheet.
  sheet.charts = charts;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Customize a stacked line chart

The `Chart` class exposes properties for the most common chart elements: chart title, data labels, legend, and line patterns. The samples below build on the same data setup.

### Sample data setup

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';
import 'package:syncfusion_officechart/officechart.dart';

void populateStackedLineChartData(Worksheet sheet) {
  // Headers in row 1.
  sheet.getRangeByName('A1').setText('Day');
  sheet.getRangeByName('B1').setText('High Temp');
  sheet.getRangeByName('C1').setText('Low Temp');

  // Day labels in column A.
  sheet.getRangeByName('A2').setText('Monday');
  sheet.getRangeByName('A3').setText('Tuesday');
  sheet.getRangeByName('A4').setText('Wednesday');
  sheet.getRangeByName('A5').setText('Thursday');
  sheet.getRangeByName('A6').setText('Friday');

  // High temperatures in column B.
  sheet.getRangeByName('B2').setNumber(34);
  sheet.getRangeByName('B3').setNumber(29);
  sheet.getRangeByName('B4').setNumber(30);
  sheet.getRangeByName('B5').setNumber(32);
  sheet.getRangeByName('B6').setNumber(35);

  // Low temperatures in column C.
  sheet.getRangeByName('C2').setNumber(20);
  sheet.getRangeByName('C3').setNumber(22);
  sheet.getRangeByName('C4').setNumber(19);
  sheet.getRangeByName('C5').setNumber(18);
  sheet.getRangeByName('C6').setNumber(21);
}
{% endhighlight %}

### Chart title

{% highlight dart %}
Future<void> configureStackedLineChartTitle() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateStackedLineChartData(sheet);

  final ChartCollection charts = ChartCollection(sheet);
  final Chart chart = charts.add();
  chart.chartType = ExcelChartType.lineStacked;
  chart.dataRange = sheet.getRangeByName('A1:C6');
  chart.isSeriesInRows = false;

  // Set the chart title with formatting.
  chart.chartTitle = 'Weekly Weather Summary';
  chart.chartTitleArea.bold = true;
  chart.chartTitleArea.size = 10;
  chart.chartTitleArea.color = '#050505';

  sheet.charts = charts;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Data labels

{% highlight dart %}
Future<void> configureStackedLineChartDataLabels() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateStackedLineChartData(sheet);

  final ChartCollection charts = ChartCollection(sheet);
  final Chart chart = charts.add();
  chart.chartType = ExcelChartType.lineStacked;
  chart.dataRange = sheet.getRangeByName('A1:C6');
  chart.isSeriesInRows = false;

  // Configure data labels on every series.
  for (final ChartSerie serie in chart.series) {
    serie.dataLabels.isValue = true;
    serie.dataLabels.textArea.bold = true;
    serie.dataLabels.textArea.size = 10;
    serie.dataLabels.textArea.color = '#920467';
    serie.dataLabels.textArea.fontName = 'Arial';
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
| `isCategoryName` | Display the category name (for example, the day). |
| `isSeriesName` | Display the name of the series. |

### Per-series line patterns

{% highlight dart %}
Future<void> configureStackedLineChartSeriesPatterns() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateStackedLineChartData(sheet);

  final ChartCollection charts = ChartCollection(sheet);
  final Chart chart = charts.add();
  chart.chartType = ExcelChartType.lineStacked;
  chart.dataRange = sheet.getRangeByName('A1:C6');
  chart.isSeriesInRows = false;

  // Apply a different line pattern to each series.
  final List<String> colors = <String>['#F40829', '#08A2F4'];
  for (int i = 0; i < chart.series.length; i++) {
    chart.series[i].linePattern = ExcelChartLinePattern.longDash;
    chart.series[i].linePatternColor = colors[i];
  }

  sheet.charts = charts;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Legend and chart borders

{% highlight dart %}
Future<void> configureStackedLineChartLegendAndBorders() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateStackedLineChartData(sheet);

  final ChartCollection charts = ChartCollection(sheet);
  final Chart chart = charts.add();
  chart.chartType = ExcelChartType.lineStacked;
  chart.dataRange = sheet.getRangeByName('A1:C6');
  chart.isSeriesInRows = false;

  // Set the legend position. The `legend` property is nullable; it is null
  // until a legend is first accessed, after which it is created automatically.
  chart.legend!.position = ExcelLegendPosition.right;

  // Set the chart border (the line around the entire chart).
  chart.linePattern = ExcelChartLinePattern.solid;
  chart.linePatternColor = '#2F4F4F';

  // Set the plot area border (the line around the plot area only).
  chart.plotArea.linePattern = ExcelChartLinePattern.dashDot;
  chart.plotArea.linePatternColor = '#0000FF';

  sheet.charts = charts;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

The following Excel document is generated by combining the samples above:

![Customizing a stacked line chart](images/StackedLineChart.png)

## See also

* [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview)
* [Working with Excel Charts](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-charts)
* [Add a line chart](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/add-line-chart)
* [Add a stacked bar chart](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/add-stacked-bar-chart)
* [Chart API reference](https://pub.dev/documentation/syncfusion_officechart/latest/officechart/Chart-class.html)
* [Release notes](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/release-notes)
