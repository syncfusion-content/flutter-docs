---
layout: post
title: Paging in Flutter DataGrid | DataPager | Syncfusion
description: Learn about the paging feature and how to customize its appearance in Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Paging in Flutter DataGrid (SfDataGrid)

The SfDataGrid interactively supports the manipulation of data using the [SfDataPager](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager-class.html) control. This provides support to load data in segments when dealing with large volumes of data. The `SfDataPager` can be placed above or below the SfDataGrid based on your requirement to easily manage data paging.

The SfDataGrid performs paging of data using the `SfDataPager`. To enable paging, follow these steps

* Create a new `SfDataPager` widget, and set the [SfDataGrid.DataGridSource](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource-class.html) to the [SfDataPager.delegate](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/delegate.html) property.
* Set the number of pages required to be displayed in the data pager by setting the [SfDataPager.pageCount](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/pageCount.html) property to a `double` value.
* Set the number of buttons that should be displayed in view by setting the [SfDataPager.visibleItemsCount](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/visibleItemsCount.html) property.
* Load the data for a specific page in the [handlePageChange](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/handlePageChange.html) method. This method is called for every page navigation from the data pager. The method notifies listeners to refresh the UI.

> **Note:**
>- The `SfDataPager.visibleItemsCount` property default value is 5.
>- Required imports - Ensure you have imported `syncfusion_flutter_datagrid`, `syncfusion_flutter_core`, and any data model classes. The `DataGridSource` is an abstract class that you must extend with your custom implementation.

The following code example illustrates using the `SfDataPager` with the SfDataGrid control:

{% tabs %}
{% highlight Dart %}

import 'package:intl/intl.dart';
import 'package:syncfusion_flutter_datagrid/datagrid.dart';
import 'package:syncfusion_flutter_core/theme.dart';

// Define OrderInfo model class
class OrderInfo {
  OrderInfo({
    required this.orderID,
    required this.customerID,
    required this.orderDate,
    required this.freight,
  });
  
  final int orderID;
  final String customerID;
  final DateTime orderDate;
  final double freight;
}

  final int _rowsPerPage = 15;
  final double _dataPagerHeight = 60.0;
  List<OrderInfo> _orders = [];
  List<OrderInfo> _paginatedOrders = [];
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
              pageCount: (_orders.length / _rowsPerPage).ceil().toDouble(),
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
    _paginatedOrders = _orders.isNotEmpty 
        ? _orders.getRange(0, _orders.length > _rowsPerPage ? _rowsPerPage : _orders.length).toList(growable: false)
        : [];
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

The [SfDataPager](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager-class.html) provides the [onPageNavigationStart](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/onPageNavigationStart.html) and [onPageNavigationEnd](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/onPageNavigationEnd.html) callbacks to listen to page navigation at the widget level.

Typically, these callbacks are used to show and hide a loading indicator during page transitions.

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
                  pageCount: (_orders.length / _rowsPerPage).ceil().toDouble(),
                  direction: Axis.horizontal,
                  onPageNavigationStart: (int pageIndex) {
                    // Customize this callback when page navigation begins
                  },
                  delegate: _orderInfoDataSource,
                  onPageNavigationEnd: (int pageIndex) {
                    // Customize this callback when page navigation completes
                  }))
        ])
      ]);
    }));
  }

{% endhighlight %}
{% endtabs %}

## Asynchronous data loading

You can load data asynchronously to the `SfDataPager` by overriding the [handlePageChange](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/handlePageChange.html) method and awaiting the data fetch operation.

Use the `onPageNavigationStart` and `onPageNavigationEnd` callbacks to show and hide a loading indicator when navigating between pages.

In the below example, we simulate asynchronous data loading with a 2000ms delay and display the loading indicator during this time.

{% tabs %}
{% highlight Dart %}

import 'package:intl/intl.dart';

  bool showLoadingIndicator = false;

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
                  pageCount: (_orders.length / _rowsPerPage).ceil().toDouble(),
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
    _paginatedOrders = _orders.isNotEmpty 
        ? _orders.getRange(0, _orders.length > _rowsPerPage ? _rowsPerPage : _orders.length).toList(growable: false)
        : [];
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

