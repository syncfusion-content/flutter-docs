---
layout: post
title: Adding a Column Chart | Syncfusion Flutter XlsIO
description: Learn how to create, add, and manipulate a column chart in an Excel worksheet using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Adding a Column Chart to an Excel Worksheet

A column chart displays categorical data with vertical rectangular bars whose heights are proportional to the data values. It is most effective when you want to compare values across a small number of categories with short labels. If the category labels are long and you want horizontal bars, use a bar chart instead.

For prerequisites and installation steps, see the [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview). For background on charts and the chart package, see [Working with Excel Charts](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-charts).

N> The code samples in this document use `await workbook.save()`. Always call `workbook.dispose()` after saving to release the XlsIO DOM memory, ideally inside a `try/finally` block.

## Create a column chart

A column chart is created in three steps: build the data, add a `Chart` to the worksheet's `ChartCollection`, and set the `chartType` and `dataRange`. The first column of the data range supplies the category labels, and the second column supplies the values.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';
import 'package:syncfusion_officechart/officechart.dart';

Future<void> createColumnChart() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Sample data: a list of cost categories and their amounts.
  sheet.getRangeByName('A11').setText('Venue');
  sheet.getRangeByName('A12').setText('Seating & Decor');
  sheet.getRangeByName('A13').setText('Technical Team');
  sheet.getRangeByName('A14').setText('Performers');
  sheet.getRangeByName('A15').setText("Performer's Transport");

  sheet.getRangeByName('B11:B15').numberFormat = r'$#,##0_)';
  sheet.getRangeByName('B11').setNumber(17500);
  sheet.getRangeByName('B12').setNumber(1828);
  sheet.getRangeByName('B13').setNumber(800);
  sheet.getRangeByName('B14').setNumber(14000);
  sheet.getRangeByName('B15').setNumber(2600);

  // Create a chart collection and add a column chart.
  final ChartCollection charts = ChartCollection(sheet);
  final Chart chart = charts.add();
  chart.chartType = ExcelChartType.column;
  chart.dataRange = sheet.getRangeByName('A11:B15');
  chart.isSeriesInRows = false;

  // Bind the chart collection to the worksheet.
  sheet.charts = charts;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

## Customize a column chart

The `Chart` class exposes properties for the most common chart elements: chart title, data labels, legend, and line patterns. The samples below build on the same data setup.

### Sample data setup

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';
import 'package:syncfusion_officechart/officechart.dart';

void populateColumnChartData(Worksheet sheet) {
  sheet.getRangeByName('A1').setText('Item');
  sheet.getRangeByName('A2').setText('Audio & Visual Equipment');
  sheet.getRangeByName('A3').setText('Catering');
  sheet.getRangeByName('A4').setText('Event Security');
  sheet.getRangeByName('A5').setText('Lighting');
  sheet.getRangeByName('A6').setText('Stage Setup');

  sheet.getRangeByName('B1').setText('Amount');
  sheet.getRangeByName('B2').setNumber(10500);
  sheet.getRangeByName('B3').setNumber(9628);
  sheet.getRangeByName('B4').setNumber(7900);
  sheet.getRangeByName('B5').setNumber(5000);
  sheet.getRangeByName('B6').setNumber(4600);

  sheet.getRangeByName('B2:B6').numberFormat = r'$#,##0_)';
}
{% endhighlight %}

### Chart title

{% highlight dart %}
Future<void> configureColumnChartTitle() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateColumnChartData(sheet);

  final ChartCollection charts = ChartCollection(sheet);
  final Chart chart = charts.add();
  chart.chartType = ExcelChartType.column;
  chart.dataRange = sheet.getRangeByName('A1:B6');
  chart.isSeriesInRows = false;

  // Set the chart title with formatting.
  chart.chartTitle = 'Event Expense Analysis';
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
Future<void> configureColumnChartDataLabels() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateColumnChartData(sheet);

  final ChartCollection charts = ChartCollection(sheet);
  final Chart chart = charts.add();
  chart.chartType = ExcelChartType.column;
  chart.dataRange = sheet.getRangeByName('A1:B6');
  chart.isSeriesInRows = false;

  // Configure data labels on the first series.
  final ChartSerie serie = chart.series[0];
  serie.dataLabels.isValue = true;
  serie.dataLabels.textArea.bold = true;
  serie.dataLabels.textArea.size = 10;
  serie.dataLabels.textArea.fontName = 'Arial';
  serie.dataLabels.textArea.color = '#48E7D1';

  sheet.charts = charts;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

The `dataLabels` flags control which parts of a data point are displayed:

| Flag | Description |
|------|-------------|
| `isValue` | Display the numeric value of the bar. |
| `isCategoryName` | Display the category name. |
| `isSeriesName` | Display the name of the series. |

### Legend and line patterns

{% highlight dart %}
Future<void> configureColumnChartLegendAndBorders() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateColumnChartData(sheet);

  final ChartCollection charts = ChartCollection(sheet);
  final Chart chart = charts.add();
  chart.chartType = ExcelChartType.column;
  chart.dataRange = sheet.getRangeByName('A1:B6');
  chart.isSeriesInRows = false;

  // Add a border to the data labels of the first series.
  final ChartSerie serie = chart.series[0];
  serie.linePattern = ExcelChartLinePattern.longDash;
  serie.linePatternColor = '#EE2828';

  // Set the legend position. The `legend` property is nullable; it is null
  // until a legend is first accessed, after which it is created automatically.
  chart.legend!.position = ExcelLegendPosition.right;

  // Set the chart border (the line around the entire chart).
  chart.linePattern = ExcelChartLinePattern.solid;
  chart.linePatternColor = '#2F4F4F';

  // Set the plot area border (the line around the plot area only).
  chart.plotArea.linePattern = ExcelChartLinePattern.roundDot;
  chart.plotArea.linePatternColor = '#0000FF';

  sheet.charts = charts;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

The following Excel document is generated by combining the samples above:

![Customizing a column chart](images/ColumnChart.png)

## See also

* [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview)
* [Working with Excel Charts](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-charts)
* [Add a bar chart](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/add-bar-chart)
* [Add a pie chart](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/add-pie-chart)
* [Add a line chart](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/add-line-chart)
* [Chart API reference](https://pub.dev/documentation/syncfusion_officechart/latest/officechart/Chart-class.html)
* [Release notes](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/release-notes)
