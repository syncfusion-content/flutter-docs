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

## Required package to add charts

Import the following package in your Dart code to add charts

{% highlight dart %}

import 'package:syncfusion_flutter_xlsio/xlsio.dart';
import 'package:syncfusion_flutter_officechart/officechart.dart';

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
workbook.save('Chart.xlsx');
workbook.dispose();

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
chart.legend.position = ExcelLegendPosition.bottom;

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
workbook.save('ChartElement.xlsx');
workbook.dispose();

{% endhighlight %}

## Adding Pie Chart

The following code snippet illustrate how to add pie chart

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Setting value in the cell.
sheet.getRangeByName('A11').setText('Venue');
sheet.getRangeByName('A12').setText('Seating & Decor');
sheet.getRangeByName('A13').setText('Technical Team');
sheet.getRangeByName('A14').setText('performers');
sheet.getRangeByName('A15').setText('performer\'s Transport');
sheet.getRangeByName('B11:B15').numberFormat = '\$#,##0_)';
sheet.getRangeByName('B11').setNumber(17500);
sheet.getRangeByName('B12').setNumber(1828);
sheet.getRangeByName('B13').setNumber(800);
sheet.getRangeByName('B14').setNumber(14000);
sheet.getRangeByName('B15').setNumber(2600);

// Create an instances of chart collection.
final ChartCollection charts = ChartCollection(sheet);

// Add the chart.
final Chart chart1 = charts.add();

// Set Chart Type.
chart1.chartType = ExcelChartType.pie;

// Set data range in the worksheet.
chart1.dataRange = sheet.getRangeByName('A11:B15');
chart1.isSeriesInRows = false;

// set charts to worksheet.
sheet.charts = charts;

// save and dispose the workbook.
workbook.save('PieChart.xlsx');
workbook.dispose();

{% endhighlight %}

## Adding bar chart

The following code snippet illustrate how to add bar chart

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Setting value in the cell.
sheet.getRangeByName('A1').setText('Items');
sheet.getRangeByName('B1').setText('Amount(in \$)');
sheet.getRangeByName('C1').setText('Count');
sheet.getRangeByName('A2').setText('Beverages');
sheet.getRangeByName('A3').setText('Condiments');
sheet.getRangeByName('A4').setText('Confections');
sheet.getRangeByName('A5').setText('Dairy Products');
sheet.getRangeByName('A6').setText('Grains / Cereals');
sheet.getRangeByName('B2').setNumber(2776);
sheet.getRangeByName('B3').setNumber(1077);
sheet.getRangeByName('B4').setNumber(2287);
sheet.getRangeByName('B5').setNumber(1368);
sheet.getRangeByName('B6').setNumber(3325);
sheet.getRangeByName('C2').setNumber(925);
sheet.getRangeByName('C3').setNumber(378);
sheet.getRangeByName('C4').setNumber(880);
sheet.getRangeByName('C5').setNumber(581);
sheet.getRangeByName('C6').setNumber(189);

// Create an instances of chart collection.
final ChartCollection charts = ChartCollection(sheet);

// Add the chart.
final Chart chart1 = charts.add();

// Set Chart Type.
chart1.chartType = ExcelChartType.bar;

// Set data range in the worksheet.
chart1.dataRange = sheet.getRangeByName('A1:C6');

chart1.isSeriesInRows = false;

// set charts to worksheet.
sheet.charts = charts;

// save and dispose the workbook.
workbook.save('BarChart.xlsx');
workbook.dispose();

{% endhighlight %}

## Adding Column Chart

The following code snippet illustrate how to add column chart.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Setting value in the cell.
sheet.getRangeByName('A11').setText('Venue');
sheet.getRangeByName('A12').setText('Seating & Decor');
sheet.getRangeByName('A13').setText('Technical Team');
sheet.getRangeByName('A14').setText('performers');
sheet.getRangeByName('A15').setText('performer\'s Transport');
sheet.getRangeByName('B11:B15').numberFormat = '\$#,##0_)';
sheet.getRangeByName('B11').setNumber(17500);
sheet.getRangeByName('B12').setNumber(1828);
sheet.getRangeByName('B13').setNumber(800);
sheet.getRangeByName('B14').setNumber(14000);
sheet.getRangeByName('B15').setNumber(2600);

// Create an instances of chart collection.
final ChartCollection charts = ChartCollection(sheet);

// Add the chart.
final Chart chart1 = charts.add();

// Set Chart Type.
chart1.chartType = ExcelChartType.column;

// Set data range in the worksheet.
chart1.dataRange = sheet.getRangeByName('A11:B15');
chart1.isSeriesInRows = false;

// set charts to worksheet.
sheet.charts = charts;

// save and dispose the workbook.
workbook.save('ExcelColumnChart.xlsx');
workbook.dispose();

{% endhighlight %}

## Adding line chart

The following code snippet illustrate how to add line chart.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Setting value in the cell.
sheet.getRangeByName('A1').setText('City Name');
sheet.getRangeByName('A2').setText('Chennai');
sheet.getRangeByName('A3').setText('Mumbai');
sheet.getRangeByName('A4').setText('Delhi');
sheet.getRangeByName('A5').setText('Hyderabad');
sheet.getRangeByName('A6').setText('Kolkata');
sheet.getRangeByName('B1').setText('Temp in C');
sheet.getRangeByName('B2').setNumber(34);
sheet.getRangeByName('B3').setNumber(40);
sheet.getRangeByName('B4').setNumber(47);
sheet.getRangeByName('B5').setNumber(20);
sheet.getRangeByName('B6').setNumber(66);

