---
layout: post
title: Excel Tables Syncfusion Flutter XlsIO
description: In this section, learn various features of Excel tables like creating, formatting, and removing an Excel table using Syncfusion Flutter XlsIO.
platform: flutter
control: Excel
documentation: ug
---

# Working with Excel Tables

Excel tables helps to organize and analyze data, and Flutter XlsIO supports creating and manipulating these tables.

## Creating a Table

The following code snippet explains how to create a simple table from scratch.

{% highlight dart %}
//Create a new Excel Document.
final Workbook workbook = Workbook(1);

//Access the sheet via index.
final Worksheet sheet = workbook.worksheets[0];

//Insert data into the sheet.
sheet.getRangeByName('A1').setText('Fruits');
sheet.getRangeByName('A2').setText('banana');
sheet.getRangeByName('A3').setText('Cherry');
sheet.getRangeByName('A4').setText('Banana');

sheet.getRangeByName('B1').setText('CostA');
sheet.getRangeByName('B2').setNumber(744.6);
sheet.getRangeByName('B3').setNumber(5079.6);
sheet.getRangeByName('B4').setNumber(1267.5);

sheet.getRangeByName('C1').setText('CostB');
sheet.getRangeByName('C2').setNumber(162.56);
sheet.getRangeByName('C3').setNumber(1249.2);
sheet.getRangeByName('C4').setNumber(1062.5);

//Create a table with the data in given range.
sheet.tableCollection.create('Table1',  sheet.getRangeByName('A1:C4'));

final List<int> bytes = workbook.saveAsStream();
saveAsExcel(bytes, 'Table.xlsx');
workbook.dispose();
{% endhighlight %}

## Built-In Table Styles

You can apply the built in table styles available in Microsoft Excel, through **ExcelTableBuiltInStyle** enum of Flutter XlsIO. The following code snippet illustrates this.

{% highlight dart %}
//Create a new Excel Document.
final Workbook workbook = Workbook(1);

//Access the sheet via index.
final Worksheet sheet = workbook.worksheets[0];

//Insert data into the sheet.
sheet.getRangeByName('A1').setText('Fruits');
sheet.getRangeByName('A2').setText('banana');
sheet.getRangeByName('A3').setText('Cherry');
sheet.getRangeByName('A4').setText('Banana');

sheet.getRangeByName('B1').setText('CostA');
sheet.getRangeByName('B2').setNumber(744.6);
sheet.getRangeByName('B3').setNumber(5079.6);
sheet.getRangeByName('B4').setNumber(1267.5);

sheet.getRangeByName('C1').setText('CostB');
sheet.getRangeByName('C2').setNumber(162.56);
sheet.getRangeByName('C3').setNumber(1249.2);
sheet.getRangeByName('C4').setNumber(1062.5);

//Create a table with the data in given range.
final ExcelTable table = sheet.tableCollection.create('Table1',  sheet.getRangeByName('A1:C4'));

//Format the table with a built-in style.
table.builtInTableStyle = ExcelTableBuiltInStyle.tableStyleDark10;

final List<int> bytes = workbook.saveAsStream();
saveAsExcel(bytes, 'BuiltInStyle.xlsx');
workbook.dispose();
{% endhighlight %}

## Table Style Options

You can customize a table with other table style options such as first column, last column, header row, total row, banded row, and banded column. The following code snippet illustrates the usage. 

### Show First Column

Enabling the **ShowFirstColumn** property applies default format to first column in the table. Its default value is FALSE.

{% highlight dart %}
//Gets or sets a Boolean value indicating whether first column format is present.
table.showFirstColumn = true;
{% endhighlight %}

### Show Last Column

Enabling the **ShowLastColumn** property applies default format to last column in the table. Its default value is FALSE.

{% highlight dart %}
//Gets or sets a Boolean value indicating whether last column format is present.
table.showLastColumn = true;
{% endhighlight %}

### Show Header Row

Disabling the **ShowHeaderRow** property hides the header row of the table. Its default value is TRUE.

{% highlight dart %}
//Gets or sets a Boolean value indicating whether to hide/display header row.
table.showHeaderRow = false;
{% endhighlight %}

### Show Total Row

Enabling the **ShowTotalRow** property shows the total row of the table. Its default value is FALSE.

{% highlight dart %}
//Gets or sets a Boolean value indicating whether to hide/display total row.
table.showTotalRow = true;
{% endhighlight %}

### Show Banded Rows

Disabling the **ShowBandedRows** property removes the row stripes for table rows. Its default value is TRUE.

{% highlight dart %}
//Gets or sets a Boolean value indicating whether row stripes should be present.
table.showBandedRows = false;
{% endhighlight %}

### Show Banded Columns

Enabling the **ShowBandedColumns** property adds the column stripes for table columns. Its default value is FALSE.

{% highlight dart %}
//Gets or sets a Boolean value indicating whether column stripes should be present.
table.showBandedColumns = true;
{% endhighlight %}

## Removing a Table

You can remove the table from Excel document in two ways. They are 

* using table object
* using specific index

The following code snippet illustrates how to remove a table from an Excel document using the table object.

