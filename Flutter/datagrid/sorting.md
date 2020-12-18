---
layout: post
title: Sorting in Flutter DataGrid | DataTable | Syncfusion
description: Learn about how to to sort one or more columns with the tristate sorting and show sort numbers to indicate the sort order.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Sorting in Flutter Datagrid

The datagrid provides the built-in support to sort one or more columns by setting the [SfDataGrid.allowSorting](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/allowSorting.html) property to true. When sorting is applied, the datagrid automatically rearranges the data to match with the current sort criteria. When `SfDataGrid.allowSorting` is true, you can sort the data simply by tapping the column header. Once sorting is applied, the datagrid shows a sort icon in the respective column header indicating the sort direction.

## Programmatic sorting

The datagrid provides support to sort the columns programmatically. You can manually define the [SortColumnDetails](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SortColumnDetails-class.html) objects, and add it in the [SfDataGrid.source.sortedColumns](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/sortedColumns.html) collection. The datagrid sorts the data based on the `SortColumnDetails` objects added to this collection. If you want to perform sorting at run time, you should call [SfDataGrid.source.sort()](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/sort.html) method after adding the `SortColumnDetails` to the `SfDataGrid.source.sortedColumns` collection. 

The `SortColumnDetails` object holds the following two properties:

* [name](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SortColumnDetails/name.html) : Name of the column to be sorted.
* [sortDirection](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SortColumnDetails/sortDirection.html) : Specifies the ascending or descending direction.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Column(
      mainAxisAlignment: MainAxisAlignment.center,
      children: [
        SfDataGrid(
          source: _employeeDataSource,
          columns: [
            GridNumericColumn(mappingName: 'id', headerText: 'ID'),
            GridTextColumn(mappingName: 'name', headerText: 'Name'),
            GridTextColumn(mappingName: 'city', headerText: 'City'),
            GridNumericColumn(mappingName: 'freight', headerText: 'Freight')
          ],
        ),
        Padding(
          padding: const EdgeInsets.all(8.0),
          child: FlatButton(
              onPressed: () {
                _employeeDataSource.sortedColumns.add(SortColumnDetails(
                    name: 'name',
                    sortDirection: DataGridSortDirection.ascending));
                _employeeDataSource.sort();
              },
              child: Text('Apply sort')),
        )
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows programmatical sorting](images/sorting/flutter-datagrid-programmatical-sorting.png)

## Multi-column sorting

The datagrid sorts the data against more than one columns by setting the [SfDataGrid.allowMultiColumnSorting](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/allowMultiColumnSorting.html) property to true. The number of columns by which the data can be sorted is unlimited. To apply sorting for multiple columns, tap the desired column headers after setting the `SfDataGrid.allowMultiColumnSorting` property.
To apply sorting for multiple columns in web, you can click the column header by pressing the <kbd>Ctrl</kbd> key.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfDataGrid(
    source: _employeeDataSource,
    allowSorting: true,
    allowMultiColumnSorting: true,
    columns: [
      GridNumericColumn(mappingName: 'id', headerText: 'ID'),
      GridTextColumn(mappingName: 'name', headerText: 'Name'),
      GridTextColumn(mappingName: 'city', headerText: 'City'),
      GridNumericColumn(mappingName: 'freight', headerText: 'Freight')
    ],
  ));
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows multi-column sorting](images/sorting/flutter-datagrid-multicolumn-sorting.gif)

## Tri-state sorting

In addition to sort the data in ascending/descending order, the SfDataGrid unsort the data in the original order by clicking the header again after sorting to descending order by setting the [SfDataGrid.allowTriStateSorting](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/allowTriStateSorting.html) property to true. When this property is set, sorting in each column iterates through three sort states: ascending, descending, and unsort.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfDataGrid(
    source: _employeeDataSource,
    allowSorting: true,
    allowMultiColumnSorting: true,
    allowTriStateSorting: true,
    columns: [
      GridNumericColumn(mappingName: 'id', headerText: 'ID'),
      GridTextColumn(mappingName: 'name', headerText: 'Name'),
      GridTextColumn(mappingName: 'city', headerText: 'City'),
      GridNumericColumn(mappingName: 'freight', headerText: 'Freight')
    ],
  ));
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows tri-state sorting](images/sorting/flutter-datagrid-tristate-sorting.gif)

