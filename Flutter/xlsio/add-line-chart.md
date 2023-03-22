---
layout: post
title: Excel Line Chart of Syncfusion Flutter XlsIO.
description: Learn how to create, add and manipulate the Line chart in Excel worksheet using Syncfusion Flutter XlsIO. 
platform: flutter
control: Excel
documentation: ug
---

# Adding Line Chart to Excel worksheet

A line chart is a type of chart which displays information as a series of data points called 'markers' connected by straight line segments.

The following code snippet illustrate how to add Line chart to Excel worksheet using Flutter XlsIO.

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
final List<int> bytes = workbook.saveSync();
workbook.dispose();

File('LineChart.xlsx').writeAsBytes(bytes);

{% endhighlight %}

