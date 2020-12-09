---
layout: post
title: Paging for Syncfusion Flutter DataGrid | DataTable
description: Learn how to create Syncfusion Flutter DataPager with DataGrid and customize the apperance of the DataPager.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Paging in Flutter (SfDataGrid)

The datagrid interactively supports the manipulation of data using [SfDataPager](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager-class.html) control. This provides support to load data in segments when dealing with large volumes of data. `SfDataPager` can be placed above or below based on the requirement to easily manage data paging.

The datagrid performs paging of data using the `SfDataPager`. To enable paging, follow below procedure

* Create a new `SfDataPager` widget, and set the [SfDataGrid.DataGridSource](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource-class.html) to the [SfDataPager.delegate](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/delegate.html) property.
* Set the number of rows to be displayed on a page by setting the [SfDataPager.rowsPerPage](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/rowsPerPage.html) property.
* Set the number of buttons that should be displayed in view by setting the [SfDataPager.visibleItemsCount](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/visibleItemsCount.html) property.
* Override the [SfDataPager.delegate.rowCount](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataPagerDelegate/rowCount.html) property and [SfDataPager.delegate.handlePageChanges](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataPagerDelegate/handlePageChange.html) method in `SfDataGrid.DataGridSource`. 
* You can load the data for the specific page in `handlePageChanges` method. This method is called for every page navigation from data pager.

N> The `SfDataPager.visibleItemsCount` property default value is 5.

The following code example illustrates using `SfDataPager` with the datagrid control:

{% tabs %}
{% highlight Dart %}

List<OrderInfo> paginatedDataSource = [];

final OrderInfoDataSource _orderInfoDataSource = OrderInfoDataSource();

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
                  source: _orderInfoDataSource,
                  columnWidthMode: ColumnWidthMode.fill,
                  columns: <GridColumn>[
                    GridNumericColumn(
                        mappingName: 'orderID', headerText: 'Order ID'),
                    GridTextColumn(
                        mappingName: 'customerID',
                        headerText: 'Customer Name'),
                    GridDateTimeColumn(
                        mappingName: 'orderDate', headerText: 'Order Date'),
                    GridNumericColumn(
                        mappingName: 'freight', headerText: 'Freight'),
                  ]),
            ),
            Container(
              height: 60,
              child: SfDataPager(
                delegate: _orderInfoDataSource,
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

class OrderInfoDataSource extends DataGridSource<OrderInfo> {
  @override
  List<OrderInfo> get dataSource => paginatedDataSource;

  @override
  Object getValue(OrderInfo orderInfos, String columnName) {
    switch (columnName) {
      case 'orderID':
        return orderInfos.orderID;
        break;
      case 'customerID':
        return orderInfos.customerID;
        break;
      case 'freight':
        return orderInfos.freight;
        break;
      case 'orderDate':
        return orderInfos.orderData;
        break;
      default:
        return '';
        break;
    }
  }

  @override
  int get rowCount => orderInfos.length;

  @override
  Future<bool> handlePageChange(int oldPageIndex, int newPageIndex,
      int startRowIndex, int rowsPerPage) async {
    int endIndex = startRowIndex + rowsPerPage;
    if (endIndex > orderInfos.length) {
      endIndex = orderInfos.length - 1;
    }
    
    paginatedDataSource = List.from(
        orderInfos.getRange(startRowIndex, endIndex).toList(growable: false));
    notifyListeners();
    return true;
  }
}

{% endhighlight %}
{% endtabs %}

![flutter datapager with datagrid](images/paging/flutter-datapager.png)

## Asynchronous data loading

You can load the data asynchronously to the `SfDataPager` by overriding the `handlePageChange` method and await the method while loading the data.

In the below example, we have set await for 2000ms and displayed the loading indicator until 2000ms.

{% tabs %}
{% highlight Dart %}

final OrderInfoDataSource _orderInfoDataSource = OrderInfoDataSource();

bool showLoadingIndicator = true;

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: LayoutBuilder(
      builder: (context, constraints) {
        return Row(children: [
          Column(
            children: [
              SizedBox(
                  height: constraints.maxHeight - 60,
                  width: constraints.maxWidth,
                  child: loadDataGrid(constraints)),
              Container(
                height: 60,
                width: constraints.maxWidth,
                child: SfDataPager(
                  delegate: _orderInfoDataSource,
                  rowsPerPage: 20,
                  direction: Axis.horizontal,
                ),
              )
            ],
          ),
        ]);
      },
    ),
  );
}

