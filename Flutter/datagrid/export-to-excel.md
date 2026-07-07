---
layout: post
title: Export Flutter DataGrid to Excel | Flutter DataTable | Syncfusion
description: Learn how to export the Syncfusion Flutter DataGrid (SfDataGrid) into Excel and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Export to Excel in Flutter DataGrid (SfDataGrid)

The [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) provides support to export the content to Excel with several customization options.

**Add dependency**

The following dependencies must be added to your pubspec.yaml file for exporting to Excel.
  
{% highlight dart %} 

dependencies:

syncfusion_flutter_datagrid: ^xx.x.xx
syncfusion_flutter_datagrid_export: ^xx.x.xx
syncfusion_flutter_xlsio: ^xx.x.xx

{% endhighlight %}

>**NOTE:** Replace **xx.x.xx** with the latest version of the packages from [pub.dev](https://pub.dev). Ensure all three packages have compatible versions. Requires Flutter 3.0 and above.

**Import package**

Import the following packages in your Dart code.

{% tabs %}
{% highlight Dart %} 

import 'dart:io';
import 'package:syncfusion_flutter_datagrid_export/export.dart';
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

{% endhighlight %}
{% endtabs %}

Export the `SfDataGrid` by using the following extension methods present in the [SfDataGridState](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGridState-class.html) class.

* [exportToExcelWorkbook](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridExcelExportExtensions/exportToExcelWorkbook.html)
* [exportToExcelWorksheet](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridExcelExportExtensions/exportToExcelWorksheet.html)
  

**Create a helper method for saving files**

Create a helper method to save and launch the exported Excel file. This method handles platform-specific file operations.

{% tabs %}
{% highlight Dart %}

class FileHelper {
  static Future<void> saveAndLaunchFile(List<int> bytes, String fileName) async {
    final String path = (await getApplicationDocumentsDirectory()).path;
    final File file = File('$path/$fileName');
    await file.writeAsBytes(bytes, flush: true);
    
    if (await file.exists()) {
      // Open the file with the default application
      await OpenFile.open('$path/$fileName');
    }
  }
}

{% endhighlight %}
{% endtabs %}

>**NOTE:** You need to add the `path_provider` and `open_file` packages to your pubspec.yaml to use the helper method above.

**Add GlobalKey for the DataGrid**
 
Create the [GlobalKey](https://api.flutter.dev/flutter/widgets/GlobalKey-class.html) using the `SfDataGridState` class. Exporting related methods are available in the [SfDataGridState](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGridState-class.html) class.

Set the created `GlobalKey` to the `SfDataGrid`.

{% tabs %}
{% highlight Dart %}

final GlobalKey<SfDataGridState> key = GlobalKey<SfDataGridState>();
    
{% endhighlight %}
{% endtabs %}

The following code illustrates how to create and export a `SfDataGrid` to Excel using the global key.

 {% tabs %}
 {% highlight Dart %}

final GlobalKey<SfDataGridState> _dataGridKey = GlobalKey<SfDataGridState>();

@override
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: const Text(
        'Syncfusion Flutter DataGrid Export',
        overflow: TextOverflow.ellipsis,
      ),
    ),
    body: Column(
      crossAxisAlignment: CrossAxisAlignment.start,
      children: <Widget>[
        Container(
          height: 50.0,
          width: 150.0,
          padding: const EdgeInsets.all(10.0),
          child: MaterialButton(
              color: Colors.blue,
              child: const Center(
                  child: Text(
                'Export to Excel',
                style: TextStyle(color: Colors.white),
              )),
              onPressed: () async {
                final Workbook workbook =
                    _dataGridKey.currentState!.exportToExcelWorkbook();
                final List<int> bytes = workbook.saveAsStream();
                workbook.dispose();
                await FileHelper.saveAndLaunchFile(bytes, 'DataGrid.xlsx');
              }),
        ),
        Expanded(
          child: SfDataGrid(
            key: _dataGridKey,
            source: employeeDataSource,
            columns: <GridColumn>[
              GridColumn(
                  columnName: 'ID',
                  label: Container(
                      padding: const EdgeInsets.all(16.0),
                      alignment: Alignment.center,
                      child: const Text(
                        'ID',
                      ))),
              GridColumn(
                  columnName: 'Name',
                  label: Container(
                      padding: const EdgeInsets.all(8.0),
                      alignment: Alignment.center,
                      child: const Text('Name'))),
              GridColumn(
                  columnName: 'Designation',
                  label: Container(
                      padding: const EdgeInsets.all(8.0),
                      alignment: Alignment.center,
                      child: const Text(
                        'Designation',
                        overflow: TextOverflow.ellipsis,
                      ))),
              GridColumn(
                  columnName: 'Salary',
                  label: Container(
                      padding: const EdgeInsets.all(8.0),
                      alignment: Alignment.center,
                      child: const Text('Salary'))),
            ],
          ),
        ),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}



## Export DataGrid to Excel workbook

You can export the data to an [Excel Workbook](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Workbook-class.html) by using the [exportToExcelWorkbook](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridExcelExportExtensions/exportToExcelWorkbook.html) method from the `currentState` of the DataGrid.

{% tabs %}
{% highlight Dart %}

final Workbook workbook = _dataGridKey.currentState!.exportToExcelWorkbook();
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();
await FileHelper.saveAndLaunchFile(bytes, 'DataGrid.xlsx');
  
{% endhighlight %}
{% endtabs %}

## Export DataGrid to Excel sheet

Export the data to an [Excel Worksheet](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Worksheet-class.html) by using the [exportToExcelWorksheet](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridExcelExportExtensions/exportToExcelWorksheet.html) method from the `currentState` of the DataGrid.

{% tabs %}
{% highlight Dart %}

final Workbook workbook = Workbook();
final Worksheet worksheet = workbook.worksheets[0];
_dataGridKey.currentState!.exportToExcelWorksheet(worksheet);
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();
await FileHelper.saveAndLaunchFile(bytes, 'DataGrid.xlsx');
  
{% endhighlight %}
{% endtabs %}

## Exporting options 

### Exclude columns when exporting

By default, all the columns in the `SfDataGrid` are exported to Excel. To exclude certain columns when exporting to Excel, add those column names to the [excludeColumns](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/excludeColumns.html) parameter.

{% tabs %}
{% highlight Dart %}

final Workbook workbook = _dataGridKey.currentState!
    .exportToExcelWorkbook(excludeColumns: ['Name']);
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();
     
{% endhighlight %}
{% endtabs %}

![excel shows the grid with excluded columns](images/export-to-excel/flutter-datagrid-excel-export-exclude-columns.png)

### Exclude table summaries when exporting

By default, table summaries in the `SfDataGrid` are exported to Excel. Set the [exportTableSummaries](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/exportTableSummaries.html) parameter as `false` to export the `SfDataGrid` without table summaries.

{% tabs %}
{% highlight Dart %}

final Workbook workbook = _dataGridKey.currentState!
    .exportToExcelWorkbook(exportTableSummaries: false);
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

{% endhighlight %}
{% endtabs %}

### Exclude stacked headers when exporting

By default, stacked headers in the `SfDataGrid` are exported to Excel. Set the [exportStackedHeaders](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/exportStackedHeaders.html) parameter as `false` to export the `SfDataGrid` without stacked headers.

{% tabs %}
{% highlight Dart %}

final Workbook workbook = _dataGridKey.currentState!
    .exportToExcelWorkbook(exportStackedHeaders: false);
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

{% endhighlight %}
{% endtabs %}

### Change the start row and column index when exporting

By default, the DataGrid is exported from the (0,0) index in an Excel sheet. Export the data from a specific row and column indexes in an Excel worksheet by setting the [startColumnIndex](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/startColumnIndex.html) and [startRowIndex](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/startRowIndex.html) properties.

{% tabs %}
{% highlight Dart %}

final Workbook workbook = _dataGridKey.currentState!
    .exportToExcelWorkbook(startRowIndex: 3, startColumnIndex: 2);
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

{% endhighlight %}
{% endtabs %}

## Export the selected rows to Excel

By default, the entire grid is exported to Excel. Export the selected rows only by passing the [selectedRows](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/selectedRows.html) from the [DataGridController](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController-class.html) to the [rows](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/rows.html) parameter in `exportToExcelWorksheet` and `exportToExcelWorkbook` methods.

{% tabs %}
{% highlight Dart %}

final DataGridController controller = DataGridController();

// In your SfDataGrid widget
SfDataGrid(
  controller: controller,
  // ... other properties
);

// Export selected rows
final Workbook workbook = _dataGridKey.currentState!
    .exportToExcelWorkbook(rows: controller.selectedRows);
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();
await FileHelper.saveAndLaunchFile(bytes, 'SelectedRows.xlsx');

{% endhighlight %}
{% endtabs %}

>**NOTE:** Ensure row selection is enabled in the SfDataGrid by setting the `selectionMode` property to `SelectionMode.multiple` or `SelectionMode.single`.

## Row height and column width customization

The following table explains how row height and column width are handled during export:

| Property | When `true` | When `false` |
|----------|-----------|-----------|
| [exportRowHeight](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/exportRowHeight.html) | Uses `SfDataGrid.headerRowHeight` and `SfDataGrid.rowHeight` from the DataGrid | Uses [defaultRowHeight](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/defaultRowHeight.html) value |
| [exportColumnWidth](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/exportColumnWidth.html) | Uses actual column widths from the DataGrid | Uses [defaultColumnWidth](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/defaultColumnWidth.html) value |

**Example: Use custom row height and column width**

{% tabs %}
{% highlight Dart %}

final Workbook workbook = _dataGridKey.currentState!.exportToExcelWorkbook(
    exportRowHeight: false,
    exportColumnWidth: false,
    defaultRowHeight: 35,
    defaultColumnWidth: 120);
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

{% endhighlight %}
{% endtabs %}

## Styling cells based on the cell type in Excel

Customize the cell styles based on cell type using the [cellExport](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/cellExport.html) callback parameter in the `exportToExcelWorkbook` and `exportToExcelWorksheet` methods.

{% tabs %}
{% highlight Dart %}

final Workbook workbook = _dataGridKey.currentState!.exportToExcelWorkbook(
    cellExport: (DataGridCellExcelExportDetails details) {
  if (details.cellType == DataGridExportCellType.columnHeader) {
    details.excelRange.cellStyle.backColor = '#42A5F5';
  } else if (details.cellType == DataGridExportCellType.row) {
    details.excelRange.cellStyle.backColor = '#FFA726';
  }
});
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

{% endhighlight %}
{% endtabs %}

![excel shows the cell styling](images/export-to-excel/flutter-datagrid-excel-export-styling.png)

## Cell customization when exporting

### Customize cell values while exporting

The cell value can be customized while exporting to Excel by directly setting the cell value to the [excelRange.value](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridCellExcelExportDetails/excelRange.html) property available in the argument of the `cellExport` callback.

{% tabs %}
{% highlight Dart %}

final Workbook workbook = _dataGridKey.currentState!.exportToExcelWorkbook(
    cellExport: (DataGridCellExcelExportDetails details) {
  if (details.cellType == DataGridExportCellType.row &&
      details.cellValue == 'Project Lead') {
    details.excelRange.value = 'Lead';
  }
});
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

{% endhighlight %}
{% endtabs %}

![excel shows the cell customization](images/export-to-excel/flutter-datagrid-excel-export-cell-customization.png)

### Customize the cells based on the column

You can customize the column style based on the column name when exporting to Excel by using the [cellExport](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/cellExport.html) callback parameter.

{% tabs %}
{% highlight Dart %}

final Workbook workbook = _dataGridKey.currentState!.exportToExcelWorkbook(
    cellExport: (DataGridCellExcelExportDetails details) {
  if (details.cellType == DataGridExportCellType.row &&
      details.columnName == 'Name') {
    details.excelRange.cellStyle
      ..bold = true
      ..fontColor = '#F44336';
  }
});
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();

{% endhighlight %}
{% endtabs %}

## Customize Exporting Behavior 

Customize the exporting behavior by overriding the available methods in the [DataGridToExcelConverter](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter-class.html) class. Use the `converter` parameter in the `exportToExcelWorksheet` or `exportToExcelWorkbook` method.

**Example: Customize column headers and apply formatting**

{% tabs %}
{% highlight Dart %}

class CustomDataGridToExcelConverter extends DataGridToExcelConverter {
  @override
  void exportColumnHeaders(SfDataGrid dataGrid, Worksheet worksheet) {
    // Apply custom formatting to headers
    super.exportColumnHeaders(dataGrid, worksheet);
    final Range headerRange = worksheet.getRangeByIndex(1, 1, 1, dataGrid.columns.length);
    headerRange.cellStyle.bold = true;
    headerRange.cellStyle.fontSize = 12;
  }

  @override
  Object? getCellValue(DataGridRow row, GridColumn column) {
    // Customize cell values during export
    final Object? cellValue = super.getCellValue(row, column);
    if (column.columnName == 'Salary' && cellValue != null) {
      return '\$$cellValue'; // Format salary with currency symbol
    }
    return cellValue;
  }

  @override
  void exportTableSummaryRows(SfDataGrid dataGrid,
      GridTableSummaryRowPosition position, Worksheet worksheet) {
    // Add custom handling for summary rows
    super.exportTableSummaryRows(dataGrid, position, worksheet);
  }
}

{% endhighlight %}
{% endtabs %}

**Use the custom converter when exporting**

{% tabs %}
{% highlight Dart %}

final CustomDataGridToExcelConverter converter = CustomDataGridToExcelConverter();
final Workbook workbook = _dataGridKey.currentState!.exportToExcelWorkbook(converter: converter);
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();
await FileHelper.saveAndLaunchFile(bytes, 'CustomExport.xlsx');

{% endhighlight %}
{% endtabs %}
