---
layout: post
title: Paging in Flutter DataGrid | DataPager | Syncfusion
description: Learn here all about paging feature and how to customize its apperance in Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Paging in Flutter DataGrid (SfDataGrid)

The datagrid interactively supports the manipulation of data using [SfDataPager](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager-class.html) control. This provides support to load data in segments when dealing with large volumes of data. `SfDataPager` can be placed above or below based on the requirement to easily manage data paging.

The datagrid performs paging of data using the `SfDataPager`. To enable paging, follow below procedure

* Create a new `SfDataPager` widget, and set the [SfDataGrid.DataGridSource](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource-class.html) to the [SfDataPager.delegate](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/delegate.html) property.
* Set the number of pages required to be displayed in data pager by setting the [SfDataPager.pageCount](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/pageCount.html) property.
* Set the number of buttons that should be displayed in view by setting the [SfDataPager.visibleItemsCount](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/visibleItemsCount.html) property.
* You can load the data for the specific page in `handlePageChanges` method. This method is called for every page navigation from data pager.

N> The `SfDataPager.visibleItemsCount` property default value is 5.

The following code example illustrates using `SfDataPager` with the datagrid control:

{% tabs %}
{% highlight Dart %}

final int rowsPerPage = 15;

final double dataPagerHeight = 60.0;

List<OrderInfo> orders = [];

List<OrderInfo> paginatedOrders = [];

final OrderInfoDataSource _orderInfoDataSource = OrderInfoDataSource();

@override
Widget build(BuildContext context) {
  return LayoutBuilder(builder: (context, constraint) {
    return Column(children: [
      SizedBox(
          height: constraint.maxHeight - _dataPagerHeight,
          width: constraint.maxWidth,
          child: _buildDataGrid(constraint)),
      Container(
          height: _dataPagerHeight,
          child: SfDataPager(
            delegate: _orderInfoDataSource,
            pageCount: _orders.length / _rowsPerPage,
            direction: Axis.horizontal,
          ))
    ]);
  });
}
Widget _buildDataGrid(BoxConstraints constraint) {
  return SfDataGrid(
      source: _orderInfoDataSource,
      columnWidthMode: ColumnWidthMode.fill,
      columns: <GridColumn>[
        GridColumn(
            columnName: 'orderID',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'Order ID',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'customerID',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Customer Name',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'orderDate',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'Order Date',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'freight',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.center,
                child: Text(
                  'Freight',
                  overflow: TextOverflow.ellipsis,
                )))
      ]);
}

class OrderInfoDataSource extends DataGridSource {
  OrderInfoDataSource() {
    _paginatedOrders = _orders.getRange(0, 19).toList(growable: false);
    buildPaginatedDataGridRows();
  }

  List<DataGridRow> dataGridRows = [];

  @override
  List<DataGridRow> get rows => dataGridRows;

  @override
  DataGridRowAdapter? buildRow(DataGridRow row) {
    return DataGridRowAdapter(
        cells: row.getCells().map<Widget>((dataGridCell) {
      if (dataGridCell.columnName == 'orderID') {
        return Container(
          padding: EdgeInsets.symmetric(horizontal: 16.0),
          alignment: Alignment.centerRight,
          child: Text(
            dataGridCell.value.toString(),
            overflow: TextOverflow.ellipsis,
          ),
        );
      } else if (dataGridCell.columnName == 'customerID') {
        return Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerLeft,
            child: Text(
              dataGridCell.value.toString(),
              overflow: TextOverflow.ellipsis,
            ));
      } else if (dataGridCell.columnName == 'orderDate') {
        return Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              DateFormat.yMd().format(dataGridCell.value).toString(),
              overflow: TextOverflow.ellipsis,
            ));
      } else {
        return Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.center,
            child: Text(
              NumberFormat.currency(locale: 'en_US', symbol: '\$')
                  .format(dataGridCell.value)
                  .toString(),
              overflow: TextOverflow.ellipsis,
            ));
      }
    }).toList());
  }

  @override
  Future<bool> handlePageChange(int oldPageIndex, int newPageIndex) async {
    int startIndex = newPageIndex * _rowsPerPage;
    int endIndex = startIndex + _rowsPerPage;
    if (startIndex < _orders.length && endIndex <= _orders.length) {
      _paginatedOrders =
          _orders.getRange(startIndex, endIndex).toList(growable: false);
      buildPaginatedDataGridRows();
      notifyListeners();
    } else {
      _paginatedOrders = [];
    }

    return true;
  }

  void buildPaginatedDataGridRows() {
    dataGridRows = _paginatedOrders.map<DataGridRow>((dataGridRow) {
      return DataGridRow(cells: [
        DataGridCell(columnName: 'orderID', value: dataGridRow.orderID),
        DataGridCell(columnName: 'customerID', value: dataGridRow.customerID),
        DataGridCell(columnName: 'orderDate', value: dataGridRow.orderDate),
        DataGridCell(columnName: 'freight', value: dataGridRow.freight),
      ]);
    }).toList(growable: false);
  }
}

