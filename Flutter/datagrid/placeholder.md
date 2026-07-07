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

N> **Note:** Ensure you have implemented a [DataGridSource](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource-class.html) class and configured [GridColumn](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridColumn-class.html) objects before implementing the placeholder feature. For detailed setup instructions, refer to the [Getting Started with SfDataGrid](getting-started.md) documentation.

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

**Behavior**

The placeholder widget is automatically displayed when:
- The data source is empty (contains no rows)
- The `SfDataGrid.placeholder` property is assigned

The placeholder is automatically hidden when:
- Data is added to the data source
- Rows become available in the DataGrid

**API Reference**

* [SfDataGrid.placeholder](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/placeholder.html) — Gets or sets the widget to display when the DataGrid is empty.
* [DataGridSource](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource-class.html) — The data source for populating the DataGrid.

**See Also**

* [Getting Started with SfDataGrid](getting-started.md)
* [Styling DataGrid Cells](styles.md)
* [DataGrid Column Types](column-types.md)

N> **Sample applications** — Refer to the [DataGrid placeholder sample](https://github.com/SyncfusionExamples/getting-started-with-flutter-datagrid) in the Syncfusion Flutter Examples repository for a complete working implementation.
