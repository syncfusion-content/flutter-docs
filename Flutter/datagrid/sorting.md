---
layout: post
title: Sorting in Flutter DataGrid | DataTable | Syncfusion
description: Learn here all about how to sort a column or multiple columns with tristate sorting in Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Sorting in Flutter Datagrid (SfDataGrid)

The Datagrid provides the built-in support to sort one or more columns by setting the [SfDataGrid.allowSorting](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/allowSorting.html) property to true. When sorting is applied, the datagrid automatically rearranges the data to match with the current sort criteria. When the `SfDataGrid.allowSorting` is true, sort the data by tapping the column header.

By default, the datagrid shows an unsort icon on every column header to indicate that sorting is enabled in the respective column. When sorting is applied to columns, datagrid shows a respective sort icon in the column header to indicate the sort direction.

## Programmatic sorting

The Datagrid provides support to sort the columns programmatically. Manually define the [SortColumnDetails](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SortColumnDetails-class.html) objects, and add them in the [SfDataGrid.source.sortedColumns](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/sortedColumns.html) collection. The Datagrid sorts the data based on the `SortColumnDetails` objects added to this collection. If you want to perform sorting at runtime, call [SfDataGrid.source.sort()](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/sort.html) method after adding the `SortColumnDetails` to the `SfDataGrid.source.sortedColumns` collection. 

The `SortColumnDetails` object holds the following two properties:

* [name](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SortColumnDetails/name.html) : Name of the column to be sorted.
* [sortDirection](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SortColumnDetails/sortDirection.html) : Specifies the ascending or descending direction.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

late EmployeeDataSource _employeeDataSource;
List<Employee> _employees = <Employee>[];

@override
void initState() {
  super.initState();
  _employees = getEmployeeData();
  _employeeDataSource = EmployeeDataSource(employees: _employees);
}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Column(mainAxisAlignment: MainAxisAlignment.center, children: [
    SfDataGrid(source: _employeeDataSource, columns: [
      GridColumn(
          columnName: 'id',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerRight,
              child: Text(
                'ID',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'name',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerLeft,
              child: Text(
                'Name',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'city',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerLeft,
              child: Text(
                'City',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'freight',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerRight,
              child: Text(
                'Freight',
                overflow: TextOverflow.ellipsis,
              ))),
    ]),
    Padding(
      padding: EdgeInsets.symmetric(horizontal: 16.0),
      child: TextButton(
          onPressed: () {
            _employeeDataSource.sortedColumns.add(SortColumnDetails(
                name: 'name', sortDirection: DataGridSortDirection.ascending));
            _employeeDataSource.sort();
          },
          child: Text('Apply sort')),
    )
  ]));
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows programmatical sorting](images/sorting/flutter-datagrid-programmatical-sorting.jpg)

## Multi-column sorting

The datagrid sorts the data against more than one column by setting the [SfDataGrid.allowMultiColumnSorting](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/allowMultiColumnSorting.html) property to true. The number of columns by which the data can be sorted is unlimited. To apply sorting for multiple columns, tap the desired column headers after setting the `SfDataGrid.allowMultiColumnSorting` property.

To apply sorting for multiple columns on the web and desktop, click the column header by pressing the <kbd>Ctrl</kbd> key.

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
      GridColumn(
          columnName: 'id',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerRight,
              child: Text(
                'ID',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'name',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerLeft,
              child: Text(
                'Name',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'city',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerLeft,
              child: Text(
                'City',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'freight',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerRight,
              child: Text(
                'Freight',
                overflow: TextOverflow.ellipsis,
              ))),
    ],
  ));
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows multi-column sorting](images/sorting/flutter-datagrid-multicolumn-sorting.gif)

## Tri-state sorting

In addition to sorting the data in ascending or descending order, the SfDataGrid unsort the data in the original order by clicking the header again after sorting to descending order by setting the [SfDataGrid.allowTriStateSorting](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/allowTriStateSorting.html) property to true. When this property is set, sorting in each column iterates through three sort states: ascending, descending, and unsort.

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
      GridColumn(
          columnName: 'id',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerRight,
              child: Text(
                'ID',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'name',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerLeft,
              child: Text(
                'Name',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'city',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerLeft,
              child: Text(
                'City',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'freight',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerRight,
              child: Text(
                'Freight',
                overflow: TextOverflow.ellipsis,
              ))),
    ],
  ));
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows tri-state sorting](images/sorting/flutter-datagrid-tristate-sorting.gif)