## Sort column in double tap

By default, column gets sorted when column header clicked. This behavior can be changed to sort the column in double click action by setting [SfDataGrid.sortingGestureType](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/sortingGestureType.html) property to `doubleTap`.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfDataGrid(
    source: _employeeDataSource,
    allowSorting: true,
    sortingGestureType: SortingGestureType.doubleTap,
    columns: [
      GridNumericColumn(mappingName: 'id', headerText: 'ID'),
      GridTextColumn(mappingName: 'name', headerText: 'Name'),
      GridTextColumn(mappingName: 'city', headerText: 'City'),
      GridNumericColumn(mappingName: 'freight', headerText: 'Freight')
    ],
  ));
}

{% endhighlight %}
{% endtabs %}

## Show sort number

The datagrid provides support the sequence numbers to display the sorted columns during multi-column sorting by setting [SfDataGrid.showSortNumbers](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/showSortNumbers.html) is set to true. This is applicable when the `SfDataGrid.allowMultiColumnSorting` property is enabled.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfDataGrid(
    source: _employeeDataSource,
    allowSorting: true,
    allowMultiColumnSorting: true,
    showSortNumbers: true,
    columns: [
      GridNumericColumn(mappingName: 'id', headerText: 'Order ID'),
      GridTextColumn(mappingName: 'name', headerText: 'Name'),
      GridTextColumn(mappingName: 'city', headerText: 'City'),
    ],
  ));
}
  
{% endhighlight %}
{% endtabs %}

![flutter datagrid shows sort sequence numbers during multi-column sorting](images/sorting/flutter-datagrid-showsortnumbers.gif)

## Disable sorting for an individual column

The data grid disables sorting for an individual column by setting the [GridColumn.allowSorting](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridColumn/allowSorting.html) property to false. The default value of this property is true. So all the columns in the [SfDataGrid.columns](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/columns.html) collection can be sorted when `SfDataGrid.allowSorting` is set to true.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfDataGrid(
    source: _employeeDataSource,
    allowSorting: true,
    columns: [
      GridNumericColumn(mappingName: 'id', headerText: 'ID',
        allowSorting: false),
      GridTextColumn(mappingName: 'name', headerText: 'Name'),
      GridTextColumn(mappingName: 'city', headerText: 'City'),
      GridNumericColumn(mappingName: 'freight', headerText: 'Freight')
    ],
  ));
}
  
{% endhighlight %}
{% endtabs %}

## Change the color of sort icon

The color of sort icon can be customized by using [SfDataGridThemeData.headerStyle.sortIconColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/headerStyle.html) and [GridColumn.headerStyle.sortIconColor](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridColumn/headerStyle.html).

The following code describes how to change sort icon color by using [GridColumn](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridColumn-class.html).

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';
import 'package:syncfusion_flutter_core/theme.dart';

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfDataGrid(
    source: _employeeDataSource,
    allowSorting: true,
    columns: [
      GridNumericColumn(mappingName: 'id', headerText: 'ID',
        headerStyle: DataGridHeaderCellStyle(sortIconColor: Colors.redAccent)),
      GridTextColumn(mappingName: 'name', headerText: 'Name'),
      GridTextColumn(mappingName: 'city', headerText: 'City'),
      GridNumericColumn(mappingName: 'freight', headerText: 'Freight')
    ],
  ));
}
  
{% endhighlight %}
{% endtabs %}

The following code describes how to change sort icon color by using [SfDataGridTheme](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridTheme-class.html).

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';
import 'package:syncfusion_flutter_core/theme.dart';

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfDataGridTheme(
    data: SfDataGridThemeData(
        headerStyle: 
            DataGridHeaderCellStyle(sortIconColor: Colors.redAccent)),
    child: SfDataGrid(
      source: _employeeDataSource,
      allowSorting: true,
      allowMultiColumnSorting: true,
      columns: [
        GridNumericColumn(mappingName: 'id', headerText: 'ID'),
        GridTextColumn(mappingName: 'name', headerText: 'Name'),
        GridTextColumn(mappingName: 'city', headerText: 'City'),
        GridNumericColumn(mappingName: 'freight', headerText: 'Freight')
      ],
    ),
  ));
}
  
