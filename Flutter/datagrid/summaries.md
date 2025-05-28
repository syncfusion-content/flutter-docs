---
layout: post
title: Summaries feature in Flutter DataGrid | DataTable | Syncfusion
description: Learn here all about how to add summary rows to the Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Summaries in Flutter DataGrid (SfDataGrid)

## Table summary

The [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) provides built-in support to display concise information about the rows by using the table summary rows. The table summary value is calculated based on all the rows in the [DataGridSource.rows](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/rows.html) property. You can add a table summary row to the DataGrid by adding the [GridTableSummaryRow](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridTableSummaryRow-class.html) to the [SfDataGrid.tableSummaryRows](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/tableSummaryRows.html) collection.

DataGrid does not automatically display the summary values. To display the summary value, you need to override the [buildTableSummaryCellWidget](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/buildTableSummaryCellWidget.html) method in the [DataGridSource](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource-class.html) class. The calculated summary value is passed as a parameter to the `DataGridSource.buildTableSummaryCellWidget` method. So, you need to return the required widget with the summary value.

### Display table summary for row

The summary information can be displayed in a row by setting the [GridTableSummaryRow.showSummaryInRow](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridTableSummaryRow/showSummaryInRow.html) property to `true` and defining the summary columns. The [GridTableSummaryRow.title](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridTableSummaryRow/title.html) content will be displayed in the corresponding row. You must define the `GridTableSummaryRow.title` based on the [GridSummaryColumn.name](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridSummaryColumn/name.html) property to customize the summary value.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Syncfusion Flutter DataGrid'),
      ),
      body: SfDataGrid(
        source: employeeDataSource,
        tableSummaryRows: [
          GridTableSummaryRow(
              showSummaryInRow: true,
              title: 'Total Salary: {Sum} for 20 employees',
              columns: [
                GridSummaryColumn(
                    name: 'Sum',
                    columnName: 'salary',
                    summaryType: GridSummaryType.sum)
              ],
              position: GridTableSummaryRowPosition.bottom)
        ],
        columns: <GridColumn>[
          GridColumn(
              columnName: 'id',
              label: Container(
                  padding: EdgeInsets.all(16.0),
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
                    'Job Title',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'salary',
              label: Container(
                  padding: EdgeInsets.all(8.0),
                  alignment: Alignment.center,
                  child: Text('Salary'))),
        ],
      ),
    );
  }

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource({required List<Employee> employeeData}) {
    _employeeData = employeeData
        .map<DataGridRow>((e) => DataGridRow(cells: [
              DataGridCell<int>(columnName: 'id', value: e.id),
              DataGridCell<String>(columnName: 'name', value: e.name),
              DataGridCell<String>(
                  columnName: 'designation', value: e.designation),
              DataGridCell<int>(columnName: 'salary', value: e.salary),
            ]))
        .toList();
  }

  List<DataGridRow> _employeeData = [];

  @override
  List<DataGridRow> get rows => _employeeData;

  @override
  Widget? buildTableSummaryCellWidget(
      GridTableSummaryRow summaryRow,
      GridSummaryColumn? summaryColumn,
      RowColumnIndex rowColumnIndex,
      String summaryValue) {
    return Container(
      padding: EdgeInsets.all(15.0),
      child: Text(summaryValue),
    );
  }

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
}

{% endhighlight %}
{% endtabs %}

![flutter Datagrid displays table summary column in the row](images/summaries/flutter-datagrid-summary-column-in-row.png)

### Display table summary for column

The summary information can be displayed in a column by setting the `GridTableSummaryRow.showSummaryInRow` property to `false`. You can define summary columns to the `GridTableSummaryRow` by adding the [GridSummaryColumn](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridSummaryColumn-class.html) to the [GridTableSummaryRow.columns](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridTableSummaryRow/columns.html) collection. The `GridSummaryColumn` contains the following required properties:

