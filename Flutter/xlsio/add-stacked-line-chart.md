---
layout: post
title: Excel Stacked Line Chart of Syncfusion Flutter XlsIO.
description: Learn how to create, add and manipulate the Stacked line chart in Excel worksheet using Syncfusion Flutter XlsIO. 
platform: flutter
control: Excel
documentation: ug
---

# Adding Stacked line Chart to Excel worksheet

A stacked line graph is a line graph in which lines don't overlap because they are cumulative at each point. A stacked line graph displays series as a set of points connected by a line. Values are represented on the y-axis and categories are displayed on the x-axis

The following code snippet illustrate how to add Stacked Line chart to Excel worksheet using Flutter XlsIO.

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
final List<int> bytes = workbook.saveSync();
workbook.dispose();

File('LineStackedChart.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Customizing Stacked Line Chart in Excel

The following code illustrates how to customize various elements of a stacked line chart in Excel using Flutter XlsIO.

{% highlight dart %}
// Create a new Excel document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Setting value in the cell.
sheet.getRangeByName('A1').setText('Day');
sheet.getRangeByName('A2').setText('Monday');
sheet.getRangeByName('A3').setText('Tuesday');
sheet.getRangeByName('A4').setText('Wednesday');
sheet.getRangeByName('A5').setText('Thursday');
sheet.getRangeByName('A6').setText('Friday');
sheet.getRangeByName('B1').setText('High Temp');
sheet.getRangeByName('B2').setNumber(34);
sheet.getRangeByName('B3').setNumber(29);
sheet.getRangeByName('B4').setNumber(30);
sheet.getRangeByName('B5').setNumber(32);
sheet.getRangeByName('B6').setNumber(35);
sheet.getRangeByName('C1').setText('Low Temp');
sheet.getRangeByName('C2').setNumber(20);
sheet.getRangeByName('C3').setNumber(22);
sheet.getRangeByName('C4').setNumber(19);
sheet.getRangeByName('C5').setNumber(18);
sheet.getRangeByName('C6').setNumber(21);

//Create an instances of chart collection.
final ChartCollection charts = ChartCollection(sheet);

// Add the chart.
final Chart chart = charts.add();

// Set Chart Type.
chart.chartType = ExcelChartType.lineStacked;

// Set data range in the worksheet.
chart.dataRange = sheet.getRangeByName('A1:C6');
chart.isSeriesInRows = false;

// Set chart title
chart.chartTitle = 'Weekly Weather Summary';
chart.chartTitleArea.bold = true;
chart.chartTitleArea.size = 10;
chart.chartTitleArea.color = "#050505";

// Set data labels
final ChartSerie serie1 = chart.series[0];
serie1.dataLabels.isValue = true;
serie1.dataLabels.textArea.bold = true;
serie1.dataLabels.textArea.size = 10;
serie1.dataLabels.textArea.color = '#920467';
serie1.dataLabels.textArea.fontName = 'Arial';
serie1.linePattern = ExcelChartLinePattern.longDash;
serie1.linePatternColor = '#F40829';

final ChartSerie serie2 = chart.series[1];
serie2.dataLabels.isValue = true;
serie2.dataLabels.textArea.bold = true;
serie2.dataLabels.textArea.size = 10;
serie2.dataLabels.textArea.color = '#920467';
serie2.dataLabels.textArea.fontName = 'Arial';
serie2.linePattern = ExcelChartLinePattern.longDash;
serie2.linePatternColor = '#08A2F4';

// Set legend position
chart.legend!.position = ExcelLegendPosition.right;

// Set line pattern for chart border
chart.linePattern = ExcelChartLinePattern.solid;
chart.linePatternColor = "#2F4F4F";

// Set line pattern for plot area
chart.plotArea.linePattern = ExcelChartLinePattern.dashDot;
chart.plotArea.linePatternColor = '#0000FF';

// Set charts to worksheet.
sheet.charts = charts;

// save and dispose the workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();

File('StackedLineChart.xlsx').writeAsBytes(bytes);
{% endhighlight %}

By executing the above code snippet, you will get the Excel document as follows.
![Customizing Stacked Line Chart](images/StackedLineChart.png)