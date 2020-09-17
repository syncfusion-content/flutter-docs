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

import 'package:syncfusion_flutter_office_core/office_core.dart';

{% endhighlight %}

## Creating a Chart

The **Chart** represents the chart in a worksheet. A chart can be created entering by values one by one.

The following code example illustrates how to create a chart.

{% highlight dart %}

//Create a new Excel document.
Workbook workbook = new Workbook();

//Accessing worksheet via index.
Worksheet sheet = workbook.worksheets[0];

//Setting value in the cell.
sheet.getRangeByName('A1').text = "John";
sheet.getRangeByName('A2').text = "Amy";
sheet.getRangeByName('A3').text = "Jack";
sheet.getRangeByName('A4').text = "Tiya";
sheet.getRangeByName('B1').number = 10;
sheet.getRangeByName('B2').number = 12;
sheet.getRangeByName('B3').number = 20;
sheet.getRangeByName('B4').number = 21;

//Create a Chart.
Chart chart = sheet.charts.add();

//Set Chart Type.
chart.chartType = ExcelChartType.Column;

//Set data range in the worksheet.
chart.dataRange = sheet.getRangeByName("A1:B4");
 
//Save the document.
workbook.save("Charts.xlsx");

//Dispose the workbook.
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

//Create a new Excel document.
Workbook workbook = new Workbook();

//Accessing worksheet via index.
Worksheet sheet = workbook.worksheets[0];

sheet.getRangeByName("A1").text = "Months";
sheet.getRangeByName("B1").text = "Internal Sales Amount";
sheet.getRangeByName("C1").text = "Reseller Sales Amount";
sheet.getRangeByName("A2").setDateTime(DateTime(2014, 01, 14, 14, 14, 14));
sheet.getRangeByName("A3").setDateTime(DateTime(2014, 02, 14, 14, 14, 14));
sheet.getRangeByName("A4").setDateTime(DateTime(2014, 03, 14, 14, 14, 14));
sheet.getRangeByName("A5").setDateTime(DateTime(2014, 04, 14, 14, 14, 14));
sheet.getRangeByName("A6").setDateTime(DateTime(2014, 05, 14, 14, 14, 14));

sheet.getRangeByName("B2").number = 700;
sheet.getRangeByName("B3").number = 200;
sheet.getRangeByName("B4").number = 300;
sheet.getRangeByName("B5").number = 500;
sheet.getRangeByName("B6").number = 800;

sheet.getRangeByName("C2").number = 30;
sheet.getRangeByName("C3").number = 40;
sheet.getRangeByName("C4").number = 70;
sheet.getRangeByName("C5").number = 2;
sheet.getRangeByName("C6").number = 100;

Chart chart = sheet.charts.add();
chart.chartType = ExcelChartType.Line;
chart.dataRange = sheet.getRangeByName("A1:C6");
chart.isSeriesInRows = false;

//setting chart tile with font properties
chart.ChartTitle = "Yearly sales";
chart.ChartTitleArea.Bold = true;
chart.ChartTitleArea.Size = 12;

//setting legend position.
chart.Legend.Position = ExcelLegendPosition.Bottom;

//setting the chart position.
chart.topRow = 0;
chart.bottomRow = 20;
chart.leftColumn = 1;
chart.rightColumn = 8;

//setting Axis number format.
chart.primaryCategoryAxis.numberFormat = "mmmm";
chart.primaryValueAxis.numberFormat = '0.00';

//setting datalabels
ChartSerie serie = chart.series[0];
serie.dataLabels.IsValue = true;
serie.dataLabels.isCategoryName = true;
serie.dataLabels.isSeriesName = true;
serie.dataLabels.textArea.Bold = true;
serie.dataLabels.textArea.Size = 12;
serie.dataLabels.textArea.FontName = "Arial";

//save and dispose workbook.
workbook.save('ChartElement.xlsx');
workbook.dispose();

{% endhighlight %}

## Adding Pie Chart

The following code snippet illustrate how to add pie chart

{% highlight dart %}

//Create a new Excel document.
Workbook workbook = new Workbook();

//Accessing worksheet via index.
Worksheet sheet = workbook.worksheets[0];

//Setting value in the cell.
sheet.getRangeByName("A1").text = "Expenses";
sheet.getRangeByName("A2").text = "Washing";
sheet.getRangeByName("A3").text = "Cleaning";
sheet.getRangeByName("A4").text = "Decoration";
sheet.getRangeByName("A5").text = "Travel";
sheet.getRangeByName("A6").text = "Food";
sheet.getRangeByName("A7").text = "Maintance";
sheet.getRangeByName("B11:B17").numberFormat = '\$#,##0_)';
sheet.getRangeByName("B1").text = "Amount";
sheet.getRangeByName("B2").number = 1828;
sheet.getRangeByName("B3").number = 800;
sheet.getRangeByName("B4").number = 14000;
sheet.getRangeByName("B5").number = 2600;
sheet.getRangeByName("B6").number = 4464;
sheet.getRangeByName("B7").number = 2700;

  
//Create a Chart.
Chart chart = sheet.charts.add();

