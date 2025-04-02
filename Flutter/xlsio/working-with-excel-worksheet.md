---
layout: post
title: Excel worksheet of Syncfusion Flutter XlsIO.
description: Learn how to create and access a worksheet of workbook and manipulating the worksheet using Syncfusion Flutter XlsIO. 
platform: flutter
control: Excel
documentation: ug
---

# Working with Excel Worksheets

A Workbook contains a collection of worksheets where the actual contents reside and Worksheet instance represents a worksheet. With Flutter XlsIO, you can add and manipulate worksheets.

## Create a Worksheet

You can add a new worksheet into the Workbook through instances of workbook. You can also specify the required number of worksheets, if not specified, Flutter XlsIO will create one worksheet by default.

The following code snippet shows how to create worksheets within a workbook.

{% highlight dart %}

// The new workbook will have 4 worksheets.
final Workbook workbook = Workbook(4);

// Creating a Sheet.
final Worksheet sheet = Worksheet(workbook);
workbook.worksheets.addWithSheet(sheet);

//Creating a Sheet with name “Sample”.
final Worksheet sheet1 = workbook.worksheets.addWithName('Sample');

// Add worksheet to the collection.
final Worksheet sheet2 = workbook.worksheets.add();

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();

File('Output.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Access a Worksheet

Worksheets collection holds one or more worksheets present in a workbook. Accessing a particular worksheet can be done by the following ways.

1. Specifying the index
2. Specifying the sheet name.

The below codes illustrate how to access a worksheet from its worksheets collection.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();
workbook.worksheets.addWithName('sample');

// Accessing via index. 
final Worksheet sheet = workbook.worksheets[0]; 

//Accessing via sheet Name. 
final Worksheet namedSheet = workbook.worksheets['Sample'];

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();

File('Output.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Worksheet Tab Color

A worksheet can be highlighted with a tab color. Tab color can be set through the **tabColor** property, as shown below.

{% highlight dart %}

//Create a new Excel Document.
final Workbook workbook = Workbook(2);

//Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[1];
sheet.getRangeByName('A1:M10').setText('TabColor');

//Applied tab color for worksheet.
sheet.tabColor = '#0000FF';

final List<int> bytes = workbook.saveSync();
File('Output.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %} 

## View Settings

**Show or Hide Grid Lines**

The following code snippet shows how to hide the grid lines using **showGridLines** property.

{% highlight dart %}

//Create a new Excel Document.
final Workbook workbook = Workbook();

//Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

//Hide grid line.
sheet.showGridlines = false;

//Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();

File('Output.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## PageSetup Settings

Excel worksheets can be customized with page setup settings such as orientation, margins, scaling, paper size, print area, gridlines, black and white, draft quality, row and column headings, and page order. The following code snippet shows how to use page setup properties.

{% highlight dart %}
//Create a new Excel Document.
final Workbook workbook = Workbook();

//Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

//Set text
sheet.getRangeByName('A1:Z100').text = 'Hello';

//Center Horizontally and center Vertically
sheet.pageSetup.isCenterHorizontally = true;
sheet.pageSetup.isCenterVertically = true;

//Orientation
sheet.pageSetup.orientation = ExcelPageOrientation.landscape;

//Margins
sheet.pageSetup.topMargin = 1;
sheet.pageSetup.leftMargin = 2;
sheet.pageSetup.rightMargin = 1.25;
sheet.pageSetup.bottomMargin = 1;
sheet.pageSetup.footerMargin = 4;
sheet.pageSetup.headerMargin = 3.5;

//Paper size
sheet.pageSetup.paperSize = ExcelPaperSize.a2Paper;

//Print area
sheet.pageSetup.printArea = 'A1:D20';

//Gridlines
sheet.pageSetup.showGridlines = true;

//Black and white
sheet.pageSetup.isBlackAndWhite = true;

//Draft
sheet.pageSetup.isDraft = true;

//Row and column headings
sheet.pageSetup.showHeadings = true;

//Page order
sheet.pageSetup.order = ExcelPageOrder.overThenDown;

//Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();
File('Output.xlsx').writeAsBytes(bytes);
{% endhighlight %}

## Show or Hide Worksheet

The following code snippet shows how to hide the worksheet using **visibility** property.

{% highlight dart %}

//Create a new Excel Document.
final Workbook workbook = Workbook(10);

//Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[2];
sheet.getRangeByName('A1:M10').setText('Visibility');

//set the visibility for the worksheet.
sheet.visibility = WorksheetVisibility.hidden;

final List<int> bytes = workbook.saveSync();
File('Output.xlsx').writeAsBytes(bytes);
workbook.dispose();

{% endhighlight %}

## Adjust Row Height and Column Width

**Resize a range of rows or columns**

Single/Multiple rows or columns can be resized and accessed by using the **rowHeight** and **columnWidth** properties of **Range**. The following code snippet shows how to resize single/multiple rows and columns.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Modifying the row height for single and multiple range.
sheet.getRangeByName('A1').rowHeight = 10;
sheet.getRangeByName('A2:A5').rowHeight = 20;

// Modifying the columnWidth for single and multiple range.
sheet.getRangeByName('A1').columnWidth = 20;
sheet.getRangeByName('A2:A5').columnWidth = 30;

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();

File('Output.xlsx').writeAsBytes(bytes);

{% endhighlight %}

Single row and column can also be resized using **SetRowHeightInPixels** and **SetColumnWidthInPixels** properties of **Worksheet**. The following code snippet explains this.

{% highlight dart %}

// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Modifying the row height for single range.
sheet.setRowHeightInPixels(2, 30);

// Modifying the column width for single range.
sheet.setColumnWidthInPixels(2, 20);

// Save and dispose workbook.
final List<int> bytes = workbook.saveSync();
workbook.dispose();

File('Output.xlsx').writeAsBytes(bytes);

{% endhighlight %}

## Move a Worksheet

XlsIO allows moving worksheets from one position to another by using the *moveTo* method. The following code example illustrates this.

{% highlight dart %}
//Create a new Excel Document.
final Workbook workbook = Workbook(20);

//Access worksheets
final Worksheet sheet = workbook.worksheets[10];
final Worksheet sheet1 = workbook.worksheets[3];

sheet.getRangeByName('A1:B10').text = 'Moving Sheet';
sheet1.getRangeByName('A1:B20').dateTime = DateTime(2006, 9, 10);
sheet.hyperlinks.add(sheet.getRangeByName('C1:C5'), HyperlinkType.url, 'http://www.gmail.com');

//Move worksheet
workbook.worksheets.moveTo(workbook.worksheets[10], 5);
workbook.worksheets.moveTo(workbook.worksheets[3], 15);

//save and dispose.
final List<int> bytes = workbook.saveSync();
File('Output.xlsx').writeAsBytes(bytes);
workbook.dispose();
{% endhighlight %}

## Freeze Panes

A portion of the worksheet can be frozen to keep it visible while scrolling through the rest of the sheet. The following code snippet shows how to create freeze panes.

{% highlight dart %}
//Create a new Excel Document.
final Workbook workbook = Workbook(1);

//Access worksheet
final Worksheet worksheet = workbook.worksheets[0];

//Set text
worksheet.getRangeByName('A1:H10').text = 'FreezePanes';

//Freeze Panes
worksheet.getRangeByName('A2').freezePanes();

//save and dispose.
final List<int> bytes = workbook.saveSync();
File('Output.xlsx').writeAsBytes(bytes);
workbook.dispose();
{% endhighlight %}

## Unfreeze Panes

The following code snippet explains how to remove freeze panes.

{% highlight dart %}
//Create a new Excel Document.
final Workbook workbook = Workbook(1);

//Access worksheet
final Worksheet worksheet = workbook.worksheets[0];

//Set text
worksheet.getRangeByName('A1:H10').text = 'FreezePanes';

//Freeze Panes
worksheet.getRangeByName('A2').freezePanes();

//Unfreeze the existing freeze panes
worksheet.unfreezePanes();

//save and dispose.
final List<int> bytes = workbook.saveSync();
File('Output.xlsx').writeAsBytes(bytes);
workbook.dispose();
{% endhighlight %}

## Right to Left Direction

A *worksheet* direction can be changed from right to left programmatically through **isRightToLeft** property of **Worksheet**. The following code snippet explains this.

{% highlight dart %}
//Create a new Excel Document.
final Workbook workbook = Workbook(1);

//Access the sheet via index.
final Worksheet sheet = workbook.worksheets[0];

//Display the worksheet in Right-To-Left direction.
sheet.isRightToLeft = true;

//Add the text using setText() method.
sheet.getRangeByName('A1').setText('Hello World');

//Save and dispose the workbook.
final List<int>? bytes = workbook.saveSync();
File('output.xlsx').writeAsBytes(bytes!);
workbook.dispose();
{% endhighlight %}

It is also possible to change the direction of entire *workbook* from right to left through **isRightToLeft** property of **Workbook**. The following code snippet explains this.

{% highlight dart %}
//Create a new Excel Document.
final Workbook workbook = Workbook(2);

//Access the sheets via index.
final Worksheet sheet1 = workbook.worksheets[0];
final Worksheet sheet2 = workbook.worksheets[1];

//Display the workbook in Right-To-Left direction.
workbook.isRightToLeft = true;

//Add the text using setText() method.
sheet1.getRangeByName('A1').setText('Hello World');
sheet2.getRangeByName('A1').setText('Hello World');

// Save and dispose the workbook.
final List<int>? bytes = workbook.saveSync();
File('Output.xlsx').writeAsBytes(bytes!);
workbook.dispose();
{% endhighlight %}

## Save as CSV

A worksheet data with text, date time, and numbers with number formatting can be exported to CSV format. This feature also allows exporting the data to CSV format with custom separators instead of the default comma separator.

{% highlight dart %}
//Create a new Excel Document.
final Workbook workbook = Workbook();

//Access the sheets via index.
final Worksheet worksheet = workbook.worksheets[0];

//Rename the worksheet.
worksheet.name = 'csv format';

worksheet.showGridlines = false;
worksheet.enableSheetCalculations();

//Set text
worksheet.getRangeByName('A1').setText('Date');
worksheet.getRangeByName('B1').setText('Region');
worksheet.getRangeByName('C1').setText('Employee');
worksheet.getRangeByName('D1').setText('Item');
worksheet.getRangeByName('E1').setText('Units');
worksheet.getRangeByName('F1').setText('Unit Cost');
worksheet.getRangeByName('G1').setText('Total');

//Set date time
worksheet.getRangeByName('A2').setDateTime(DateTime(2007, 12, 15));
worksheet.getRangeByName('A3').setDateTime(DateTime(2007, 12, 18));
worksheet.getRangeByName('A4').setDateTime(DateTime(2007, 12, 21));
worksheet.getRangeByName('A5').setDateTime(DateTime(2007, 12, 24));
worksheet.getRangeByName('A6').setDateTime(DateTime(2007, 12, 27));
worksheet.getRangeByName('A7').setDateTime(DateTime(2007, 12, 30));
worksheet.getRangeByName('A8').setDateTime(DateTime(2008, 1, 2));

//Set text
worksheet.getRangeByName('B2').setText('Central');
worksheet.getRangeByName('B3').setText('Wast');
worksheet.getRangeByName('B4').setText('Central');
worksheet.getRangeByName('B5').setText('East');
worksheet.getRangeByName('B6').setText('East');
worksheet.getRangeByName('B7').setText('East');
worksheet.getRangeByName('B8').setText('East');

//Set text
worksheet.getRangeByName('C2').setText('Jones');
worksheet.getRangeByName('C3').setText('Kivell');
worksheet.getRangeByName('C4').setText('Howard');
worksheet.getRangeByName('C5').setText('Gill');
worksheet.getRangeByName('C6').setText('Anderson');
worksheet.getRangeByName('C7').setText('Anderson');
worksheet.getRangeByName('C8').setText('Anderson');

//Set text
worksheet.getRangeByName('D2').setText('Pen Set');
worksheet.getRangeByName('D3').setText('Binder');
worksheet.getRangeByName('D4').setText('Pen & Pencil');
worksheet.getRangeByName('D5').setText('Pen');
worksheet.getRangeByName('D6').setText('Binder');
worksheet.getRangeByName('D7').setText('Pen Set');
worksheet.getRangeByName('D8').setText('Pen Set');

//Set number
worksheet.getRangeByName('E2').number = 700;
worksheet.getRangeByName('E3').number = 85;
worksheet.getRangeByName('E4').number = 62;
worksheet.getRangeByName('E5').number = 58;
worksheet.getRangeByName('E6').number = 10;
worksheet.getRangeByName('E7').number = 19;
worksheet.getRangeByName('E8').number = 6;

//Set number
worksheet.getRangeByName('F2').number = 1.99;
worksheet.getRangeByName('F3').number = 19.99;
worksheet.getRangeByName('F4').number = 4.99;
worksheet.getRangeByName('F5').number = 19.99;
worksheet.getRangeByName('F6').number = 4.99;
worksheet.getRangeByName('F7').number = 2.99;
worksheet.getRangeByName('F8').number = 1.99;

//Set number format
worksheet.getRangeByName('F2:F8').numberFormat = r"'$'#,##0.00";

//Set formula
worksheet.getRangeByName('G2').formula = 'E2*F2';
worksheet.getRangeByName('G3').formula = 'E3*F3';
worksheet.getRangeByName('G4').formula = 'E4*F4';
worksheet.getRangeByName('G5').formula = 'E5*F5';
worksheet.getRangeByName('G6').formula = 'E6*F6';
worksheet.getRangeByName('G7').formula = 'E7*F7';
worksheet.getRangeByName('G8').formula = 'E8*F8';

//Set number format
worksheet.getRangeByName('G2:G8').numberFormat = r"'$'#,##0_)";

//Save workbook as CSV
final List<int> bytes = workbook.saveAsCSV(',');
File('Output.csv').writeAsBytes(bytes);
workbook.dispose();
{% endhighlight %}

## Named Range

A named range is one or more cells that have been given a name. Using named ranges can make formulas easier to read and understand. This section explains about creating named ranges and accessing them from workbook or worksheet levels.

The following code shows how to define a named range from workbook level. 

{% highlight dart %}
//Create a new Excel Document.
final Workbook workbook = Workbook(1);

//Access the sheet via index.
final Worksheet worksheet = workbook.worksheets[0];

//Access the sheet range.
final Range range = worksheet.getRangeByName('A1:C1'); 

//Define named range in workbook level.
workbook.names.add('BookName', range);

//Save and dispose the workbook.
final List<int>? bytes = workbook.saveSync();
File('Output.xlsx').writeAsBytes(bytes!);
workbook.dispose();
{% endhighlight %}

The following code shows how to define a named range from worksheet level. 

{% highlight dart %}
//Create a new Excel Document.
final Workbook workbook = Workbook(1);

//Access the sheet via index.
final Worksheet worksheet = workbook.worksheets[0];

//Access the sheet range.
final Range range = worksheet.getRangeByName('A1:C1'); 

//Define named range in worksheet level.
worksheet.names.add('SheetName', range);

//Save and dispose the workbook.
final List<int>? bytes = workbook.saveSync();
File('Output.xlsx').writeAsBytes(bytes!);
workbook.dispose();
{% endhighlight %}

### Named range in formulas

Following code example illustrates how to create workbook-level named ranges and use it in formulas. 

{% highlight dart %}
//Create a new Excel Document.
final Workbook workbook = Workbook(1);

//Access the sheet via index.
final Worksheet worksheet = workbook.worksheets[0];

//Set the value to the cell.
worksheet.getRangeByName('A1').setNumber(10);
worksheet.getRangeByName('A2').setNumber(20);

//Access the sheet range and define named range in worksheet level.
final Range range1 = worksheet.getRangeByName('A1'); 
worksheet.names.add('FirstRange', range1);

final Range range2 = worksheet.getRangeByName('A2'); 
worksheet.names.add('SecondRange', range2);

//Set formula in the cell.
worksheet.getRangeByName('A3').formula = '=IF(FirstRange<SecondRange, "Yes", "No")';

//Save and dispose the workbook.
final List<int>? bytes = workbook.saveSync();
File('Output.xlsx').writeAsBytes(bytes!);
workbook.dispose();
{% endhighlight %}

### Delete named range

Named ranges defined in workbook and worksheet levels can be deleted. The following code shows this. 

{% highlight dart %}
//Create a new Excel Document.
final Workbook workbook = Workbook(1);

//Access the sheet via index.
final Worksheet worksheet = workbook.worksheets[0];

//Set text in worksheet range
worksheet.getRangeByName('A1:D4').setText('NamedRange');

//Access the sheet range and define named range in worksheet level.
final Range range1 = worksheet.getRangeByName('A1:C1');
final Name name1 = worksheet.names.add('named1', range1);

final Range range2 = worksheet.getRangeByName('A2:C2');
final Name name2 = worksheet.names.add('named2', range2);

final Range range3 = worksheet.getRangeByName('A3:C3');
final Name name3 = worksheet.names.add('named3', range3);

final Range range4 = worksheet.getRangeByName('A4:C4');
final Name name4 = worksheet.names.add('named4', range4);

//Delete the named range
name2.delete();

//Save and dispose the workbook.
final List<int>? bytes = workbook.saveSync();
File('Output.xlsx').writeAsBytes(bytes!);
workbook.dispose();
{% endhighlight %}