{% endhighlight %}
{% endtabs %}

![flutter datagrid shows customized the sort icon color](images/sorting/flutter-datagrid-customized-sorticon-color.png)

## Custom sorting

The datagrid allows to sort columns based on custom logic. For each column, you can provide different sorting criteria by overriding the following methods from [DataGridSource](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource-class.html),

* **[handleSort](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/handleSort.html)** : This method will be called when you tap the column header and sorting is being applied. You can override this method to provide the entire logic for sorting for columns.
* **[compare](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/compare.html)** : You can override this method to compare two objects and return the sorting order based on the criteria.

### Sort column based on string length

The following code shows how to perform custom sorting for the columns based on the string length by overriding the `compare` method.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

class EmployeeDataSource extends DataGridSource<Employee> {
  @override
  List<Employee> get dataSource => _employeeData;

  @override
  Object getValue(Employee employee, String columnName) {
    switch (columnName) {
      case 'id':
        return employee.id;
        break;
      case 'name':
        return employee.name;
        break;
      case 'city':
        return employee.city;
        break;
      case 'freight':
        return employee.freight;
        break;
      default:
        return ' ';
        break;
    }
  }

  @override
  int compare(Employee a, Employee b, SortColumnDetails sortColumn) {
    var x = getValue(a, sortColumn.name);
    var y = getValue(b, sortColumn.name);
    if (x == null || y == null) {
      if (sortColumn.sortDirection == DataGridSortDirection.ascending)
        return x == null ? -1 : 1;
      else
        return x == null ? 1 : -1;
    }
    int xLength = x.toString().length;
    int yLength = y.toString().length;
    if (xLength.compareTo(yLength) > 0)
      return sortColumn.sortDirection == DataGridSortDirection.ascending ? 1 : -1;
    else if (xLength.compareTo(yLength) == -1) 
      return sortColumn.sortDirection == DataGridSortDirection.ascending ? -1 : 1;
    else
      return 0;
  }
}

{% endhighlight %}
{% endtabs %}

>**NOTE**  
  Download demo application from [GitHub](https://github.com/SyncfusionExamples/how-to-sort-the-columns-based-on-length-of-the-text-in-Flutter-datagrid).

![flutter datagrid shows custom sorting for the columns based on string length](images/sorting/flutter-datagrid-custom-sorting.png)

### Case-insensitive sorting

The following code shows how to perform custom sorting for the columns based on the case-insensitive by overriding the `compare` method.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

class EmployeeDataSource extends DataGridSource<Employee> {
  @override
  List<Employee> get dataSource => _employeeData;

  @override
  Object getValue(Employee employee, String columnName) {
    switch (columnName) {
      case 'id':
        return employee.id;
        break;
      case 'name':
        return employee.name;
        break;
      case 'city':
        return employee.city;
        break;
      case 'freight':
        return employee.freight;
        break;
      default:
        return ' ';
        break;
    }
  }

  @override
  int compare(Employee a, Employee b, SortColumnDetails sortColumn) {
    if (sortColumn.name == 'name') {
      if (sortColumn.sortDirection == DataGridSortDirection.ascending) {
        if (a.name == null || b.name == null)
          return a.name == null ? -1 : 1;
        else 
          return a.name.toLowerCase().compareTo(b.name.toLowerCase());
      } else {
        if (a.name == null || b.name == null)
          return a.name == null ? 1 : -1;
        else
          return b.name.toLowerCase().compareTo(a.name.toLowerCase());
      }
    }
    return super.compare(a, b, sortColumn);
  }
}

{% endhighlight %}
{% endtabs %}

>**NOTE**  
  Download demo application from [GitHub](https://github.com/SyncfusionExamples/how-to-perform-case-insensitive-sorting-in-flutter-datagrid).

![flutter datagrid shows custom sorting for the columns based on case-insensitive](images/sorting/flutter-datagrid-custom-sorting-case-insensitive.png)