//set chart Type.
chart.chartType = ExcelChartType.Pie;

//Set Data Range in worksheet.
chart.dataRange = sheet.getRangeByName("A2:B7");
chart.isSeriesInRows = false;

//Set Chart title.
chart.ChartTitle = "Monthly Expenses";
chart.ChartTitleArea.Bold = true;
chart.ChartTitleArea.Size = 12;

//Positioning chart in the worksheet.
chart.topRow = 0;
chart.bottomRow = 10;
chart.leftColumn = 0;
chart.rightColumn = 7;

//Save workbook.
workbook.save("PieChart.xlsx");

//Dispose workbook
workbook.dispose();

{% endhighlight %}

## Adding bar chart

The following code snippet illustrate how to add bar chart

{% highlight dart %}

//Create a new Excel document.
Workbook workbook = new Workbook();

//Accessing worksheet via index.
Worksheet sheet = workbook.worksheets[0];

//Setting value in the cell.
sheet.getRangeByName("A1").text = "Items";
sheet.getRangeByName("B1").text = "Amount(in \$)";
sheet.getRangeByName("C1").text = "Count";

sheet.getRangeByName("A2").text = "Beverages";
sheet.getRangeByName("A3").text = "Condiments";
sheet.getRangeByName("A4").text = "Confections";
sheet.getRangeByName("A5").text = "Dairy Products";
sheet.getRangeByName("A6").text = "Grains / Cereals";

sheet.getRangeByName("B2").number = 2776;
sheet.getRangeByName("B3").number = 1077;
sheet.getRangeByName("B4").number = 2287;
sheet.getRangeByName("B5").number = 1368;
sheet.getRangeByName("B6").number = 3325;

sheet.getRangeByName("C2").number = 925;
sheet.getRangeByName("C3").number = 378;
sheet.getRangeByName("C4").number = 880;
sheet.getRangeByName("C5").number = 581;
sheet.getRangeByName("C6").number = 189;

//Create a Chart.
Chart chart = sheet.charts.add();

//Set Chart type.
chart.chartType = ExcelChartType.Bar;

//Set DataRange.  
chart.dataRange = sheet.getRangeByName("A1:C6");
  
//save and dispose workbook.
workbook.save("BarChart.xlsx");
workbook.dispose();

{% endhighlight %}

## Adding Column Chart

The following code snippet illustrate how to add column chart.

{% highlight dart %}

//Create a new Excel document.
Workbook workbook = new Workbook();

//Accessing worksheet via index.
Worksheet sheet = workbook.worksheets[0];

//Setting value in the cell.
sheet.getRangeByName("A1").text = "Expense";
sheet.getRangeByName("A2").text = "Seating & Decor";
sheet.getRangeByName("A3").text = "Technical Team";
sheet.getRangeByName("A4").text = "performers";
sheet.getRangeByName("B2").number = 1828;
sheet.getRangeByName("B3").number = 800;
sheet.getRangeByName("B4").number = 1400;

//Create a Chart.
Chart chart = sheet.charts.add();

//Set Chart Type.
chart.chartType = ExcelChartType.Column;

//Set data range in the worksheet.
chart.dataRange = sheet.getRangeByName("A1:B4");
chart.isSeriesInRows = false;

//save and dispose workbook.
workbook.save('ColumnChart.xlsx');
workbook.dispose();

{% endhighlight %}

## Adding line chart

The following code snippet illustrate how to add line chart.

{% highlight dart %}

//Create a new Excel document.
Workbook workbook = new Workbook();

//Accessing worksheet via index.
Worksheet sheet = workbook.worksheets[0];

//Setting value in the cell.
sheet.getRangeByName("A1").text = "City Name";
sheet.getRangeByName("A2").text = "Chennai";
sheet.getRangeByName("A3").text = "Mumbai";
sheet.getRangeByName("A4").text = "Delhi";
sheet.getRangeByName("A5").text = "Hyderabad";
sheet.getRangeByName("A6").text = "Kolkata";
sheet.getRangeByName("B1").text = "Temp in C";
sheet.getRangeByName("B2").number = 34;
sheet.getRangeByName("B3").number = 40;
sheet.getRangeByName("B4").number = 47;
sheet.getRangeByName("B5").number = 20;
sheet.getRangeByName("B6").number = 66;

//Create a Chart.
Chart chart = sheet.charts.add();

//Set Chart Type.
chart.chartType = ExcelChartType.Line;

//Set data range in the worksheet.
chart.dataRange = sheet.getRangeByName("A1:B6");
chart.isSeriesInRows = false;

//save and dispose workbook.
workbook.save('LineChart.xlsx');
workbook.dispose();

{% endhighlight %}

## Adding stacked Column chart

The following code snippet illustrate how to add stacked column chart.


