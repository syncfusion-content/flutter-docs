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

syncfusion_flutter_datagrid_export: ^xx.x.xx

{% endhighlight %}

  >**NOTE:** Here, **xx.x.xx** denotes the current version of `Syncfusion Flutter DataGrid Export` package.

**Import package**

Import the following package in your Dart code.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid_export/export.dart';

import 'package:syncfusion_flutter_xlsio/xlsio.dart';

{% endhighlight %}
{% endtabs %}

Export the `SfDataGrid` by using the following extension methods present in the [SfDataGridState](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGridState-class.html) class.

* [exportToExcelWorkbook](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridExcelExportExtensions/exportToExcelWorkbook.html)
* [exportToExcelWorksheet](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridExcelExportExtensions/exportToExcelWorksheet.html)
  

**Add GlobalKey for the DataGrid**
 
Create the [GlobalKey](https://api.flutter.dev/flutter/widgets/GlobalKey-class.html) using the `SfDataGridState` class. Exporting related methods are available in the `SfDataGridState` class.

Set the created `GlobalKey` to the `SfDataGrid`.

{% tabs %}
{% highlight Dart %}

final GlobalKey<SfDataGridState> key = GlobalKey<SfDataGridState>();
    
{% endhighlight %}
{% endtabs %}

The following code illustrates how to create and export a `SfDataGrid` to Excel using the global key.

 {% tabs %}
 {% highlight Dart %}

final GlobalKey<SfDataGridState> key = GlobalKey<SfDataGridState>();

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
                    key.currentState!.exportToExcelWorkbook();
                final List<int> bytes = workbook.saveAsStream();
                workbook.dispose();
                await helper.saveAndLaunchFile(bytes, 'DataGrid.xlsx');
              }),
        ),
        Expanded(
          child: SfDataGrid(
            key: key,
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

## Save the Excel document as a file

To save the file as an Excel document, it’s necessary to include [mobile](https://help.syncfusion.com/flutter/xlsio/getting-started#create-an-excel-document-in-mobile), [web](https://help.syncfusion.com/flutter/xlsio/getting-started#create-an-excel-document-in-web) and [desktop](https://help.syncfusion.com/flutter/xlsio/getting-started#create-an-excel-document-in-desktop) platform-specific file generating code.

## Export DataGrid to Excel workbook

You can export the data to [Excel Workbook](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Workbook-class.html) by using the `exportToExcelWorkbook` method from the `key.currentState` of the DataGrid.

{% tabs %}
{% highlight Dart %}

final Workbook workbook = key.currentState!.exportToExcelWorkbook();
final List<int> bytes = workbook.saveAsStream();
File('DataGrid.xlsx').writeAsBytes(bytes, flush: true);
  
{% endhighlight %}
{% endtabs %}

## Export DataGrid to Excel sheet

Export the data to [Excel Worksheet](https://pub.dev/documentation/syncfusion_flutter_xlsio/latest/xlsio/Worksheet-class.html) by using the `exportToExcelWorksheet` method from the `key.currentState` of the DataGrid.

{% tabs %}
{% highlight Dart %}

final Workbook workbook = Workbook();
final Worksheet worksheet = workbook.worksheets[0];
key.currentState!.exportToExcelWorksheet(worksheet);
final List<int> bytes = workbook.saveAsStream();
File('DataGrid.xlsx').writeAsBytes(bytes, flush: true);
  
{% endhighlight %}
{% endtabs %}

## Exporting options 

### Exclude columns when exporting

By default, all the columns in the `SfDataGrid` are exported to Excel. To exclude certain columns when exporting to Excel, add those column names to the [excludeColumns](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/excludeColumns.html) parameter.

{% tabs %}
{% highlight Dart %}

Workbook workbook = key.currentState!
    .exportToExcelWorkbook(excludeColumns: ['Name']);
final List<int> bytes = workbook.saveAsStream();
     
{% endhighlight %}
{% endtabs %}

![excel shows the grid with excluded columns](images/export-to-excel/flutter-datagrid-excel-export-exclude-columns.png)

### Exclude table summaries when exporting

By default, table summaries in the `SfDataGrid` are exported to Excel. Set the [exportTableSummaries](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/exportTableSummaries.html) parameter as `false` to export the `SfDataGrid` without table summaries.

{% tabs %}
{% highlight Dart %}

Workbook workbook = key.currentState!
    .exportToExcelWorkbook(exportTableSummaries: false);
final List<int> bytes = workbook.saveAsStream();

{% endhighlight %}
{% endtabs %}

### Exclude stacked headers when exporting

By default, stacked headers in the `SfDataGrid` are exported to Excel. Set the [exportStackedHeaders](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/exportStackedHeaders.html) parameter as `false` to export the `SfDataGrid` without stacked headers.

{% tabs %}
{% highlight Dart %}

Workbook workbook = key.currentState!
    .exportToExcelWorkbook(exportStackedHeaders: false);
final List<int> bytes = workbook.saveAsStream();

{% endhighlight %}
{% endtabs %}

### Change the start row and column index when exporting

By default, the DataGrid is exported from the (0,0) index in an Excel sheet. Export the data from a specific row and column indexes in an Excel worksheet by setting the [startColumnIndex](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/startColumnIndex.html) and [startRowIndex](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/startRowIndex.html) properties.

{% tabs %}
{% highlight Dart %}

Workbook workbook = key.currentState!
    .exportToExcelWorkbook(startRowIndex: 3, startColumnIndex: 2);
final List<int> bytes = workbook.saveAsStream();

{% endhighlight %}
{% endtabs %}

## Export the selected rows to Excel

By default, the entire grid is exported to Excel. Export the selected rows only by passing the [dataGridController.selectedRows](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/selectedRows.html) to [rows](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/rows.html) parameter in `exportToExcelWorksheet` and `exportToExcelWorkbook` methods.

{% tabs %}
{% highlight Dart %}

Workbook workbook = key.currentState!
    .exportToExcelWorkbook(rows: dataGridController.selectedRows);
final List<int> bytes = workbook.saveAsStream();

{% endhighlight %}
{% endtabs %}

## Row height and column width customization

By default, [SfDataGrid.rowHeight](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/rowHeight.html) and [SfDataGrid.defaultColumnWidth](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/defaultColumnWidth.html) properties will be set to the cells in the Excel sheet. To customize the row height and column width in Excel, you can use the [defaultRowHeight](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/defaultRowHeight.html) and [defaultColumnWidth](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/defaultColumnWidth.html) properties. But these properties are only applicable when the [exportRowHeight](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/exportRowHeight.html) and [exportColumnWidth](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/exportColumnWidth.html) properties are `false`.

If the `exportRowHeight` and `exportColumnWidth` properties are `true`, the [SfDataGrid.headerRowHeight](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/headerRowHeight.html) and `SfDataGrid.rowHeight` properties are considered for row heights in Excel and the actual width of the column is considered for columns in Excel.

{% tabs %}
{% highlight Dart %}

Workbook workbook = key.currentState!.exportToExcelWorkbook(
    exportRowHeight: false,
    exportColumnWidth: false,
    defaultRowHeight: 35,
    defaultColumnWidth: 120);
final List<int> bytes = workbook.saveAsStream();

{% endhighlight %}
{% endtabs %}

## Styling cells based on the cell type in Excel

Customize the cell styles based on cell type using the [cellExport](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/cellExport.html) parameter, which is a callback in the `exportToExcelWorkbook` and `exportToExcelWorksheet` methods.

{% tabs %}
{% highlight Dart %}

final Workbook workbook = key.currentState!.exportToExcelWorkbook(
    cellExport: (DataGridCellExcelExportDetails details) {
  if (details.cellType == DataGridExportCellType.columnHeader) {
    details.excelRange.cellStyle.backColor = '#42A5F5';
  } else if (details.cellType == DataGridExportCellType.row) {
    details.excelRange.cellStyle.backColor = '#FFA726';
  }
});
final List<int> bytes = workbook.saveAsStream();

{% endhighlight %}
{% endtabs %}

![excel shows the cell styling](images/export-to-excel/flutter-datagrid-excel-export-styling.png)

## Cell customization when exporting

### Customize cell values while exporting

The cell value can be customized while exporting to Excel by directly setting the cell value of a cell to the [excelRange.value](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridCellExcelExportDetails/excelRange.html) property available in the argument of `cellExport` callback.

{% tabs %}
{% highlight Dart %}

final Workbook workbook = key.currentState!.exportToExcelWorkbook(
    cellExport: (DataGridCellExcelExportDetails details) {
  if (details.cellType == DataGridExportCellType.row &&
      details.cellValue == 'Project Lead') {
    details.excelRange.value = 'Lead';
  }
});
final List<int> bytes = workbook.saveAsStream();

{% endhighlight %}
{% endtabs %}

![excel shows the cell customization](images/export-to-excel/flutter-datagrid-excel-export-cell-customization.png)

### Customize the cells based on the column

You can customize the column style based on the column name when exporting to Excel by using the [cellExport](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter/cellExport.html) parameter.

{% tabs %}
{% highlight Dart %}

final Workbook workbook = key.currentState!.exportToExcelWorkbook(
    cellExport: (DataGridCellExcelExportDetails details) {
  if (details.cellType == DataGridExportCellType.row &&
      details.columnName == 'Name') {
    details.excelRange.cellStyle
      ..bold = true
      ..fontColor = '#F44336';
  }
});
final List<int> bytes = workbook.saveAsStream();

{% endhighlight %}
{% endtabs %}

## Customize Exporting Behavior 

Customize the exporting behavior by overriding the available methods in the [DataGridToExcelConverter](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToExcelConverter-class.html) Customize the exporting behavior by overriding the available methods in the `converter` parameter in the `exportToExcelWorksheet` or `exportToExcelWorkbook` method.

{% tabs %}
{% highlight Dart %}

class CustomDataGridToExcelConverter extends DataGridToExcelConverter {
  @override
  void exportColumnHeader(SfDataGrid dataGrid, GridColumn column,
      String columnName, Worksheet worksheet) {
    // TODO: Add your requirements in exportColumnHeader
    super.exportColumnHeader(dataGrid, column, columnName, worksheet);
  }

  @override
  void exportColumnHeaders(SfDataGrid dataGrid, Worksheet worksheet) {
    // TODO: Add your requirements in exportColumnHeaders
    super.exportColumnHeaders(dataGrid, worksheet);
  }

  @override
  void exportRow(SfDataGrid dataGrid, DataGridRow row, GridColumn column,
      Worksheet worksheet) {
    // TODO: Add your requirements in exportRow
    super.exportRow(dataGrid, row, column, worksheet);
  }

  @override
  void exportRows(
      SfDataGrid dataGrid, List<DataGridRow> rows, Worksheet worksheet) {
    // TODO: Add your requirements in exportRows
    super.exportRows(dataGrid, rows, worksheet);
  }

  @override
  void exportStackedHeaderRow(SfDataGrid dataGrid,
      StackedHeaderRow stackedHeaderRow, Worksheet worksheet) {
    // TODO: Add your requirements in exportStackedHeaderRow
    super.exportStackedHeaderRow(dataGrid, stackedHeaderRow, worksheet);
  }

  @override
  void exportStackedHeaderRows(SfDataGrid dataGrid, Worksheet worksheet) {
    // TODO: Add your requirements in exportStackedHeaderRows
    super.exportStackedHeaderRows(dataGrid, worksheet);
  }

  @override
  void exportTableSummaryRow(SfDataGrid dataGrid,
      GridTableSummaryRow summaryRow, Worksheet worksheet) {
    // TODO: Add your requirements in exportTableSummaryRow
    super.exportTableSummaryRow(dataGrid, summaryRow, worksheet);
  }

  @override
  void exportTableSummaryRows(SfDataGrid dataGrid,
      GridTableSummaryRowPosition position, Worksheet worksheet) {
    // TODO: Add your requirements in exportTableSummaryRows
    super.exportTableSummaryRows(dataGrid, position, worksheet);
  }

  @override
  Object? getCellValue(DataGridRow row, GridColumn column) {
    // TODO: Add your requirements in getCellValue
    super.getCellValue(row, column);
  }
}

{% endhighlight %}
{% endtabs %}

The following code sample illustrates how to create an instance of the `CustomDataGridToExcelConverter` class and set the instance to the `converter` parameter in the `exportToExcelWorksheet` or `exportToExcelWorkbook` method.

{% tabs %}
{% highlight Dart %}

CustomDataGridToExcelConverter converter = CustomDataGridToExcelConverter();
Workbook workbook = key.currentState!.exportToExcelWorkbook(converter: converter);
final List<int> bytes = workbook.saveAsStream();

{% endhighlight %}
{% endtabs %}