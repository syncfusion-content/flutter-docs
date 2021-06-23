---
layout: post
title: Editing in Flutter DataGrid | DataTable | Syncfusion
description: Learn here all about how to perform editing in Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Editing in Flutter DataGrid

`SfDataGrid` supports to editing the cell values by setting the `SfDataGrid.allowEditing` property, `SfDataGrid.navigationMode` as Cell and setting the `SfDataGrid.selectionMode` as any other than None.

To enable editing, follow the code example:

{% tabs %}
{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDataGrid(
      source: _employeeDataSource,
      allowEditing: true,
      selectionMode: SelectionMode.single,
      navigationMode: GridNavigationMode.cell,
      columns: [
        GridColumn(
          columnName: 'id',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              'ID',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridColumn(
          columnName: 'name',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerLeft,
            child: Text(
              'Name',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridColumn(
          columnName: 'designation',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerLeft,
            child: Text(
              'Designation',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridColumn(
          columnName: 'salary',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              'Salary',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

### buildEditWidget

The `DataGridSource.buildEditWidget` must to override in `DataGridSource` and it will call every time to obtain the editable widget when cell enter into edit mode. If return `null` cell will not enter into edit mode. The `DataGridRow`, `RowColumnIndex`, `GridColumn` and `CellSubmit` has the following members which provides information for `DataGridSource.buildEditWidget` callback.

* `DataGridRow`: Gets the DataGridRow of the SfDataGrid.
* `RowColumnIndex`: Gets the current row and column index of the DataGrid.
* `Column`: Gets the Grid Column of the SfDataGrid.
* `CellSubmit`: Programmatically call to end editing.

>N In Mobile platforms must to call the `CellSubmit` inside the respective callback of editable widget, i.e `TextField.onSubmitted` and `DropDownWidget.onChanged`. After calling the `CellSubmit`, from it `canSubmitCell` and `onCellSubmit` will call.

>N In desktop platform, we will call the `canSubmitCell` and `onCellSubmit` on key navigation itself and no need to call the  `CellSubmit` callback inside editable widget.

{% tabs %}
{% highlight dart %} 

class EmployeeDataSource extends DataGridSource {
  /// Helps to hold the new value of all editable widget.
  /// Based on the new value we will commit the new value into the corresponding
  /// DataGridCell on onCellSubmit method.
  dynamic newCellValue;

  /// Help to control the editable text in [TextField] widget.
  TextEditingController editingController = TextEditingController();

  @override
  Widget? buildEditWidget(DataGridRow dataGridRow,
      RowColumnIndex rowColumnIndex, GridColumn column, CellSubmit submitCell) {
    // Text going to display on editable widget
    final String displayText = dataGridRow
            .getCells()
            .firstWhereOrNull((DataGridCell dataGridCell) =>
                dataGridCell.columnName == column.columnName)
            ?.value
            ?.toString() ??
        '';

    // The new cell value must be reset.
    // To avoid committing the [DataGridCell] value that was previously edited
    // into the current non-modified [DataGridCell].
    newCellValue = null;    

    final bool isTextAlignRight =
        column.columnName == 'id' || column.columnName == 'salary';

    final bool isNumericKeyBoardType =
        column.columnName == 'id' || column.columnName == 'salary';

    return Container(
      padding: const EdgeInsets.all(8.0),
      alignment:
          isTextAlignRight ? Alignment.centerRight : Alignment.centerLeft,
      child: TextField(
        autofocus: true,
        controller: editingController..text = displayText,
        textAlign: isTextAlignRight ? TextAlign.right : TextAlign.left,
        decoration: InputDecoration(
            contentPadding: const EdgeInsets.fromLTRB(0, 0, 0, 16.0),
            focusedBorder: UnderlineInputBorder(
                borderSide: BorderSide(color: Colors.black))),
        keyboardType:
            isNumericKeyBoardType ? TextInputType.number : TextInputType.text,
        onChanged: (String value) {
          if (value.isNotEmpty) {
            if (isNumericKeyBoardType) {
              newCellValue = int.parse(value);
            } else {
              newCellValue = value;
            }
          } else {
            newCellValue = null;
          }
        },
        onSubmitted: (String value) {
          /// In Mobile Platform.
          /// Call [CellSubmit] callback to fire the canSubmitCell and
          /// onCellSubmit to commit the new value in single place.
          submitCell();
        },
      ),
    );
  }
}

{% endhighlight %}
{% endtabs %}

>N `DataGridSource.onCellSubmit` will call when the `DataGridSource.canSubmitCell` return true.

### Column Editing

To enable or disable editing for a particular column, set the `GridColumn.allowEditing` property.

The following code example shows how to disable the editing for first column.

{% tabs %}
{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDataGrid(
      source: _employeeDataSource,
      allowEditing: true,
      selectionMode: SelectionMode.single,
      navigationMode: GridNavigationMode.cell,
      columns: [
        GridColumn(
          columnName: 'id',
          allowEditing: false,
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              'ID',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridColumn(
          columnName: 'name',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerLeft,
            child: Text(
              'Name',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridColumn(
          columnName: 'designation',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerLeft,
            child: Text(
              'Designation',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridColumn(
          columnName: 'salary',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              'Salary',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Entering edit mode

To enter into edit mode by just tapping or double tapping the grid cells, set the `SfDataGrid.editingGestureType` property.

The following code example shows how to enter into edit mode on tap.

{% tabs %}
{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDataGrid(
      source: _employeeDataSource,
      allowEditing: true,
      selectionMode: SelectionMode.single,
      navigationMode: GridNavigationMode.cell,
      editingGestureType: EditingGestureType.tap,
      columns: [
        GridColumn(
          columnName: 'id',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              'ID',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridColumn(
          columnName: 'name',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerLeft,
            child: Text(
              'Name',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridColumn(
          columnName: 'designation',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerLeft,
            child: Text(
              'Designation',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridColumn(
          columnName: 'salary',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              'Salary',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

The following code example shows how to enter into edit mode on double tap.

{% tabs %}
{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDataGrid(
      source: _employeeDataSource,
      allowEditing: true,
      selectionMode: SelectionMode.single,
      navigationMode: GridNavigationMode.cell,
      editingGestureType: EditingGestureType.doubleTap,
      columns: [
        GridColumn(
          columnName: 'id',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              'ID',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridColumn(
          columnName: 'name',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerLeft,
            child: Text(
              'Name',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridColumn(
          columnName: 'designation',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerLeft,
            child: Text(
              'Designation',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
        GridColumn(
          columnName: 'salary',
          label: Container(
            padding: EdgeInsets.symmetric(horizontal: 16.0),
            alignment: Alignment.centerRight,
            child: Text(
              'Salary',
              overflow: TextOverflow.ellipsis,
            ),
          ),
        ),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Callbacks

### onCellBeginEdit

The `DataGridSource.onCellBeginEdit` callback occurs when the `CurrentCell` enters into edit mode. If does not want to enter into edit mode, you can return `false`. Otherwise return `true`. The `DataGridRow`, `RowColumnIndex` and `GridColumn` has the following members which provides information for `DataGridSource.onCellBeginEdit` callback.

* `DataGridRow`: Gets the DataGridRow of the SfDataGrid.
* `RowColumnIndex`: Gets the current row and column index of the DataGrid.
* `Column`: Gets the Grid Column of the SfDataGrid.

{% tabs %}
{% highlight dart %} 

class EmployeeDataSource extends DataGridSource {
  @override
  bool onCellBeginEdit(DataGridRow dataGridRow, RowColumnIndex rowColumnIndex,
      GridColumn column) {

    /// Return false, to restrict entering into the editing.    
    return true;
  }
}

{% endhighlight %}
{% endtabs %}

### canSubmitCell

The `DataGridSource.canSubmitCell` occurs before cell’s editing is completed. If you want to restrict the cell from being end its editing, you can return false. Otherwise, return true. `onCellSubmit` will be called only if the `canSubmitCell` returns true.The `DataGridRow`, `RowColumnIndex` and `GridColumn` has the following members which provides information for `DataGridSource.canSubmitCell` callback.

* `DataGridRow`: Gets the DataGridRow of the SfDataGrid.
* `RowColumnIndex`: Gets the current row and column index of the DataGrid.
* `Column`: Gets the Grid Column of the SfDataGrid.

{% tabs %}
{% highlight dart %} 

class EmployeeDataSource extends DataGridSource {
  @override
  bool canSubmitCell(DataGridRow dataGridRow, RowColumnIndex rowColumnIndex,
      GridColumn column) {
    /// Return false, to retain in edit mode.
    return true; // or super.canSubmitCell(dataGridRow, rowColumnIndex, column);
  }
}

{% endhighlight %}
{% endtabs %}

### onCellSubmit

The `DataGridSource.onCellSubmit` callback will call when `DataGridSource.canSubmitCell` return true and it's common place to committing the edited cell value into the repective collection and `SfDataGrid.DataGridCell`. The `DataGridRow`, `RowColumnIndex` and `GridColumn` has the following members which provides information for `DataGridSource.onCellSubmit` callback.

>N No need to call the notifyListener inside it.

{% tabs %}
{% highlight dart %}

class EmployeeDataSource extends DataGridSource {
  
  @override
  void onCellSubmit(DataGridRow dataGridRow, RowColumnIndex rowColumnIndex,
      GridColumn column) {
    final dynamic oldValue = dataGridRow
            .getCells()
            .firstWhereOrNull((DataGridCell dataGridCell) =>
                dataGridCell.columnName == column.columnName)
            ?.value ??
        '';

    final int dataRowIndex = dataGridRows.indexOf(dataGridRow);

    if (newCellValue == null || oldValue == newCellValue) {
      return;
    }

    if (column.columnName == 'id') {
      dataGridRows[dataRowIndex].getCells()[rowColumnIndex.columnIndex] =
          DataGridCell<int>(columnName: 'id', value: newCellValue);
      _employees[dataRowIndex].id = newCellValue as int;
    } else if (column.columnName == 'name') {
      dataGridRows[dataRowIndex].getCells()[rowColumnIndex.columnIndex] =
          DataGridCell<String>(columnName: 'name', value: newCellValue);
      _employees[dataRowIndex].name = newCellValue.toString();
    } else if (column.columnName == 'designation') {
      dataGridRows[dataRowIndex].getCells()[rowColumnIndex.columnIndex] =
          DataGridCell<String>(columnName: 'designation', value: newCellValue);
      _employees[dataRowIndex].designation = newCellValue.toString();
    } else {
      dataGridRows[dataRowIndex].getCells()[rowColumnIndex.columnIndex] =
          DataGridCell<int>(columnName: 'salary', value: newCellValue);
      _employees[dataRowIndex].salary = newCellValue as int;
    }
  }
}

{% endhighlight %}
{% endtabs %}

### onCellCancelEdit

The `DataGridSource.onCellCancelEdit` callback will call when press the `Escape` key. The `canSubmitCell` and `onCellSubmit` will not call when `Escape` key is pressed.

>N No need to call the notifyListener inside it.

{% tabs %}
{% highlight dart %} 

class EmployeeDataSource extends DataGridSource {
  @override
  void onCellCancelEdit(DataGridRow dataGridRow, RowColumnIndex rowColumnIndex, GridColumn column) {
    // handle the cancel editing code here
  }
}

{% endhighlight %}
{% endtabs %}

## Programmatic editing

### BeginEdit

The SfDataGrid allows to edit the cell programmatically by calling the `SfDataGrid.beginEdit` method. By calling this method, the particular cell enters into edit mode. It edits the data manually or programmatically. To edit a cell programmatically, follow the code example:

{% tabs %}
{% highlight dart %} 

final DataGridController _dataGridController = DataGridController();

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Column(
      children: [
        TextButton(
          child: Text("Begin Edit"),
          onPressed: () {
            _dataGridController.beginEdit(RowColumnIndex(2, 3));
          },
        ),
        Expanded(
          child: SfDataGrid(
            source: _employeeDataSource,
            allowEditing: true,
            selectionMode: SelectionMode.single,
            navigationMode: GridNavigationMode.cell,
            controller: _dataGridController,
            columns: [
              GridColumn(
                columnName: 'id',
                label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'ID',
                    overflow: TextOverflow.ellipsis,
                  ),
                ),
              ),
              GridColumn(
                columnName: 'name',
                label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Name',
                    overflow: TextOverflow.ellipsis,
                  ),
                ),
              ),
              GridColumn(
                columnName: 'designation',
                label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Designation',
                    overflow: TextOverflow.ellipsis,
                  ),
                ),
              ),
              GridColumn(
                columnName: 'salary',
                label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'Salary',
                    overflow: TextOverflow.ellipsis,
                  ),
                ),
              ),
            ],
          ),
        ),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

### EndEdit

The `SfDataGrid.endEdit` method can be called to programmatically end editing. To end the editing programmatically, follow the code example:

{% tabs %}
{% highlight dart %} 

final DataGridController _dataGridController = DataGridController();

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: Column(
      children: [
        TextButton(
          child: Text("End Edit"),
          onPressed: () {
            _dataGridController.endEdit();
          },
        ),
        Expanded(
          child: SfDataGrid(
            source: _employeeDataSource,
            allowEditing: true,
            selectionMode: SelectionMode.single,
            navigationMode: GridNavigationMode.cell,
            controller: _dataGridController,
            columns: [
              GridColumn(
                columnName: 'id',
                label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'ID',
                    overflow: TextOverflow.ellipsis,
                  ),
                ),
              ),
              GridColumn(
                columnName: 'name',
                label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Name',
                    overflow: TextOverflow.ellipsis,
                  ),
                ),
              ),
              GridColumn(
                columnName: 'designation',
                label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Designation',
                    overflow: TextOverflow.ellipsis,
                  ),
                ),
              ),
              GridColumn(
                columnName: 'salary',
                label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'Salary',
                    overflow: TextOverflow.ellipsis,
                  ),
                ),
              ),
            ],
          ),
        ),
      ],
    ),
  );
}

{% endhighlight %}
{% endtabs %}

## Cancel the editing for specific cell or column at run time

The following code example shows how to cancel the editing for specific cell.

{% tabs %}
{% highlight dart %} 

class EmployeeDataSource extends DataGridSource {
  @override
  bool onCellBeginEdit(DataGridRow dataGridRow, RowColumnIndex rowColumnIndex,
      GridColumn column) {

    // Editing prevented for the cell at RowColumnIndex(2,2).    
    if (rowColumnIndex.equals(RowColumnIndex(2, 2))) {
      return false;
    } else {
      return false;
    }
  }
}

{% endhighlight %}
{% endtabs %}


The following code example shows how to cancel the editing for specific column.

{% tabs %}
{% highlight dart %} 

class EmployeeDataSource extends DataGridSource {
  @override
  bool onCellBeginEdit(DataGridRow dataGridRow, RowColumnIndex rowColumnIndex,
      GridColumn column) {
    if (column.columnName == 'id' || column.columnName == 'salary') {
      return false;
    } else {
      return true;
    }
  }
}

{% endhighlight %}
{% endtabs %}

## Cancel edited cell value from being committed

The following code example shows how to cancel the committing of cell value.

{% tabs %}
{% highlight dart %} 

class EmployeeDataSource extends DataGridSource {
  @override
  bool canSubmitCell(DataGridRow dataGridRow, RowColumnIndex rowColumnIndex,
      GridColumn column) { 
    // Editing widget will retain in view.         
    if (newCellValue == null || newCellValue == '') {
      return false;
    } else {
      return true;
    }
  }
}

{% endhighlight %}
{% endtabs %}