# Working with Images

## Adding Images to worksheet

Flutter XlsIO allows to insert images like JPEG and PNG formats into a worksheet. 

Refer to the following code snippet to add images to worksheet.

{% highlight dart %}

//Create a new Excel document.
Workbook workbook = new Workbook();

//Accessing worksheet via index.
Worksheet sheet = workbook.worksheets[0];

//Adding an image.
sheet.pictures.addBase64(1, 1, image1jpg);

//Adding an image.
sheet.pictures.addFile(10, 10, "image1.png");

//Save a workbook.
workbook.save("AddImage.xlsx");

//dispose workbook.
workbook.dispose();

{% endhighlight %}


## Re-Sizing, Flip and Rotation Images

Pictures can be re-sized, flip and formatted using various properties of **Picture** class. Refer to the following code snippet.

{% highlight dart %}

//Create a new Excel document.
Workbook workbook = new Workbook();

//Accessing worksheet via index.
Worksheet sheet = workbook.worksheets[0];

//Add a image.
Picture picture = sheet.pictures.addFile(1, 1, "image1.png");

//Re-size an image
picture.height = 200;
picture.width = 200;

//rotate an image.
picture.rotation = 100;

//Flip an image.
picture.horizontalFlip = true;

//save and dispose workbook
workbook.save('Image.xlsx');
workbook.dispose();

{% endhighlight %}

## Remove image from Worksheet

The following code snippet shows how to remove the image from the worksheet using **Remove** method.

{% highlight dart %}
 
//Create a new Excel document.
Workbook workbook = new Workbook();

//Accessing worksheet via index.
Worksheet sheet = workbook.worksheets[0];

//Add an image.
Picture picture = sheet.pictures.addFile(1, 1, "image1.png");

//Remove an image.
picture.remove();

//save and dispose workbook.
workbook.save('Image.xlsx');
workbook.dispose();

{% endhighlight %}