> **Note:** Download a complete demo application from [GitHub](https://github.com/SyncfusionExamples/how-to-show-loading-indicator-on-loading-page-in-flutter-datatable).


## Programmatic page navigation

The `SfDataPager` provides support to navigate between pages programmatically using a [DataPagerController](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataPagerController-class.html) with the following methods:

* [nextPage()](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataPagerController/nextPage.html) - Navigate to the next page
* [previousPage()](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataPagerController/previousPage.html) - Navigate to the previous page
* [lastPage()](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataPagerController/lastPage.html) - Navigate to the last page
* [firstPage()](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataPagerController/firstPage.html) - Navigate to the first page

The following code example shows how to navigate to the previous page programmatically:

{% tabs %}
{% highlight Dart %}

  late DataPagerController _controller;

  @override
  void initState() {
    super.initState();
    _controller = DataPagerController();
  }

  @override
  void dispose() {
    _controller.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(body: LayoutBuilder(builder: (context, constraint) {
      return Column(children: [
        MaterialButton(
          onPressed: () {
            _controller.previousPage();
          },
          child: Text('Move to Previous Page'),
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
                  pageCount: (_orders.length / _rowsPerPage).ceil().toDouble(),
                  direction: Axis.horizontal,
                )))
      ]);
    }));
  }

{% endhighlight %}
{% endtabs %}

## Show dropdown button to choose rows per page

Display a dropdown button option to select a different number of rows per page by defining the [onRowsPerPageChanged](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/onRowsPerPageChanged.html) callback. If it is null, no option will be provided to change the number of rows per page.

Use the [availableRowsPerPage](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/availableRowsPerPage.html) property to define the list of row counts displayed in the dropdown. The default value is [10, 15, 20].

> **Note:** You can view the dropdown button by horizontally scrolling the SfDataPager. The dropdown button option is not supported when the [direction](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/direction.html) property is set to vertical.

{% tabs %}
{% highlight Dart %}

  int _rowsPerPage = 10;
  List<Employee> employees = <Employee>[];
  late EmployeeDataSource employeeDataSource;
  double datapagerHeight = 70.0;
  final List<GridColumn> _column = <GridColumn>[
    GridColumn(columnName: 'id', label: Container(child: Text('ID'))),
    GridColumn(columnName: 'name', label: Container(child: Text('Name'))),
    GridColumn(columnName: 'designation', label: Container(child: Text('Designation'))),
    GridColumn(columnName: 'salary', label: Container(child: Text('Salary'))),
  ];

  @override
  void initState() {
    super.initState();
    employees = getEmployeeData();
    employeeDataSource = EmployeeDataSource(employeeData: employees);
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: const Text('Syncfusion Flutter DataGrid'),
        ),
        body: LayoutBuilder(
            builder: (BuildContext context, BoxConstraints constraints) {
          return Column(
            children: [
              Container(
                height: constraints.maxHeight - datapagerHeight,
                child: SfDataGrid(
                    source: employeeDataSource,
                    columnWidthMode: ColumnWidthMode.fill,
                    columns: _column),
              ),
              Container(
                  height: datapagerHeight,
                  child: SfDataPager(
                    delegate: employeeDataSource,
                    availableRowsPerPage: [10, 20, 30],
                    onRowsPerPageChanged: (int? rowsPerPage) {
                      setState(() {
                        _rowsPerPage = rowsPerPage!;
                        employeeDataSource.updateDataGridDataSource();
                      });
                    },
                    pageCount: ((employees.length / _rowsPerPage).ceil()).toDouble(),
                  )),
            ],
          );
        }));
  }

class EmployeeDataSource extends DataGridSource {
  /// Creates the employee data source class with required details.
  EmployeeDataSource({required List<Employee> employeeData}) {
    _employeeData = employeeData;
    _paginatedRows = employeeData;
    buildDataGridRow();
  }

  void buildDataGridRow() {
    _employeeDataGridRows = _paginatedRows
        .map<DataGridRow>((e) => DataGridRow(cells: [
              DataGridCell<int>(columnName: 'id', value: e.id),
              DataGridCell<String>(columnName: 'name', value: e.name),
              DataGridCell<String>(
                  columnName: 'designation', value: e.designation),
              DataGridCell<int>(columnName: 'salary', value: e.salary),
            ]))
        .toList();
  }

  List<DataGridRow> _employeeDataGridRows = [];
  List<Employee> _paginatedRows = [];
  List<Employee> _employeeData = [];

  @override
  List<DataGridRow> get rows => _employeeDataGridRows;

