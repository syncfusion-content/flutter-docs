# Getting Started for Syncfusion Flutter XlsIO

This section explains the steps required to create a Excel document by a single button click. This section covers only the minimal features needed to learn to get started with the Excel.

## Steps to create Excel document in Flutter application

Create a simple project using the instructions given in the [`Getting Started with your first Flutter app'](https://flutter.dev/docs/get-started/test-drive?tab=vscode#create-app) documentation.

### Add dependency

Add the Syncfusion Flutter XlsIO dependency to your pub spec file.

{% tabs %}
{% highlight dart %}
dependencies: 
syncfusion_flutter_xlsio: ^xx.x.xx
{% endhighlight %}
{% endtabs %}

N>**Here xx.x.xx denotes the current version of [Syncfusion Flutter XlsIO](syncfusion-flutter-xlsio) **package.

### Get packages
Run the following command to get the required packages.

{% tabs %}
{% highlight dart %}
$ flutter pub get
{% endhighlight %}
{% endtabs %}

### Import package

Import the following package in your Dart code.
{% tabs %}
{% highlight dart %}
import 'package:syncfusion_flutter_xlsio/xlsio.dart';
{% endhighlight %}
{% endtabs %}
Add a new button widget as a child of your container widget.
{% tabs %}
{% highlight dart %}
@override
Widget build(BuildContext context) {
  return Scaffold(
	body: Center(
	  child: RaisedButton(
		onPressed: _createExcel,
		  child: Text('Create Excel')
		)
	 )
  );
}
{% endhighlight %}
{% endtabs %}

Include the following code snippet in the button click event to create a PDF file.

{% tabs %}
{% highlight dart %}
Future<void> _createExcel() async {
//Create a new Excel Document
Workbook workbook = new Workbook();
//Accessing worksheet via index
Workbook.worksheets[0];
//Save the document
Workbook.save(“CreateExcel.xlsx”);
//dispose workbook
Workbook.dispose();
}
{% endhighlight %}
{% endtabs %}

## Save and open a Excel document in mobile

You can save and open a Excel document in mobile by using the following steps:

### Add dependency
Add the following packages to your pub spec file.
{% tabs %}
{% highlight dart %}
path_provider: ^1.6.5
open_file: ^3.0.1
{% endhighlight %}
{% endtabs %}
### Import package
{% tabs %}
{% highlight dart %}
import 'dart:io';
import 'package:open_file/open_file.dart';
import 'package:path_provider/path_provider.dart';
{% endhighlight %}
{% endtabs %}
Include the following code snippet in _createExcel method to open the Excel document in mobile after saving it.
{% tabs %}
{% highlight dart %}
//Get external storage directory
final directory = await getExternalStorageDirectory();
//Get directory path
final path = directory.path;
//Create an empty file to write Excel data
File file = File('$path/Output.xlsx');
//Write PDF data
await file.writeAsBytes(bytes, flush: true);
//Open the PDF document in mobile
OpenFile.open('$path/Output.xlsx');
{% endhighlight %}
{% endtabs %}
## Save and download a PDF document in web
You can save and download a Excel document in web by using the following steps.
### Import package
{% tabs %}
{% highlight dart %}
import 'dart:async';
import 'dart:convert';
import 'dart:js' as js;
{% endhighlight %}
{% endtabs %}
Include the following code snippet in _createExcel method to open the document in web after saving it.
{% tabs %}
{% highlight dart %}
js.context['excelData'] = base64.encode(bytes);
js.context['filename'] = 'Output.xlsx'; 
Timer.run(() { 
js.context.callMethod('download');
 });
{% endhighlight %}
{% endtabs %}
Add the following code in the header section of index.html file under the web folder.
{% tabs %}
{% highlight dart %}
<script>
 async function download() {
 var excelAsDataUri = "data:application/excel;base64, " + excelData;
 var link = document.createElement('a');
 link.download = filename; 
 link.href = excelAsDataUri;
 link.type = 'application/excel';
 link.click(); 
} 
</script>
{% endhighlight %}
{% endtabs %}
