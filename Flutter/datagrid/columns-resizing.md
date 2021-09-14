---
layout: post
title: Columns Resizing in Flutter DataGrid | Syncfusion | DataTable
description: Learn here all about how to resize a column in Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Columns Resizing in Flutter DataGrid (SfDataGrid)

[SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) allows resizing the columns by dragging the column resizing indicator. This can be enabled by setting `SfDataGrid.allowColumnsResizing` property to `true`. The column resizing indicator appears based on the platform. In Web and Desktop, the indicator appears when you hover over the column edge. In Mobile, the indicator appears when you long press the column header.

> **NOTE:**
    Column resizing considers the [GridColumn.minimumWidth](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridColumn/minimumWidth.html) and [GridColumn.maximumWidth](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridColumn/maximumWidth.html) properties.

{% tabs %}
{% highlight Dart %} 

late Map<String, double> columnWidths = {
  'id': double.nan,
  'name': double.nan,
  'designation': double.nan,
  'salary': double.nan
};

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: const Text('Syncfusion Flutter DataGrid'),
    ),
    body: SfDataGrid(
      source: _employeeDataSource,
      allowColumnsResizing: true,
      onColumnResizeUpdate: (ColumnResizeUpdateDetails details) {
        setState(() {
          columnWidths[details.column.columnName] = details.width;
        });
        return true;
      },
      columns: <GridColumn>[
        GridColumn(
            width: columnWidths['id']!,
            columnName: 'id',
            label: Container(
                padding: EdgeInsets.all(16.0),
                alignment: Alignment.center,
                child: Text(
                  'ID',
                ))),
        GridColumn(
            width: columnWidths['name']!,
            columnName: 'name',
            label: Container(
                padding: EdgeInsets.all(8.0),
                alignment: Alignment.center,
                child: Text('Name'))),
        GridColumn(
            width: columnWidths['designation']!,
            columnName: 'designation',
            label: Container(
                padding: EdgeInsets.all(8.0),
                alignment: Alignment.center,
                child: Text(
                  'Designation',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            width: columnWidths['salary']!,
            columnName: 'salary',
            label: Container(
                padding: EdgeInsets.all(8.0),
                alignment: Alignment.center,
                child: Text('Salary'))),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows column resizing with onResize mode](images/columns-resizing/flutter-datagrid-resizing-onResize.gif)

## Column resizing modes

`SfDataGrid` provides the following modes to resizing a column by setting it to the `SfDataGrid.columnResizeMode` property.

- `onResize`: The resizing indicator is moved based on the dragging gesture. The width of the column will update as the resizing indicator moves.
- `onResizeEnd`: The resizing indicator is moved based on the dragging gesture. However, the width of the column is updated when you release the pointer.

The following example demonstrates that how to resize a column by setting the `SfDataGrid.columnResizeMode` property to `onResize`.

{% tabs %}
{% highlight Dart %} 

late Map<String, double> columnWidths = {
  'id': double.nan,
  'name': double.nan,
  'designation': double.nan,
  'salary': double.nan
};

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: const Text('Syncfusion Flutter DataGrid'),
    ),
    body: SfDataGrid(
      source: _employeeDataSource,
      allowColumnsResizing: true,
      columnResizeMode: ColumnResizeMode.onResize,
      onColumnResizeUpdate: (ColumnResizeUpdateDetails details) {
        setState(() {
          columnWidths[details.column.columnName] = details.width;
        });
        return true;
      },
      columns: <GridColumn>[
        GridColumn(
            width: columnWidths['id']!,
            columnName: 'id',
            label: Container(
                padding: EdgeInsets.all(16.0),
                alignment: Alignment.center,
                child: Text(
                  'ID',
                ))),
        GridColumn(
            width: columnWidths['name']!,
            columnName: 'name',
            label: Container(
                padding: EdgeInsets.all(8.0),
                alignment: Alignment.center,
                child: Text('Name'))),
        GridColumn(
            width: columnWidths['designation']!,
            columnName: 'designation',
            label: Container(
                padding: EdgeInsets.all(8.0),
                alignment: Alignment.center,
                child: Text(
                  'Designation',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            width: columnWidths['salary']!,
            columnName: 'salary',
            label: Container(
                padding: EdgeInsets.all(8.0),
                alignment: Alignment.center,
                child: Text('Salary'))),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows column resizing with onResize mode](images/columns-resizing/flutter-datagrid-resizing-onResize.gif)

The following example demonstrates that how to resize a column by setting the `SfDataGrid.columnResizeMode` property to `onResizeEnd`.

{% tabs %}
{% highlight Dart %} 

late Map<String, double> columnWidths = {
  'id': double.nan,
  'name': double.nan,
  'designation': double.nan,
  'salary': double.nan
};

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: const Text('Syncfusion Flutter DataGrid'),
    ),
    body: SfDataGrid(
      source: _employeeDataSource,
      allowColumnsResizing: true,
      columnResizeMode: ColumnResizeMode.onResizeEnd,
      onColumnResizeUpdate: (ColumnResizeUpdateDetails details) {
        setState(() {
          columnWidths[details.column.columnName] = details.width;
        });
        return true;
      },
      columns: <GridColumn>[
        GridColumn(
            width: columnWidths['id']!,
            columnName: 'id',
            label: Container(
                padding: EdgeInsets.all(16.0),
                alignment: Alignment.center,
                child: Text(
                  'ID',
                ))),
        GridColumn(
            width: columnWidths['name']!,
            columnName: 'name',
            label: Container(
                padding: EdgeInsets.all(8.0),
                alignment: Alignment.center,
                child: Text('Name'))),
        GridColumn(
            width: columnWidths['designation']!,
            columnName: 'designation',
            label: Container(
                padding: EdgeInsets.all(8.0),
                alignment: Alignment.center,
                child: Text(
                  'Designation',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            width: columnWidths['salary']!,
            columnName: 'salary',
            label: Container(
                padding: EdgeInsets.all(8.0),
                alignment: Alignment.center,
                child: Text('Salary'))),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows column resizing with onResizeEnd mode](images/columns-resizing/flutter-datagrid-resizing-onResizeEnd.gif)

## Column resizing callbacks

SfDataGrid provides the following callbacks to notify the column resizing operations.

- `onColumnResizeStart`: Called when column resizing is started. In Mobile platforms, this callback will be called at the time of showing the resizing indicator when long press a column header. In Web and Windows platforms, this method will be called when click and drag the resizing indicator.
- `onColumnResizeUpdate`: Called when a column is being resized.
- `onColumnResizeEnd`: Called when a column resizing is ended. Typically, this will be called when you release the pointer.

{% tabs %}
{% highlight Dart %}

late Map<String, double> columnWidths = {
  'id': double.nan,
  'name': double.nan,
  'designation': double.nan,
  'salary': double.nan
};

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: const Text('Syncfusion Flutter DataGrid'),
    ),
    body: SfDataGrid(
      source: _employeeDataSource,
      allowColumnsResizing: true,
      onColumnResizeStart: (ColumnResizeStartDetails details) {
        return true;
      },
      onColumnResizeUpdate: (ColumnResizeUpdateDetails details) {
        setState(() {
          columnWidths[details.column.columnName] = details.width;
        });
        return true;
      },
      onColumnResizeEnd: (ColumnResizeEndDetails details) {},
      columns: <GridColumn>[
        GridColumn(
            width: columnWidths['id']!,
            columnName: 'id',
            label: Container(
                padding: EdgeInsets.all(16.0),
                alignment: Alignment.center,
                child: Text(
                  'ID',
                ))),
        GridColumn(
            width: columnWidths['name']!,
            columnName: 'name',
            label: Container(
                padding: EdgeInsets.all(8.0),
                alignment: Alignment.center,
                child: Text('Name'))),
        GridColumn(
            width: columnWidths['designation']!,
            columnName: 'designation',
            label: Container(
                padding: EdgeInsets.all(8.0),
                alignment: Alignment.center,
                child: Text(
                  'Designation',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            width: columnWidths['salary']!,
            columnName: 'salary',
            label: Container(
                padding: EdgeInsets.all(8.0),
                alignment: Alignment.center,
                child: Text('Salary'))),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Disable resizing for a particular column

To disable resizing for a particular column, simply hook the `SfDataGrid.onColumnResizeStart` callback and return `false` to the corresponding column.

{% tabs %}
{% highlight Dart %}

late Map<String, double> columnWidths = {
  'id': double.nan,
  'name': double.nan,
  'designation': double.nan,
  'salary': double.nan
};

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: const Text('Syncfusion Flutter DataGrid'),
    ),
    body: SfDataGrid(
      source: _employeeDataSource,
      allowColumnsResizing: true,
      onColumnResizeStart: (ColumnResizeStartDetails details) {
        // Disable resizing for the `id` column.
        if (details.column.columnName == 'id') {
          return false;
        }
        return true;
      },
      onColumnResizeUpdate: (ColumnResizeUpdateDetails details) {
        setState(() {
          columnWidths[details.column.columnName] = details.width;
        });
        return true;
      },
      columns: <GridColumn>[
        GridColumn(
            width: columnWidths['id']!,
            columnName: 'id',
            label: Container(
                padding: EdgeInsets.all(16.0),
                alignment: Alignment.center,
                child: Text(
                  'ID',
                ))),
        GridColumn(
            width: columnWidths['name']!,
            columnName: 'name',
            label: Container(
                padding: EdgeInsets.all(8.0),
                alignment: Alignment.center,
                child: Text('Name'))),
        GridColumn(
            width: columnWidths['designation']!,
            columnName: 'designation',
            label: Container(
                padding: EdgeInsets.all(8.0),
                alignment: Alignment.center,
                child: Text(
                  'Designation',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            width: columnWidths['salary']!,
            columnName: 'salary',
            label: Container(
                padding: EdgeInsets.all(8.0),
                alignment: Alignment.center,
                child: Text('Salary'))),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Prevent column from being hidden on resizing

To prevent a column from being hidden while resizing, use `GridColumn.minimumWidth` property to set the minimum width of the column. Then, the column will not be resized below the minimum width. The column resizing considers the `GridColumn.minimumWidth` and `GridColumn.maximumWidth` properties.

{% tabs %}
{% highlight Dart %}

late Map<String, double> columnWidths = {
  'id': double.nan,
  'name': double.nan,
  'designation': double.nan,
  'salary': double.nan
};

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: const Text('Syncfusion Flutter DataGrid'),
    ),
    body: SfDataGrid(
      source: _employeeDataSource,
      allowColumnsResizing: true,
      onColumnResizeUpdate: (ColumnResizeUpdateDetails details) {
        setState(() {
          columnWidths[details.column.columnName] = details.width;
        });
        return true;
      },
      columns: <GridColumn>[
        GridColumn(
            width: columnWidths['id']!,
            columnName: 'id',
            label: Container(
                padding: EdgeInsets.all(16.0),
                alignment: Alignment.center,
                child: Text(
                  'ID',
                ))),
        GridColumn(
            width: columnWidths['name']!,
            minimumWidth: 30.0,
            columnName: 'name',
            label: Container(
                padding: EdgeInsets.all(8.0),
                alignment: Alignment.center,
                child: Text('Name'))),
        GridColumn(
            width: columnWidths['designation']!,
            columnName: 'designation',
            label: Container(
                padding: EdgeInsets.all(8.0),
                alignment: Alignment.center,
                child: Text(
                  'Designation',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            width: columnWidths['salary']!,
            columnName: 'salary',
            label: Container(
                padding: EdgeInsets.all(8.0),
                alignment: Alignment.center,
                child: Text('Salary'))),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Customize indicator appearance

The column resizing indicator color and its width can be customized by the `SfDataGridThemeData.columnResizeIndicatorColor` and `SfDataGridThemeData.columnResizeIndicatorStrokeWidth` properties.

{% tabs %}
{% highlight Dart %}

late Map<String, double> columnWidths = {
  'id': double.nan,
  'name': double.nan,
  'designation': double.nan,
  'salary': double.nan
};

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: const Text('Syncfusion Flutter DataGrid'),
    ),
    body: SfDataGridTheme(
      data: SfDataGridThemeData(
        columnResizeIndicatorColor: Colors.orange,
        columnResizeIndicatorStrokeWidth: 2.0,
      ),
      child: SfDataGrid(
        source: _employeeDataSource,
        allowColumnsResizing: true,
        onColumnResizeUpdate: (ColumnResizeUpdateDetails details) {
          setState(() {
            columnWidths[details.column.columnName] = details.width;
          });
          return true;
        },
        columns: <GridColumn>[
          GridColumn(
              width: columnWidths['id']!,
              columnName: 'id',
              label: Container(
                  padding: EdgeInsets.all(16.0),
                  alignment: Alignment.center,
                  child: Text(
                    'ID',
                  ))),
          GridColumn(
              width: columnWidths['name']!,
              columnName: 'name',
              label: Container(
                  padding: EdgeInsets.all(8.0),
                  alignment: Alignment.center,
                  child: Text('Name'))),
          GridColumn(
              width: columnWidths['designation']!,
              columnName: 'designation',
              label: Container(
                  padding: EdgeInsets.all(8.0),
                  alignment: Alignment.center,
                  child: Text(
                    'Designation',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              width: columnWidths['salary']!,
              columnName: 'salary',
              label: Container(
                  padding: EdgeInsets.all(8.0),
                  alignment: Alignment.center,
                  child: Text('Salary'))),
        ],
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows column resizing with onResize mode](images/columns-resizing/flutter-datagrid-resizing-indicator-customization.png)