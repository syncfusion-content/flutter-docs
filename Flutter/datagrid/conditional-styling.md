---
layout: post
title: Conditional Styling in Flutter DataGrid | DataTable | Syncfusion
description: Learn here all about how to style the rows and columns in Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Conditional Styling in Flutter DataGrid (SfDataGrid)

The [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) allows customizing the style of individual cells and rows based on your requirements. You can customize your widget in the `DataGridSource.buildRow` method with the help of `DataGridRowAdapter`.

## Cells

### Styling based on content

The appearance of cells in `SfDataGrid` can be customized conditionally based on their content by setting your widget to the `DataGridRowAdapter.cells`.

{% tabs %}
{% highlight Dart %} 

  import 'package:syncfusion_flutter_datagrid/datagrid.dart';

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SfDataGrid(
        source: _employeeDataSource,
        columnWidthMode: ColumnWidthMode.lastColumnFill,
        columns: <GridColumn>[
          GridColumn(
            columnName: 'id',
            label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerRight,
              child: Text(
                'ID',
                overflow: TextOverflow.ellipsis,
              )
            )
          ),
          GridColumn(
            columnName: 'name',
            label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerLeft,
              child: Text(
                'Name',
                overflow: TextOverflow.ellipsis,
              )
            )
          ),
          GridColumn(
            columnName: 'designation',
            label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerLeft,
              child: Text(
                'Designation',
                overflow: TextOverflow.ellipsis,
              )
            )
          ),
          GridColumn(
            columnName: 'salary',
            label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerRight,
              child: Text(
                'Salary',
                overflow: TextOverflow.ellipsis,
              )
            )
          )
        ]
      )
    );
  }

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource(List<Employee> employees) {
    dataGridRows = employees
      .map<DataGridRow>((dataGridRow) => DataGridRow(cells: [
        DataGridCell<int>(columnName: 'id', value: dataGridRow.id),
        DataGridCell<String>(columnName: 'name', value: dataGridRow.name),
        DataGridCell<String>(
          columnName: 'designation', value: dataGridRow.designation),
        DataGridCell<int>(
          columnName: 'salary', value: dataGridRow.salary),
      ]))
      .toList();
  }

  List<DataGridRow> dataGridRows = [];

  @override
  List<DataGridRow> get rows => dataGridRows;

  @override
  DataGridRowAdapter? buildRow(DataGridRow row) {
    return DataGridRowAdapter(
      cells: row.getCells().map<Widget>((dataGridCell) {
        Color getColor() {
          if (dataGridCell.columnName == 'designation') {
            if (dataGridCell.value == 'Developer') {
              return Colors.tealAccent;
            } else if (dataGridCell.value == 'Manager') {
              return Colors.blue[200]!;
            }
          }
          return Colors.transparent;
        }

        TextStyle? getTextStyle() {
          if (dataGridCell.columnName == 'designation') {
            if (dataGridCell.value == 'Developer') {
              return TextStyle(fontStyle: FontStyle.italic);
            } else if (dataGridCell.value == 'Manager') {
              return TextStyle(fontStyle: FontStyle.italic);
            }
          }
          return null;
        }

        return Container(
          color: getColor(),
          alignment: (dataGridCell.columnName == 'id' ||
                    dataGridCell.columnName == 'salary')
              ? Alignment.centerRight
              : Alignment.centerLeft,
          padding: EdgeInsets.symmetric(horizontal: 16.0),
          child: Text(
            dataGridCell.value.toString(),
            overflow: TextOverflow.ellipsis,
            style: getTextStyle(),
          )
        );
      }).toList()
    );
  }
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows conditional formatting in cells](images/conditional-styling/flutter-datagrid-cells-styling-based-on-content.png)

### Styling alternate cells

The appearance of alternating cells in a column can be customized conditionally by using the `DataGridSource.buildRow` method.

{% tabs %}
{% highlight Dart %} 

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource(List<Employee> employees) {
    dataGridRows = employees
      .map<DataGridRow>((dataGridRow) => DataGridRow(cells: [
        DataGridCell<int>(columnName: 'id', value: dataGridRow.id),
        DataGridCell<String>(columnName: 'name', value: dataGridRow.name),
        DataGridCell<String>(
          columnName: 'designation', value: dataGridRow.designation),
        DataGridCell<int>(
          columnName: 'salary', value: dataGridRow.salary),
      ]))
      .toList();
  }

  List<DataGridRow> dataGridRows = [];

  @override
  List<DataGridRow> get rows => dataGridRows;

  @override
  DataGridRowAdapter? buildRow(DataGridRow row) {
    return DataGridRowAdapter(
      cells: row.getCells().map<Widget>((dataGridCell) {
        if (dataGridCell.columnName == 'id') {
          final int index = effectiveRows.indexOf(row);
          return Container(
            color: (index % 2 != 0) ? Colors.blueAccent : Colors.transparent,
            alignment: Alignment.centerRight,
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            child: Text(
              dataGridCell.value.toString(),
              overflow: TextOverflow.ellipsis,
              style: (index % 2 != 0)
                ? TextStyle(fontStyle: FontStyle.italic)
                : null,
            )
          );
        }
        return Container(
          alignment: (dataGridCell.columnName == 'salary')
              ? Alignment.centerRight
              : Alignment.centerLeft,
          padding: EdgeInsets.symmetric(horizontal: 16.0),
          child: Text(
            dataGridCell.value.toString(),
            overflow: TextOverflow.ellipsis,
          )
        );
      }).toList()
    );
  }
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows alternate cells styling](images/conditional-styling/flutter-datagrid-alternate-cells-styling.png)