* [name](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridSummaryColumn/name.html): Defines the corresponding column name for the summary calculation. This should be the same value as the [GridColumn.columnName](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridCell/columnName.html) property.
* [columnName](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridSummaryColumn/columnName.html): Defines the corresponding column name for the summary calculation.
* [summaryType](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridSummaryColumn/summaryType.html): Defines the summary calculation type.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Syncfusion Flutter DataGrid'),
      ),
      body: SfDataGrid(
        source: employeeDataSource,
        tableSummaryRows: [
          GridTableSummaryRow(
              showSummaryInRow: false,
              columns: [
                GridSummaryColumn(
                    name: 'Sum',
                    columnName: 'salary',
                    summaryType: GridSummaryType.sum),
              ],
              position: GridTableSummaryRowPosition.bottom)
        ],
        columns: <GridColumn>[
          GridColumn(
              columnName: 'id',
              label: Container(
                  padding: EdgeInsets.all(16.0),
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
                    'Job Title',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'salary',
              label: Container(
                  padding: EdgeInsets.all(8.0),
                  alignment: Alignment.center,
                  child: Text('Salary'))),
        ],
      ),
    );
  }

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource({required List<Employee> employeeData}) {
    _employeeData = employeeData
        .map<DataGridRow>((e) => DataGridRow(cells: [
              DataGridCell<int>(columnName: 'id', value: e.id),
              DataGridCell<String>(columnName: 'name', value: e.name),
              DataGridCell<String>(
                  columnName: 'designation', value: e.designation),
              DataGridCell<int>(columnName: 'salary', value: e.salary),
            ]))
        .toList();
  }

  List<DataGridRow> _employeeData = [];

  @override
  List<DataGridRow> get rows => _employeeData;

  @override
  Widget? buildTableSummaryCellWidget(
      GridTableSummaryRow summaryRow,
      GridSummaryColumn? summaryColumn,
      RowColumnIndex rowColumnIndex,
      String summaryValue) {
    return Container(
      padding: EdgeInsets.all(15.0),
      child: Text(summaryValue),
    );
  }

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
} 

{% endhighlight %}
{% endtabs %}

![flutter Datagrid displays table summary column in column](images/summaries/flutter-datagrid-summary-column-in-column.png)

### Positioning table summary row

The table summary row can be shown at the either top or bottom position by using the [GridTableSummaryRow.position](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridTableSummaryRow/position.html) property.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Syncfusion Flutter DataGrid'),
      ),
      body: SfDataGrid(
        source: employeeDataSource,
        tableSummaryRows: [
          GridTableSummaryRow(
              showSummaryInRow: false,
              columns: [
                GridSummaryColumn(
                    name: 'Sum',
                    columnName: 'salary',
                    summaryType: GridSummaryType.sum)
              ],
              position: GridTableSummaryRowPosition.top),
          GridTableSummaryRow(
              showSummaryInRow: true,
              title: 'Total Salary: {Sum} for 20 employees',
              columns: [
                GridSummaryColumn(
                    name: 'Sum',
                    columnName: 'salary',
                    summaryType: GridSummaryType.sum)
              ],
              position: GridTableSummaryRowPosition.bottom)
        ],
        columns: <GridColumn>[
          GridColumn(
              columnName: 'id',
              label: Container(
                  padding: EdgeInsets.all(16.0),
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
                    'Job Title',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'salary',
              label: Container(
                  padding: EdgeInsets.all(8.0),
                  alignment: Alignment.center,
                  child: Text('Salary'))),
        ],
      ),
    );
  }

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource({required List<Employee> employeeData}) {
    _employeeData = employeeData
        .map<DataGridRow>((e) => DataGridRow(cells: [
              DataGridCell<int>(columnName: 'id', value: e.id),
              DataGridCell<String>(columnName: 'name', value: e.name),
              DataGridCell<String>(
                  columnName: 'designation', value: e.designation),
              DataGridCell<int>(columnName: 'salary', value: e.salary),
            ]))
        .toList();
  }

  List<DataGridRow> _employeeData = [];

  @override
  List<DataGridRow> get rows => _employeeData;

  @override
  Widget? buildTableSummaryCellWidget(
      GridTableSummaryRow summaryRow,
      GridSummaryColumn? summaryColumn,
      RowColumnIndex rowColumnIndex,
      String summaryValue) {
    return Container(
      padding: EdgeInsets.all(15.0),
      child: Text(summaryValue),
    );
  }

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
}

{% endhighlight %}
{% endtabs %}

![flutter Datagrid shows the positioning of the table summary column](images/summaries/flutter-datagrid-position-of-summary-column.png)

### Summary calculation types