  @override
  DataGridRowAdapter buildRow(DataGridRow row) {
    return DataGridRowAdapter(
        cells: row.getCells().map<Widget>((e) {
      return Container(
        alignment: Alignment.center,
        padding: EdgeInsets.all(8.0),
        child: Text(e.value.toString()),
      );
    }).toList());
  }

  @override
  Future<bool> handlePageChange(int oldPageIndex, int newPageIndex) {
    final int startIndex = newPageIndex * _rowsPerPage;
    int endIndex = startIndex + _rowsPerPage;
    if (endIndex > _employeeData.length) {
      endIndex = _employeeData.length;
    }

    // Get a particular range from the data collection.
    if (startIndex < _employeeData.length &&
        endIndex <= _employeeData.length) {
      _paginatedRows = _employeeData.getRange(startIndex, endIndex).toList();
    } else {
      _paginatedRows = <Employee>[];
    }
    buildDataGridRow();
    notifyListeners();
    return Future<bool>.value(true);
  }

  void updateDataGridDataSource() {
    notifyListeners();
  }
}
{% endhighlight %}
{% endtabs %}

![flutter datapager with rowsperpage](images/paging/flutter_datapager_rowsperpage.gif)

## Orientation

`SfDataPager` allows you to arrange the navigation and page buttons either horizontally or vertically by using the [direction](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/direction.html) property. The `direction` property accepts an `Axis` enum value.

<table>
<tr>
<th>
Value 
</th>
<th>
Description</th>
</tr>
<tr>
<td>
Axis.horizontal
</td>
<td>
This is the default value. Arranges all navigation buttons and page number buttons horizontally.{{'![flutter datapager in horizontal direction](images/paging/flutter-datapager-direction-horizontal.png)'|markdownify}}
</td>
</tr>
<tr>
<td>
Axis.vertical
</td>
<td>
Arranges all navigation buttons and page number buttons vertically.{{'![flutter datapager in vertical direction](images/paging/flutter-datapager-direction-vertical.png)'|markdownify}}
</td>
</tr>
</table>


## Appearance

Customize the appearance of the SfDataPager using the [SfDataPagerThemeData](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataPagerThemeData-class.html) class within the [SfDataPagerTheme](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataPagerTheme-class.html) widget. Wrap the `SfDataPager` inside `SfDataPagerTheme` and configure the theme data.

> **Note:** Import the theming package: `import 'package:syncfusion_flutter_core/theme.dart';`

The following code example illustrates customizing the SfDataPager appearance:

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
          pageCount: (_orders.length / _rowsPerPage).ceil().toDouble(),
          direction: Axis.horizontal,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

![flutter datapager with customization](images/paging/flutter-datapager-customization.png)

### Set the padding between page items

The spacing between page number buttons and navigation buttons (first, last, previous, next) can be changed using the [itemPadding](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/itemPadding.html) property.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: const Text('Syncfusion Flutter DataGrid'),
        ),
        body: SfDataPager(
            itemPadding: EdgeInsets.all(8.0),
            pageCount: 5,
            delegate: employeeDataSource,
          ),
        );
  }

{% endhighlight %}
{% endtabs %}

> **Note:** The default value of `SfDataPager.itemPadding` is 5.0.

### Set the height and width of the page items

The default width and height of the page number buttons are 50 and 50, respectively. To customize the size of page number buttons, use the [itemWidth](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/itemWidth.html) and [itemHeight](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/itemHeight.html) properties. For customizing navigation button sizes (first, last, previous, next), use the [navigationItemHeight](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/navigationItemHeight.html) and [navigationItemWidth](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/navigationItemWidth.html) properties.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: const Text('Syncfusion Flutter DataGrid'),
        ),
        body: Center(
            child: SfDataPagerTheme(
          data: SfDataPagerThemeData(
            itemBorderWidth: 0.5,
            itemBorderColor: Colors.grey.shade400,
            itemBorderRadius: BorderRadius.circular(5),
          ),
          child: SfDataPager(
            pageCount: 5,
            visibleItemsCount: 2,
            itemWidth: 70,
            itemHeight: 55,
            navigationItemWidth: 70,
            navigationItemHeight: 55,
            delegate: employeeDataSource,
          ),
        )));
  }

{% endhighlight %}
{% endtabs %}

![flutter datapager with page button resizing](images/paging/flutter-datapager-page-item-resizing.png)

### Hide certain navigation page items

