---
layout: post
title: Column drag and drop in Flutter DataGrid | DataTable | Syncfusion
description: Learn all about how to drag and drop the columns in Syncfusion Flutter DataGrid (SfDataGrid) widget and more here.
platform: flutter
control: SfDataGrid
documentation: ug
--- 

# Column drag and drop in Flutter DataGrid (SfDataGrid)

The SfDataGrid allows column header dragging and dropping by setting the `SfDataGrid.allowColumnsDragging` property to `true` and returning `true` from the `SfDataGrid.onColumnDragging` callback. During the column dragging process, a drag feedback widget is displayed. By utilizing the `SfDataGrid.onColumnDragging` event, you can handle drag and drop operations according to your requirements.

The DataGrid provides the rearranged index of the dragged column, indicating its new position after being dropped. Inside the `onColumnDragging` callback, you can utilize this index to reorder the columns according to the desired position. This allows you to handle the column reordering directly within the callback at the sample level.

{% tabs %}
{% highlight Dart %} 

class MyHomePageState extends State<MyHomePage> {
  List<Employee> employees = <Employee>[];
  late List<GridColumn> columns;
  late EmployeeDataSource employeeDataSource;

  @override
  void initState() {
    super.initState();
    columns = getColumns;
    employees = getEmployeeData();
    employeeDataSource =
        EmployeeDataSource(employees: employees, columns: columns);
  }

  List<GridColumn> get getColumns {
    return <GridColumn>[
      GridColumn(
          columnName: 'id',
          label: Container(
              padding: const EdgeInsets.all(16.0),
              alignment: Alignment.center,
              child: const Text(
                'ID',
              ))),
      GridColumn(
          columnName: 'name',
          label: Container(
              padding: const EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: const Text('Name'))),
      GridColumn(
          columnName: 'designation',
          label: Container(
              padding: const EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: const Text(
                'Designation',
                overflow: TextOverflow.ellipsis,
              ))),
      GridColumn(
          columnName: 'salary',
          label: Container(
              padding: const EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: const Text('Salary'))),
    ];
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: SfDataGrid(
        source: employeeDataSource,
        allowColumnsDragging: true,
        columns: columns,
        onColumnDragging: (DataGridColumnDragDetails details) {
          if (details.action == DataGridColumnDragAction.dropped &&
              details.to != null) {
            final GridColumn rearrangeColumn = columns[details.from];
            columns.removeAt(details.from);
            columns.insert(details.to!, rearrangeColumn);
            employeeDataSource.buildDataGridRow();
            employeeDataSource.updateDtaGrid();
          }
          return true;
        },
      ),
    );
  }
}

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource({required this.employees, required this.columns}) {
    buildDataGridRow();
  }

  void buildDataGridRow() {
    dataGridRows = employees.map<DataGridRow>((employee) {
      Map<String, dynamic> employeeValues = {
        'id': employee.id,
        'name': employee.name,
        'designation': employee.designation,
        'salary': employee.salary,
      };
      return DataGridRow(
          cells: columns.map<DataGridCell>((column) {
        final columnName = column.columnName;
        final value = employeeValues[columnName];
        return DataGridCell(
          columnName: columnName,
          value: value,
        );
      }).toList());
    }).toList();
  }

  List<Employee> employees = [];

  List<GridColumn> columns = [];

  List<DataGridRow> dataGridRows = [];

  @override
  List<DataGridRow> get rows => dataGridRows;

  @override
  DataGridRowAdapter? buildRow(DataGridRow row) {
    return DataGridRowAdapter(
        cells: row.getCells().map((dataGridCell) {
      return Container(
          alignment: Alignment.center,
          padding: const EdgeInsets.symmetric(horizontal: 8.0),
          child: Text(
            dataGridCell.value.toString(),
          ));
    }).toList());
  }

  updateDtaGrid() {
    notifyListeners();
  }
}

{% endhighlight %}
{% endtabs %}


<img alt="Flutter datagrid shows a checkbox filter in web platform" src="images/column-drag-and-drop/column-drag-and-drop.gif" width="400"/>

>**NOTE**:  
To reorder the columns in the DataGrid, you should create an instance to hold the columns and then assign that instance to 
the SfDataGrid.columns property instead of directly assigning the list of GridColumn. This allows you to reorder the collection within the callback, maintaining the desired column order.
Additionally, it is important to build the rows based on the columns collection after reordering. This is necessary because
the column index may change after the columns have been rearranged. By rebuilding the rows based on the updated columns collection, you ensure that the row data aligns correctly with the reordered columns.

## onColumnDragging callback