The following calculation types are supported for the summary calculation:

* **Sum**: Calculate the sum of a column
* **Average**: Calculate the average of a column.
* **Count**: Calculate the total of rows in `SfDataGrid`.
* **Maximum**: Calculate the maximum value in a column.
* **Minimum**: Calculate the minimum value in a column.

### Display table summary row with title

The SfDataGrid supports displaying columns’ summary value along with the title by defining the `GridTableSummaryRow.title` and [GridTableSummaryRow.titleColumnSpan](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridTableSummaryRow/titleColumnSpan.html) properties along with the summary columns. Showing a column summary with the title can be supported only if the `GridSummaryRow.showSummaryInRow` is `false`. The `GridTableSummaryRow.titleColumnSpan` property defines how long the title should be spanned in the corresponding summary row.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Syncfusion Flutter DataGrid'),
      ),
      body: SfDataGrid(
        source: employeeDataSource,
        tableSummaryRows: [
          GridTableSummaryRow(
              showSummaryInRow: false,
              title: 'Total Employee Count: {Count}',
              titleColumnSpan: 3,
              columns: [
                GridSummaryColumn(
                    name: 'Count',
                    columnName: 'id',
                    summaryType: GridSummaryType.count),
                GridSummaryColumn(
                    name: 'Sum',
                    columnName: 'salary',
                    summaryType: GridSummaryType.sum)
              ],
              position: GridTableSummaryRowPosition.bottom),
        ],
        columns: <GridColumn>[
          GridColumn(
              columnName: 'id',
              label: Container(
                  padding: EdgeInsets.all(16.0),
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
                    'Job Title',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'salary',
              label: Container(
                  padding: EdgeInsets.all(8.0),
                  alignment: Alignment.center,
                  child: Text('Salary'))),
        ],
      ),
    );
  }

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource({required List<Employee> employeeData}) {
    _employeeData = employeeData
        .map<DataGridRow>((e) => DataGridRow(cells: [
              DataGridCell<int>(columnName: 'id', value: e.id),
              DataGridCell<String>(columnName: 'name', value: e.name),
              DataGridCell<String>(
                  columnName: 'designation', value: e.designation),
              DataGridCell<int>(columnName: 'salary', value: e.salary),
            ]))
        .toList();
  }

  List<DataGridRow> _employeeData = [];

  @override
  List<DataGridRow> get rows => _employeeData;

  @override
  Widget? buildTableSummaryCellWidget(
      GridTableSummaryRow summaryRow,
      GridSummaryColumn? summaryColumn,
      RowColumnIndex rowColumnIndex,
      String summaryValue) {
    return Container(
      padding: EdgeInsets.all(15.0),
      child: Text(summaryValue),
    );
  }

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
}

{% endhighlight %}
{% endtabs %}

![flutter Datagrid shows the table summary column along with the title](images/summaries/flutter-datagrid-summary-column-with-title.png)

### Set the background color for the table summary row

The background color of the table summary row can be customized by using the [GridTableSummaryRow.color](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridTableSummaryRow/color.html) property.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Syncfusion Flutter DataGrid'),
      ),
      body: SfDataGrid(
        source: employeeDataSource,
        tableSummaryRows: [
          GridTableSummaryRow(
              color: Colors.indigo,
              showSummaryInRow: true,
              title: 'Minimum Salary: {Minimum} for 20 employees',
              columns: [
                GridSummaryColumn(
                    name: 'Minimum',
                    columnName: 'salary',
                    summaryType: GridSummaryType.minimum)
              ],
              position: GridTableSummaryRowPosition.bottom),
        ],
        columns: <GridColumn>[
          GridColumn(
              columnName: 'id',
              label: Container(
                  padding: EdgeInsets.all(16.0),
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
                    'Job Title',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'salary',
              label: Container(
                  padding: EdgeInsets.all(8.0),
                  alignment: Alignment.center,
                  child: Text('Salary'))),
        ],
      ),
    );
  }

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource({required List<Employee> employeeData}) {
    _employeeData = employeeData
        .map<DataGridRow>((e) => DataGridRow(cells: [
              DataGridCell<int>(columnName: 'id', value: e.id),
              DataGridCell<String>(columnName: 'name', value: e.name),
              DataGridCell<String>(
                  columnName: 'designation', value: e.designation),
              DataGridCell<int>(columnName: 'salary', value: e.salary),
            ]))
        .toList();
  }

  List<DataGridRow> _employeeData = [];

  @override
  List<DataGridRow> get rows => _employeeData;

  @override
  Widget? buildTableSummaryCellWidget(
      GridTableSummaryRow summaryRow,
      GridSummaryColumn? summaryColumn,
      RowColumnIndex rowColumnIndex,
      String summaryValue) {
    return Container(
      padding: EdgeInsets.all(15.0),
      child: Text(
        summaryValue,
        style: TextStyle(fontWeight: FontWeight.bold, color: Colors.white),
      ),
    );
  }

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
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows customization of table summary row](images/summaries/flutter-datagrid-summary-row-customization.png)

