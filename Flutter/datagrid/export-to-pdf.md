---
layout: post
title: Export Flutter DataGrid to PDF | Flutter DataTable | Syncfusion®
description: Learn here all about how to export the Syncfusion® Flutter DataGrid (SfDataGrid) into PDF Document and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Export Flutter DataGrid to PDF (SfDataGrid)

The [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) provides support to export the content to PDF document with several customization options. 

**Add dependency**

The following dependencies must be added to your `pubspec.yaml` file for exporting to PDF.
  
{% highlight dart %} 

dependencies:

syncfusion_flutter_datagrid_export: ^xx.x.xx

{% endhighlight %}

  >**NOTE** Here, **xx.x.xx** denotes the current version of `Syncfusion® Flutter DataGrid Export` package.

**Import package**

Import the following package in your Dart code.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_datagrid_export/export.dart';

import 'package:syncfusion_flutter_pdf/pdf.dart';

{% endhighlight %}
{% endtabs %}


You can export the `SfDataGrid` to PDF by using the following extension methods present in the [SfDataGridState]((https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGridState-class.html)) class:

   * [exportToPdfDocument](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridPdfExportExtensions/exportToPdfDocument.html)
   * [exportToPdfGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridPdfExportExtensions/exportToPdfGrid.html)

**Add GlobalKey for the DataGrid**
 
Create the [GlobalKey](https://api.flutter.dev/flutter/widgets/GlobalKey-class.html) using the `SfDataGridState` class. Exporting related methods are available via `SfDataGridState` class.

Set the created `GlobalKey` to the `SfDataGrid`.

{% tabs %}
{% highlight Dart %}

final GlobalKey<SfDataGridState> key = GlobalKey<SfDataGridState>();
    
{% endhighlight %}
{% endtabs %}

The following code illustrates how to create and display a `SfDataGrid` using the global key.

{% tabs %}
{% highlight Dart %}

GlobalKey<SfDataGridState> key = GlobalKey<SfDataGridState>();

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Column(
      children: [
        ElevatedButton(
            child: Text('Export To Pdf'),
            onPressed: () {
              PdfDocument document = key.currentState!.exportToPdfDocument()
              final List<int> bytes = document.saveSync();
            }),
        Expanded(
          child: SfDataGrid(
            source: _employeeDataSource,
            columns: [
              GridColumn(
                  columnName: 'ID',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.center,
                      child: Text(
                        'ID',
                        overflow: TextOverflow.ellipsis,
                      ))),
              GridColumn(
                  columnName: 'Name',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.center,
                      child: Text(
                        'Name',
                        overflow: TextOverflow.ellipsis,
                      ))),
              GridColumn(
                  columnName: 'Designation',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.center,
                      child: Text(
                        'Designation',
                        overflow: TextOverflow.ellipsis,
                      ))),
              GridColumn(
                  columnName: 'Salary',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.center,
                      child: Text(
                        'Salary',
                        overflow: TextOverflow.ellipsis,
                      ))),
            ],
          ),
        ),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Save the PDF document as a file