{% highlight dart %}
//Create a new Excel document.
Workbook workbook = new Workbook();

//Accessing worksheet via index.
Worksheet sheet = workbook.worksheets[0];

//Setting value in the cell.
sheet.getRangeByName("A1").text = "Items";
sheet.getRangeByName("B1").text = "Amount(in \$)";
sheet.getRangeByName("C1").text = "Count";

sheet.getRangeByName("A2").text = "Beverages";
sheet.getRangeByName("A3").text = "Condiments";
sheet.getRangeByName("A4").text = "Confections";
sheet.getRangeByName("A5").text = "Dairy Products";
heet.getRangeByName("A6").text = "Grains / Cereals";

sheet.getRangeByName("B2").number = 2776;
sheet.getRangeByName("B3").number = 1077;
sheet.getRangeByName("B4").number = 2287;
sheet.getRangeByName("B5").number = 1368;
sheet.getRangeByName("B6").number = 3325;

sheet.getRangeByName("C2").number = 925;
sheet.getRangeByName("C3").number = 378;
sheet.getRangeByName("C4").number = 880;
sheet.getRangeByName("C5").number = 581;
sheet.getRangeByName("C6").number = 189;

//Create a Chart.
Chart chart1 = sheet.charts.add();

//Set Chart Type.
chart1.chartType = ExcelChartType.ColumnStacked;

//Set data range in the worksheet.
chart1.dataRange = sheet.getRangeByName("A1:C6");
chart1.isSeriesInRows = false;

//save and dispose workbook.
workbook.save('ColunmStackedChart.xlsx');
workbook.dispose();

{% endhighlight %}

## Adding stacked bar chart

The following code snippet illustrate how to add stacked bar chart.

{% highlight dart %}

//Create a new Excel document.
Workbook workbook = new Workbook();

//Accessing worksheet via index.
Worksheet sheet = workbook.worksheets[0];

//Setting value in the cell.
sheet.getRangeByName("A1").text = "Name";
sheet.getRangeByName("B1").text = "Salary";
sheet.getRangeByName("C1").text = "Working hr";

sheet.getRangeByName("A2").text = "Ben";
sheet.getRangeByName("A3").text = "Mark";
sheet.getRangeByName("A4").text = "Sundar";
sheet.getRangeByName("A5").text = "Geo";
sheet.getRangeByName("A6").text = "Andrew";

sheet.getRangeByName("B2").number = 1000;
sheet.getRangeByName("B3").number = 2000;
sheet.getRangeByName("B4").number = 2392;
sheet.getRangeByName("B5").number = 3211;
sheet.getRangeByName("B6").number = 4211;

sheet.getRangeByName("C2").number = 287;
sheet.getRangeByName("C3").number = 355;
sheet.getRangeByName("C4").number = 134;
sheet.getRangeByName("C5").number = 581;
sheet.getRangeByName("C6").number = 426;

//Create a Chart.
Chart chart1 = sheet.charts.add();

//Set Chart Type.
chart1.chartType = ExcelChartType.BarStacked;

//Set data range in the worksheet.
chart1.dataRange = sheet.getRangeByName("A1:C6");
chart1.isSeriesInRows = false;

//save and dispose workbook.
workbook.save('BarStackedChart.xlsx');
workbook.dispose();

{% endhighlight %}


## Added stacked line chart

The following code snippet illustrate how to add stacked Line chart.

{% highlight dart %}

//Create a new Excel document.
Workbook workbook = new Workbook();

//Accessing worksheet via index.
Worksheet sheet = workbook.worksheets[0];

//Setting value in the cell.
sheet.getRangeByName("A1").text = "City Name";
sheet.getRangeByName("A2").text = "Chennai";
sheet.getRangeByName("A3").text = "Mumbai";
sheet.getRangeByName("A4").text = "Delhi";
sheet.getRangeByName("A5").text = "Hyderabad";
sheet.getRangeByName("A6").text = "Kolkata";
sheet.getRangeByName("B1").text = "Temp in C";
sheet.getRangeByName("B2").number = 34;
sheet.getRangeByName("B3").number = 40;
sheet.getRangeByName("B4").number = 47;
sheet.getRangeByName("B5").number = 20;
sheet.getRangeByName("B6").number = 66;
sheet.getRangeByName("C1").text = "Temp in F";
sheet.getRangeByName("C2").number = 93;
sheet.getRangeByName("C3").number = 104;
sheet.getRangeByName("C4").number = 120;
sheet.getRangeByName("C5").number = 80;
sheet.getRangeByName("C6").number = 140;

//Create a Chart.
Chart chart = sheet.charts.add();

//Set Chart Type.
chart.chartType = ExcelChartType.LineStacked;

//Set data range in the worksheet.
chart.dataRange = sheet.getRangeByName("A1:C6");
chart.isSeriesInRows = false;

//save and dispose workbook.
workbook.save('LineStackedChart.xlsx');
workbook.dispose();

{% endhighlight %}