The `SfDataGrid.onColumnDragging` callback is triggered when the column is dragging. This callback provides provides the following properties in the `DataGridColumnDragDetails`.

* `from`: Returns index of the currently dragging column.
* `to`: Returns index of the column after being dropped.
* `action`: Returns the column dragging details as the `DataGridColumnDragAction` enum.
* `offset`: Returns the current offset of the dragging column.

## Cancel the column dropping for a specific column

You can cancel the column dropping at a specific column by returning `false` from the `SfDataGrid.onColumnDragging` callback. This allows you to restrict the column dropping for a specific column.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: SfDataGrid(
        source: employeeDataSource,
        allowColumnsDragging: true,
        columns: columns,
        onColumnDragging: (DataGridColumnDragDetails details) {
         if (details.action == DataGridColumnDragAction.update &&
              details.to == 2) {
            return false;
          }
          if (details.action == DataGridColumnDragAction.dropped &&
              details.to != null) {
            final GridColumn rearrangeColumn = columns[details.from];
            columns.removeAt(details.from);
            columns.insert(details.to!, rearrangeColumn);
            employeeDataSource.buildDataGridRow();
            employeeDataSource.updateDtaGrid();
          }
          return true;
        },
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Changing the feedback widget

The DataGrid allows you to change the drag feedback widget by returning a custom widget from the `SfDataGrid.columnDragFeedbackBuilder` builder. This allows you to change the drag feedback widget according to your requirements.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: SfDataGrid(
        source: employeeDataSource,
        allowColumnsDragging: true,
        columns: columns,
        columnDragFeedbackBuilder: (context, column) {
          return Container(
            height: 50,
            width: column.actualWidth,
            color: Colors.grey,
            child: const Center(
              child: DefaultTextStyle(
                style: TextStyle(
                    fontSize: 14,
                    color: Colors.pink,
                    fontWeight: FontWeight.bold),
                child: Text('Drag View'),
              ),
            ),
          );
        },
        onColumnDragging: (DataGridColumnDragDetails details) {
         if (details.action == DataGridColumnDragAction.dropped &&
              details.to != null) {
            final GridColumn rearrangeColumn = columns[details.from];
            columns.removeAt(details.from);
            columns.insert(details.to!, rearrangeColumn);
            employeeDataSource.buildDataGridRow();
            employeeDataSource.updateDtaGrid();
          }
          return true;
        },
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

<img alt="Flutter datagrid shows a checkbox filter in web platform" src="images/column-drag-and-drop/feedback-widget.gif" width="400"/>

## Drag indicator customization

The DataGrid allows you to customize the drag indicator by changing its color and thickness. The DataGrid should be wrapped inside the `SfDataGridTheme`.

The `SfDataGridThemeData` and `SfDataGridTheme` classes are available in `syncfusion_flutter_core package`. So, import the following file.

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_core/theme.dart';

{% endhighlight %}
{% endtabs %}

### Change the drag indicator color

The color of drag indicator can be customized by using `SfDataGridThemeData.columnDragIndicatorColor` property. 

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: SfDataGridTheme(
        data: SfDataGridThemeData(columnDragIndicatorColor: Colors.pink),
        child: SfDataGrid(
          source: employeeDataSource,
          allowColumnsDragging: true,
          columns: columns,
          onColumnDragging: (DataGridColumnDragDetails details) {
            if (details.action == DataGridColumnDragAction.dropped &&
              details.to != null) {
            final GridColumn rearrangeColumn = columns[details.from];
            columns.removeAt(details.from);
            columns.insert(details.to!, rearrangeColumn);
            employeeDataSource.buildDataGridRow();
            employeeDataSource.updateDtaGrid();
          }
            return true;
          },
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

<img alt="Flutter datagrid shows a checkbox filter in web platform" src="images/column-drag-and-drop/drag-indicator-color.png" width="400"/>

### Change the drag indicator thickness

The thickness of drag indicator can be customized by using `SfDataGridThemeData.columnDragIndicatorStrokeWidth` property. 

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: SfDataGridTheme(
        data: SfDataGridThemeData(columnDragIndicatorStrokeWidth: 5),
        child: SfDataGrid(
          source: employeeDataSource,
          allowColumnsDragging: true,
          columns: columns,
          onColumnDragging: (DataGridColumnDragDetails details) {
            if (details.action == DataGridColumnDragAction.dropped &&
              details.to != null) {
            final GridColumn rearrangeColumn = columns[details.from];
            columns.removeAt(details.from);
            columns.insert(details.to!, rearrangeColumn);
            employeeDataSource.buildDataGridRow();
            employeeDataSource.updateDtaGrid();
          }
            return true;
          },
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}