{% endhighlight %}
{% endtabs %}

![flutter datapager with datagrid](images/paging/flutter-datapager.png)

## Callbacks

The SfDataPager provides [onPageNavigationStart](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/onPageNavigationStart.html) and [onPageNavigationEnd](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/onPageNavigationEnd.html) callbacks to listen the page navigation in widget level. 

Typically, these callbacks are used to show and hide loading indicator.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(body: LayoutBuilder(builder: (context, constraints) {
    return Row(children: [
      Column(children: [
        SizedBox(
            height: constraints.maxHeight - 60,
            width: constraints.maxWidth,
            child: _buildDataGrid(constraints)),
        Container(
            height: 60,
            width: constraints.maxWidth,
            child: SfDataPager(
                pageCount: _orders.length / _rowsPerPage,
                direction: Axis.horizontal,
                onPageNavigationStart: (int pageIndex) {
                  //You can do your customization
                },
                delegate: _orderInfoDataSource,
                onPageNavigationEnd: (int pageIndex) {
                  //You can do your customization
                }))
      ])
    ]);
  }));
}

{% endhighlight %}
{% endtabs %}

## Asynchronous data loading

You can load the data asynchronously to the `SfDataPager` by overriding the `handlePageChange` method and await the method while loading the data.

You can use `onPageNavigationStart` and `onPageNavigationEnd` callbacks to show and hide the loading indicator when navigating between pages.

In the below example, we have set await for 2000ms and displayed the loading indicator until 2000ms.

{% tabs %}
{% highlight Dart %}

bool showLoadingIndicator = true;

@override
Widget build(BuildContext context) {
  return Scaffold(body: LayoutBuilder(builder: (context, constraints) {
    return Row(children: [
      Column(children: [
        SizedBox(
            height: constraints.maxHeight - 60,
            width: constraints.maxWidth,
            child: _buildStack(constraints)),
        Container(
            height: 60,
            width: constraints.maxWidth,
            child: SfDataPager(
                pageCount: _orders.length / _rowsPerPage,
                direction: Axis.horizontal,
                onPageNavigationStart: (int pageIndex) {
                  setState(() {
                    showLoadingIndicator = true;
                  });
                },
                delegate: _orderInfoDataSource,
                onPageNavigationEnd: (int pageIndex) {
                  setState(() {
                    showLoadingIndicator = false;
                  });
                }))
      ])
    ]);
  }));
}

Widget _buildStack(BoxConstraints constraints) {
  List<Widget> _getChildren() {
    final List<Widget> stackChildren = [];
    stackChildren.add(_buildDataGrid(constraints));

    if (showLoadingIndicator) {
      stackChildren.add(Container(
          color: Colors.black12,
          width: constraints.maxWidth,
          height: constraints.maxHeight,
          child: Align(
              alignment: Alignment.center,
              child: CircularProgressIndicator(
                strokeWidth: 3,
              ))));
    }

    return stackChildren;
  }

  return Stack(
    children: _getChildren(),
  );
}

class OrderInfoDataSource extends DataGridSource {
  OrderInfoDataSource() {
    _paginatedOrders = _orders.getRange(0, 19).toList(growable: false);
    buildPaginatedDataGridRows();
  }

  List<DataGridRow> dataGridRows = [];

  @override
  List<DataGridRow> get rows => dataGridRows;

  @override
  DataGridRowAdapter? buildRow(DataGridRow row) {
    return DataGridRowAdapter(
        cells: row.getCells().map<Widget>((dataGridCell) {
      if (dataGridCell.columnName == 'orderID') {
        return Container(
          padding: EdgeInsets.symmetric(horizontal: 16.0),
          alignment: Alignment.centerRight,
          child: Text(
            dataGridCell.value.toString(),
            overflow: TextOverflow.ellipsis,
          ),
        );
      } else if (dataGridCell.columnName == 'customerID') {
        return Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerLeft,
            child: Text(
              dataGridCell.value.toString(),
              overflow: TextOverflow.ellipsis,
            ));
      } else if (dataGridCell.columnName == 'orderDate') {
        return Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              DateFormat.yMd().format(dataGridCell.value).toString(),
              overflow: TextOverflow.ellipsis,
            ));
      } else {
        return Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.center,
            child: Text(
              NumberFormat.currency(locale: 'en_US', symbol: '\$')
                  .format(dataGridCell.value)
                  .toString(),
              overflow: TextOverflow.ellipsis,
            ));
      }
    }).toList());
  }

  @override
  Future<bool> handlePageChange(int oldPageIndex, int newPageIndex) async {
    int startIndex = newPageIndex * _rowsPerPage;
    int endIndex = startIndex + _rowsPerPage;
    if (startIndex < _orders.length && endIndex <= _orders.length) {
      await Future.delayed(Duration(milliseconds: 2000));
      _paginatedOrders =
          _orders.getRange(startIndex, endIndex).toList(growable: false);
      buildPaginatedDataGridRows();
      notifyListeners();
    } else {
      _paginatedOrders = [];
    }

    return true;
  }

  void buildPaginatedDataGridRows() {
    dataGridRows = _paginatedOrders.map<DataGridRow>((dataGridRow) {
      return DataGridRow(cells: [
        DataGridCell(columnName: 'orderID', value: dataGridRow.orderID),
        DataGridCell(columnName: 'customerID', value: dataGridRow.customerID),
        DataGridCell(columnName: 'orderDate', value: dataGridRow.orderDate),
        DataGridCell(columnName: 'freight', value: dataGridRow.freight),
      ]);
    }).toList(growable: false);
  }
}

