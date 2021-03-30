---
layout: post
title: Row Height Customization in Syncfusion Flutter DataGrid | DataTable
description: Learn how to  customize the header row height and the row height of all the grid rows by using Row Height feature in Syncfusion Flutter DataGrid.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Row Height Customization in Flutter DataGrid (SfDataGrid)

This section explains about options to customize the header row height and the row height of all the grid rows or particular row based on your requirements.

## Set height for header row

[SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) allows you to customize the height of the header row by using the [headerRowHeight](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/headerRowHeight.html) property.

{% tabs %}
{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfDataGrid(
    source: _employeeDatasource,
    headerRowHeight: 70,
    columns: <GridColumn>[
      GridTextColumn(
        columnName: 'id',
        label: Container(
          padding: EdgeInsets.symmetric(horizontal: 16.0),
          alignment: Alignment.centerRight,
          child: Text(
            'ID',
            overflow: TextOverflow.ellipsis,
          ))),
      GridTextColumn(
        columnName: 'name',
        label: Container(
          padding: EdgeInsets.symmetric(horizontal: 16.0),
          alignment: Alignment.centerLeft,
          child: Text(
            'Name',
            overflow: TextOverflow.ellipsis,
          ))),
      GridTextColumn(
        columnName: 'designation',
        label: Container(
          padding: EdgeInsets.symmetric(horizontal: 16.0),
          alignment: Alignment.centerLeft,
          child: Text(
            'Designation',
            overflow: TextOverflow.ellipsis,
          ))),
      GridTextColumn(
        columnName: 'salary',
        label: Container(
          padding: EdgeInsets.symmetric(horizontal: 16.0),
          alignment: Alignment.centerRight,
          child: Text(
            'Salary',
            overflow: TextOverflow.ellipsis,
          ))),
    ],
  ));
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows header row with custom height ](images/row-height-customization/flutter-datagrid-header-row-height.jpg)

## Set height for rows except header row

You can customize the height of the grid rows in `SfDataGrid` by using the [rowHeight](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/rowHeight.html) property.

{% tabs %}
{% highlight Dart %} 
        
@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfDataGrid(
    source: _employeeDatasource,
    rowHeight: 60,
    columns: <GridColumn>[
      GridTextColumn(
        columnName: 'id',
        label: Container(
          padding: EdgeInsets.symmetric(horizontal: 16.0),
          alignment: Alignment.centerRight,
          child: Text(
            'ID',
            overflow: TextOverflow.ellipsis,
          ))),
      GridTextColumn(
        columnName: 'name',
        label: Container(
          padding: EdgeInsets.symmetric(horizontal: 16.0),
          alignment: Alignment.centerLeft,
          child: Text(
            'Name',
            overflow: TextOverflow.ellipsis,
          ))),
      GridTextColumn(
        columnName: 'designation',
        label: Container(
          padding: EdgeInsets.symmetric(horizontal: 16.0),
          alignment: Alignment.centerLeft,
          child: Text(
            'Designation',
            overflow: TextOverflow.ellipsis,
          ))),
      GridTextColumn(
        columnName: 'salary',
        label: Container(
          padding: EdgeInsets.symmetric(horizontal: 16.0),
          alignment: Alignment.centerRight,
          child: Text(
            'Salary',
            overflow: TextOverflow.ellipsis,
          ))),
    ],
  ));
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows rows except header row with custom height](images/row-height-customization/flutter-datagrid-row-height.jpg)

## Refresh row height for specific row

The `SfDataGrid` allows you to update or refresh specific row and it's height when 
an underlying data is updated.

You can refresh a specific row and its height by using the [DataGridController.refreshRow](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/refreshRow.html) method. This method has following two arguments,

* **rowIndex**- Specify the required row index which is required to refresh. If you specify this, the data alone will be refreshed for a row.

* **recalculateRowHeight** - Decides whether a height of a row should be refreshed along with the data.

If you call `refreshRow` method, `onQueryRowHeight` callback will called for that specific row. So, auto-calculation of height can be recalculated for that row.

In the below example, row data is updated when the `refreshRow` is called in `onPressed` callback of the `FlatButton`.

{% tabs %}
{% highlight Dart %} 

List<Employee> _employees;

EmployeeDataSource _employeeDataSource;

final DataGridController _controller = DataGridController();

final ColumnSizer _columnSizer = ColumnSizer();

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: const Text('Syncfusion Flutter DataGrid'),
    ),
    body: Column(
      children: [
        FlatButton(
          child: const Text('Update cell value),
              onPressed: () {
                _employees[0].id=1010;
                _employeeData[0].name = 'Maria Anders';
                _employeeData[0].designation = 'Sales Representative';
                _employees[0].salary = 25000;
                _controller.refreshRow(0);
                _employeeDataSource.getData(_employees);
                _employeeDataSource.updateDataSource();
              }),
          SfDataGrid(
            source: _employeeDataSource,
            controller: _controller,
            columnSizer: _columnSizer,
            onQueryRowHeight: (RowHeightDetails details) {
              if (details.rowIndex == 0) {
                return 100.0;
              }
              return 50.0; 
            },
            columns: <GridColumn>[
              GridTextColumn(
                columnName: 'id',
                label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'ID',
                    overflow: TextOverflow.ellipsis,
                  ))),
              GridTextColumn(
                columnName: 'name',
                label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Name',
                    overflow: TextOverflow.ellipsis,
                  ))),
              GridTextColumn(
                columnName: 'designation',
                label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Designation',
                    overflow: TextOverflow.ellipsis,
                  ))),
              GridTextColumn(
                columnName: 'salary',
                label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'Salary',
                    overflow: TextOverflow.ellipsis,
                  ))),
            ],
          ),
        ],
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

In the below example, row data is refreshed along with its row height when the `refreshRow` is called in `onPressed` callback of the `FlatButton`.

{% tabs %}
{% highlight Dart %} 

List<Employee> _employees;

EmployeeDataSource _employeeDataSource;

final DataGridController _controller = DataGridController();

final ColumnSizer _columnSizer = ColumnSizer();

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: const Text('Syncfusion Flutter DataGrid'),
    ),
    body: Column(
      children: [
        FlatButton(
          child: const Text('Update cell value),
              onPressed: () {
                _employees[0].id=1010;
                _employeeData[0].name = 'Maria Anders';
                _employeeData[0].designation = 'Sales Representative';
                _employees[0].salary = 25000;
                _controller.refreshRow(0, recalculateRowHeight: true);
                _employeeDataSource.getData(_employees);
                _employeeDataSource.updateDataSource();
              }),
          SfDataGrid(
            source: _employeeDataSource,
            controller: _controller,
            columnSizer: _columnSizer,
            onQueryRowHeight: (RowHeightDetails details) {
              if (details.rowIndex == 0) {
                return 100;
              }
              return 50;    
            },
            columns: <GridColumn>[
              GridTextColumn(
                columnName: 'id',
                label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'ID',
                    overflow: TextOverflow.ellipsis,
                  ))),
              GridTextColumn(
                columnName: 'name',
                label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Name',
                    overflow: TextOverflow.ellipsis,
                  ))),
              GridTextColumn(
                columnName: 'designation',
                label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Designation',
                    overflow: TextOverflow.ellipsis,
                  ))),
              GridTextColumn(
                columnName: 'salary',
                label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'Salary',
                    overflow: TextOverflow.ellipsis,
                  ))),
            ],
          ),
        ],
      ),
    );
  }

{% endhighlight %}
{% endtabs %}
