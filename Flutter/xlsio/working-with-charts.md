---
layout: post
title: Working with Excel Charts | Syncfusion Flutter XlsIO
description: Learn how to create and manipulate different types of Excel charts in a worksheet using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with Excel Charts

Syncfusion Flutter XlsIO supports creating and modifying Excel charts inside a workbook. The chart model is provided by the `syncfusion office chart` package, which extends the worksheet model with a `ChartCollection`. A chart is created by setting a chart type, a data range, and optional chart elements such as a title, a legend, axis labels, and data labels.

For prerequisites and installation steps, see the [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview).

N> The code samples in this document use `await workbook.save()`. Always call `workbook.dispose()` after saving to release the XlsIO DOM memory, ideally inside a `try/finally` block.

## Installation

To add chart support to a project that already uses `syncfusion_flutter_xlsio`, add the `syncfusion office chart` dependency. The package is available on [pub.dev](https://pub.dev/packages/syncfusion_officechart).

Add the dependency to `pubspec.yaml`:

```yaml
dependencies:
  syncfusion_flutter_xlsio: ^<latest-version>
  syncfusion_officechart: ^<latest-version>
```

Then run the following command to fetch the package:

```bash
flutter pub get
```

N> The `syncfusion office chart` package depends on `syncfusion_flutter_xlsio`, so the XlsIO package is added automatically if it is not already in your dependencies.

Import the chart package in your Dart code:

{% highlight dart %}
import 'package:syncfusion_officechart/officechart.dart';
{% endhighlight %}

## Create a chart

A chart is created in three steps:

1. Create a `ChartCollection` for the worksheet.
2. Add a `Chart` to the collection and set its `chartType` and `dataRange`.
3. Assign the collection back to the worksheet through the `sheet.charts` property.

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';
import 'package:syncfusion_officechart/officechart.dart';

Future<void> createChart() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  // Sample data.
  sheet.getRangeByName('A1').setText('John');
  sheet.getRangeByName('A2').setText('Amy');
  sheet.getRangeByName('A3').setText('Jack');
  sheet.getRangeByName('A4').setText('Tiya');
  sheet.getRangeByName('B1').setNumber(10);
  sheet.getRangeByName('B2').setNumber(12);
  sheet.getRangeByName('B3').setNumber(20);
  sheet.getRangeByName('B4').setNumber(21);

  // Create a chart collection and add a column chart.
  final ChartCollection charts = ChartCollection(sheet);
  final Chart chart = charts.add();
  chart.chartType = ExcelChartType.column;
  chart.dataRange = sheet.getRangeByName('A1:B4');

  // Bind the chart collection to the worksheet.
  sheet.charts = charts;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

The supported values of the `ExcelChartType` enum are listed at the end of this page. The `dataRange` is the range of cells that supplies the chart's data; the first column (or first row, when `isSeriesInRows` is `true`) provides the category labels, and the remaining columns (or rows) provide the series values.

## Configure chart elements

The `Chart` class exposes properties for the most common chart elements: chart title, legend, axes, data labels, plot area, and line pattern. The following sub-samples each demonstrate one element. They all build on the same data setup.

### Sample data setup

{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';
import 'package:syncfusion_officechart/officechart.dart';

void populateChartSampleData(Worksheet sheet) {
  sheet.getRangeByName('A1').setText('Months');
  sheet.getRangeByName('B1').setText('Internal Sales Amount');
  sheet.getRangeByName('C1').setText('Reseller Sales Amount');

  sheet.getRangeByName('A2').setDateTime(DateTime(2014, 1, 14, 14, 14, 14));
  sheet.getRangeByName('A3').setDateTime(DateTime(2014, 2, 14, 14, 14, 14));
  sheet.getRangeByName('A4').setDateTime(DateTime(2014, 3, 14, 14, 14, 14));
  sheet.getRangeByName('A5').setDateTime(DateTime(2014, 4, 14, 14, 14, 14));
  sheet.getRangeByName('A6').setDateTime(DateTime(2014, 5, 14, 14, 14, 14));

  sheet.getRangeByName('B2').setNumber(700);
  sheet.getRangeByName('B3').setNumber(200);
  sheet.getRangeByName('B4').setNumber(300);
  sheet.getRangeByName('B5').setNumber(500);
  sheet.getRangeByName('B6').setNumber(800);

  sheet.getRangeByName('C2').setNumber(30);
  sheet.getRangeByName('C3').setNumber(40);
  sheet.getRangeByName('C4').setNumber(70);
  sheet.getRangeByName('C5').setNumber(2);
  sheet.getRangeByName('C6').setNumber(100);
}
{% endhighlight %}

### Chart title and position

{% highlight dart %}
Future<void> configureTitle() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateChartSampleData(sheet);

  final ChartCollection charts = ChartCollection(sheet);
  final Chart chart = charts.add();
  chart.chartType = ExcelChartType.line;
  chart.dataRange = sheet.getRangeByName('A1:C6');
  chart.isSeriesInRows = false;

  // Chart title with formatting.
  chart.chartTitle = 'Yearly sales';
  chart.chartTitleArea.bold = true;
  chart.chartTitleArea.size = 12;

  // Chart position on the worksheet (1-based row and column).
  chart.topRow = 0;
  chart.bottomRow = 20;
  chart.leftColumn = 1;
  chart.rightColumn = 8;

  sheet.charts = charts;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Legend

{% highlight dart %}
Future<void> configureLegend() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateChartSampleData(sheet);

  final ChartCollection charts = ChartCollection(sheet);
  final Chart chart = charts.add();
  chart.chartType = ExcelChartType.line;
  chart.dataRange = sheet.getRangeByName('A1:C6');
  chart.isSeriesInRows = false;

  // Legend position. The `legend` property is nullable; it is null until a
  // legend is first accessed, after which it is created automatically.
  chart.legend!.position = ExcelLegendPosition.bottom;

  sheet.charts = charts;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Axes

{% highlight dart %}
Future<void> configureAxes() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateChartSampleData(sheet);

  final ChartCollection charts = ChartCollection(sheet);
  final Chart chart = charts.add();
  chart.chartType = ExcelChartType.line;
  chart.dataRange = sheet.getRangeByName('A1:C6');
  chart.isSeriesInRows = false;

  // Category axis (dates): show the month name.
  chart.primaryCategoryAxis.title = 'Month';
  chart.primaryCategoryAxis.numberFormat = 'mmmm';

  // Value axis: show values with two decimal places.
  chart.primaryValueAxis.title = 'Sales amount';
  chart.primaryValueAxis.numberFormat = '0.00';

  sheet.charts = charts;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

### Data labels

{% highlight dart %}
Future<void> configureDataLabels() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateChartSampleData(sheet);

  final ChartCollection charts = ChartCollection(sheet);
  final Chart chart = charts.add();
  chart.chartType = ExcelChartType.line;
  chart.dataRange = sheet.getRangeByName('A1:C6');
  chart.isSeriesInRows = false;

  // Configure data labels on the first series.
  final ChartSerie serie = chart.series[0];
  serie.dataLabels.isValue = true;
  serie.dataLabels.isCategoryName = true;
  serie.dataLabels.isSeriesName = true;
  serie.dataLabels.textArea.bold = true;
  serie.dataLabels.textArea.size = 12;
  serie.dataLabels.textArea.fontName = 'Arial';

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

### Plot area and chart line pattern

{% highlight dart %}
Future<void> configureLinePattern() async {
  final Workbook workbook = Workbook();
  final Worksheet sheet = workbook.worksheets[0];

  populateChartSampleData(sheet);

  final ChartCollection charts = ChartCollection(sheet);
  final Chart chart = charts.add();
  chart.chartType = ExcelChartType.line;
  chart.dataRange = sheet.getRangeByName('A1:C6');
  chart.isSeriesInRows = false;

  // Plot area line pattern (the border around the plot area).
  chart.plotArea.linePattern = ExcelChartLinePattern.solid;
  chart.plotArea.linePatternColor = '#00FFFF';

  // Chart line pattern (the line that surrounds the chart).
  chart.linePattern = ExcelChartLinePattern.longDashDotDot;
  chart.linePatternColor = '#0000FF';

  sheet.charts = charts;

  final List<int> bytes = await workbook.save();
  workbook.dispose();
}
{% endhighlight %}

The supported `ExcelChartLinePattern` values include `solid`, `dash`, `dashDot`, `dashDotDot`, `longDash`, `longDashDot`, `longDashDotDot`, and `none`. The supported `ExcelLegendPosition` values include `top`, `bottom`, `left`, `right`, `topRight`, and `none`.

## Supported chart types

The following chart types are supported by Syncfusion Flutter XlsIO. Chart types with a dedicated page are linked.

| Chart type | `ExcelChartType` value | Dedicated page |
|------------|------------------------|----------------|
| Column | `ExcelChartType.column` | [Add column chart](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/add-column-chart) |
| Stacked column | `ExcelChartType.columnStacked` | [Add stacked column chart](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/add-stacked-column-chart) |
| Bar | `ExcelChartType.bar` | [Add bar chart](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/add-bar-chart) |
| Stacked bar | `ExcelChartType.barStacked` | [Add stacked bar chart](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/add-stacked-bar-chart) |
| Line | `ExcelChartType.line` | [Add line chart](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/add-line-chart) |
| Stacked line | `ExcelChartType.lineStacked` | [Add stacked line chart](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/add-stacked-line-chart) |
| Line with markers | `ExcelChartType.lineMarkers` | — |
| Stacked line with markers | `ExcelChartType.lineMarkersStacked` | — |
| 100% stacked line with markers | `ExcelChartType.lineMarkers100PercentStacked` | — |
| 3-D line | `ExcelChartType.line3D` | — |
| 3-D column | `ExcelChartType.column3D` | — |
| 3-D clustered column | `ExcelChartType.column3DClustered` | — |
| 3-D stacked column | `ExcelChartType.column3DStacked` | — |
| 3-D 100% stacked column | `ExcelChartType.column3D100PercentStacked` | — |
| 3-D clustered bar | `ExcelChartType.bar3DClustered` | — |
| 3-D stacked bar | `ExcelChartType.bar3DStacked` | — |
| 3-D 100% stacked bar | `ExcelChartType.bar3D100PercentStacked` | — |
| Pie | `ExcelChartType.pie` | [Add pie chart](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/add-pie-chart) |
| 3-D pie | `ExcelChartType.pie3D` | — |
| Pie of pie | `ExcelChartType.pieOfPie` | — |
| Bar of pie | `ExcelChartType.barOfPie` | — |
| Doughnut | `ExcelChartType.doughnut` | — |
| Doughnut exploded | `ExcelChartType.doughnutExploded` | — |
| High-low-close | `ExcelChartType.highLowClose` | — |
| Open-high-low-close | `ExcelChartType.openHighLowClose` | — |
| Volume-high-low-close | `ExcelChartType.volumeHighLowClose` | — |
| Volume-open-high-low-close | `ExcelChartType.volumeOpenHighLowClose` | — |

## See also

* [Flutter XlsIO Overview](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/overview)
* [Working with Workbook](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-workbook)
* [Working with Excel Worksheets](https://help.syncfusion.com/document-processing/excel/excel-library/flutter/working-with-excel-worksheet)
* [Chart API reference](https://pub.dev/documentation/syncfusion_officechart/latest/officechart/Chart-class.html)
* [ChartCollection API reference](https://pub.dev/documentation/syncfusion_officechart/latest/officechart/ChartCollection-class.html)
