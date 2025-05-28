---
layout: post
title: Selection in Flutter DataGrid | DataTable | Syncfusion
description: Learn here all about how to select a row or multiple rows in Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
---
# Selection in Flutter DataGrid (SfDataGrid)

This section explains how to enable selection in the Datagrid; modes, properties, and callbacks involved in selection and customizations available for selection.

The Datagrid allows you to select a specific row or group of rows either programmatically or by touch interactions. To enable selection, set the [selectionMode](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/selectionMode.html) property of the SfDataGrid to a value other than `none`. SfDataGrid has different selection modes to perform the selection operation as follows.

N> The [rows](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/rows.html) property must be initialized in the [source](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/source.html). The `rows` is the collection of `DataGridRow` to populate the rows in DataGrid.

## Selection modes 

<table>
<tr>
<th> Modes </th>
<th> Description </th>
</tr>
<tr>
<td> none </td>
<td> Disables selection and no rows can be selected. This is the default value.</td>
</tr>
<tr>
<td> single </td>
<td> Allows selection of a single row only. Upon selecting the next row, the selection in the previous row is cleared. </td>
</tr>
<tr>
<td> multiple </td>
<td> Allows selection of more than one row. Selection is not cleared when selecting more than one row. When you click on a selected row for the second time, the selection is cleared. </td>
</tr>
<tr>
<td> singleDeselect </td>
<td> Allows selection of only a single row. However, upon tapping the row again, the selection is cleared. Similar to single mode, upon selecting the next row, the selection in the previous row is cleared. </td>
</tr>
</table>

### Current cell navigation

Keyboard navigation through the cells and rows is determined based on the [navigationMode](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/navigationMode.html) property. The `GridNavigationMode.cell` allows you to navigate between the cells in a row and between the rows. The `GridNavigationMode.row` allows you to navigate between the rows.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SfDataGrid(
        source: _employeeDataSource,
        columns: [
          GridColumn(
              columnName: 'id',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'ID',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'name',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Name',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'designation',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Designation',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'salary',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'Salary',
                    overflow: TextOverflow.ellipsis,
                  ))),
        ],
        selectionMode: SelectionMode.single,
        navigationMode: GridNavigationMode.cell,
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows currentCell](images/selection/flutter-datagrid-currentcell.png)

### Single row selection

It allows you to select only one row. For example, you have selected a row. Now if you select some other row, the previous row selection will be cleared. Hence it is a `single` row selection mode.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: SfDataGrid(
            source: _employeeDataSource,
            columns: [
              GridColumn(
                  columnName: 'id',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.centerRight,
                      child: Text(
                        'ID',
                        overflow: TextOverflow.ellipsis,
                      ))),
              GridColumn(
                  columnName: 'name',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.centerLeft,
                      child: Text(
                        'Name',
                        overflow: TextOverflow.ellipsis,
                      ))),
              GridColumn(
                  columnName: 'designation',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.centerLeft,
                      child: Text(
                        'Designation',
                        overflow: TextOverflow.ellipsis,
                      ))),
              GridColumn(
                  columnName: 'salary',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.centerRight,
                      child: Text(
                        'Salary',
                        overflow: TextOverflow.ellipsis,
                      ))),
            ],
            selectionMode: SelectionMode.single));
  }

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows single row selection](images/selection/flutter-datagrid-single-selection.png)

### Multiple row selection

The SfDataGrid allows you to select multiple rows by setting the `selectionMode` property as `multiple,` where you can select multiple rows by clicking on SfDataGrid and also using the key modifiers.

While using `multiple`, you can select multiple rows by pressing the key modifiers <kbd>Shift</kbd> + <kbd>Down</kbd> and <kbd>Shift</kbd> + <kbd>Up</kbd>.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: SfDataGrid(
            source: _employeeDataSource,
            columns: [
              GridColumn(
                  columnName: 'id',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.centerRight,
                      child: Text(
                        'ID',
                        overflow: TextOverflow.ellipsis,
                      ))),
              GridColumn(
                  columnName: 'name',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.centerLeft,
                      child: Text(
                        'Name',
                        overflow: TextOverflow.ellipsis,
                      ))),
              GridColumn(
                  columnName: 'designation',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.centerLeft,
                      child: Text(
                        'Designation',
                        overflow: TextOverflow.ellipsis,
                      ))),
              GridColumn(
                  columnName: 'salary',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.centerRight,
                      child: Text(
                        'Salary',
                        overflow: TextOverflow.ellipsis,
                      ))),
            ],
            selectionMode: SelectionMode.multiple));
  }

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows multiple row selection](images/selection/flutter-datagrid-multiple-selection.png)

