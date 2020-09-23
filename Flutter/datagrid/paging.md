---
layout: post
title: Paging for Syncfusion Flutter DataGrid | DataTable
description: Learn how to create Syncfusion Flutter DataPager with DataGrid and customize the apperance of the DataPager.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Paging in Flutter (SfDataGrid)

The data grid interactively supports the manipulation of data using `SfDataPager` control. This provides to load data in segments when dealing with large volumes of data. SfDataPager can be placed above or below based on the requirement to easily manage data paging.

The data grid performs paging of data using the `SfDataPager`. To enable paging, follow the procedure:

* Create a new SfDataPager widget, and bind the `SfDatGrid.DataGridSource` to the `SfDataPager.delegate` property.
* Set the number of rows to be displayed on a page by setting the `SfDataPager.rowsPerPage` property.
* Set the number of buttons that should be displayed in view by setting the `SfDataPager.visibleItemsCount` property.
* Extent `SfDataPager.delegate.rowCount` propety and `SfDataPager.delegate.handlePageChanges` method in `SfDataGrid.DataGridSource`.

N> The `SfDataPager.visibleItemsCount` property default value is 5.

The following code example illustrates using `SfDataPager` with the data grid control:

{% tabs %}
{% highlight Dart %}

List<Employee> paginatedDataSource = [];

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: LayoutBuilder(
      builder: (context, constraint) {
        return Column(
          children: [
            SizedBox(
              height: constraint.maxHeight - 60,
              width: constraint.maxWidth,
              child: SfDataGrid(
                  source: _employeeDataSource,
                  columnWidthMode: ColumnWidthMode.fill,
                  columns: <GridColumn>[
                    GridNumericColumn(mappingName: 'id', headerText: 'ID'),
                    GridTextColumn(mappingName: 'name', headerText: 'Name'),
                    GridTextColumn(
                        mappingName: 'designation',
                        headerText: 'Designation'),
                    GridNumericColumn(
                        mappingName: 'salary', headerText: 'Salary')
                  ]),                                                                                   
            ),                                                                                          
            Container(
              height: 60,
              child: SfDataPager(
                delegate: _employeeDataSource,
                rowsPerPage: 20,
                direction: Axis.horizontal,
              ),
            )
          ],
        );
      },
    ),
  );
}

class EmployeeDataSource extends DataGridSource<Employee> {

  @override                                                                    
  List<Employee> get dataSource => paginatedDataSource;

  @override
  int get rowCount => _employees.length;

  @override                                                                    
  Object getValue(Employee data, String columnName) {
    switch (columnName) {
      case 'id':
        return data.id;
        break;
      case 'name':
        return data.name;
        break;
      case 'salary':
        return data.salary;
        break;
      case 'designation':
        return data.designation;
        break;
      default:
        return ' ';                                                            
        break;                                                                 
    }
  }

  @override
  Future<bool> handlePageChange(int oldPageIndex, int newPageIndex,            
      int startRowIndex, int rowsPerPage) async {

    int endIndex = startRowIndex + rowsPerPage;                               
    if (endIndex > _employees.length) {
      endIndex = _employees.length - 1;
    }

    paginatedDataSource = List.from(
      _employees.getRange(startRowIndex, endIndex).toList(growable: false);

    notifyDataSourceListeners();
    return true;
  }
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows customized current cell](images/selection/flutter-datagrid-customized-currentcell.png)

## Asynchronous data loading

Data to the SfDataPager can be loaded asynchronously using the ProgressIndicator from the `SfDataPager.delegate.handlePageChange` method.

{% tabs %}
{% highlight Dart %}

class EmployeeDataSource extends DataGridSource<Employee> {
  @override
  Future<bool> handlePageChange(int oldPageIndex, int newPageIndex,
      int startRowIndex, int rowsPerPage) async {
    int endIndex = startRowIndex + rowsPerPage;
    if (endIndex > _employees.length) {
      endIndex = _employees.length - 1;
    }

    showLoadingIndicator = true;
    notifyListeners();
    await Future.delayed(Duration(milliseconds: 1000));
    paginatedDataSource = List.from(
        _employees.getRange(startRowIndex, endIndex).toList(growable: false));
    showLoadingIndicator = false;
    notifyListeners();
    return true;
  }
}

{% endhighlight %}
{% endtabs %}

You can download the source code of asynchronous data loading sample [here](http://www.syncfusion.com/downloads/support/directtrac/general/ze/SfGrid_Sample788022149)

## Orientation

SfDataPager allows you to arrange the child elements either horizontally or vertically. This can be achieved by using the `direction` Property. `direction` is an Enum type. The following table describes the direction enum values.

<table>
<tr>
<th>
Enum Value</th><th>
Description</th></tr>
<tr>
<td>
horizontal</td><td>
This is the default enum value for direction. Arranges all the navigation buttons and numeric buttons horizontally.
{{'!![flutter datagrid shows customized current cell](images/selection/flutter-datagrid-customized-currentcell.png)'|markdownify}}

</td></tr>
<tr>
<td>
vertical</td><td>
Arranges all the navigation buttons and numeric buttons vertically.
{{'!![flutter datagrid shows customized current cell](images/selection/flutter-datagrid-customized-currentcell.png)'|markdownify}}

</td></tr>
</table>


## Apperance

SfDataPager allows to customize the appearance of the data pager through [SfDataPagerTheme.SfDataPagerThemeData] property.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfDataPagerTheme(
    data: SfDataPagerThemeData(
      itemColor: Colors.white,
      selectedItemColor: Colors.lightGreen,
      itemBorderRadius: BorderRadius.circular(5),
      backgroundColor: Colors.teal,
    ),
    child: SfDataPager(
      delegate: _employeeDataSource,
      rowsPerPage: 20,
      direction: Axis.horizontal,
    ),
  ));
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows customized current cell](images/selection/flutter-datagrid-customized-currentcell.png)