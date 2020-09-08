# Working with Cells

## Adding a Text to Excel worksheet

You can add text to the Excel worksheet using setText method and text property of the Range class.

The following code snippet shows how to add text to Excel worksheet.

{% highlight dart %}

//Create a new Excel Document.
Workbook workbook = new Workbook();

//Accessing sheet via index.
Worksheet sheet = workbook.worksheets[0];

//Adding text using setText() method.
sheet.getRangeByName("A1").setText(“Hello World”);

//Adding text using text property.
sheet.getRangeByName(“A2”).text = “Welcome”;

//Save workbook
workbook.save('Output.xlsx');

//dispose workbook
Workbook.dispose();

{% endhighlight %}

## Adding a Number to Excel worksheet

You can add number to the Excel worksheet using setNumber method and number property of the Range class.

The following code snippet shows how to add number to Excel worksheet.

{% highlight dart %}

//Create a new Excel Document.
Workbook workbook = new Workbook();

//Accessing sheet via index.
Worksheet sheet = workbook.worksheets[0];

//Adding text using setnumber() method.
sheet.getRangeByName("A1").setNumber(4444);

//Adding text using number property.
sheet.getRangeByName(“A2”).number = 1000;

//Save workbook
workbook.save('Output.xlsx');

//dispose workbook
Workbook.dispose();

{% endhighlight %}

## Adding a DateTime to Excel worksheet

You can add number to the Excel worksheet using setDateTime method and datetime property of the Range class.

The following code snippet shows how to add datetime to Excel worksheet.

{% highlight dart %}

//Create a new Excel Document.
Workbook workbook = new Workbook();

//Accessing sheet via index.
Worksheet sheet = workbook.worksheets[0];

//Adding text using setDateTime() method.
sheet.getRangeByName("A1").setDateTime(DateTime(2020, 7, 7, 1, 0, 0));

//Adding text using dateTime property.
sheet.getRangeByName(“A2”).dateTime = DateTime(2442, 12, 6, 23, 34, 23);

//Save workbook
workbook.save('Output.xlsx');

//dispose workbook
Workbook.dispose();

{% endhighlight %}

## Adding a value to Excel Worksheet

You can add value to the Excel worksheet using setValue method and value property of the Range class.The value can be number, text or date time.

The following code snippet shows how to add value to Excel worksheet.

{% highlight dart %}

//Create a new Excel Document.
Workbook workbook = new Workbook();

//Accessing sheet via index.
Worksheet sheet = workbook.worksheets[0];

//Adding text using setValue() method.
sheet.getRangeByName("A1").setValue(44);

//Adding text using text property.
sheet.getRangeByName("A2").value(“Hello World”);

//Save workbook
workbook.save('Output.xlsx');

//dispose workbook
Workbook.dispose();

{% endhighlight %}