## Rows

### Styling based on content

The appearance of rows in `SfDataGrid` can be customized conditionally based on the content using `DataGridRowAdapter.color`.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource(List<Employee> employees) {
    dataGridRows = employees
      .map<DataGridRow>((dataGridRow) => DataGridRow(cells: [
        DataGridCell<int>(columnName: 'id', value: dataGridRow.id),
        DataGridCell<String>(columnName: 'name', value: dataGridRow.name),
        DataGridCell<String>(
          columnName: 'designation', value: dataGridRow.designation),
        DataGridCell<int>(
          columnName: 'salary', value: dataGridRow.salary),
      ]))
      .toList();
  }

  List<DataGridRow> dataGridRows = [];

  @override
  List<DataGridRow> get rows => dataGridRows;

  @override
  DataGridRowAdapter buildRow(DataGridRow row) {
    Color getRowBackgroundColor() {
      final int salary = row.getCells()[3].value;
      if (salary >= 10000 && salary < 15000) {
        return Colors.blue[300]!;
      } else if (salary <= 15000) {
        return Colors.orange[300]!;
      }
      return Colors.transparent;
    }

    TextStyle? getTextStyle() {
      final int salary = row.getCells()[3].value;
      if (salary >= 10000 && salary < 15000) {
        return TextStyle(color: Colors.white);
      } else if (salary <= 15000) {
        return TextStyle(color: Colors.white);
      }
      return null;
    }

    return DataGridRowAdapter(
      color: getRowBackgroundColor(),
      cells: row.getCells().map<Widget>((dataGridCell) {
        return Container(
          alignment: (dataGridCell.columnName == 'id' ||
                     dataGridCell.columnName == 'salary')
              ? Alignment.centerRight
              : Alignment.centerLeft,
          padding: EdgeInsets.symmetric(horizontal: 16.0),
          child: Text(
            dataGridCell.value.toString(),
            overflow: TextOverflow.ellipsis,
            style: getTextStyle(),
          )
        );
      }).toList()
    );
  }
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows styling a row based on content](images/conditional-styling/flutter-datagrid-rows-styling-based-on-content.png)

### Styling alternate rows

The appearance of the alternating rows in `SfDataGrid` can be customized using the `DataGridRowAdapter.color`. Use the [effectiveRows](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/effectiveRows.html) property to get the index of the row. This collection contains the sorted collection if the sorting is applied.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid/datagrid.dart';

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource(List<Employee> employees) {
    dataGridRows = employees
        .map<DataGridRow>((dataGridRow) => DataGridRow(cells: [
              DataGridCell<int>(columnName: 'id', value: dataGridRow.id),
              DataGridCell<String>(columnName: 'name', value: dataGridRow.name),
              DataGridCell<String>(
                  columnName: 'designation', value: dataGridRow.designation),
              DataGridCell<int>(
                  columnName: 'salary', value: dataGridRow.salary),
            ]))
        .toList();
  }

  List<DataGridRow> dataGridRows = [];

  @override
  List<DataGridRow> get rows => dataGridRows;

  @override
  DataGridRowAdapter? buildRow(DataGridRow row) {
    Color getRowBackgroundColor() {
      final int index = effectiveRows.indexOf(row);
      if (index % 2 != 0) {
        return Colors.lightGreen[300]!;
      }

      return Colors.transparent;
    }

    return DataGridRowAdapter(
        color: getRowBackgroundColor(),
        cells: row.getCells().map<Widget>((dataGridCell) {
          return Container(
              alignment: (dataGridCell.columnName == 'id' ||
                      dataGridCell.columnName == 'salary')
                  ? Alignment.centerRight
                  : Alignment.centerLeft,
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              child: Text(
                dataGridCell.value.toString(),
                overflow: TextOverflow.ellipsis,
              ));
        }).toList());
  }
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows styling alternate rows](images/conditional-styling/flutter-datagrid-alternate-rows-styling.png)