## Sort column in double tap

By default, the column gets sorted when the column header is clicked. This behavior can be changed to sort the column in double click action by setting the [SfDataGrid.sortingGestureType](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/sortingGestureType.html) property to `doubleTap`.

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
      GridColumn(
          columnName: 'id',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerRight,
              child: Text(
                'ID',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'name',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerLeft,
              child: Text(
                'Name',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'city',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerLeft,
              child: Text(
                'City',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'freight',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerRight,
              child: Text(
                'Freight',
                overflow: TextOverflow.ellipsis,
              ))),
    ],
  ));
}

{% endhighlight %}
{% endtabs %}

### Callbacks

The `SfDataGrid` provides the following callbacks for sorting:

* [onColumnSortChanging]() : This callback is invoked before a sort operation is performed on the `SfDataGrid`. If the callback returns `true`, the `SfDataGrid` will proceed with the sorting; if it returns `false`, the sort operation will be canceled.

* [onColumnSortChanged]() : This callback is triggered after the sort operation has been completed on the `SfDataGrid`.

The followings are the parameters of the [SfDataGrid.onColumnSortChanging]() and [SfDataGrid.onColumnSortChanged]() callbacks,

* newSortedColumn: Retrieves the `SortColumnDetails` of the DataGrid row that was added for sorting.

* oldSortedColumn: Retrieves the `SortColumnDetails` of the DataGrid row that was removed from sorting.

The following example demonstrates how to use the `SfDataGrid.onColumnSortChanging` and `SfDataGrid.onColumnSortChanged` callbacks to sort a column and retrieve sorting details:

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfDataGrid(
    source: _employeeDataSource,
    allowSorting: true,
    onColumnSortChanging: (newSortedColumn, oldSortedColumn) {
      print(newSortedColumn);
      print(oldSortedColumn);
      return true;
    },
    onColumnSortChanged: (newSortedColumn, oldSortedColumn) {
      print(newSortedColumn);
      print(oldSortedColumn);
    },
    columns: [
      GridColumn(
          columnName: 'id',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerRight,
              child: Text(
                'ID',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'name',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerLeft,
              child: Text(
                'Name',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'city',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerLeft,
              child: Text(
                'City',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'freight',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerRight,
              child: Text(
                'Freight',
                overflow: TextOverflow.ellipsis,
              ))),
    ],
  ));
}

{% endhighlight %}
{% endtabs %}

## Show sort number

The Datagrid provides support for the sequence numbers to display the sorted columns during multi-column sorting by setting [SfDataGrid.showSortNumbers](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/showSortNumbers.html) to true. This is applicable when the `SfDataGrid.allowMultiColumnSorting` property is enabled.

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
      GridColumn(
          columnName: 'id',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerRight,
              child: Text(
                'ID',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'name',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerLeft,
              child: Text(
                'Name',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'city',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerLeft,
              child: Text(
                'City',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'freight',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerRight,
              child: Text(
                'Freight',
                overflow: TextOverflow.ellipsis,
              ))),
    ],
  ));
}
  
{% endhighlight %}
{% endtabs %}

![flutter datagrid shows sort sequence numbers during multi-column sorting](images/sorting/flutter-datagrid-showsortnumbers.gif)

## Change the sort number and background color