// Create an instances of chart collection.
final ChartCollection charts = ChartCollection(sheet);

// Add the chart.
final Chart chart = charts.add();

//Set Chart Type.
chart.chartType = ExcelChartType.line;

//Set data range in the worksheet.
chart.dataRange = sheet.getRangeByName('A1:B6');
chart.isSeriesInRows = false;

// set charts to worksheet.
sheet.charts = charts;

//save and dispose workbook.
workbook.save('LineChart.xlsx');
workbook.dispose();

{% endhighlight %}

## Adding stacked Column chart

The following code snippet illustrate how to add stacked column chart.


{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Setting value in the cell.
sheet.getRangeByName('A1').setText('Items');
sheet.getRangeByName('B1').setText('Amount(in \$)');
sheet.getRangeByName('C1').setText('Count');
sheet.getRangeByName('A2').setText('Beverages');
sheet.getRangeByName('A3').setText('Condiments');
sheet.getRangeByName('A4').setText('Confections');
sheet.getRangeByName('A5').setText('Dairy Products');
sheet.getRangeByName('A6').setText('Grains / Cereals');
sheet.getRangeByName('B2').setNumber(2776);
sheet.getRangeByName('B3').setNumber(1077);
sheet.getRangeByName('B4').setNumber(2287);
sheet.getRangeByName('B5').setNumber(1368);
sheet.getRangeByName('B6').setNumber(3325);
sheet.getRangeByName('C2').setNumber(925);
sheet.getRangeByName('C3').setNumber(378);
sheet.getRangeByName('C4').setNumber(880);
sheet.getRangeByName('C5').setNumber(581);
sheet.getRangeByName('C6').setNumber(189);

// Create an instances of chart collection.
final ChartCollection charts = ChartCollection(sheet);

// Add the chart.
final Chart chart1 = charts.add();

//Set Chart Type.
chart1.chartType = ExcelChartType.columnStacked;

//Set data range in the worksheet.
chart1.dataRange = sheet.getRangeByName('A1:C6');
chart1.isSeriesInRows = false;

// set charts to worksheet.
sheet.charts = charts;

// save and dispose workbook.
workbook.save('ColunmStackedChart.xlsx');
workbook.dispose();

{% endhighlight %}

## Adding stacked bar chart

The following code snippet illustrate how to add stacked bar chart.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Setting value in the cell.
sheet.getRangeByName('A1').setText('Name');
sheet.getRangeByName('B1').setText('Salary');
sheet.getRangeByName('C1').setText('Working hr');
sheet.getRangeByName('A2').setText('Ben');
sheet.getRangeByName('A3').setText('Mark');
sheet.getRangeByName('A4').setText('Sundar');
sheet.getRangeByName('A5').setText('Geo');
sheet.getRangeByName('A6').setText('Andrew');
sheet.getRangeByName('B2').setNumber(1000);
sheet.getRangeByName('B3').setNumber(2000);
sheet.getRangeByName('B4').setNumber(2392);
sheet.getRangeByName('B5').setNumber(3211);
sheet.getRangeByName('B6').setNumber(4211);
sheet.getRangeByName('C2').setNumber(287);
sheet.getRangeByName('C3').setNumber(355);
sheet.getRangeByName('C4').setNumber(134);
sheet.getRangeByName('C5').setNumber(581);
sheet.getRangeByName('C6').setNumber(426);

// Create an instances of chart collection.
final ChartCollection charts = ChartCollection(sheet);

// Add the chart.
final Chart chart1 = charts.add();

// Set Chart Type.
chart1.chartType = ExcelChartType.barStacked;

// Set data range in the worksheet.
chart1.dataRange = sheet.getRangeByName('A1:C6');
chart1.isSeriesInRows = false;

// set charts to worksheet.
sheet.charts = charts;

//save and dispose workbook.
workbook.save('BarStackedChart.xlsx');
workbook.dispose();

{% endhighlight %}


## Added stacked line chart

The following code snippet illustrate how to add stacked Line chart.

{% highlight dart %}

// Create a new Excel document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Setting value in the cell.
sheet.getRangeByName('A1').setText('City Name');
sheet.getRangeByName('A2').setText('Chennai');
sheet.getRangeByName('A3').setText('Mumbai');
sheet.getRangeByName('A4').setText('Delhi');
sheet.getRangeByName('A5').setText('Hyderabad');
sheet.getRangeByName('A6').setText('Kolkata');
sheet.getRangeByName('B1').setText('Temp in C');
sheet.getRangeByName('B2').setNumber(34);
sheet.getRangeByName('B3').setNumber(40);
sheet.getRangeByName('B4').setNumber(47);
sheet.getRangeByName('B5').setNumber(20);
sheet.getRangeByName('B6').setNumber(66);
sheet.getRangeByName('C1').setText('Temp in F');
sheet.getRangeByName('C2').setNumber(93);
sheet.getRangeByName('C3').setNumber(104);
sheet.getRangeByName('C4').setNumber(120);
sheet.getRangeByName('C5').setNumber(80);
sheet.getRangeByName('C6').setNumber(140);

//Create an instances of chart collection.
final ChartCollection charts = ChartCollection(sheet);

// Add the chart.
final Chart chart1 = charts.add();

// Set Chart Type.
chart1.chartType = ExcelChartType.lineStacked;

// Set data range in the worksheet.
chart1.dataRange = sheet.getRangeByName('A1:C6');
chart1.isSeriesInRows = false;

// set charts to worksheet.
sheet.charts = charts;

//save and dispose workbook.
workbook.save('LineStackedChart.xlsx');
workbook.dispose();

{% endhighlight %}