{% highlight dart %}
//Create a new Excel Document.
final Workbook workbook = Workbook(1);

//Access the sheet via index.
final Worksheet sheet = workbook.worksheets[0];

//Insert data into the sheet.
sheet.getRangeByName('A1').setText('Fruits');
sheet.getRangeByName('A2').setText('banana');
sheet.getRangeByName('A3').setText('Cherry');
sheet.getRangeByName('A4').setText('Banana');

sheet.getRangeByName('B1').setText('CostA');
sheet.getRangeByName('B2').setNumber(744.6);
sheet.getRangeByName('B3').setNumber(5079.6);
sheet.getRangeByName('B4').setNumber(1267.5);

sheet.getRangeByName('C1').setText('CostB');
sheet.getRangeByName('C2').setNumber(162.56);
sheet.getRangeByName('C3').setNumber(1249.2);
sheet.getRangeByName('C4').setNumber(1062.5);
 
sheet.getRangeByName('F1').setText('Vegetables');
sheet.getRangeByName('F2').setText('Egg Plant');
sheet.getRangeByName('F3').setText(Lettuce);
sheet.getRangeByName('F4').setText('Tomato');

sheet.getRangeByName('G1').setText('CostA1');
sheet.getRangeByName('G2').setNumber(744.6);
sheet.getRangeByName('G3').setNumber(5079.6);
sheet.getRangeByName('G4').setNumber(1267.5);

sheet.getRangeByName('H1').setText('CostB1');
sheet.getRangeByName('H2').setNumber(162.56);
sheet.getRangeByName('H3').setNumber(1249.2);
sheet.getRangeByName('H4').setNumber(1062.5);

//Create tables with the data in given range.
final ExcelTable table1 = sheet.tableCollection.create('Table1',  sheet.getRangeByName('A1:C4'));
final ExcelTable table2 = sheet.tableCollection.create('Table2',  sheet.getRangeByName('F1:H4'));

//Remove a table from the worksheet.
sheet.tableCollection.remove(table1);

final List<int> bytes = workbook.saveAsStream();
saveAsExcel(bytes, 'RemoveTable.xlsx');
workbook.dispose();
{% endhighlight %}

The following code snippet illustrates how to remove a table from an Excel document using a specific index.

{% highlight dart %}
//Create a new Excel Document.
final Workbook workbook = Workbook(1);

//Access the sheet via index.
final Worksheet sheet = workbook.worksheets[0];

//Insert data into the sheet.
sheet.getRangeByName('A1').setText('Fruits');
sheet.getRangeByName('A2').setText('banana');
sheet.getRangeByName('A3').setText('Cherry');
sheet.getRangeByName('A4').setText('Banana');

sheet.getRangeByName('B1').setText('CostA');
sheet.getRangeByName('B2').setNumber(744.6);
sheet.getRangeByName('B3').setNumber(5079.6);
sheet.getRangeByName('B4').setNumber(1267.5);

sheet.getRangeByName('C1').setText('CostB');
sheet.getRangeByName('C2').setNumber(162.56);
sheet.getRangeByName('C3').setNumber(1249.2);
sheet.getRangeByName('C4').setNumber(1062.5);
 
sheet.getRangeByName('F1').setText('Vegetables');
sheet.getRangeByName('F2').setText('Egg Plant');
sheet.getRangeByName('F3').setText(Lettuce);
sheet.getRangeByName('F4').setText('Tomato');

sheet.getRangeByName('G1').setText('CostA1');
sheet.getRangeByName('G2').setNumber(744.6);
sheet.getRangeByName('G3').setNumber(5079.6);
sheet.getRangeByName('G4').setNumber(1267.5);

sheet.getRangeByName('H1').setText('CostB1');
sheet.getRangeByName('H2').setNumber(162.56);
sheet.getRangeByName('H3').setNumber(1249.2);
sheet.getRangeByName('H4').setNumber(1062.5);

sheet.getRangeByName('D6').setText('Product A');
sheet.getRangeByName('D7').setText('shirt');
sheet.getRangeByName('D8').setText('bags');
sheet.getRangeByName('D9').setText('Trousers');

sheet.getRangeByName('E6').setText('Cost1');
sheet.getRangeByName('E7').setNumber(654);
sheet.getRangeByName('E8').setNumber(745);
sheet.getRangeByName('E9').setNumber(187);
sheet.getRangeByName('F6').setText('Cost2');
sheet.getRangeByName('F7').setNumber(967);
sheet.getRangeByName('F8').setNumber(543);
sheet.getRangeByName('F9').setNumber(864);

//Create tables with the data in given range.
final ExcelTable table1 = sheet.tableCollection.create('Table1',  sheet.getRangeByName('A1:C4'));
final ExcelTable table2 = sheet.tableCollection.create('Table2',  sheet.getRangeByName('F1:H4'));

//Remove a table from the worksheet at the specified index.
sheet.tableCollection.removeAt(1);

final List<int> bytes = workbook.saveAsStream();
saveAsExcel(bytes, 'RemoveTable.xlsx');
workbook.dispose();
{% endhighlight %}