N>  When the `selectionMode` is `multiple`, multiple rows can be selected or deselected by clicking the respective rows. In multiple selections, pressing the navigation keys will move the current cell alone. The rows can be selected or deselected by pressing the <kbd>Space</kbd> key.

### Disable selection

The selection can be disabled by setting the `selectionMode` property as `none`.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: SfDataGrid(
            source: _employeeDataSource,
            columns: [
              GridColumn(
                  columnName: 'id',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.centerRight,
                      child: Text(
                        'ID',
                        overflow: TextOverflow.ellipsis,
                      ))),
              GridColumn(
                  columnName: 'name',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.centerLeft,
                      child: Text(
                        'Name',
                        overflow: TextOverflow.ellipsis,
                      ))),
              GridColumn(
                  columnName: 'designation',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.centerLeft,
                      child: Text(
                        'Designation',
                        overflow: TextOverflow.ellipsis,
                      ))),
              GridColumn(
                  columnName: 'salary',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.centerRight,
                      child: Text(
                        'Salary',
                        overflow: TextOverflow.ellipsis,
                      ))),
            ],
            selectionMode: SelectionMode.none));
  }

{% endhighlight %}
{% endtabs %}

Selection on a particular row can be disabled by handling the [onCurrentCellActivating](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/onCurrentCellActivating.html) callback.

 N> You cannot select the header row of SfDataGrid.

## Getting selected rows

Get the information of the selected rows by using the [controller](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/controller.html) property. Create an instance of the [DataGridController](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController-class.html) and set it to controller property. The [selectedRow](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/selectedRow.html) property returns the selected DataGridRow and the [selectedIndex](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/selectedIndex.html) property returns the index of the [selectedRow](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/selectedRow.html) in SfDataGrid. The [selectedRow](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/selectedRow.html) denotes the last selected row in multiple selections.

{% tabs %}
{% highlight Dart %}

  final DataGridController _dataGridController = DataGridController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: Column(children: [
      TextButton(
          child: Text('Get Selection Information'),
          onPressed: () {
            //SelectedIndex
            var _selectedIndex = _dataGridController.selectedIndex;

            //SelectedRow
            var _selectedRow = _dataGridController.selectedRow;

            //SelectedRows
            var _selectedRows = _dataGridController.selectedRows;

            print(_selectedIndex);
            print(_selectedRow);
            print(_selectedRows);
          }),
      Expanded(
          child: SfDataGrid(
              source: _employeeDataSource,
              columns: [
                GridColumn(
                    columnName: 'id',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerRight,
                        child: Text(
                          'ID',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'name',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerLeft,
                        child: Text(
                          'Name',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'designation',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerLeft,
                        child: Text(
                          'Designation',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'salary',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerRight,
                        child: Text(
                          'Salary',
                          overflow: TextOverflow.ellipsis,
                        ))),
              ],
              controller: _dataGridController,
              selectionMode: SelectionMode.multiple))
    ]));
  }

{% endhighlight %}
{% endtabs %}

N> DataGridController objects are expected to be long-lived, not re-created with each build.

## Programmatic selection

When `selectionMode` is set to a value other than `none`, the selected rows from the code by setting the `DataGridController.selectedIndex`, `DataGridController.selectedRow`, or `DataGridController.selectedRows` property based on the selection mode.  

When the selection mode is `single`, programmatically select a row in two ways either by setting the row index to the `DataGridController.selectedIndex` property, or by setting the `DataGridRow` to be selected to the `DataGridController.selectedRow` property

The following code example shows how to select a row using `selectedIndex`,

