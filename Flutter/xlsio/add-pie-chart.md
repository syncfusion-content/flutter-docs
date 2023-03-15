---
layout: post
title: Excel Pie Chart of Syncfusion Flutter XlsIO.
description: Learn how to create, add and manipulate the pie chart in Excel worksheet using Syncfusion Flutter XlsIO. 
platform: flutter
control: Excel
documentation: ug
---

# Adding Pie Chart to Excel worksheet

A pie chart is a circular statistical graphic, which is divided into slices to illustrate numerical proportion of data in the Excel worksheet.

The following code snippet illustrate how to add pie chart to Excel worksheet using Flutter XlsIO.

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
final List<int> bytes = workbook.saveSync();
workbook.dispose();

File('PieChart.xlsx').writeAsBytes(bytes);

{% endhighlight %}