### Customize table summary calculation

You can write the custom logic for the summary calculation by overriding the [calculateSummaryValue](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/calculateSummaryValue.html) method from the `DataGridSource` class. The `summaryColumn` parameter will be null for the summary cells in the spanned summary columns.

The following example demonstrates how to customize the summary calculation to find the standard deviation for all employees' salaries.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Syncfusion Flutter DataGrid'),
      ),
      body: SfDataGrid(
        source: employeeDataSource,
        tableSummaryRows: [
          GridTableSummaryRow(
              showSummaryInRow: true,
              title: 'Standard Deviation: {Deviation}',
              columns: [
                GridSummaryColumn(
                    name: 'Deviation',
                    columnName: 'salary',
                    summaryType: GridSummaryType.sum)
              ],
              position: GridTableSummaryRowPosition.bottom),
        ],
        columns: <GridColumn>[
          GridColumn(
              columnName: 'id',
              label: Container(
                  padding: EdgeInsets.all(16.0),
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
                    'Job Title',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'salary',
              label: Container(
                  padding: EdgeInsets.all(8.0),
                  alignment: Alignment.center,
                  child: Text('Salary'))),
        ],
      ),
    );
  }

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource({required List<Employee> employeeData}) {
    _employeeData = employeeData
        .map<DataGridRow>((e) => DataGridRow(cells: [
              DataGridCell<int>(columnName: 'id', value: e.id),
              DataGridCell<String>(columnName: 'name', value: e.name),
              DataGridCell<String>(
                  columnName: 'designation', value: e.designation),
              DataGridCell<int>(columnName: 'salary', value: e.salary),
            ]))
        .toList();
  }

  List<DataGridRow> _employeeData = [];

  @override
  List<DataGridRow> get rows => _employeeData;

  @override
  String calculateSummaryValue(GridTableSummaryRow summaryRow,
      GridSummaryColumn? summaryColumn, RowColumnIndex rowColumnIndex) {
    List<int> getCellValues(GridSummaryColumn summaryColumn) {
      final List<int> values = <int>[];
      for (final DataGridRow row in rows) {
        final DataGridCell? cell = row.getCells().firstWhereOrNull(
            (DataGridCell element) =>
                element.columnName == summaryColumn.columnName);
        if (cell != null && cell.value != null) {
          values.add(cell.value);
        }
      }
      return values;
    }

    String? title = summaryRow.title;
    if (title != null) {
      if (summaryRow.showSummaryInRow && summaryRow.columns.isNotEmpty) {
        for (final GridSummaryColumn summaryColumn in summaryRow.columns) {
          if (title!.contains(summaryColumn.name)) {
            double deviation = 0;
            final List<int> values = getCellValues(summaryColumn);
            if (values.isNotEmpty) {
              int sum = values.reduce((value, element) =>
                  value + pow(element - values.average, 2).toInt());
              deviation = sqrt((sum) / (values.length - 1));
            }
            title = title.replaceAll(
                '{${summaryColumn.name}}', deviation.toString());
          }
        }
      }
    }
    return title ?? '';
  }

  @override
  Widget? buildTableSummaryCellWidget(
      GridTableSummaryRow summaryRow,
      GridSummaryColumn? summaryColumn,
      RowColumnIndex rowColumnIndex,
      String summaryValue) {
    return Container(
      padding: EdgeInsets.all(15.0),
      child: Text(summaryValue),
    );
  }

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
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows custom logic for table summary column](images/summaries/flutter-datagrid-summary-column-custom-logic.png)