{% tabs %}
{% highlight Dart %}

  final DataGridController _dataGridController = DataGridController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: Column(children: [
      TextButton(
          child: Text('Set Selection'),
          onPressed: () {
            //SelectedIndex
            _dataGridController.selectedIndex = 4;
          }),
      Expanded(
          child: SfDataGrid(
              source: _employeeDataSource,
              columns: [
                GridColumn(
                    columnName: 'id',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerRight,
                        child: Text(
                          'ID',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'name',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerLeft,
                        child: Text(
                          'Name',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'designation',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerLeft,
                        child: Text(
                          'Designation',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'salary',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerRight,
                        child: Text(
                          'Salary',
                          overflow: TextOverflow.ellipsis,
                        ))),
              ],
              controller: _dataGridController,
              selectionMode: SelectionMode.single))
    ]));
  }

{% endhighlight %}
{% endtabs %}

The following code example shows how to select a row using `selectedRow`,

{% tabs %}
{% highlight Dart %}

  late EmployeeDataSource _employeeDataSource;
  final DataGridController _dataGridController = DataGridController();
  List<Employee> _employees = <Employee>[];

  @override
  void initState() {
    super.initState();
    _employees = getEmployeeData();
    _employeeDataSource = EmployeeDataSource(employees: _employees);
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: Column(children: [
      TextButton(
          child: Text('Set Selection'),
          onPressed: () {
            //SelectedRow
            _dataGridController.selectedRow = _employeeDataSource.dataGridRows[3];
          }),
      Expanded(
          child: SfDataGrid(
              source: _employeeDataSource,
              columns: [
                GridColumn(
                    columnName: 'id',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerRight,
                        child: Text(
                          'ID',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'name',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerLeft,
                        child: Text(
                          'Name',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'designation',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerLeft,
                        child: Text(
                          'Designation',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'salary',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerRight,
                        child: Text(
                          'Salary',
                          overflow: TextOverflow.ellipsis,
                        ))),
              ],
              controller: _dataGridController,
              selectionMode: SelectionMode.single))
    ]));
  }

{% endhighlight %}
{% endtabs %}

Multiple rows can be selected by adding a collection of `DataGridRow` to the `selectedRows` property.

{% tabs %}
{% highlight Dart %}

  late EmployeeDataSource _employeeDataSource;
  final DataGridController _dataGridController = DataGridController();
  List<Employee> _employees = <Employee>[];

  @override
  void initState() {
    super.initState();
    _employees = getEmployeeData();
    _employeeDataSource = EmployeeDataSource(employees: _employees);
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: Column(children: [
      TextButton(
          child: Text('Set Selection'),
          onPressed: () {
            //SelectedRows
            _dataGridController.selectedRows = [
              _employeeDataSource.dataGridRows[1],
              _employeeDataSource.dataGridRows[3],
              _employeeDataSource.dataGridRows[6],
            ];
          }),
      Expanded(
          child: SfDataGrid(
              source: _employeeDataSource,
              columns: [
                GridColumn(
                    columnName: 'id',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerRight,
                        child: Text(
                          'ID',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'name',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerLeft,
                        child: Text(
                          'Name',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'designation',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerLeft,
                        child: Text(
                          'Designation',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'salary',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerRight,
                        child: Text(
                          'Salary',
                          overflow: TextOverflow.ellipsis,
                        ))),
              ],
              controller: _dataGridController,
              selectionMode: SelectionMode.multiple))
    ]));
  }

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows multiple row selection](images/selection/flutter-datagrid-programmatic-multiple-selection.png)

### Get the current cell

The current cell information such as row index, and column index can be retrieved using the [currentCell](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/currentCell.html) property of `DataGridController.`

{% tabs %}
{% highlight Dart %}

  final DataGridController _dataGridController = DataGridController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: Column(children: [
      TextButton(
          child: Text('Get current cell'),
          onPressed: () {
            var _currentCell = _dataGridController.currentCell;
            print(_currentCell);
          }),
      Expanded(
          child: SfDataGrid(
              source: _employeeDataSource,
              columns: [
                GridColumn(
                    columnName: 'id',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerRight,
                        child: Text(
                          'ID',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'name',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerLeft,
                        child: Text(
                          'Name',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'designation',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerLeft,
                        child: Text(
                          'Designation',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'salary',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerRight,
                        child: Text(
                          'Salary',
                          overflow: TextOverflow.ellipsis,
                        ))),
              ],
              controller: _dataGridController,
              selectionMode: SelectionMode.single,
              navigationMode: GridNavigationMode.cell))
    ]));
  }

{% endhighlight %}
{% endtabs %}


### Process current cell

The CurrentCell can be moved to a particular cell by using the [moveCurrentCellTo](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/moveCurrentCellTo.html) method in `DataGridController`.

{% tabs %}
{% highlight Dart %}

  final DataGridController _dataGridController = DataGridController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: Column(children: [
      TextButton(
          child: Text('Move current cell'),
          onPressed: () {
            _dataGridController.moveCurrentCellTo(RowColumnIndex(6, 3));
          }),
      Expanded(
          child: SfDataGrid(
              source: _employeeDataSource,
              columns: [
                GridColumn(
                    columnName: 'id',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerRight,
                        child: Text(
                          'ID',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'name',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerLeft,
                        child: Text(
                          'Name',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'designation',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerLeft,
                        child: Text(
                          'Designation',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'salary',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerRight,
                        child: Text(
                          'Salary',
                          overflow: TextOverflow.ellipsis,
                        ))),
              ],
              controller: _dataGridController,
              selectionMode: SelectionMode.single,
              navigationMode: GridNavigationMode.cell))
    ]));
  }

{% endhighlight %}
{% endtabs %}

### Clear selection

DataGrid allows you to clear the selection applied in the grid rows by setting the `DataGridController.selectedIndex` to `-1` or `DataGridController.selectedRow` to null when the `selectionMode` property is in `single` or `singleDeselect.` When the selectionMode property is in `multiple,` clear the selection from grid rows by setting the `DataGridController.selectedRows` to `empty.`

The following code example shows how to clear selection when the `selectionMode` property is in `single` or `singleDeselect.`

{% tabs %}
{% highlight Dart %}

  final DataGridController _dataGridController = DataGridController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: Column(children: [
      TextButton(
          child: Text('Clear Selection'),
          onPressed: () {
            _dataGridController.selectedIndex = -1;
            //or
            //this._dataGridController.selectedRow = null;
          }),
      Expanded(
          child: SfDataGrid(
              source: _employeeDataSource,
              columns: [
                GridColumn(
                    columnName: 'id',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerRight,
                        child: Text(
                          'ID',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'name',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerLeft,
                        child: Text(
                          'Name',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'designation',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerLeft,
                        child: Text(
                          'Designation',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'salary',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerRight,
                        child: Text(
                          'Salary',
                          overflow: TextOverflow.ellipsis,
                        ))),
              ],
              controller: _dataGridController,
              selectionMode: SelectionMode.single))
    ]));
  }

{% endhighlight %}
{% endtabs %}

The following code example shows how to clear selection when the `selectionMode` property is in `multiple.`

{% tabs %}
{% highlight Dart %}

  final DataGridController _dataGridController = DataGridController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: Column(children: [
      TextButton(
          child: Text('Clear Selection'),
          onPressed: () {
            _dataGridController.selectedRows = [];
          }),
      Expanded(
          child: SfDataGrid(
              source: _employeeDataSource,
              columns: [
                GridColumn(
                    columnName: 'id',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerRight,
                        child: Text(
                          'ID',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'name',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerLeft,
                        child: Text(
                          'Name',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'designation',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerLeft,
                        child: Text(
                          'Designation',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'salary',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerRight,
                        child: Text(
                          'Salary',
                          overflow: TextOverflow.ellipsis,
                        ))),
              ],
              controller: _dataGridController,
              selectionMode: SelectionMode.multiple))
    ]));
  }

{% endhighlight %}
{% endtabs %}

N> Selected rows and selections will be cleared whenever the `dataSource` is changed at runtime.

## Keyboard behavior

<table>
<tr>
<th>
Key or KeyCombinations
</th>
<th>
Description
</th>
</tr>
<tr>
<td>
<kbd>DownArrow</kbd>
</td>
<td>
Moves CurrentCell directly under the active current cell. If the CurrentCell is in the last row, pressing <kbd>DownArrow</kbd> does nothing.
</td>
</tr>
<tr>
<td>
<kbd>UpArrow</kbd>
</td>
<td>
Moves the CurrentCell directly above the active current cell. If the CurrentCell is in the first row, pressing <kbd>UpArrow</kbd> does nothing.
</td>
</tr>
<tr>
<td>
<kbd>LeftArrow</kbd>
</td>
<td>
Moves the current cell to the previous to the active current cell. If the CurrentCell is in the first cell, pressing <kbd>LeftArrow</kbd> does nothing. If the focused row is a group header, the group will be collapsed when it is in an expanded state.
</td>
</tr>
<tr>
<td>
<kbd>RightArrow</kbd>
</td>
<td>
Moves the current cell to next to the active current cell. If the CurrentCell is in the last cell, pressing <kbd>RightArrow</kbd> does nothing. If the focused row is a group header, the group will expand when it is in a collapsed state.
</td>
</tr>
<tr>
<td>
<kbd>Home</kbd> / <kbd> Ctrl</kbd> + <kbd>LeftArrow</kbd>
</td>
<td>
Moves the current cell to the first cell of the current row.
</td>
</tr>
<tr>
<td>
<kbd>End</kbd> / <kbd>Ctrl</kbd> + <kbd>RightArrow</kbd>
</td>
<td>
Moves the current cell to the last cell of the current row.
</td>
</tr>
<tr>
<td>
<kbd>PageDown</kbd>
</td>
<td>
The SfDataGrid will be scrolled to the next set of rows that are not displayed in the view, including the row that is partially displayed and the current cell is set to the last row.
</td>
</tr>
<tr>
<td>
<kbd>PageUp</kbd>
</td>
<td>
The SfDataGrid will be scrolled to the previous set of rows that are not displayed in the view, including the row that is partially displayed and the current cell is set to the first row.
</td>
</tr>
<tr>
<td>
<kbd>Tab</kbd>
</td>
<td>
Moves the current cell to next to the active current cell. If the active current cell is the last cell of the current row, the focus will move to the first cell of the row next to the current row. If the active current cell is the last cell of the last row, the focus will be moved to the next widget in the tab order of the parent container.
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>Tab</kbd>
</td>
<td>
Moves the current cell to the previous to the active current cell. If the active current cell is the first cell of the current row, the current cell will move to the last cell of the row previous to the current row. If the active current cell is the first cell of the first row, the focus will be moved to the previous widget in the tab order of the parent container.
</td>
</tr>
<tr>
<td>
<kbd>Ctrl</kbd> + <kbd>DownArrow</kbd>
</td>
<td>
Moves the current cell to the current column of the last row.
</td>
</tr>
<tr>
<td>
<kbd>Ctrl</kbd> + <kbd>UpArrow</kbd>
</td>
<td>
Moves the current cell to the current column of the first row.
</td>
</tr>
<tr>
<td>
<kbd>Ctrl</kbd> + <kbd>Home</kbd>
</td>
<td>
Moves the current cell to the first cell of the first row.
</td>
</tr>
<tr>
<td>
<kbd>Ctrl</kbd> + <kbd>End</kbd>
</td>
<td>
Moves the current cell to the last cell of the last row.
</td>
</tr>
<tr>
<td>
<kbd>Enter</kbd>
</td>
<td>
 The current cell will be moved to the next focused row of the same column.
</td>
</tr>
<tr>
<td>
<kbd>Ctrl</kbd> + <kbd>A</kbd>
</td>
<td>
All rows or cells will be selected.
</td>
</tr>
<tr>
<td>
<kbd>F2</kbd> 
</td>
<td>
If the <a href= "https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/allowEditing.html">DataGrid.AllowEditing </a> property is true and the <a href= "https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridColumn/allowEditing.html">GridColumn.AllowEditing </a> property is true for the current column, the current cell enters into edit mode.
</td>
</tr>
<tr>
<td>
<kbd>Esc</kbd>
</td>
<td>
If the current cell is in edit mode, call the <a href= "https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/onCellCancelEdit.html">DataGridSource.onCellCancelEdit </a> method to revert the current changes and ends the editing.
</td>
</tr>
</table>

## Callbacks

The Datagrid provides the following callbacks for selection:

 * `onSelectionChanging` : This callback is raised while selecting a row at the execution time before the row is selected. So, it allows canceling the selection action by returning `false`.
 * `onSelectionChanged` : This callback is raised after the row is selected.

The followings are the parameters of the [onSelectionChanging](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/onSelectionChanging.html) and [onSelectionChanged](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/onSelectionChanged.html) callbacks,

 * newItems: Gets a collection of the `DataGridRow` added for the selection.
 * oldItems: Gets a collection of the `DataGridRow` removed from the selection.

The following example shows how to cancel the selection when selecting a row that contains the designation of the Manager.

{% tabs %}
{% highlight Dart %}

  late EmployeeDataSource _employeeDataSource;
  List<Employee> _employees = <Employee>[];

  @override
  void initState() {
    super.initState();
    _employees = getEmployeeData();
    _employeeDataSource = EmployeeDataSource(employees: _employees);
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: SfDataGrid(
      source: _employeeDataSource,
      columns: [
        GridColumn(
            columnName: 'id',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'ID',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'name',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Name',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'designation',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Designation',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'salary',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'Salary',
                  overflow: TextOverflow.ellipsis,
                ))),
      ],
      selectionMode: SelectionMode.single,
      onSelectionChanging:
          (List<DataGridRow> addedRows, List<DataGridRow> removedRows) {
        final index = _employeeDataSource.dataGridRows.indexOf(addedRows.last);
        Employee employee = _employees[index];
        if (employee.designation == 'Manager') {
          return false;
        }

        return true;
      },
      onSelectionChanged:
          (List<DataGridRow> addedRows, List<DataGridRow> removedRows) {
        // apply your logic
      },
    ));
  }

