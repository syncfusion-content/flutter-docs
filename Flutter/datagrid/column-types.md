---
layout: post
title: Column types in Syncfusion Flutter DataGrid | DataTable
description: Learn how to use and customize the different types of column and its properties in Syncfusion Flutter DataGrid.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Column Types in Flutter DataGrid

SfDataGrid provides support for various built-in column types. Each column has its own properties and renderer to handle different types of data. Based on the requirements, any column can be used.

The following table describes the types of columns and its usage:

| Column Type           | Renderer                        | Description                            |
|-----------------------|---------------------------------|----------------------------------------|
| GridTextColumn        | GridCellTextFieldRenderer       | Use to display the String data         |
| GridNumericColumn     | GridCellNumericTextFieldRenderer| Use to display the Numeric data        |
| GridDateTimeColumn    | GridCellDateTimeRenderer        | Use to display the DateTime value      |
| GridWidgetColumn      | GridCellWidgetRenderer          | Use to display the Widget in each row  |

## GridColumn

GridColumn is a class that provides base functionalities for all the column types in SfDataGrid.

### Mapping column to a property

Column can be bound to a property in data object using `GridColumn.mappingName` property. `headerText` is used to display the required text in a column header. If the `headerText` is not mentioned, `mappingName` is considered.

{% tabs %}
{% highlight Dart %} 

    final EmployeeDataSource _employeeDataSource = EmployeeDataSource();
  
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SfDataGrid(
          source: _employeeDataSource,
          columns: [
            GridNumericColumn(mappingName: 'id', headerText: 'ID'),
            GridTextColumn(mappingName: 'name', headerText: 'Name'),
            GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary'),
          ],
        ),
      );
    }

{% endhighlight %}
{% endtabs %}

### Set padding for column

`GridColumn.padding` property can be used to set the padding for the cells in the column. It is also applicable to the column header cell except `GridWidgetColumn`. The default value of padding is 16.0.

{% tabs %}
{% highlight Dart %} 

    final EmployeeDataSource _employeeDataSource = EmployeeDataSource();
  
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SfDataGrid(
          source: _employeeDataSource,
          columns: [
            GridNumericColumn(mappingName: 'id', headerText: 'ID')
              ..padding = EdgeInsets.all(20.0),
            GridTextColumn(mappingName: 'name', headerText: 'Name'),
            GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary')
          ],
        ),
      );
    }

{% endhighlight %}
{% endtabs %}

### Hiding a column

`GridColumn.isHidden` property can be used to set a column as hidden. The default value of the `isHidden` property is false.

>**NOTE**  
   Set the `isHidden` property to `True` instead of setting column width as `0` to hide a column.

{% tabs %}
{% highlight Dart %} 

    final EmployeeDataSource _employeeDataSource = EmployeeDataSource();
  
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SfDataGrid(
          source: _employeeDataSource,
          columns: [
            GridNumericColumn(mappingName: 'id', headerText: 'ID'),
            GridTextColumn(mappingName: 'name', headerText: 'Name'),
            GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary')
              ..isHidden = true,
          ],
        ),
      );
    }

{% endhighlight %}
{% endtabs %}

### Set manual width for column

SfDataGrid allows you to customize the width of each `GridColumn` in the `SfDataGrid.Columns` collection. To customize column width, use the `GridColumn.width` property. By default, this property will not be assigned any value. The GridColumn renders in view based on the value of the `defaultColumnWidth` property.

>**NOTE**  
   Set the `isHidden` property to `True` instead of setting column width as `0` to hide a column.

{% tabs %}
{% highlight Dart %} 

    final EmployeeDataSource _employeeDataSource = EmployeeDataSource();
  
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SfDataGrid(
          source: _employeeDataSource,
          columns: [
            GridNumericColumn(mappingName: 'id', headerText: 'ID'),
            GridTextColumn(mappingName: 'name', headerText: 'Name')
              ..width = 100.0,
            GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary')
          ],
        ),
      );
    }

{% endhighlight %}
{% endtabs %}

### Set alignment for column

`GridColumn.textAlignment` and `GridColumn.headerTextAlignment` can be used to customize the alignment for the cells and header cells in the column.

