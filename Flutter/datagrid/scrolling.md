---
layout: post
title: Scrolling in Flutter DataGrid | DataTable | Syncfusion
description: Learn here all about scrolling features of Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Scrolling in Flutter DataGrid (SfDataGrid)

SfDataGrid provides support to scroll the content in both the horizontal and vertical direction. 

## Show Scrollbars always

You can show horizontal and vertical scrollbars always by using the [SfDataGrid.isScrollbarAlwaysShown](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/isScrollbarAlwaysShown.html) property. When the `isScrollbarAlwaysShown` is set to false, the scrollbar will be shown during scrolling and will fade out otherwise. When it is true, the scrollbar will always be visible and never fade out even after the scrolling.

N> The default value of `isScrollbarAlwaysShown` is false.

{% tabs %}
{% highlight Dart %}

 @override
 Widget build(BuildContext context) {
    return Scaffold(
      body: SfDataGrid(
        source: _employeeDataSource,
        isScrollbarAlwaysShown: true,
        columns: [
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
    );
  }

{% endhighlight %}
{% endtabs %}

## Setting scroll physics for scroll bars

SfDataGrid allows you to set the [ScrollPhysics](https://api.flutter.dev/flutter/widgets/ScrollPhysics-class.html) for horizontal and vertical scrollbars to control how the scroll view should respond to user input by using [horizontalScrollPhysics](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/horizontalScrollPhysics.html) and [verticalScrollPhysics](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/verticalScrollPhysics.html) properties respectively.

N> The default values of `horizontalScrollPhysics` and `verticalScrollPhysics` properties are `AlwaysScrollableScrollPhysics()`.

The following example shows how to disable the horizontal and vertical scrolling by setting `NeverScrollableScrollPhysics()`.

{% tabs %}
{% highlight Dart %}

 @override
 Widget build(BuildContext context) {
    return Scaffold(
      body: SfDataGrid(
        source: _employeeDataSource,
        horizontalScrollPhysics: NeverScrollableScrollPhysics(),
        verticalScrollPhysics: NeverScrollableScrollPhysics(),
        columns: [
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
    );
  }

{% endhighlight %}
{% endtabs %}

## Programmatic scrolling

The Flutter DataTable provides support to scroll to a particular row and column index programmatically.

### Scroll to cell

Scroll programmatically to a particular cell can be achieved by passing the row and column index in the [scrollToCell](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/scrollToCell.html) method. SfDataGrid allows to enable or disable the scrolling animation by passing `true` to the `canAnimate` parameter in `scrollToCell` method. 

N> The default value of `canAnimate` is `false`.

{% tabs %}
{% highlight Dart %}

final DataGridController _controller = DataGridController();

 @override
 Widget build(BuildContext context) {
    return Scaffold(
      body: Column(children: [
        FlatButton(
          child: Text('ScrollToCell'),
          onPressed: () {
            _controller.scrollToCell(15, 2);
          },
        ),
        Expanded( child:SfDataGrid(
          source: _employeeDataSource,
          columns: [
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
          controller: _controller,
        )),
    );
  }

{% endhighlight %}
{% endtabs %}

![Flutter DataTable shows programmatic scrolling to cell](images/scrolling/flutter-datagrid-programmatic-scrolling-scroll-to-cell.gif)

### Scroll to row

You can scroll programmatically to a particular row by passing the row index in the [scrollToRow](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/scrollToRow.html) method. SfDataGrid allows to enable or disable the scrolling animation by passing `true` to the `canAnimate` parameter in `scrollToRow` method. 

N> The default value of `canAnimate` is `false`.

{% tabs %}
{% highlight Dart %}

final DataGridController _controller = DataGridController();

 @override
 Widget build(BuildContext context) {
    return Scaffold(
      body: Column(children: [
        FlatButton(
          child: Text('ScrollToRow'),
          onPressed: () {
            _controller.scrollToRow(15);
          },
        ),
        Expanded( child:SfDataGrid(
          source: _employeeDataSource,
          columns: [
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
          controller: _controller,
        )),
    );
  }

{% endhighlight %}
{% endtabs %}

### Scroll to column

You can scroll programmatically to a particular column by passing the column index in the [scrollToColumn](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/scrollToColumn.html) method. SfDataGrid allows to enable or disable the scrolling animation by passing `true` to the `canAnimate` parameter in `scrollToColumn` method. 

N> The default value of `canAnimate` is `false`.

{% tabs %}
{% highlight Dart %}

final DataGridController _controller = DataGridController();

 @override
 Widget build(BuildContext context) {
    return Scaffold(
      body: Column(children: [
        FlatButton(
          child: Text('ScrollToColumn'),
          onPressed: () {
            _controller.scrollToColumn(2);
          },
        ),
        Expanded( child:SfDataGrid(
          source: _employeeDataSource,
          columns: [
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
          controller: _controller,
        )),
    );
  }

{% endhighlight %}
{% endtabs %}

![Flutter DataTable shows programmatic scrolling to column](images/scrolling/flutter-datagrid-programmatic-scrolling-scroll-to-column.gif)

### Scroll to specific position

`SfDataGrid` allows to position the scrolled row or column in view programmatically by passing [DataGridScrollPosition](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridScrollPosition-class.html) to `rowPosition` and `columnPosition` arguments respectively in `scrollToCell` and `position` argument of `scrollToRow` and `scrollToColumn` methods. Below are the four types of positions available,

`makeVisible`: Scroll to make a specified row/column visible in datagrid. If the specified row/column is already in view, scrolling will not occur.
`start`: Scroll to make the row/column positioned at the start of the datagrid.
`center`: Scroll to make the row/column positioned at the center of the datagrid.
`end`: Scroll to make the row/column positioned at the end of the datagrid.

N> The default value of `DataGridScrollPosition` is `Start`.

{% tabs %}
{% highlight Dart %}

final DataGridController _controller = DataGridController();

 @override
 Widget build(BuildContext context) {
    return Scaffold(
      body: Column(children: [
        FlatButton(
          child: Text('ScrollToCell'),
          onPressed: () {
            _controller.scrollToCell(15, 2,
                canAnimate: true,
                rowPosition: DataGridScrollPosition.start,
                columnPosition: DataGridScrollPosition.start);
          },
        ),
        Expanded( child:SfDataGrid(
          source: _employeeDataSource,
          columns: [
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
          controller: _controller,
        )),
    );
  }

{% endhighlight %}
{% endtabs %}

### Scroll to vertical offset

The Flutter DataTable supports to scroll programmatically to a particular vertical offset by passing the offset value to the [scrollToVerticalOffset](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/scrollToVerticalOffset.html) method. Also, it allows to enable the scrolling animation by passing `true` to the `canAnimate` parameter in `scrollToVerticalOffset` method. 

N> The default value of `canAnimate` is `false`.

{% tabs %}
{% highlight Dart %}

final DataGridController _controller = DataGridController();

 @override
 Widget build(BuildContext context) {
    return Scaffold(
      body: Column(children: [
        FlatButton(
          child: Text('ScrollToVerticalOffset'),
          onPressed: () {
            _controller.scrollToVerticalOffset(500);
          },
        ),
        Expanded( child:SfDataGrid(
          source: _employeeDataSource,
          columns: [
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
          controller: _controller,
        )),
    );
  }

{% endhighlight %}
{% endtabs %}

### Scroll to horizontal offset

The Flutter DataTable supports to scroll programmatically to a particular horizontal offset by passing the offset value to the [scrollToHorizontalOffset](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/scrollToHorizontalOffset.html) method. Also, it allows to enable the scrolling animation by passing `true` to the `canAnimate` parameter in `scrollToHorizontalOffset` method. 

N> The default value of `canAnimate` is `false`.

{% tabs %}
{% highlight Dart %}

final DataGridController _controller = DataGridController();

 @override
 Widget build(BuildContext context) {
    return Scaffold(
      body: Column(children: [
        FlatButton(
          child: Text('ScrollToHorizontalOffset'),
          onPressed: () {
            _controller.scrollToHorizontalOffset(400);
          },
        ),
        Expanded( child:SfDataGrid(
          source: _employeeDataSource,
          columns: [
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
          controller: _controller,
        )),
    );
  }

{% endhighlight %}
{% endtabs %}

N> The vertical and horizontal scrolled offset can be retrieved by using `DataGridController.verticalOffset` and `DataGridController.horizontalOffset` properties.