{% endhighlight %}
{% endtabs %}

* `onCurrentCellActivating`: This callback is raised before the current cell applies to the corresponding grid cell of the selecting row. So, it allows canceling the selection action by returning  `false.` If the return is false, the selection will not apply, and also, `onSelectionChanging`, `onSelectionChanged` and `onCurrentCellActivated` are not called.
 * `onCurrentCellActivated`: This callback is raised after the current cell is applied in the grid cell on the selecting row.

 The followings are the parameters of the [onCurrentCellActivating](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/onCurrentCellActivating.html) and [onCurrentCellActivated](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/onCurrentCellActivated.html) callbacks,

 * newRowColumnIndex: Gets the current RowColumnIndex of the current cell.
 * oldRowColumnIndex: Gets the previous RowColumnIndex of the current cell.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: SfDataGrid(
      source: _employeeDataSource,
      columns: [
        GridColumn(
            columnName: 'id',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'ID',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'name',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Name',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'designation',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Designation',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'salary',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'Salary',
                  overflow: TextOverflow.ellipsis,
                ))),
      ],
      selectionMode: SelectionMode.single,
      navigationMode: GridNavigationMode.cell,
      onCurrentCellActivating: (RowColumnIndex currentRowColumnIndex,
          RowColumnIndex previousRowColumnIndex) {
        if (currentRowColumnIndex.rowIndex == 2 &&
            currentRowColumnIndex.columnIndex == 3) {
          return false;
        }

        return true;
      },
      onCurrentCellActivated: (RowColumnIndex currentRowColumnIndex,
          RowColumnIndex previousRowColumnIndex) {
        // apply your logic
      },
    ));
  }