To hide specific navigation buttons, use the following properties:

 * [firstPageItemVisible](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/firstPageItemVisible.html) - Show/hide the first page button
 * [lastPageItemVisible](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/lastPageItemVisible.html) - Show/hide the last page button
 * [nextPageItemVisible](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/nextPageItemVisible.html) - Show/hide the next page button
 * [previousPageItemVisible](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/previousPageItemVisible.html) - Show/hide the previous page button

 > **Note:** The default value for all these properties is `true`.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: const Text('Syncfusion Flutter DataGrid'),
        ),
        body: SfDataPagerTheme(
          data: SfDataPagerThemeData(
              itemBorderWidth: 0.5,
              itemBorderColor: Colors.grey.shade400,
              itemBorderRadius: BorderRadius.circular(5),
              selectedItemColor: Colors.indigo.shade500),
          child: SfDataPager(
            firstPageItemVisible: false,
            lastPageItemVisible: false,
            pageCount: 5,
            visibleItemsCount: 3,
            navigationItemWidth: 100,
            delegate: employeeDataSource,
            pageItemBuilder: (String itemName) {
              if (itemName == 'Next') {
                return Center(
                  child: Text('Next'),
                );
              }
              if (itemName == 'Previous') {
                return Center(
                  child: Text('Previous'),
                );
              }
            },
            itemPadding: EdgeInsets.all(8.0),
          ),
        ));
  }

{% endhighlight %}
{% endtabs %}

![flutter datapager with page button resizing](images/paging/flutter_datagrid_resize_page_button.png)

## Change the number of visible items (buttons) in the view

You can control the number of page buttons displayed at once using the [visibleItemsCount](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/visibleItemsCount.html) property.

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
                pageCount: (_orders.length / _rowsPerPage).ceil().toDouble(),
                direction: Axis.horizontal,
              ),
            )
          ],
        );
      }));
  }

{% endhighlight %}
{% endtabs %}

## Load any widget in the page button

Customize the appearance of page buttons by providing a custom widget using the [pageItemBuilder](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataPager/pageItemBuilder.html) callback.

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
                      pageCount: (_orders.length / _rowsPerPage).ceil().toDouble(),
                      direction: Axis.horizontal,
                    )))
          ]);
        }));
  }

{% endhighlight %}
{% endtabs %}

## Alternative: Automatic pagination without manual handlePageChange

By default, when you override the `handlePageChange` method, you manually manage which rows to display for each page. However, if you want automatic pagination where sorting and filtering apply to all rows before pagination, do not override the `handlePageChange` method in the `DataGridSource` class.

When `handlePageChange` is not overridden, the SfDataGrid automatically splits the rows required for each page based on the `pageCount` property using the following formula: `pageCount = (total rows / rowsPerPage)`.

Use the [rowsPerPage](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/rowsPerPage.html) property on the SfDataGrid to specify how many rows should appear per page. This approach ensures that operations like sorting apply to the entire dataset before pagination occurs.

{% tabs %}
{% highlight Dart %}

  final int _rowsPerPage = 15;
  final double _dataPagerHeight = 60.0;
  List<OrderInfo> _orders = [];

  @override
  Widget build(BuildContext context) {
    return Scaffold(body: LayoutBuilder(builder: (context, constraint) {
      return Column(children: [
        SizedBox(
            height: constraint.maxHeight - _dataPagerHeight,
            width: constraint.maxWidth,
            child: _buildDataGrid(constraint)),
        Container(
            height: _dataPagerHeight,
            child: SfDataPager(
              delegate: _orderInfoDataSource,
              pageCount: (_orders.length / _rowsPerPage).ceil().toDouble(),
              direction: Axis.horizontal,
            ))
      ]);
    }));
  }

  Widget _buildDataGrid(BoxConstraints constraint) {
    return SfDataGrid(
        source: _orderInfoDataSource,
        columnWidthMode: ColumnWidthMode.fill,
        rowsPerPage: _rowsPerPage,
        allowSorting: true,
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
    buildDataGridRows();
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

  // Note: handlePageChange is NOT overridden in this example.
  // The SfDataGrid automatically handles pagination and sorting.

  void buildDataGridRows() {
    dataGridRows = _orders.map<DataGridRow>((dataGridRow) {
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

![sorting applied for all the rows in flutter datagrid paging](images/paging/sorting-applied-for-all-the-rows-in-flutter-datagrid-paging.gif)
