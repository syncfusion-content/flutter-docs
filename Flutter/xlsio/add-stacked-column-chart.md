---
layout: post
title: Excel Stacked Column Chart of Syncfusion Flutter XlsIO.
description: Learn how to create, add and manipulate the Stacked Column chart in Excel worksheet using Syncfusion Flutter XlsIO. 
platform: flutter
control: Excel
documentation: ug
---

# Adding Stacked Column Chart to Excel worksheet

A stacked column chart is a basic Excel chart type to allow part-to-whole comparisons over time, or across categories and data series are stacked one on top of the other in vertical columns. Stacked column charts can show change over time because it's easy to compare total column lengths.

The following code snippet illustrate how to add Stacked Column chart to Excel worksheet using Flutter XlsIO.

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
final List<int> bytes = workbook.saveSync();
workbook.dispose();

File('ColunmStackedChart.xlsx').writeAsBytes(bytes);

{% endhighlight %}