Widget getDataGrid(BoxConstraints constraint) {
  return SfDataGrid(
      source: _orderInfoDataSource,
      columnWidthMode: ColumnWidthMode.fill,
      columns: <GridColumn>[
        GridNumericColumn(mappingName: 'orderID', headerText: 'Order ID'),
        GridTextColumn(
            mappingName: 'customerID', headerText: 'Customer Name'),
        GridDateTimeColumn(
            mappingName: 'orderDate', headerText: 'Order Date'),
        GridNumericColumn(mappingName: 'freight', headerText: 'Freight'),
      ]);
}

Widget loadDataGrid(BoxConstraints constraints) {
  List<Widget> _getChildren() {
    final List<Widget> stackChildren = [];
    if (paginatedDataSource.isNotEmpty) {
      stackChildren.add(getDataGrid(constraints));
    }

    if (showLoadingIndicator) {
      stackChildren.add(Container(
        color: Colors.black12,
        width: constraints.maxWidth,
        height: constraints.maxHeight,
        child: Align(
          alignment: Alignment.center,
          child: CircularProgressIndicator(
            strokeWidth: 3,
          ),
        ),
      ));
    }

    return stackChildren;
  }

  return Stack(
    children: _getChildren(),
  );
}

class OrderInfoDataSource extends DataGridSource<OrderInfo> {
  @override
  Future<bool> handlePageChange(int oldPageIndex, int newPageIndex,
      int startRowIndex, int rowsPerPage) async {
    int endIndex = startRowIndex + rowsPerPage;
    if (endIndex > orderInfos.length) {
      endIndex = orderInfos.length - 1;
    }

    // Show the circle progress indicator
    showLoadingIndicator = true;
    notifyListeners();
    await Future.delayed(Duration(milliseconds: 2000));

    // hide the circle progress indicator
    showLoadingIndicator = false;

    paginatedDataSource = List.from(
        orderInfos.getRange(startRowIndex, endIndex).toList(growable: false));
    notifyListeners();
    return true;
  }
}

{% endhighlight %}
{% endtabs %}

![flutter datapager with asynchronous loading](images/paging/flutter-datapager-asynchronous-loading.gif)

## Orientation

`SfDataPager` allows you to arrange the child elements either horizontally or vertically. This can be achieved by using the [direction](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/direction.html) Property. `direction` is an Enum type.

<table>
<tr>
<th>
Enum 
</th>
<th>
Description</th>
</tr>
<tr>
<td>
horizontal
</td>
<td>
This is the default enum value for direction. Arranges all the navigation buttons and numeric buttons horizontally.{{'![flutter datapager in horizontal direction](images/paging/flutter-datapager-direction-horizontal.png)'|markdownify}}
</td>
</tr>
<tr>
<td>
vertical
</td>
<td>
Arranges all the navigation buttons and numeric buttons vertically by setting Axis.vertical to direction property.{{'![flutter datapager in vertical direction](images/paging/flutter-datapager-direction-vertical.png)'|markdownify}}
</td>
</tr>
</table>


## Appearance

SfDataPager allows to customize the appearance of the data pager using the [SfDataPagerThemeData](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataPagerThemeData-class.html) in [SfDataPagerTheme](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataPagerTheme-class.html). The `SfDataPager` should be wrapped inside the `SfDataPagerTheme`.

Import the following class from the syncfusion_flutter_core package.

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_core/theme.dart';

{% endhighlight %}
{% endtabs %}

The following code example illustrates using `SfDataPagerThemeData` with the data pager control

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
      delegate: _orderInfoDataSource,
      rowsPerPage: 20,
      direction: Axis.horizontal,
    ),
  ));
}

{% endhighlight %}
{% endtabs %}

![flutter datapager with customization](images/paging/flutter-datapager-customization.png)