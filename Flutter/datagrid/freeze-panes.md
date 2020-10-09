---
layout: post
title: Freeze panes for Syncfusion Flutter DataGrid | DataTable
description: Learn how to freeze the row and column in Syncfusion Flutter DataGrid with support to customize the freeze count in the runtime.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Freeze Panes in Flutter (SfDataGrid)

The rows and columns can freeze in view like Excel. The rows and columns can be freeze by setting following properties,

<table>
<tr>
<th> Property Name </th>
<th> Description </th>
</tr>
<tr>
<td>
frozenRowsCount
</td>
<td>
Set the frozen rows count at top of the <code>SfDataGrid</code>.
</td>
</tr>
<tr>
<td>
footerFrozenRowsCount
</td>
<td>
Set the footer rows count at bottom of the <code>SfDataGrid</code>.
</td>
</tr>
<tr>
<td>
frozenColumnsCount
</td>
<td>
Set the frozen columns count in left side of the <code>SfDataGrid</code>.
</td>
</tr>
<tr>
<td>
footerFrozenColumnsCount
</td>
<td>
Set the footer columns in right side of the <code>SfDataGrid</code>.
</td>
</tr>
</table>

## Freeze columns

The columns can be frozen in view at left and right like Excel by setting the [frozenColumnsCount](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/frozenColumnsCount.html) and [footerFrozenColumnsCount](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/footerFrozenColumnsCount.html) properties.

The following code example shows how to freeze a column at left using `frozenColumnsCount`,

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
        body: SfDataGrid(
        columns: [
          GridNumericColumn(mappingName: 'id', headerText: 'ID'),
          GridNumericColumn(mappingName: 'productId', headerText: 'Product ID'),
          GridTextColumn(mappingName: 'name', headerText: 'Customer Name'),
          GridTextColumn(mappingName: 'product', headerText: 'Product'),
          GridDateTimeColumn(
              mappingName: 'orderDate', headerText: 'Order Date'),
          GridNumericColumn(mappingName: 'quantity', headerText: 'Quantity'),
          GridTextColumn(mappingName: 'city', headerText: 'City'),
          GridNumericColumn(mappingName: 'unitPrice', headerText: 'Unit Price'),
        ],
        frozenColumnsCount: 1,
        ),
    );
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows frozen column at left](images/frozen-pane/flutter-datagrid-frozen-column.gif)

The following code example shows how to freeze a column at right using `footerFrozenColumnsCount`,

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
        body: SfDataGrid(
        columns: [
          GridNumericColumn(mappingName: 'id', headerText: 'ID'),
          GridNumericColumn(mappingName: 'productId', headerText: 'Product ID'),
          GridTextColumn(mappingName: 'name', headerText: 'Customer Name'),
          GridTextColumn(mappingName: 'product', headerText: 'Product'),
          GridDateTimeColumn(
              mappingName: 'orderDate', headerText: 'Order Date'),
          GridNumericColumn(mappingName: 'quantity', headerText: 'Quantity'),
          GridTextColumn(mappingName: 'city', headerText: 'City'),
          GridNumericColumn(mappingName: 'unitPrice', headerText: 'Unit Price'),
        ],
        footerFrozenColumnsCount: 1,
        ),
    );
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows frozen column at right](images/frozen-pane/flutter-datagrid-footer-frozen-column.png)

### Limitation

* `frozenColumnsCount` or  `footerFrozenColumnsCount` should be lesser than number of columns displayed in the view. For example, If you have 5 columns in view, then you can set `frozenColumnsCount` to a maximum value of 4.

## Freeze rows

The rows can be frozen in view at top and bottom like Excel by setting the [frozenRowsCount](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/frozenRowsCount.html) and [footerFrozenRowsCount](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/footerFrozenRowsCount.html) properties.

The following code example shows how to freeze a row at top using `frozenRowsCount`,

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
        body: SfDataGrid(
        columns: [
          GridNumericColumn(mappingName: 'id', headerText: 'ID'),
          GridNumericColumn(mappingName: 'productId', headerText: 'Product ID'),
          GridTextColumn(mappingName: 'name', headerText: 'Customer Name'),
          GridTextColumn(mappingName: 'product', headerText: 'Product'),
          GridDateTimeColumn(
              mappingName: 'orderDate', headerText: 'Order Date'),
          GridNumericColumn(mappingName: 'quantity', headerText: 'Quantity'),
          GridTextColumn(mappingName: 'city', headerText: 'City'),
          GridNumericColumn(mappingName: 'unitPrice', headerText: 'Unit Price'),
        ],
        frozenRowsCount: 1,
        ),
    );
}
{% endhighlight %}
{% endtabs %}

![flutter datagrid shows frozen row at top](images/frozen-pane/flutter-datagrid-frozen-row.gif)

The following code example shows how to freeze a row at bottom using `footerFrozenRowsCount`,

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
        body: SfDataGrid(
        columns: [
          GridNumericColumn(mappingName: 'id', headerText: 'ID'),
          GridNumericColumn(mappingName: 'productId', headerText: 'Product ID'),
          GridTextColumn(mappingName: 'name', headerText: 'Customer Name'),
          GridTextColumn(mappingName: 'product', headerText: 'Product'),
          GridDateTimeColumn(
              mappingName: 'orderDate', headerText: 'Order Date'),
          GridNumericColumn(mappingName: 'quantity', headerText: 'Quantity'),
          GridTextColumn(mappingName: 'city', headerText: 'City'),
          GridNumericColumn(mappingName: 'unitPrice', headerText: 'Unit Price'),
        ],
        footerFrozenRowsCount: 1,
        ),
    );
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows frozen row at bottom](images/frozen-pane/flutter-datagrid-footer-frozen-row.png)

### Limitation

* `frozenRowsCount` or `footerFrozenRowsCount` should be lesser than the number of rows displayed in the view. For example, If you have 10 rows in view, then you set `frozenRowsCount` to a maximum value of 9.

N> Header row is frozen by default and works regardless of the `frozenRowsCount` property.

## Appearance

`SfDataGrid` allows to customize the appearance of the freeze pane through [SfDataGridTheme.SfDataGridThemeData](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData-class.html) property.

The freeze pane line and freeze pane width can be changed by [frozenPaneLineColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/frozenPaneLineColor.html) and [frozenPaneLineWidth](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/frozenPaneLineWidth.html). 

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Scaffold(
        body: SfDataGridTheme(
            data: SfDataGridThemeData(
                frozenPaneLineColor: Colors.red, frozenPaneLineWidth: 1.5),
            child: SfDataGrid(
            columns: [
              GridNumericColumn(mappingName: 'id', headerText: 'ID'),
              GridNumericColumn(mappingName: 'productId', headerText: 'Product ID'),
              GridTextColumn(mappingName: 'name', headerText: 'Customer Name'),
              GridTextColumn(mappingName: 'product', headerText: 'Product'),
              GridDateTimeColumn(
                    mappingName: 'orderDate', headerText: 'Order Date'),
              GridNumericColumn(mappingName: 'quantity', headerText: 'Quantity'),
              GridTextColumn(mappingName: 'city', headerText: 'City'),
              GridNumericColumn(mappingName: 'unitPrice', headerText: 'Unit Price'),
            ],
            frozenRowsCount: 1,
            footerFrozenRowsCount: 1,
            frozenColumnsCount: 1,
            footerFrozenColumnsCount: 1,
            )),
    );
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows freeze pane customization](images/frozen-pane/flutter-datagrid-frozen-pane-customization.png)