The color of the sort order number and its rounded background color can be customized by using the [SfDataGridThemeData.sortOrderNumberColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/sortOrderNumberColor.html) and [SfDataGridThemeData.sortOrderNumberBackgroundColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/sortOrderNumberBackgroundColor.html) respectively.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_core/theme.dart';
import 'package:syncfusion_flutter_datagrid/datagrid.dart';

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
    body: SfDataGridTheme(
      data: SfDataGridThemeData(
          sortOrderNumberBackgroundColor: Colors.tealAccent,
          sortOrderNumberColor: Colors.pink),
      child: SfDataGrid(
          source: employeeDataSource,
          columnWidthMode: ColumnWidthMode.auto,
          allowSorting: true,
          allowMultiColumnSorting: true,
          showSortNumbers: true,
          columns: <GridColumn>[
            GridColumn(
                columnName: 'id',
                label: Container(
                    padding: const EdgeInsets.symmetric(horizontal: 8.0),
                    alignment: Alignment.center,
                    child: const Text(
                      'ID'))),
            GridColumn(
                columnName: 'name',
                label: Container(
                    padding: const EdgeInsets.symmetric(horizontal: 8.0),
                    alignment: Alignment.center,
                    child: const Text('Name'))),
            GridColumn(
                columnName: 'city',
                label: Container(
                    padding: const EdgeInsets.symmetric(horizontal: 8.0),
                    alignment: Alignment.center,
                    child: const Text('City'))),
            GridColumn(
                columnName: 'freight',
                label: Container(
                    padding: const EdgeInsets.symmetric(horizontal: 8.0),
                    alignment: Alignment.center,
                    child: const Text('Freight'))),
          ]),
    ),
  );
}
  
{% endhighlight %}
{% endtabs %}

![flutter datagrid sort order number and its background color change](images/sorting/flutter-datagrid-sort-order-number-style.png)

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
      GridColumn(
          columnName: 'id',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerRight,
              child: Text(
                'ID',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'name',
          allowSorting: false,
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerLeft,
              child: Text(
                'Name',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'city',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerLeft,
              child: Text(
                'City',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'freight',
          label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerRight,
              child: Text(
                'Freight',
                overflow: TextOverflow.ellipsis,
              ))),
    ],
  ));
}
  
{% endhighlight %}
{% endtabs %}

## Change the color of the sort icon

The color of the sort icon can be customized by using [SfDataGridThemeData.sortIconColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/sortIconColor.html).

The following code describes how to change the sort icon color by using [SfDataGridTheme](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridTheme-class.html).

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';
import 'package:syncfusion_flutter_core/theme.dart';

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfDataGridTheme(
    data: SfDataGridThemeData(sortIconColor: Colors.redAccent),
    child: SfDataGrid(
      source: _employeeDataSource,
      allowSorting: true,
      allowMultiColumnSorting: true,
      columns: [
        GridColumn(
            columnName: 'id',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'ID',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'name',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Name',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'city',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'City',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'freight',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'Freight',
                  overflow: TextOverflow.ellipsis,
                ))),
      ],
    ),
  ));
}
  
{% endhighlight %}
{% endtabs %}

![flutter datagrid shows customized the sort icon color](images/sorting/flutter-datagrid-customized-sorticon-color.jpg)

## Change the position of the sort icon

The position of the sort icon can be changed by using the [GridColumn.sortIconPosition](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridColumn/sortIconPosition.html) property.

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
      gridLinesVisibility: GridLinesVisibility.both,
      headerGridLinesVisibility: GridLinesVisibility.both,
      columns: [
        GridColumn(
            sortIconPosition: ColumnHeaderIconPosition.start,
            columnName: 'id',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 8.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'ID',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'name',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 8.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Name',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'designation',
            label: Container(
                padding: EdgeInsets.all(8.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Designation',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'salary',
            label: Container(
                padding: EdgeInsets.all(8.0),
                alignment: Alignment.centerRight,
                child: Text('Salary'
                ))),
      ],
    ),
  );
}
  
{% endhighlight %}
{% endtabs %}

![flutter datagrid shows customized the sort icon position](images/sorting/flutter-datagrid-customized-sorticon-position.png)

## Set a custom sorting icon

`SfDataGrid` allows you to change the sort icon by using the [SfDataGridThemeData.sortIcon](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/sortIcon.html) property. The DataGrid should be wrapped inside the `SfDataGridTheme`. 

