---
layout: post
title: Excel Stacked Bar Chart of Syncfusion Flutter XlsIO.
description: Learn how to create, add and manipulate the Stacked Bar chart in Excel worksheet using Syncfusion Flutter XlsIO. 
platform: flutter
control: Excel
documentation: ug
---

# Adding Stacked Bar Chart to Excel worksheet

A stacked bar chart is a type of bar chart used in excel for the graphical representation of part-to-whole comparison over time. This helps you to represent data in a stacked manner. This type of graph is suitable for data which is represented in different parts and one as a whole.

The following code snippet illustrate how to add Stacked Bar chart to Excel worksheet using Flutter XlsIO.

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
final List<int> bytes = workbook.saveSync();
workbook.dispose();

File('BarStackedChart.xlsx').writeAsBytes(bytes);

{% endhighlight %}