To save the file as a PDF document, it’s necessary to include [mobile](https://help.syncfusion.com/flutter/pdf/getting-started#save-and-open-a-pdf-document-in-mobile), [web](https://help.syncfusion.com/flutter/pdf/getting-started#save-and-download-a-pdf-document-in-web) and desktop platform-specific file generating code.

## Export DataGrid to PDF document

Export the data to the [PdfDocument](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocument-class.html) by using the `exportToPdfDocument` method from the `key.currentState` of the DataGrid.

{% tabs %}
{% highlight Dart %}

PdfDocument document = key.currentState!.exportToPdfDocument();
final List<int> bytes = document.saveSync();
File('DataGrid.pdf').writeAsBytes(bytes);
  
{% endhighlight %}
{% endtabs %}

## Export DataGrid to PDF Grid

Export the data to the [PdfGrid](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfGrid-class.html) by using the `exportToPdfGrid` method from the `key.currentState` of the DataGrid.

{% tabs %}
{% highlight Dart %}

PdfDocument document = PdfDocument();
PdfPage pdfPage = document.pages.add();
PdfGrid pdfGrid = key.currentState!.exportToPdfGrid();
pdfGrid.draw(
 page: pdfPage,
 bounds: Rect.fromLTWH(0, 0, 0, 0),
);
final List<int> bytes = document.saveSync();
File('DataGrid.pdf').writeAsBytes(bytes);
  
{% endhighlight %}
{% endtabs %}

## Exporting options 

### Exclude columns when exporting

By default, all the columns in the SfDataGrid are exported to PDF. To exclude some particular columns while exporting to PDF, add those column names to the [excludeColumns](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToPdfConverter-class.html) parameter.

{% tabs %}
{% highlight Dart %}

PdfDocument document = key.currentState!.exportToPdfDocument( excludeColumns: ['Name']);
final List<int> bytes = document.saveSync();
     
{% endhighlight %}
{% endtabs %}

![pdf document shows grid with exclude column ](images/export-to-pdf/flutter-datagrid-pdf-exclude-column.png)

### Disable column headers on each page

You can disable the column headers on each page by setting the [canRepeatHeaders](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToPdfConverter/canRepeatHeaders.html) parameter as `false`.

{% tabs %}
{% highlight Dart %}

PdfDocument document = key.currentState!.exportToPdfDocument(canRepeatHeaders: false);
final List<int> bytes = document.saveSync();

{% endhighlight %}
{% endtabs %}

### Export all columns on one page

Fit all the columns on one page by setting the [fitAllColumnsInOnePage](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToPdfConverter/fitAllColumnsInOnePage.html) parameter as `true.`

{% tabs %}
{% highlight Dart %}

PdfDocument document = key.currentState!.exportToPdfDocument(fitAllColumnsInOnePage: true);
final List<int> bytes = document.saveSync();

{% endhighlight %}
{% endtabs %}

### Exclude table summaries when exporting

By default, table summaries in `SfDataGrid` are exported to PDF. Set the [exportTableSummaries](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToPdfConverter/exportTableSummaries.html) parameter as `false` to export the `SfDataGrid` without table summaries.

{% tabs %}
{% highlight Dart %}

PdfDocument document = key.currentState!.exportToPdfDocument(exportTableSummaries: false);
final List<int> bytes = document.saveSync();

{% endhighlight %}
{% endtabs %}


### Exclude stacked headers when exporting

By default, stacked headers in `SfDataGrid` are exported to PDF. Set the [exportStackedHeaders](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToPdfConverter/exportStackedHeaders.html) parameter as `false` to export the `SfDataGrid` without stacked headers.

{% tabs %}
{% highlight Dart %}

PdfDocument document = key.currentState!.exportToPdfDocument(exportStackedHeaders: false);
final List<int> bytes = document.saveSync();

{% endhighlight %}
{% endtabs %}

### Auto-size column widths in PDF

In order, to export the actual column width from `SfDataGrid` instead of the auto column width, set the [autoColumnWidth](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToPdfConverter/autoColumnWidth.html) parameter as `false`.

{% tabs %}
{% highlight Dart %}

PdfDocument document = key.currentState!.exportToPdfDocument(autoColumnWidth: false);
final List<int> bytes = document.saveSync();

{% endhighlight %}
{% endtabs %}

>**NOTE**
       If you disabled the `autoColumnWidth`, then you must set `fitAllColumnsInOnePage` as false. Then only, the overflowing columns are drawn in next page. Because `fitAllColumnsInOnePage` has topmost priority.


## Change the orientation of the PDF document

Change the orientation of a page in a PDF document by using the [PdfDocument.pageSettings.orientation](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPageSettings/orientation.html) property.

To change the page orientation, you need to export the `SfDataGrid` to `PdfGrid` using the `exportToPdfGrid` method and draw the exported `PdfGrid` into a `PdfDocument`.

{% tabs %}
{% highlight Dart %}

PdfDocument document = PdfDocument();
document.pageSettings.orientation = PdfPageOrientation.landscape;
PdfPage pdfPage = document.pages.add();
PdfGrid pdfGrid = key.currentState!.exportToPdfGrid();
pdfGrid.draw(
  page: pdfPage,
  bounds: Rect.fromLTWH(0, 0, 0, 0));
final List<int> bytes = document.saveSync();
  
{% endhighlight %}
{% endtabs %}

## Export the selected rows to PDF

By default, the entire grid is exported to PDF. Export the selected rows only by passing the [dataGridController.selectedRows](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/selectedRows.html) to [rows](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/rows.html) parameter in `exportToPdfDocument` and `exportToPdfGrid` methods.

{% tabs %}
{% highlight Dart %}

PdfDocument document = key.currentState!.exportToPdfDocument(rows: dataGridController.selectedRows,);
final List<int> bytes = document.saveSync();

{% endhighlight %}
{% endtabs %}

## Setting header and footer in PDF document

`SfDataGrid` provides a way to display additional content at the top (Header) and bottom (Footer) of the PDF page while exporting to PDF. This can be achieved by using the [headerFooterExport](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToPdfConverter/headerFooterExport.html) parameter in the `exportToPdfDocument` or `exportToPdfGrid` methods.

Setting the [PdfPageTemplateElement](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfPageTemplateElement-class.html) to [headerFooterExport.pdfDocumentTemplate.top](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocumentTemplate/top.html) loads the content at the top of the page, while setting the `PdfPageTemplateElement` to [headerFooterExport.pdfDocumentTemplate.bottom](https://pub.dev/documentation/syncfusion_flutter_pdf/latest/pdf/PdfDocumentTemplate/bottom.html) loads the content at the bottom of the page.

{% tabs %}
{% highlight Dart %}

PdfDocument document = key.currentState!.exportToPdfDocument(
    headerFooterExport: (DataGridPdfHeaderFooterExportDetails headerFooterExport) {
      final double width = headerFooterExport.pdfPage.getClientSize().width;
      final PdfPageTemplateElement header = PdfPageTemplateElement(Rect.fromLTWH(0, 0, width, 65));
      header.graphics.drawString(
        'Company Details',
        PdfStandardFont(PdfFontFamily.helvetica, 13, style: PdfFontStyle.bold),
        bounds: const Rect.fromLTWH(0, 25, 200, 60),
      );
      headerFooterExport.pdfDocumentTemplate.top = header;
    },
);
final List<int> bytes = document.saveSync();


{% endhighlight %}
{% endtabs %}

![pdf document shows the document header](images/export-to-pdf/flutter-datagrid-pdf-document-header.png)

## Styling cells based on the cell type in PDF

You can customize the cell styles based on cell type using the [cellExport](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToPdfConverter/cellExport.html) parameter, which is a callback in `exportToPdfDocument` or `exportToPdfGrid` methods.

{% tabs %}
{% highlight Dart %}

PdfDocument document = key.currentState!.exportToPdfDocument(cellExport: (details) {
    if (details.cellType == DataGridExportCellType.columnHeader) {
      details.pdfCell.style.backgroundBrush = PdfBrushes.pink;
    }
    if (details.cellType == DataGridExportCellType.row) {
      details.pdfCell.style.backgroundBrush = PdfBrushes.lightCyan;
    }
});
final List<int> bytes = document.saveSync();

{% endhighlight %}
{% endtabs %}

![pdf document show the cell styles](images/export-to-pdf/flutter-datagrid-pdf-cell-styles.png)

## Cell customization when exporting

### Customize cell values while exporting

The cell value can be customized while exporting to PDF by directly setting the cell value of a cell in the `PdfGrid` via the [PdfCell](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridCellPdfExportDetails/pdfCell.html) property available in the argument of the `cellExport` callback.

{% tabs %}
{% highlight Dart %}

PdfDocument document = key.currentState!.exportToPdfDocument(cellExport: (details) {
   if (details.cellType == DataGridExportCellType.row &&
       details.columnName == 'Designation') {
     if (details.cellValue == 'Project Lead') {
       details.pdfCell.value = 'Lead';
     }
   }    
});
final List<int> bytes = document.saveSync();

{% endhighlight %}
{% endtabs %}

![pdf document shows the cell customization](images/export-to-pdf/flutter-datagrid-pdf-cell-customization.png)

### Customize the Cells based on Column Name

You can customize the column style based on the column name while exporting to PDF by using the `cellExport` parameter.

{% tabs %}
{% highlight Dart %}

PdfDocument document = key.currentState!.exportToPdfDocument(cellExport: (details) {
    if (details.cellType == DataGridExportCellType.row && details.columnName == 'Customer Name') {
     details.pdfCell.style.textBrush = PdfBrushes.red;
    }
  }
);
final List<int> bytes = document.saveSync();

{% endhighlight %}
{% endtabs %}

## Customize Exporting Behavior 

Customize the exporting behavior by overriding the available methods in the [DataGridToPdfConverter](https://pub.dev/documentation/syncfusion_flutter_datagrid_export/latest/syncfusion_flutter_datagrid_export/DataGridToPdfConverter-class.html) Customize the exporting behavior by overriding the available methods in the `converter` parameter in the `exportToPdfDocument` or `exportToPdfGrid` method.

{% tabs %}
{% highlight Dart %}

class CustomDataGridToPdfConverter extends DataGridToPdfConverter {
  @override
  void exportColumnHeader(SfDataGrid dataGrid, GridColumn column,
      String columnName, PdfGrid pdfGrid) {
    // TODO: Add your requirements column header

    super.exportColumnHeader(dataGrid, column, columnName, pdfGrid);
  }

  @override
  void exportColumnHeaders(
      SfDataGrid dataGrid, List<GridColumn> columns, PdfGrid pdfGrid) {
    // TODO: Add your requirements column headers

    super.exportColumnHeaders(dataGrid, columns, pdfGrid);
  }

  @override
  void exportRows(
      List<GridColumn> columns, List<DataGridRow> rows, PdfGrid pdfGrid) {
    // TODO: Add your requirements in exportRows

    super.exportRows(columns, rows, pdfGrid);
  }

  @override
  void exportRow(List<GridColumn> columns, DataGridRow row, PdfGrid pdfGrid) {
    // TODO: Add your requirements in exportRow

    super.exportRow(columns, row, pdfGrid);
  }
}
{% endhighlight %}
{% endtabs %}

The following code sample illustrates how to create an instance of the `CustomDataGridToPdfConverter` class and set the instance to the `converter` parameter in the `exportToPdfDocument` or `exportToPdfGrid` method.

{% tabs %}
{% highlight Dart %}

CustomDataGridToPdfConverter customDataGridToPdfConverter = CustomDataGridToPdfConverter();

PdfDocument document = key.currentState!.exportToPdfDocument(converter: customDataGridToPdfConverter);
final List<int> bytes = document.saveSync();

{% endhighlight %}
{% endtabs %}