The `SfDataGridThemeData` and `SfDataGridTheme` classes are available in the [syncfusion_flutter_core](https://pub.dev/packages/syncfusion_flutter_core) package. So, import the following file.

By using the [Builder](https://api.flutter.dev/flutter/widgets/Builder-class.html) widget, you can change the icon based on each state of the sorting. You have to return the icons for all three states even if you want to change the icon for a specific state.

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_core/theme.dart';

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_core/theme.dart';
import 'package:syncfusion_flutter_datagrid/datagrid.dart';

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: SfDataGridTheme(
        data: SfDataGridThemeData(
          sortIcon: Builder(
            builder: (context) {
              Widget? icon;
              String columnName = '';
              context.visitAncestorElements((element) {
                if (element is GridHeaderCellElement) {
                  columnName = element.column.columnName;
                }
                return true;
              });
              var column = _employeeDataSource.sortedColumns
                  .where((element) => element.name == columnName)
                  .firstOrNull;
              if (column != null) {
                if (column.sortDirection == DataGridSortDirection.ascending) {
                  icon = const Icon(Icons.arrow_circle_up_rounded, size: 16);
                } else if (column.sortDirection ==
                    DataGridSortDirection.descending) {
                  icon = const Icon(Icons.arrow_circle_down_rounded, size: 16);
                }
              }
              return icon ??
                  const Icon(
                    Icons.sort_outlined,
                    size: 16,
                  );
            },
          ),
        ),
        child: SfDataGrid(
          source: _employeeDataSource,
          allowSorting: true,
          columns: <GridColumn>[
            GridColumn(
                columnName: 'id',
                label: Container(
                    padding: const EdgeInsets.symmetric(horizontal: 8.0),
                    alignment: Alignment.centerRight,
                    child: const Text(
                      'ID',
                    ))),
            GridColumn(
                columnName: 'name',
                label: Container(
                    padding: const EdgeInsets.symmetric(horizontal: 8.0),
                    alignment: Alignment.centerLeft,
                    child: const Text('Name'))),
            GridColumn(
                columnName: 'city',
                label: Container(
                    padding: const EdgeInsets.symmetric(horizontal: 8.0),
                    alignment: Alignment.centerLeft,
                    child: const Text('City'))),
            GridColumn(
                columnName: 'freight',
                label: Container(
                    padding: const EdgeInsets.symmetric(horizontal: 8.0),
                    alignment: Alignment.centerRight,
                    child: const Text('Freight'))),
          ],
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows custom the sort icon](images/sorting/flutter-datagrid-custom-sort-icon.jpg)

## Custom sorting

The datagrid allows sorting columns based on custom logic. For each column, provide different sorting criteria by overriding the following methods from the [DataGridSource](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource-class.html),

* **[performSorting](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/performSorting.html)** : Called when the sorting is applied to the column. Overriding this method gives complete control over sorting. You can handle the sorting completely in your own way. 
* **[compare](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/compare.html)** : You can override this method to compare two objects and return the sorting order based on the criteria.

### Sort columns based on string length

The following code shows how to perform custom sorting for the columns based on the string length by overriding the `compare` method.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource({required List<Employee> employees}) {
    dataGridRows = employees
        .map<DataGridRow>((dataGridRow) => DataGridRow(cells: [
              DataGridCell<int>(columnName: 'id', value: dataGridRow.id),
              DataGridCell<String>(columnName: 'name', value: dataGridRow.name),
              DataGridCell<String>(
                  columnName: 'designation', value: dataGridRow.designation),
              DataGridCell<int>(columnName: 'salary', value: dataGridRow.salary)
            ]))
        .toList();
  }

  List<DataGridRow> dataGridRows = [];

  @override
  List<DataGridRow> get rows => dataGridRows;

  @override
  DataGridRowAdapter? buildRow(DataGridRow row) {
    return DataGridRowAdapter(
        cells: row.getCells().map<Widget>((dataGridCell) {
      return Container(
          alignment: (dataGridCell.columnName == 'id' ||
                  dataGridCell.columnName == 'salary')
              ? Alignment.centerRight
              : Alignment.centerLeft,
          padding: EdgeInsets.symmetric(horizontal: 16.0),
          child: Text(
            dataGridCell.value.toString(),
            overflow: TextOverflow.ellipsis,
          ));
    }).toList());
  }

  @override
  int compare(DataGridRow? a, DataGridRow? b, SortColumnDetails sortColumn) {
    final String? value1 = a
        ?.getCells()
        .firstWhereOrNull((element) => element.columnName == sortColumn.name)
        ?.value;
    final String? value2 = b
        ?.getCells()
        .firstWhereOrNull((element) => element.columnName == sortColumn.name)
        ?.value;

    int? aLength = value1?.length;
    int? bLength = value2?.length;

    if (aLength == null || bLength == null) {
      return 0;
    }

    if (aLength.compareTo(bLength) > 0) {
      return sortColumn.sortDirection == DataGridSortDirection.ascending
          ? 1
          : -1;
    } else if (aLength.compareTo(bLength) == -1) {
      return sortColumn.sortDirection == DataGridSortDirection.ascending
          ? -1
          : 1;
    } else {
      return 0;
    }
  }
}

{% endhighlight %}
{% endtabs %}

>**NOTE**  
  Download demo application from [GitHub](https://github.com/SyncfusionExamples/how-to-sort-the-columns-based-on-length-of-the-text-in-Flutter-datagrid).

![flutter datagrid shows custom sorting for the columns based on string length](images/sorting/flutter-datagrid-custom-sorting.jpg)

### Case-insensitive sorting

The following code shows how to perform custom sorting for the columns based on the case-insensitive by overriding the `compare` method.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource({required List<Employee> employees}) {
    dataGridRows = employees
        .map<DataGridRow>((dataGridRow) => DataGridRow(cells: [
              DataGridCell<int>(columnName: 'id', value: dataGridRow.id),
              DataGridCell<String>(columnName: 'name', value: dataGridRow.name),
              DataGridCell<String>(
                  columnName: 'designation', value: dataGridRow.designation),
              DataGridCell<int>(columnName: 'salary', value: dataGridRow.salary)
            ]))
        .toList();
  }

  List<DataGridRow> dataGridRows = [];

  @override
  List<DataGridRow> get rows => dataGridRows;

  @override
  DataGridRowAdapter? buildRow(DataGridRow row) {
    return DataGridRowAdapter(
        cells: row.getCells().map<Widget>((dataGridCell) {
      return Container(
          alignment: (dataGridCell.columnName == 'id' ||
                  dataGridCell.columnName == 'salary')
              ? Alignment.centerRight
              : Alignment.centerLeft,
          padding: EdgeInsets.symmetric(horizontal: 16.0),
          child: Text(
            dataGridCell.value.toString(),
            overflow: TextOverflow.ellipsis,
          ));
    }).toList());
  }

  @override
  int compare(DataGridRow? a, DataGridRow? b, SortColumnDetails sortColumn) {
    if (sortColumn.name == 'name') {
      final String? value1 = a
          ?.getCells()
          .firstWhereOrNull((element) => element.columnName == sortColumn.name)
          ?.value
          .toString();
      final String? value2 = b
          ?.getCells()
          .firstWhereOrNull((element) => element.columnName == sortColumn.name)
          ?.value
          .toString();

      if (value1 == null || value2 == null) {
        return 0;
      }

      if (sortColumn.sortDirection == DataGridSortDirection.ascending) {
        return value1.toLowerCase().compareTo(value2.toLowerCase());
      } else {
        return value2.toLowerCase().compareTo(value1.toLowerCase());
      }
    }

    return super.compare(a, b, sortColumn);
  }
}

{% endhighlight %}
{% endtabs %}

>**NOTE**  
  Download demo application from [GitHub](https://github.com/SyncfusionExamples/how-to-perform-case-insensitive-sorting-in-flutter-datagrid).

![flutter datagrid shows custom sorting for the columns based on case-insensitive](images/sorting/flutter-datagrid-custom-sorting-case-insensitive.jpg)

## Perform sorting asynchronously

[performSorting](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/performSorting.html) method can be used to perform the sorting asynchronously. This method is called whenever the sorting is applied for each column.

The following example shows how to apply the sorting asynchronously for the underlying model collection instead of built-in sorting and apply the Future.delay for a specific time,

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

StreamController<bool> loadingController = StreamController<bool>();

class _MyHomePageState extends State<MyHomePage> {
  List<Employee> employees = <Employee>[];
  late EmployeeDataSource employeeDataSource;

  @override
  void initState() {
    super.initState();
    employees = getEmployeeDataAscending();
    employeeDataSource = EmployeeDataSource(employeeData: employees);
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: const Text('Syncfusion Flutter DataGrid'),
        ),
        body: StreamBuilder(
            stream: loadingController.stream,
            builder: (BuildContext context, AsyncSnapshot<bool> snapshot) {
              return Stack(children: [
                SfDataGrid(
                  source: employeeDataSource,
                  columnWidthMode: ColumnWidthMode.fill,
                  allowSorting: true,
                  allowMultiColumnSorting: true,
                  showSortNumbers: true,
                  gridLinesVisibility: GridLinesVisibility.both,
                  headerGridLinesVisibility: GridLinesVisibility.both,
                  columns: <GridColumn>[
                    GridColumn(
                        columnName: 'id',
                        label: Container(
                            padding: const EdgeInsets.all(16.0),
                            alignment: Alignment.centerRight,
                            child: const Text(
                              'ID',
                            ))),
                    GridColumn(
                        columnName: 'name',
                        label: Container(
                            padding: const EdgeInsets.all(8.0),
                            alignment: Alignment.centerLeft,
                            child: const Text('Name'))),
                    GridColumn(
                        columnName: 'designation',
                        label: Container(
                            padding: const EdgeInsets.all(8.0),
                            alignment: Alignment.centerLeft,
                            child: const Text(
                              'Designation',
                              overflow: TextOverflow.ellipsis,
                            ))),
                    GridColumn(
                        columnName: 'salary',
                        label: Container(
                            padding: const EdgeInsets.all(8.0),
                            alignment: Alignment.centerRight,
                            child: const Text('Salary'))),
                  ],
                ),
                if (snapshot.data==true)
                  const Center(
                    child: CircularProgressIndicator(),
                  ),
              ]);
            }));
  }
}

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource({required List<Employee> employeeData}) {
    _employeeData = employeeData
        .map<DataGridRow>((e) => DataGridRow(cells: [
              DataGridCell<int>(columnName: 'id', value: e.id),
              DataGridCell<String>(columnName: 'name', value: e.name),
              DataGridCell<String>(
                  columnName: 'designation', value: e.designation),
              DataGridCell<int>(columnName: 'salary', value: e.salary),
            ]))
        .toList();
  }

  List<DataGridRow> _employeeData = [];

  @override
  List<DataGridRow> get rows => _employeeData;

  @override
  DataGridRowAdapter buildRow(DataGridRow row) {
    return DataGridRowAdapter(
        cells: row.getCells().map<Widget>((e) {
      return Container(
        alignment: e.columnName == 'id' || e.columnName == 'salary'
            ? Alignment.centerRight
            : Alignment.centerLeft,
        padding: const EdgeInsets.all(8.0),
        child: Text(e.value.toString()),
      );
    }).toList());
  }

bool isSuspend =true;
  @override
  Future<void> performSorting(List<DataGridRow> rows) async {
    if(!isSuspend)
      return;
    if (sortedColumns.isEmpty) 
      return;
    loadingController.add(true);
    await Future<void>.delayed(const Duration(seconds: 2));
    loadingController.add(false);
    _employeeData.clear();
    for (int i = 0; i < sortedColumns.length; i++) {
      if(sortedColumns[i].sortDirection==DataGridSortDirection.ascending)
      {
    var employee2=getEmployeeDataAscending();
   _employeeData = employee2
       .map<DataGridRow>((e) => DataGridRow(cells: [
              DataGridCell<int>(columnName: 'id', value: e.id),
              DataGridCell<String>(columnName: 'name', value: e.name),
              DataGridCell<String>(
                  columnName: 'designation', value: e.designation),
              DataGridCell<int>(columnName: 'salary', value: e.salary),
            ]))
        .toList();
  isSuspend=false;     
  notifyListeners();
  }
  else if(sortedColumns[i].sortDirection==DataGridSortDirection.descending)
  {
    var employee2=getEmployeeDataDescending();
   _employeeData = employee2
       .map<DataGridRow>((e) => DataGridRow(cells: [
              DataGridCell<int>(columnName: 'id', value: e.id),
              DataGridCell<String>(columnName: 'name', value: e.name),
              DataGridCell<String>(
                  columnName: 'designation', value: e.designation),
              DataGridCell<int>(columnName: 'salary', value: e.salary),
            ]))
        .toList();
  isSuspend=false;     
  notifyListeners();
  }
 }
 isSuspend=true;
 }
}
  
{% endhighlight %}
{% endtabs %}