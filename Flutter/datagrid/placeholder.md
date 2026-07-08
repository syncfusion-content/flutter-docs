---
layout: post
title: Placeholder in Flutter DataGrid | DataTable | Syncfusion
description: Learn here all about how to add a placeholder to the Syncfusion Flutter DataGrid (SfDataGrid) control and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Placeholder in Flutter DataGrid (SfDataGrid)

The `SfDataGrid` provides built-in support for displaying a placeholder when the data source is empty by setting the [SfDataGrid.placeholder](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/placeholder.html) property. The `placeholder` property accepts a `Widget` that will be displayed in the scroll view area when the DataGrid has no data to show.

The following example shows how to add a `placeholder` in SfDataGrid:

{% tabs %}
{% highlight Dart %} 

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Syncfusion Flutter DataGrid'),
      ),
      body: SfDataGrid(
        source: _employeeDataSource,
        columnWidthMode: ColumnWidthMode.auto,
        columns: <GridColumn>[
          GridColumn(
            columnName: 'id',
            label: Container(
              padding: EdgeInsets.all(16.0),
              alignment: Alignment.center,
              child: Text('ID'),
            ),
          ),
          GridColumn(
            columnName: 'name',
            label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text('Name'),
            ),
          ),
          GridColumn(
            columnName: 'designation',
            label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text(
                'Designation',
                overflow: TextOverflow.ellipsis,
              ),
            ),
          ),
          GridColumn(
            columnName: 'salary',
            label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text('Salary'),
            ),
          ),
        ],
        placeholder: Center(
          child: Column(
            mainAxisSize: MainAxisSize.min,
            children: [
              Icon(Icons.thumb_down_alt_outlined, size: 30),
              SizedBox(height: 8),
              Text(
                'No Records Found',
                style: TextStyle(fontSize: 16),
              ),
            ],
          ),
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

<img alt="Flutter DataGrid displays a placeholder when there are no rows" src="images/placeholder/flutter-datagrid-placeholder.png" width="404" height="396"/>

> **Sample application:** — Refer to the [DataGrid placeholder sample](https://support.syncfusion.com/kb/article/19825/how-to-show-an-empty-message-in-flutter-datatable) in the Syncfusion Flutter Examples repository for a complete working implementation.