{% endhighlight %}
{% endtabs %}

## Cell Tap callbacks

The Datagrid provides the following callbacks to handle interactions with the cells.

* [onCellTap](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/onCellTap.html) : Called when a tap with a cell has occurred.
* [onCellDoubleTap](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/onCellDoubleTap.html) : Called when user is tapped a cell with a primary button at the same cell twice in quick succession.
* [onCellLongPress](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/onCellLongPress.html) : Called when a long press gesture with a primary button has been recognized for a cell. 
* [onCellSecondaryTap](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/onCellSecondaryTap.html) : Called when a tap with a cell has occurred with a secondary button.

{% tabs %}
{% highlight Dart %}

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: SfDataGrid(
            source: _employeeDataSource,
            columns: [
              GridColumn(
                  columnName: 'id',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.centerRight,
                      child: Text(
                        'ID',
                        overflow: TextOverflow.ellipsis,
                      ))),
              GridColumn(
                  columnName: 'name',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.centerLeft,
                      child: Text(
                        'Name',
                        overflow: TextOverflow.ellipsis,
                      ))),
              GridColumn(
                  columnName: 'designation',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.centerLeft,
                      child: Text(
                        'Designation',
                        overflow: TextOverflow.ellipsis,
                      ))),
              GridColumn(
                  columnName: 'salary',
                  label: Container(
                      padding: EdgeInsets.symmetric(horizontal: 16.0),
                      alignment: Alignment.centerRight,
                      child: Text(
                        'Salary',
                        overflow: TextOverflow.ellipsis,
                      ))),
            ],
            onCellTap: (DataGridCellTapDetails details) {
              print(details);
            },
            onCellDoubleTap: (DataGridCellDoubleTapDetails details) {
              print(details);
            },
            onCellLongPress: (DataGridCellLongPressDetails details) {
              print(details);
            },
            onCellSecondaryTap: (DataGridCellTapDetails details) {
              print(details);
            }));
  }