{% tabs %}
{% highlight Dart %} 

    final EmployeeDataSource _employeeDataSource = EmployeeDataSource();
  
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SfDataGrid(
          source: _employeeDataSource,
          columns: [
            GridNumericColumn(mappingName: 'id', headerText: 'ID')
              ..textAlignment = Alignment.center
              ..headerTextAlignment = Alignment.center,
            GridTextColumn(mappingName: 'name', headerText: 'Name'),
            GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary')
          ],
        ),
      );
    }

{% endhighlight %}
{% endtabs %}

### Set text wrapping for column

When the text for the record cells exceeds the content area, wrap the record cell by setting the `GridColumn.softWrap` as `True`. The default value of `softWrap` is false.

{% tabs %}
{% highlight Dart %} 

    final EmployeeDataSource _employeeDataSource = EmployeeDataSource();
  
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SfDataGrid(
          source: _employeeDataSource,
          columns: [
            GridNumericColumn(mappingName: 'id', headerText: 'ID'),
            GridTextColumn(mappingName: 'name', headerText: 'Name'),
            GridTextColumn(mappingName: 'designation', headerText: 'Designation')
              ..softWrap = true,
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary')
            
          ],
        ),
      );
    }

{% endhighlight %}
{% endtabs %}

### Change text overflow behavior

`GridColumn.overflow` property can be used to change the behavior of the text overflow. The default value of overflow is ellipsis.

{% tabs %}
{% highlight Dart %} 

    final EmployeeDataSource _employeeDataSource = EmployeeDataSource();
  
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SfDataGrid(
          source: _employeeDataSource,
          columns: [
            GridNumericColumn(mappingName: 'id', headerText: 'ID')
              ..overflow = TextOverflow.fade,
            GridTextColumn(mappingName: 'name', headerText: 'Name')
              ..overflow = TextOverflow.clip,
            GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary')
          ],
        ),
      );
    }

{% endhighlight %}
{% endtabs %}

## Column styling

GridColumn provides support to customize the style of column using `GridColumn.cellStyle` and `GridColumn.headerStyle` properties. The type of `cellStyle` and `headerStyle` property is `DataGridCellStyle` and `DataGridHeaderCellStyle`. For more information, refer [Styling](styles.md\#styles) section.

### Change column text style

`GridColumn.cellStyle.textStyle` and ` GridColumn.headerStyle.textStyle` properties can be used to change the text style for the column's cells.

{% tabs %}
{% highlight Dart %} 

    final EmployeeDataSource _employeeDataSource = EmployeeDataSource();
  
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SfDataGrid(
          source: _employeeDataSource,
          columns: [
            GridNumericColumn(mappingName: 'id', headerText: 'ID')
              ..headerStyle = DataGridHeaderCellStyle(
                  textStyle:
                      TextStyle(color: Colors.red, fontWeight: FontWeight.bold))
              ..cellStyle =
                  DataGridCellStyle(textStyle: TextStyle(color: Colors.red)),
            GridTextColumn(mappingName: 'name', headerText: 'Name'),
            GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary')
          ],
        ),
      );
    }

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows columns with text style](images/column-types/flutter-datagrid-change-textstyle.png)

### Change column background color

` GridColumn.cellStyle.backgroundColor` and ` GridColumn.headerStyle.backgroundColor` properties can be used to change the background color for the column's cells.

{% tabs %}
{% highlight Dart %} 

    final EmployeeDataSource _employeeDataSource = EmployeeDataSource();
  
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SfDataGrid(
          source: _employeeDataSource,
          columns: [
            GridNumericColumn(mappingName: 'id', headerText: 'ID'),
            GridTextColumn(mappingName: 'name', headerText: 'Name'),
            GridTextColumn(mappingName: 'designation', headerText: 'Designation')
              ..headerStyle = DataGridHeaderCellStyle(
                  textStyle:
                      TextStyle(color: Colors.white, fontWeight: FontWeight.bold),
                  backgroundColor: Colors.deepPurple)
              ..cellStyle =
                  DataGridCellStyle(backgroundColor: Colors.deepPurple[200]),
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary')
          ],
        ),
      );
    }

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows columns with backgroundcolor](images/column-types/flutter-datagrid-change-backgroundcolor.png)

## GridTextColumn

`GridTextColumn` inherits all the properties of GridColumn. It is used to display the textual content to the column's cells.