{% endhighlight %}
{% endtabs %}

![flutter datapager with asynchronous loading](images/paging/flutter-datapager-asynchronous-loading.gif)

>**NOTE**  
  Download demo application from [GitHub](https://github.com/SyncfusionExamples/how-to-show-loading-indicator-on-loading-page-in-flutter-datatable).


## Programmatic page navigation

The `SfDataPager` provides the support to navigate between the pages programmatically using [controller](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController-class.html) with following options,

* [nextPage](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataPagerController/nextPage.html) 
* [previousPage](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataPagerController/previousPage.html) 
* [LastPage](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataPagerController/lastPage.html)
* [firstPage](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataPagerController/firstPage.html)

The following code example shows how to navigate the previous page programmatically,

{% tabs %}
{% highlight Dart %}

DataPagerController _controller = DataPagerController();

@override
Widget build(BuildContext context) {
  return Scaffold(body: LayoutBuilder(builder: (context, constraint) {
    return Column(children: [
      MaterialButton(
        onPressed: () {
          _controller.previousPage();
        },
        child: Text('Move Previous page'),
      ),
      SizedBox(
          height: constraint.maxHeight - 120,
          width: constraint.maxWidth,
          child: _buildDataGrid(constraint)),
      Container(
          height: 60,
          child: Align(
              alignment: Alignment.center,
              child: SfDataPager(
                delegate: _orderInfoDataSource,
                initialPageIndex: 2,
                controller: _controller,
                pageCount: _orders.length / _rowsPerPage,
                direction: Axis.horizontal,
              )))
    ]);
  }));
}

{% endhighlight %}
{% endtabs %}


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

Import the following class from the [syncfusion_flutter_core](https://pub.dev/packages/syncfusion_flutter_core) package.

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
        pageCount: _orders.length / _rowsPerPage,
        direction: Axis.horizontal,
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![flutter datapager with customization](images/paging/flutter-datapager-customization.png)

## Change the number of visible items (buttons) in view

You can change the number of visible items i.e. page buttons in view by using the [SfDataPager.visibleItemsCount](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/visibleItemsCount.html).

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      appBar: AppBar(
        title: Text('Flutter DataGrid Sample'),
      ),
      body: LayoutBuilder(builder: (context, constraint) {
        return Column(
          children: [
            SizedBox(
                height: constraint.maxHeight - _dataPagerHeight,
                width: constraint.maxWidth,
                child: _buildDataGrid(constraint)),
            Container(
              height: _dataPagerHeight,
              child: SfDataPager(
                visibleItemsCount: 1,
                delegate: _orderInfoDataSource,
                pageCount: _orders.length / _rowsPerPage,
                direction: Axis.horizontal,
              ),
            )
          ],
        );
      }));
}

{% endhighlight %}
{% endtabs %}

## Load any widget in page button

You can load any widget to page button by using [SfDataPager.pageItemBuilder](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/pageItemBuilder.html).

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      appBar: AppBar(
        title: Text('Flutter DataGrid Sample'),
      ),
      body: LayoutBuilder(builder: (context, constraint) {
        return Column(children: [
          SizedBox(
              height: constraint.maxHeight - _dataPagerHeight,
              width: constraint.maxWidth,
              child: _buildDataGrid(constraint)),
          Container(
              height: _dataPagerHeight,
              child: SfDataPagerTheme(
                  data: SfDataPagerThemeData(
                    itemBorderColor: Colors.blue,
                    itemBorderWidth: 1,
                    backgroundColor: Colors.transparent,
                    itemBorderRadius: BorderRadius.circular(0),
                  ),
                  child: SfDataPager(
                    pageItemBuilder: (String value) {
                      return Container(
                          child: Text(
                        value,
                        style: TextStyle(
                            fontSize: 10, fontWeight: FontWeight.w700),
                      ));
                    },
                    delegate: _orderInfoDataSource,
                    pageCount: _orders.length / _rowsPerPage,
                    direction: Axis.horizontal,
                  )))
        ]);
      }));
}
{% endhighlight %}
{% endtabs %}