{% endhighlight %}
{% endtabs %}

## Customizing selection behavior

To perform custom actions apart from the functionalities mentioned in the above tables for key press actions of the keyboard, implement your custom actions in the [handleKeyEvent()](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/RowSelectionManager/handleKeyEvent.html) override of the custom written selection manager class derived from [RowSelectionManager](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/RowSelectionManager-class.html) and assign it to the [SfDataGrid.selectionManager](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/selectionManager.html) property.

{% tabs %}
{% highlight Dart %}

  final CustomSelectionManager _customSelectionManager = CustomSelectionManager();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: SfDataGrid(
      source: _employeeDataSource,
      columns: [
        GridColumn(
            columnName: 'id',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'ID',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'name',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Name',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'designation',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Designation',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'salary',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'Salary',
                  overflow: TextOverflow.ellipsis,
                ))),
      ],
      selectionMode: SelectionMode.multiple,
      selectionManager: _customSelectionManager,
    ));
  }

class CustomSelectionManager extends RowSelectionManager {
  @override
  void handleKeyEvent(KeyEvent keyEvent) {
    if (keyEvent.logicalKey == LogicalKeyboardKey.keyA) {
      if (HardwareKeyboard.instance.isControlPressed) {
        //apply your logic
        return;
      }
    }

    super.handleKeyEvent(keyEvent);
  }
}

