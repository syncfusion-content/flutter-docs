---
layout: post
title: Scrolling in Syncfusion Flutter DataGrid | DataTable
description: Learn about scrolling and how to customize the horizontal and vertical scrollbar in Syncfusion Flutter DataGrid.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Scrolling in Flutter (SfDataGrid)

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

# Programmatic scrolling

SfDataGrid provides support to scroll to a particular row and column index programmatically.

## Scroll to row column index

Scroll programmatically to a particular cell can be achieved by passing the row and column indexes in the [scrollToCell]() method. SfDataGrid allows to enable or disable the scrolling animation by passing `true` to the `canAnimate` parameter in `scrollToCell` method. 

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
            _controller.scrollToCell(15, 2,
                canAnimate: true,
                rowPosition: DataGridScrollPosition.start,
                columnPosition: DataGridScrollPosition.start);
          },
        ),
        Expanded( child:SfDataGrid(
          source: _employeeDataSource,
          columns: [
            GridNumericColumn(mappingName: 'id', headerText: 'ID'),
            GridTextColumn(mappingName: 'name', headerText: 'Name'),
            GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary'),
          ],
          controller: _controller,
        )),
    );
  }

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows programmatic scrolling with scroll to cell](images/scrolling/flutter-datagrid-programmatic-scrolling-scroll-to-cell.gif)

## Scroll to row index

Scroll programmatically to a particular row can be achieved by passing the row index in the [scrollToRow]() method. SfDataGrid allows to enable or disable the scrolling animation by passing `true` to the `canAnimate` parameter in `scrollToRow` method. 

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
            _controller.scrollToRow(15,
                canAnimate: true,
                rowPosition: DataGridScrollPosition.start,
                columnPosition: DataGridScrollPosition.start);
          },
        ),
        Expanded( child:SfDataGrid(
          source: _employeeDataSource,
          columns: [
            GridNumericColumn(mappingName: 'id', headerText: 'ID'),
            GridTextColumn(mappingName: 'name', headerText: 'Name'),
            GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary'),
          ],
          controller: _controller,
        )),
    );
  }

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows programmatic scrolling with scroll to row](images/scrolling/flutter-datagrid-programmatic-scrolling-scroll-to-row.gif)

## Scroll to column index

Scroll programmatically to a particular column can be achieved by passing the column index in the [scrollToColumn]() method. SfDataGrid allows to enable or disable the scrolling animation by passing `true` to the `canAnimate` parameter in `scrollToColumn` method. 

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
            _controller.scrollToColumn(2,
                canAnimate: true,
                rowPosition: DataGridScrollPosition.start,
                columnPosition: DataGridScrollPosition.start);
          },
        ),
        Expanded( child:SfDataGrid(
          source: _employeeDataSource,
          columns: [
            GridNumericColumn(mappingName: 'id', headerText: 'ID'),
            GridTextColumn(mappingName: 'name', headerText: 'Name'),
            GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary'),
          ],
          controller: _controller,
        )),
    );
  }

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows programmatic scrolling with scroll to column](images/scrolling/flutter-datagrid-programmatic-scrolling-scroll-to-column.gif)

## Scroll to specific position

SfDataGrid allows to position the scrolled row and column indexes in view programmatically by passing [DataGridScrollPosition]() to `rowPosition` and `columnPosition` in `scrollToCell`, `ScrollToRow`, `ScrollToColumn` methods. Below are the four types of positions. 

`MakeVisible`: Scroll to make a specified row/column visible in datagrid. If the specified row/column is already in view, scrolling will not occur.
`Start`: Scroll to make the row/column positioned at the start of the datagrid.
`Center`: Scroll to make the row/column positioned at the center of the datagrid.
`End`: Scroll to make the row/column positioned at the end of the datagrid.

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
            GridNumericColumn(mappingName: 'id', headerText: 'ID'),
            GridTextColumn(mappingName: 'name', headerText: 'Name'),
            GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary'),
          ],
          controller: _controller,
        )),
    );
  }

{% endhighlight %}
{% endtabs %}

## Scroll to particular offset

SfDataGrid supports to Scroll programmatically to a particular offset value by passing the vertical and horizontal offset values to the [scrollToVerticalOffset]() and [scrollToHorizontalOffset]() method. Also, it allows to enable or disable the scrolling animation by passing `true` to the `canAnimate` parameter in `scrollToVerticalOffset` and `scrollToHorizontalOffset` method. 

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
            _controller.scrollToVerticalOffset(500,
                canAnimate: true);
          },
        ),
        Expanded( child:SfDataGrid(
          source: _employeeDataSource,
          columns: [
            GridNumericColumn(mappingName: 'id', headerText: 'ID'),
            GridTextColumn(mappingName: 'name', headerText: 'Name'),
            GridTextColumn(mappingName: 'designation', headerText: 'Designation'),
            GridNumericColumn(mappingName: 'salary', headerText: 'Salary'),
          ],
          controller: _controller,
        )),
    );
  }

{% endhighlight %}
{% endtabs %}