{% tabs %}
{% highlight Dart %} 

    final EmployeeDataSource _employeeDataSource = EmployeeDataSource();
  
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SfDataGrid(
          source: _employeeDataSource,
          columns: [
            GridNumericColumn(mappingName: 'id', headerText: 'ID'),
            GridTextColumn(mappingName: 'name', headerText: 'Name'),
            GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary')
          ],
        ),
      );
    }

{% endhighlight %}
{% endtabs %}

## GridNumericColumn

`GridNumericColumn` inherits all the properties of GridColumn. It is used to display the columns data as numeric values.

{% tabs %}
{% highlight Dart %} 

    final EmployeeDataSource _employeeDataSource = EmployeeDataSource();
  
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SfDataGrid(
          source: _employeeDataSource,
          columns: [
            GridNumericColumn(mappingName: 'id', headerText: 'ID'),
            GridTextColumn(mappingName: 'name', headerText: 'Name'),
            GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary')
          ],
        ),
      );
    }

{% endhighlight %}
{% endtabs %}

### Number formatting

The numeric value can be formatted by using `GridNumericColumn.numberFormat` property, which contains the set of predefined number patterns. For more information about predefined patterns, refer [NumberFormat](https://api.flutter.dev/flutter/intl/NumberFormat-class.html) class.

{% tabs %}
{% highlight Dart %} 

    final EmployeeDataSource _employeeDataSource = EmployeeDataSource();
  
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SfDataGrid(
          source: _employeeDataSource,
          columns: [
            GridNumericColumn(mappingName: 'id', headerText: 'ID'),
            GridTextColumn(mappingName: 'name', headerText: 'Name'),
            GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary')
              ..numberFormat = NumberFormat.currency(locale: 'en_US', symbol: '\$')
          ],
        ),
      );
    }

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows columns with number formatting](images/column-types/flutter-datagrid-numberformatting.png)

## GridDateTimeColumn

`GridDateTimeColumn` inherits all the properties of GridColumn. It is used to display the columns data as datetime values.

{% tabs %}
{% highlight Dart %} 

    final EmployeeDataSource _employeeDataSource = EmployeeDataSource();
  
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SfDataGrid(
          source: _employeeDataSource,
          columns: [
            GridNumericColumn(mappingName: 'id', headerText: 'ID'),
            GridTextColumn(mappingName: 'name', headerText: 'Name'),
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary')
            GridDateTimeColumn(
                mappingName: 'dateOfJoining', headerText: 'Date of Joining')
          ],
        ),
      );
    }

{% endhighlight %}
{% endtabs %}

### Date formatting

The datetime value can be formatted by using `GridDateTimeColumn.dateFormat` property, which contains the set of predefined datetime patterns. The default format of a date is `dd-MM-yyyy`. For more information about predefined patterns, refer [DateFormat](https://api.flutter.dev/flutter/intl/DateFormat-class.html) class.

{% tabs %}
{% highlight Dart %} 

    final EmployeeDataSource _employeeDataSource = EmployeeDataSource();
  
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SfDataGrid(
          source: _employeeDataSource,
          columns: [
            GridNumericColumn(mappingName: 'id', headerText: 'ID'),
            GridTextColumn(mappingName: 'name', headerText: 'Name'),
            GridDateTimeColumn(
                mappingName: 'dateOfJoining', headerText: 'Date of Joining')
              ..dateFormat = DateFormat('dd/MM/yyyy'),
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary'),
          ],
        ),
      );
    }

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows columns with date formatting](images/column-types/flutter-datagrid-dateformatting.png)

## GridWidgetColumn

`GridWidgetColumn` is used to load any custom widget or multiple widgets to the column's cells. Any widget can be loaded using the `cellBuilder` callback. You can simply return a required widget in a callback.

In the below example, image is returned in `cellBuilder` callback. Image is already added in the Employee class.

{% tabs %}
{% highlight Dart %} 

    final EmployeeDataSource _employeeDataSource = EmployeeDataSource();
  
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: SfDataGrid(
          source: _employeeDataSource,
          cellBuilder: (BuildContext context, GridColumn column, int rowindex) {
            return employees[rowIndex].image;
          },
          columns: [
            GridNumericColumn(mappingName: 'id', headerText: 'ID'),
            GridWidgetColumn(mappingName: 'image', headerText: 'Image'),
            GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary')
          ],
        ),
      );
    }

{% endhighlight %}
{% endtabs %}