{% endhighlight %}
{% endtabs %}   

## Change Enter key behavior

When pressing the <kbd>Enter</kbd> key, the current cell will be moved to the next focused row of the same column, by default. The following code shows how to change the <kbd>Enter</kbd> key behavior by overriding the `handleKeyEvent()` method in `RowSelectionManager`.

{% tabs %}
{% highlight Dart %}

  final CustomSelectionManager _customSelectionManager = CustomSelectionManager();

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
        home: Scaffold(
            body: SfDataGrid(
      source: _employeeDataSource,
      columns: [
        GridColumn(
            columnName: 'id',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'ID',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'name',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Name',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'designation',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerLeft,
                child: Text(
                  'Designation',
                  overflow: TextOverflow.ellipsis,
                ))),
        GridColumn(
            columnName: 'salary',
            label: Container(
                padding: EdgeInsets.symmetric(horizontal: 16.0),
                alignment: Alignment.centerRight,
                child: Text(
                  'Salary',
                  overflow: TextOverflow.ellipsis,
                ))),
      ],
      selectionMode: SelectionMode.multiple,
      navigationMode: GridNavigationMode.cell,
      selectionManager: _customSelectionManager,
    )));
  }

class CustomSelectionManager extends RowSelectionManager {
  @override
  void handleKeyEvent(KeyEvent keyEvent) {
    if (keyEvent.logicalKey == LogicalKeyboardKey.enter) {
      //apply your logic
      return;
    }

    super.handleKeyEvent(keyEvent);
  }
}

{% endhighlight %}
{% endtabs %}   

## Appearance
 
The SfDataGrid allows customizing the appearance of the selected rows and current cell through the [SfDataGridTheme.SfDataGridThemeData](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData-class.html) property.

