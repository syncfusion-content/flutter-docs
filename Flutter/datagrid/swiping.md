---
layout: post
title: Swiping in Flutter DataGrid | DataTable | Syncfusion
description: Learn here all about how to swipe the data rows in both directions in Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Swiping in Flutter DataGrid (SfDataGrid)

The Flutter DataTable provides support to swipe a row by setting the [SfDataGrid.allowSwiping](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/allowSwiping.html) property to true. Swipe actions will be displayed when swiping a row from `left to right` or `right to left` direction. The swipe dragging gesture can be restricted to a certain point on the row by setting the [SfDataGrid.swipeMaxOffset](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/swipeMaxOffset.html) property.

## Swipe action builders

The Flutter DataTable enables you to load the desired widget behind the swiped row by using [SfDataGrid.startSwipeActionsBuilder](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/startSwipeActionsBuilder.html) and [SfDataGrid.endSwipeActionsBuilder](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/endSwipeActionsBuilder.html) properties. The swipe widget's width that loads from the actions builder is arranged based on the `SfDataGrid.swipeMaxOffset` property and it takes height based on the current swiping row height.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

@override
Widget build(BuildContext context) {
  return SfDataGrid(
    allowSwiping: true,
    swipeMaxOffset: 100.0,
    source: employeeDataSource,
      startSwipeActionsBuilder: 
          (BuildContext context, DataGridRow row, int rowIndex) {
        return GestureDetector(
          onTap: () {
            _employeeDataSource.dataGridRows.insert(
            rowIndex,
            DataGridRow(cells: [
              DataGridCell(value: 1011, columnName: 'id'),
              DataGridCell(value: 'Tom Bass', columnName: 'name'),
              DataGridCell(value: 'Developer', columnName: 'designation'),
              DataGridCell(value: 20000, columnName: 'salary')
            ]));
            _employeeDataSource.updateDataSource();
          },
          child: Container(
          color: Colors.greenAccent,
          child: Center(
            child: Icon(Icons.add),
          ),
        ),
      );
    },
    endSwipeActionsBuilder: 
        (BuildContext context, DataGridRow row, int rowIndex) {
      return GestureDetector(
        onTap: () {
          _employeeDataSource.dataGridRows.removeAt(rowIndex);
          _employeeDataSource.updateDataSource();
        },
        child: Container(
          color: Colors.redAccent,
          child: Center(
            child: Icon(Icons.delete),
          ),
        ),
      );
    },
    columns: <GridColumn>[
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
        columnName: 'designation',
        label: Container(
          padding: EdgeInsets.symmetric(horizontal: 16.0),
          alignment: Alignment.centerLeft,
          child: Text(
            'Designation',
            overflow: TextOverflow.ellipsis,
          ))),
      GridColumn(
        columnName: 'salary',
        label: Container(
          padding: EdgeInsets.symmetric(horizontal: 16.0),
          alignment: Alignment.centerRight,
          child: Text(
            'Salary',
            overflow: TextOverflow.ellipsis,
          ))),
    ],
  );
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows swiping a row in both directions](images/swiping/flutter-datagrid-swiping.gif)

## Swipe callbacks

The data grid provides the following callbacks to notify the swiping stages:  

* [onSwipeStart](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/onSwipeStart.html): Called when the swipe offset changes from its initial value. The swipe action can be canceled by return `false`.
* [onSwipeUpdate](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/onSwipeUpdate.html): Called while swiping a row is in progress. The swipe action can be canceled by return `false`.
* [onSwipeEnd](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/onSwipeEnd.html): called when the swipe offset value reaches the `SfDataGrid.maxSwipeOffset` indicating that the swipe action is completed.

The swipe callbacks provide the following properties in their arguments:

* [RowIndex](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSwipeUpdateDetails/rowIndex.html): Defines the swiping row index.
* [SwipeDirection](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSwipeUpdateDetails/swipeDirection.html): Defines the swipe direction of the swiped row.
* [SwipeOffset](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSwipeUpdateDetails/swipeOffset.html): Defines the current swipe offset of the row being swiped.

By handling the swipe callbacks, you can use these properties value from the arguments to perform any desired action such as deleting the row, editing the data, etc.

## Customized swipes delete functionality

You can perform customized swipe functionality using the swiping callbacks. The below example shows how to delete a row when swiping a data row from one to another end.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

@override
Widget build(BuildContext context) {
  return LayoutBuilder(builder: (context, constraints) {
    return SfDataGrid(
      allowSwiping: true,
      swipeMaxOffset: constraints.maxWidth,
      source: employeeDataSource,
      startSwipeActionsBuilder: 
          (BuildContext context, DataGridRow row, int rowIndex) {
        return GestureDetector(
          onTap: () {
            _employeeDataSource.dataGridRows.removeAt(rowIndex);
            _employeeDataSource.updateDataSource();
          },
          child: Container(
            color: Colors.green,
            padding: EdgeInsets.only(left: 30.0),
            alignment: Alignment.centerLeft,
            child: Text('Delete', style: TextStyle(color: Colors.white)),
          ),
        );
      },
      onSwipeUpdate: (details) {
        isReachedCenter =
            (details.swipeOffset >= constraints.maxWidth / 2) ? true : false;
        return true;
      },
      onSwipeEnd: (details) async {
        if (isReachedCenter &&
          _employeeDataSource.dataGridRows.isNotEmpty) {
            _employeeDataSource.dataGridRows.removeAt(details.rowIndex);
          _employeeDataSource.updateDataSource();
          isReachedCenter = false;
        }
      },
      columns: <GridColumn>[
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
          columnName: 'designation',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerLeft,
            child: Text(
              'Designation',
              overflow: TextOverflow.ellipsis,
            ))),
        GridColumn(
          columnName: 'salary',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              'Salary',
              overflow: TextOverflow.ellipsis,
            ))),
      ],
    );
  });
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows customized swiping delete functionality](images/swiping/flutter-datagrid-customized-swiping-delete-funtionality.gif)