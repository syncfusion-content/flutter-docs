---
layout: post
title: Excel Charts of Syncfusion Flutter XlsIO.
description: Learn how to create, add and manipulate different type of Excel charts in worksheet using Syncfusion Flutter XlsIO. 
platform: flutter
control: Excel
documentation: ug
---

# Working with Excel Charts

Flutter XlsIO has support for creating and modifying Excel charts inside a workbook.

**Add dependency**

Add the Syncfusion Flutter OfficeChart dependency to your pub spec file.

{% highlight dart %}

dependencies: 
syncfusion_officechart: ^xx.x.xx

{% endhighlight %}

N> Here **xx.x.xx** denotes the current version of ['Syncfusion Flutter OfficeChart'](https://pub.dev/packages/syncfusion_officechart/versions) package.

**Get packages**

Run the following command to get the required packages.

{% highlight dart %}

$ flutter pub get

{% endhighlight %}

N> If you add OfficeChart package in your dependency, it will automatically fetch the Syncfusion XlsIO package while getting OfficeChart package in your machine.

## Required package to add charts

Import the following package in your Dart code to add charts

{% highlight dart %}

import 'package:syncfusion_officechart/officechart.dart';

{% endhighlight %}

## Creating a Chart

The **Chart** represents the chart in a worksheet. A chart can be created entering by values one by one.

The following code example illustrates how to create a chart.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Setting value in the cell.
sheet.getRangeByName('A1').setText('John');
sheet.getRangeByName('A2').setText('Amy');
sheet.getRangeByName('A3').setText('Jack');
sheet.getRangeByName('A4').setText('Tiya');
sheet.getRangeByName('B1').setNumber(10);
sheet.getRangeByName('B2').setNumber(12);
sheet.getRangeByName('B3').setNumber(20);
sheet.getRangeByName('B4').setNumber(21);

// Create an instances of chart collection.
final ChartCollection charts = ChartCollection(sheet);

// Add the chart.
final Chart chart = charts.add();

// Set Chart Type.
chart.chartType = ExcelChartType.column;

// Set data range in the worksheet.
chart.dataRange = sheet.getRangeByName('A1:B4');

// set charts to worksheet.
sheet.charts = charts;

// save and dispose the workbook.
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

File('Chart.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Supported chart elements

* A chart axis title that you can use in the chart.
* A chart title that you can use in the chart.
* The legend of the chart.
* The horizontal (category) and vertical (value) axis along which the data is plotted in the chart.
* A data label that you can use to identify the details of a data point in a data series.

The following code illustrate the support chart elements.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Setting value in the cell.
sheet.getRangeByName('A1').setText('Months');
sheet.getRangeByName('B1').setText('Internal Sales Amount');
sheet.getRangeByName('C1').setText('Reseller Sales Amount');
sheet.getRangeByName('A2').setDateTime(DateTime(2014, 01, 14, 14, 14, 14));
sheet.getRangeByName('A3').setDateTime(DateTime(2014, 02, 14, 14, 14, 14));
sheet.getRangeByName('A4').setDateTime(DateTime(2014, 03, 14, 14, 14, 14));
sheet.getRangeByName('A5').setDateTime(DateTime(2014, 04, 14, 14, 14, 14));
sheet.getRangeByName('A6').setDateTime(DateTime(2014, 05, 14, 14, 14, 14));
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

// Create an instances of chart collection.
final ChartCollection charts = ChartCollection(sheet);

// Add the chart.
final Chart chart = charts.add();

// Set Chart Type.
chart.chartType = ExcelChartType.line;

// Set data range in the worksheet.
chart.dataRange = sheet.getRangeByName('A1:C6');
chart.isSeriesInRows = false;

// setting chart tile with font properties
chart.chartTitle = 'Yearly sales';
chart.chartTitleArea.bold = true;
chart.chartTitleArea.size = 12;

// setting legend position.
chart.legend!.position = ExcelLegendPosition.bottom;

// setting the chart position.
chart.topRow = 0;
chart.bottomRow = 20;
chart.leftColumn = 1;
chart.rightColumn = 8;

//setting Axis number format.
chart.primaryCategoryAxis.numberFormat = 'mmmm';
chart.primaryValueAxis.numberFormat = '0.00';

//setting datalabels
final ChartSerie serie = chart.series[0];
serie.dataLabels.isValue = true;
serie.dataLabels.isCategoryName = true;
serie.dataLabels.isSeriesName = true;
serie.dataLabels.textArea.bold = true;
serie.dataLabels.textArea.size = 12;
serie.dataLabels.textArea.fontName = 'Arial';

// Setting Line pattern
chart.plotArea.linePattern = ExcelChartLinePattern.solid;
chart.plotArea.linePatternColor = '#00FFFF';
chart.linePattern = ExcelChartLinePattern.longDashDotDot;
chart.linePatternColor = '#0000FF';

// set charts to worksheet.
sheet.charts = charts;

// save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

File('ChartElement.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Supported Chart Types

The following chart types are supported in Flutter XlsIO.

* [Pie](https://help.syncfusion.com/flutter/xlsio/add-pie-chart)
* [Bar](https://help.syncfusion.com/flutter/xlsio/add-bar-chart)
* [Column](https://help.syncfusion.com/flutter/xlsio/add-column-chart)
* [line](https://help.syncfusion.com/flutter/xlsio/add-line-chart)
* [Bar_Stacked](https://help.syncfusion.com/flutter/xlsio/add-stacked-bar-chart)
* [Column_Stacked](https://help.syncfusion.com/flutter/xlsio/add-stacked-column-chart)
* [Line_Stacked](https://help.syncfusion.com/flutter/xlsio/add-stacked-line-chart)
* Line With Markers
* Stacked Line With Markers
* 100% Stacked Line With Markers
* 3-D Line3D
* 3-D Column
* 3-D Clustered Column
* 3-D 100% Stacked Column
* 3-D Stacked Column
* 3-D Clustered Bar
* 3-D 100% Stacked Bar
* High Low Close
* Open High Low Close
* Volume High Low Close
* Volume Open High Low Close
* 3-D Pie
* Pie Of Pie
* Bar Of Pie
* Doughnut
* Doughnut Exploded