All the styles such as [selectionColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/selectionColor.html), and [DataGridCurrentCellStyle](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/DataGridCurrentCellStyle-class.html) related to `SfDataGrid` are available in the [syncfusion_flutter_core](https://pub.dev/packages/syncfusion_flutter_core) package. To access those classes, import the following file in your application.

{% tabs %}
{% highlight Dart %} 

import 'package:syncfusion_flutter_core/theme.dart';

{% endhighlight %}
{% endtabs %}

### Selection
The selection background can be changed by the `selectionColor` property of the `SfDataGridThemeData` in [SfDataGridTheme](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridTheme-class.html).

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_datagrid/datagrid.dart';
import 'package:syncfusion_flutter_core/theme.dart';

  final DataGridController _dataGridController = DataGridController();

  late EmployeeDataSource _employeeDataSource;

  @override
  void initState() {
      super.initState();
      _employeeDataSource = EmployeeDataSource(_dataGridController);
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: SfDataGridTheme(
            data: SfDataGridThemeData(selectionColor: Colors.red),
            child: SfDataGrid(
              source: _employeeDataSource,
              columns: [
                GridColumn(
                    columnName: 'id',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerRight,
                        child: Text(
                          'ID',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'name',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerLeft,
                        child: Text(
                          'Name',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'designation',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerLeft,
                        child: Text(
                          'Designation',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'salary',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerRight,
                        child: Text(
                          'Salary',
                          overflow: TextOverflow.ellipsis,
                        ))),
              ],
              selectionMode: SelectionMode.multiple,
            )));
  }

class EmployeeDataSource extends DataGridSource {
  EmployeeDataSource(this.dataGridController) {
    dataGridRows = _employees
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

  final DataGridController dataGridController;

  List<DataGridRow> dataGridRows = [];

  @override
  List<DataGridRow> get rows => dataGridRows;

  @override
  DataGridRowAdapter? buildRow(DataGridRow row) {
    TextStyle? getSelectionTextStyle() {
      return dataGridController.selectedRows.contains(row)
          ? TextStyle(
              fontFamily: 'Raleway',
              fontWeight: FontWeight.w300,
              color: Colors.white,
            )
          : null;
    }

    return DataGridRowAdapter(
        cells: row.getCells().map<Widget>((dataGridCell) {
      return Container(
        color: Colors.transparent,
        alignment: (dataGridCell.columnName == 'id' ||
                dataGridCell.columnName == 'salary')
            ? Alignment.centerRight
            : Alignment.centerLeft,
        padding: EdgeInsets.symmetric(horizontal: 16.0),
        child: Text(
          dataGridCell.value.toString(),
          overflow: TextOverflow.ellipsis,
          style: getSelectionTextStyle(),
        ),
      );
    }).toList());
  }
}

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows customized multiple selection](images/selection/flutter-datagrid-customized-multiple-selection.png)

### Current cell

The current cell border's color and thickness can be changed by the [currentCellStyle](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/currentCellStyle.html) property of `SfDataGridThemeData` in `SfDataGridTheme.`

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_datagrid/datagrid.dart';
import 'package:syncfusion_flutter_core/theme.dart';

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: SfDataGridTheme(
            data: SfDataGridThemeData(
                currentCellStyle: DataGridCurrentCellStyle(
                    borderWidth: 2, borderColor: Colors.pinkAccent)),
            child: SfDataGrid(
              source: _employeeDataSource,
              columns: [
                GridColumn(
                    columnName: 'id',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerRight,
                        child: Text(
                          'ID',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'name',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerLeft,
                        child: Text(
                          'Name',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'designation',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerLeft,
                        child: Text(
                          'Designation',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'salary',
                    label: Container(
                        padding: EdgeInsets.symmetric(horizontal: 16.0),
                        alignment: Alignment.centerRight,
                        child: Text(
                          'Salary',
                          overflow: TextOverflow.ellipsis,
                        ))),
              ],
              selectionMode: SelectionMode.multiple,
              navigationMode: GridNavigationMode.cell,
            )));
  }

{% endhighlight %}
{% endtabs %}

![flutter datagrid shows customized current cell](images/selection/flutter-datagrid-customized-currentcell.png)

>**NOTE**
 You can change the current row border's color by the `currentCellStyle` property of `SfDataGridThemeData` in `SfDataGridTheme`. The current row border is shown when navigationMode is row to navigate between rows.  
