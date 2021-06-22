---
layout: post
title: Footer in Flutter DataGrid | Flutter DataTable | Syncfusion
description: Learn here all about how to set footer view to the Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Footer in Flutter DataGrid (SfDataGrid)

Creates an additional row that can be displayed below to the last row. Widgets can be displayed to the additional row by setting the `SfDataGrid.footer` property.

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return SfDataGrid(
    source: _employeeDataSource,
    footer: Container(
      color: Colors.grey[400],
      child: Center(
        child: Text(
          'FOOTER VIEW',
          style: TextStyle(fontWeight: FontWeight.bold),
        ),
      ),
    ),
    columns: <GridColumn>[
      GridColumn(
          columnName: 'id',
          label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text(
                'ID',
              ))),
      GridColumn(
          columnName: 'name',
          label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text('Name'))),
      GridColumn(
          columnName: 'designation',
          label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text(
                'Designation',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'salary',
          label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text('Salary'))),
    ],
  );
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows footer](images/footer/flutter-datagrid-footer.png)

## Change the footer row height

An additional row height can be personalized by using the `SfDataGrid.footerHeight` property. The default value of the additional row is 49.0.

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return SfDataGrid(
    source: _employeeDataSource,
    footerHeight: 60.0,
    footer: Container(
      color: Colors.grey[400],
      child: Center(
        child: Text(
          'FOOTER VIEW',
          style: TextStyle(fontWeight: FontWeight.bold),
        ),
      ),
    ),
    columns: <GridColumn>[
      GridColumn(
          columnName: 'id',
          label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text(
                'ID',
              ))),
      GridColumn(
          columnName: 'name',
          label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text('Name'))),
      GridColumn(
          columnName: 'designation',
          label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text(
                'Designation',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'salary',
          label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text('Salary'))),
    ],
  );
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows footer height customization](images/footer/flutter-datagrid-footer-height-customization.png)

## Show footer row always

By default, the additional row can be displayed below to the last row. If you want to show the additional row always on the view bottom, you can simply set the `SfDataGrid.frozenFooterRowsCount` property to 1.

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return SfDataGrid(
    source: _employeeDataSource,
    footerFrozenRowsCount: 1,
    footer: Container(
      child: Center(
        child: Text(
          'FOOTER VIEW',
          style: TextStyle(fontWeight: FontWeight.bold),
        ),
      ),
    ),
    columns: <GridColumn>[
      GridColumn(
          columnName: 'id',
          label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text(
                'ID',
              ))),
      GridColumn(
          columnName: 'name',
          label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text('Name'))),
      GridColumn(
          columnName: 'designation',
          label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text(
                'Designation',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'salary',
          label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text('Salary'))),
    ],
  );
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows footer always on bottom](images/footer/flutter-datagrid-footer-on-bottom.gif)