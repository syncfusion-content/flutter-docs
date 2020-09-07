# Working with Workbook

## Saving a Excel workbook to file system

You can save the created or manipulated workbook to file system using Save method of Workbook. The workbook is saved in the XLSX format.

{% highlight dart %}
//Creates a new instance for workbook.
Workbook workbook = new Workbook();

//Save the workbook in file system as XLSX format
workbook.save('Output.xlsx');

{% endhighlight %}

## Closing a workbook

Once after the workbook manipulation and save operation are completed, you should dispose the instance of Workbook, in order to release all the memory consumed by XlsIO’s DOM. The following code snippet illustrates how dispose the instance of Workbook.

{% highlight dart %}
//Creates a new instance for workbook.
Workbook workbook = new Workbook();

//Save the workbook in file system as XLSX format
workbook.save('Output.xlsx');

//Dispose the instance of workbook
workbook.dispose();

{% endhighlight %}
