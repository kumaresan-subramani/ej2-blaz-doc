---
title: "Migration from Essential JS 1"
component: "Grid"
description: "Learn how to migrate the EJ2 data grid from EJ1 Grid."
---

# Migration from Essential JS 1

This article describes the API migration process of Grid component from Essential JS 1 to Essential JS 2.

## Sorting

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Default | **Property:** *allowSorting* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `allowSorting: true` <br> `});`| **Property:** *allowSorting* <br><br>`var gridObj = new ej.grids.Grid({` &nbsp;`allowSorting: true` <br>`});`<br>`gridObj.appendTo('#Grid');` |
|Clear the Sorted columns | **Method:** *clearSorting()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.clearSorting();`| **Method:** *clearSorting()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.clearSorting()`
|Get the Sorted Columns by using the Fieldname | **Method:** *getsortColumnByField(field)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getsortColumnByField("OrderID");`| **Property:** *sortSettings.columns* <br><br>Sorted Column for a particular field can be get by iterating the `sortSettings.columns` with the fieldname
|Remove the Sorted Columns | **Method:** *removeSortedColumns(fieldName)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.removeSortedColumns("OrderID");`| **Method:** *removeSortColumn()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.removeSortColumn("OrderID")`
|Sort a Column by using the method| **Method:** *sortColumn(columnName, [sortingDirection])* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.sortColumn("OrderID", "ascending");`| **Method:** *sortColumn(columnName, Direction)* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.sortColumn("OrderID", "ascending");`

## Grouping

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Default | **Property:** *allowGrouping* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `allowGrouping: true` <br> `});`| **Property:** *allowGrouping* <br><br>`var gridObj = new ej.grids.Grid({`<br>&nbsp;`allowGrouping: true` <br>`});`<br>`gridObj.appendTo('#Grid');` |
|   Group Columns initially      | **Property:** *groupSettings.groupedColumns* <br><br> `$("#Grid").ejGrid({`<br>&nbsp;&nbsp;`allowGrouping: true,`<br>&nbsp; `groupSettings: {`<br>  &nbsp;&nbsp;`groupedColumns:[“OrderID”, “CustomerID”]`<br>&nbsp;&nbsp; `}`<br>`});` | **Property:** *groupSettings.columns* <br><br> `var gridObj = new ej.grids.Grid({`<br>&nbsp;`allowGrouping: true,`<br>&nbsp;`groupSettings: {`<br>&nbsp;`columns: [“OrderID”, “CustomerID”]`<br>&nbsp;&nbsp;`}`<br>`});`<br>`gridObj.appendTo('#Grid');`
|   Caption Template           | **Property:** *groupSettings.captionFormat* <br><br> `$("#Grid").ejGrid({`<br>&nbsp;&nbsp;`allowGrouping: true,`<br>&nbsp; `groupSettings: {`<br>  &nbsp;&nbsp;`captionFormat: "#template"`<br>&nbsp;&nbsp; `}`<br>`});` | **Property:** *groupSettings.captionTemplate* <br><br> `var gridObj = new ej.grids.Grid({`<br>&nbsp;`allowGrouping: true,`<br>&nbsp;`groupSettings: {`<br>&nbsp;`captionTemplate: '#template'`<br>&nbsp;&nbsp;`}`<br>`});`<br>`gridObj.appendTo('#Grid');`
| Show Drop Area | **Property:** *groupSettings.showDropArea* <br><br> `$("#Grid").ejGrid({`<br>&nbsp;&nbsp;`allowGrouping: true,`<br>&nbsp; `groupSettings: {`<br>  &nbsp;&nbsp;`showDropArea: false`<br>&nbsp;&nbsp; `}`<br>`});` | **Property:** *groupSettings.showDropArea* <br><br> `var gridObj = new ej.grids.Grid({`<br>&nbsp;`allowGrouping: true,`<br>&nbsp;`groupSettings: {`<br>&nbsp;`showDropArea: false`<br>&nbsp;&nbsp;`}`<br>`});`<br>`gridObj.appendTo('#Grid');`
|Collapse all group caption rows | **Method:** *collapseAll()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.collapseAll();`| **Method:** *collapseAll()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.groupModule.collapseAll()`
|Expand all group caption rows | **Method:** *expandAll()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.expandAll();`| **Method:** *expandAll()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.groupModule.expandAll()`
|Expand or collapse the row based <br>on the row state in grid | **Method:** *expandCollapse($target)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.expandCollapse($("tr td.recordplusexpand > div").first());`| **Method:** *expandCollapseRows()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]`<br>`gridObj.groupModule.expandCollapseRows(`<br>`gridObj.getContent().querySelectorAll('.e-recordplusexpand')[0])`
|Collapse the group drop area in grid | **Method:** *collapseGroupDropArea()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.collapseGroupDropArea();`| Not Applicable
|Expand the group drop area in grid | **Method:** *expandGroupDropArea()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.expandGroupDropArea();`| Not Applicable
|Group a column by using the method | **Method:** *groupColumn(fieldName)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.groupColumn("OrderID");`| **Method:** *groupColumn(fieldName)* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.groupColumn("OrderID")`
|Ungroup a grouped column by using the method | **Method:** *ungroupColumn(fieldName)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.ungroupColumn("OrderID");`| **Method:** *ungroupColumn(fieldName)* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.ungroupColumn("OrderID")`

## Filtering

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Default | **Property:** *allowFiltering* <br><br> `$("#Grid").ejGrid({`<br>&nbsp; `allowFiltering: true` <br> `});`| **Property:** *allowFiltering* <br><br>`var gridObj = new ej.grids.Grid({`<br>&nbsp;`allowFiltering: true` <br>`});`<br>`gridObj.appendTo('#Grid');` |
|   Menu Filtering           | **Property:** *filterSettings.filterType* <br><br>`$("#Grid").ejGrid({`<br>&nbsp;&nbsp;`allowFiltering: true,`<br>&nbsp; `filterSettings: {`<br>&nbsp;&nbsp;`filterType : "menu"`<br>&nbsp;&nbsp; `}`<br>`});`|  **Property:** *filterSettings.type* <br><br> `var gridObj = new ej.grids.Grid({`<br>&nbsp;`allowFiltering: true,`<br>&nbsp;`filterSettings: {`<br>&nbsp;`type:'Menu'`<br>&nbsp;&nbsp;`}`<br>`});`<br>`gridObj.appendTo('#Grid');`
|   Excel Filtering           | **Property:** *filterSettings.filterType* <br><br> `$("#Grid").ejGrid({`<br>&nbsp;&nbsp;`allowFiltering: true,`<br>&nbsp;`filterSettings: {`<br>  &nbsp;&nbsp;`filterType : "excel"`<br>&nbsp;&nbsp; `}`<br>`});`|  **Property:** *filterSettings.type* <br><br> `var gridObj = new ej.grids.Grid({`<br>&nbsp;`allowFiltering: true,`<br>&nbsp;`filterSettings: {`<br>&nbsp;`type:'Excel'`<br>&nbsp;&nbsp;`}`<br>`});`<br>`gridObj.appendTo('#Grid');`
|Clear the Filtered values | **Method:** *clearFiltering(field) - field is optional* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.clearFiltering();`| **Method:** *clearFiltering()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.clearFiltering()`
|Filter a column by using the method| **Method:** *filterColumn(fieldName, filterOperator, filterValue, <br>predicate, [matchcase],[actualFilterValue])* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.filterColumn("OrderID",`<br>`"equal","10248","and", true);`| **Method:** *filterByColumn(fieldName, filterOperator, filterValue, predicate, matchCase, ignoreAccent, actualFilterValue, actualOperator)* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br>`gridObj.filterByColumn("OrderID","equal",10248)`
|Filter columns by Collection| **Method:** *filterColumn(filterCollection)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.filterColumn([{field:"OrderID",`<br>&nbsp;`operator:"lessthan",value:"10266",`<br>`predicate:"and",matchcase:true},`<br>&nbsp;`{field:"EmployeeID",operator:`<br>&nbsp;`"equal",value:2,predicate:"and", matchcase:true}])`| **Property:** *filterSettings.columns* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br>`gridObj.filterSettings:{columns: [{ field: 'ShipCity', matchCase: false, operator: 'startswith', predicate: 'and', value: 'reims' }]}`
|Get the Filtered Records| **Method:** *getFilteredRecords()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getFilteredRecords();`| Not Applicable

## Searching

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|   Default           | **Property:** *toolbarSettings.toolbarItems* <br><br> `$("#Grid").ejGrid({`<br>&nbsp;&nbsp;`showToolbar: true, toolbarItems : ["search"]`<br>  &nbsp;&nbsp;`allowSearching : true`<br>`});` | **Property:** *toolbar* <br><br> `var gridObj = new ej.grids.Grid({`<br>&nbsp;`toolbar: ['Search']`<br>`});`<br>`gridObj.appendTo('#Grid');`
|Clear the Searched values | **Method:** *clearSearching()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.clearSearching();`| **Method:** *searchModule.search()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.searchModule.search("");`
|Search a value | **Method:** *search(searchString)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.search("France");`| **Method:** *searchModule.search()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.searchModule.search("France");`

## Paging

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Default | **Property:** *allowPaging* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `allowPaging: true` <br> `});`| **Property:** *allowPaging* <br><br>`var gridObj = new ej.grids.Grid({` &nbsp;`allowPaging: true` <br>`});`<br>`gridObj.appendTo('#Grid');` |
|   Customize Paging           | **Property:** *pageSettings.pageSize* <br><br>`$("#Grid").ejGrid({`<br>&nbsp;&nbsp;`allowPaging: true,`<br>&nbsp;`pageSettings: {`<br>  &nbsp;&nbsp;`pageSize: 8,pageSizeList: [5, 10],pageCount:3`<br>&nbsp;&nbsp;`}`<br>`});`|**Property:** *pageSettings.pageSize* <br><br> `var gridObj = new ej.grids.Grid({`<br>&nbsp;`allowPaging: true,`<br>&nbsp;`pageSettings: {`<br>&nbsp;`pageSize:8, pageSizes: [5, 10],pageCount:3`<br>&nbsp;&nbsp;`}`<br>`});`<br>`gridObj.appendTo('#Grid');`
|Change Page Size | **Method:** *changePageSize(pageSize)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.changePageSize(7);`| **Property:** *pageSettings.pageSize* <br><br>Pagesize can be modified dynamically by using the below code <br>`pageSettings.pageSize = 7;`|
|Get Current Page Index | **Method:** *getCurrentIndex()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getCurrentIndex();`| **Property:** *pageSettings.currentPage* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.pageSettings.currentPage;`
|Get Pager Element | **Method:** *getPager()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getPager();`| **Method:** *getPager()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.getPager();`
|Send a paging request to specified Page | **Method:** *gotoPage(pageIndex)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.gotoPage(3);`| **Method:** *gotoPage(pageIndex)* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.gotoPage(3);`
|Calculate Pagesize of grid by using its Parent height(containerHeight) | **Method:** *calculatePageSizeBy*<br>*ParentHeight(containerHeight)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.`<br>`calculatePageSizeByParentHeight(400);`| Not Applicable

## Selection

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Default | **Property:** *allowSelection* <br><br> `$("#Grid").ejGrid({`<br>&nbsp; `allowSelection: true` <br>`});`| **Property:** *allowSelection* <br><br>`var gridObj = new ej.grids.Grid({`&nbsp;`allowSelection: true` <br>`});`<br>`gridObj.appendTo('#Grid');` |
|   Single Selection           |**Property:** *selectionType*<br><br>`$("#Grid").ejGrid({`<br>&nbsp;&nbsp;`allowSelection: true,`<br>&nbsp;`selectionType : "single"`<br>&nbsp;&nbsp;`});`|**Property:** *selectionSettings.type*<br><br>`var gridObj = new ej.grids.Grid({`<br>&nbsp;`allowSelection: true,`<br>&nbsp;`selectionSettings: {`<br>&nbsp;`type : "Single"`<br>&nbsp;&nbsp;`}`<br>`});`<br>`gridObj.appendTo('#Grid');`
|   Multiple Selection           | **Property:** *selectionType* <br><br> `$("#Grid").ejGrid({`<br>&nbsp;&nbsp;`allowSelection: true,`<br>&nbsp;`selectionType : "multiple"`<br>&nbsp;&nbsp;`});`|**Property:** *selectionSettings.type*<br><br>`var gridObj = new ej.grids.Grid({`<br>&nbsp;`allowSelection: true,`<br>&nbsp;`selectionSettings: {`<br>&nbsp;`type : "Multiple"`<br>&nbsp;&nbsp;`}`<br>`});`<br>`gridObj.appendTo('#Grid');`
|   Row Selection           | **Property:** *selectionSettings.selectionMode* <br><br> `$("#Grid").ejGrid({`<br>&nbsp;&nbsp;`allowSelection: true,`<br>&nbsp; `selectionSettings : {selectionMode: ["row"]}`<br>&nbsp;&nbsp;`});`|**Property:** *selectionSettings.mode* <br><br>`var gridObj = new ej.grids.Grid({`<br>&nbsp;`allowSelection: true,`<br>&nbsp;`selectionSettings: {`<br>&nbsp;`mode: 'Row'`<br>&nbsp;&nbsp;`}`<br>`});`<br>`gridObj.appendTo('#Grid');`
|   Cell Selection           | **Property:** *selectionSettings.selectionMode* <br><br> `$("#Grid").ejGrid({`<br>&nbsp;&nbsp;`allowSelection: true,`<br>&nbsp; `selectionSettings : {selectionMode: ["cell"]}`<br>&nbsp;&nbsp;`});`|**Property:** *selectionSettings.mode* <br><br>`var gridObj = new ej.grids.Grid({`<br>&nbsp;`allowSelection: true,`<br>&nbsp;`selectionSettings: {`<br>&nbsp;`mode: 'Cell'`<br>&nbsp;&nbsp;`}`<br>`});`<br>`gridObj.appendTo('#Grid');`
|Clear the selected Cells | **Method:** *clearCellSelection()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.clearCellSelection();`| **Method:** *clearCellSelection()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.selectionModule.clearCellSelection()`
|Clear the selected Columns | **Method:** *clearColumnSelection([index]) - index is optional* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.clearColumnSelection();`| Not Applicable
|Get the selected Records | **Method:** *getSelectedRecords()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getSelectedRecords();`| **Method:** *getSelectedRecords()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.getSelectedRecords();`
|Get the selected Rows | **Method:** *getSelectedRows()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getSelectedRows();`| **Method:** *getSelectedRows()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.getSelectedRows();`
|Select Cells | **Method:** *selectCells(rowCellIndexes)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.selectCells([[1, [4, 3, 2]]]);`| **Method:** *selectionModule.selectCells();* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.selectionModule.selectCells([{ rowIndex: 0, cellIndexes: [0] }, { rowIndex: 1, cellIndexes: [1] }]);;`
|Select Rows | **Method:** *selectRows(fromIndex, toIndex)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.selectRows(1, 4);`| **Method:** *selectionModule.selectRows()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]`<br> `gridObj.selectionModule.selectRows([0, 2])`
|Triggers when a <br>cell is selected| **Event:** *cellSelected* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `cellSelected: function (args){}` <br> `});`| **Event:** *cellSelected* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `cellSelected: function (args){}`<br> `});`
|Triggers before the cell is being selected| **Event:** *cellSelecting* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `cellSelecting: function (args){}` <br> `});`| **Event:** *cellSelecting* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `cellSelecting: function (args){}`<br> `});`
|Triggers when a <br>cell is deselected| **Event:** *cellDeselected* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `cellDeselected: function (args){}` <br> `});`| **Event:** *cellDeselected* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `cellDeselected: function (args){}`<br> `});`
|Triggers before the cell is being deselected| **Event:** *cellDeselecting* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `cellDeselecting: function (args){}` <br> `});`| **Event:** *cellDeselecting* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `cellDeselecting: function (args){}`<br> `});`
|Triggers when the <br>row is selected| **Event:** *rowSelected* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `rowSelected: function (args){}` <br> `});`| **Event:** *rowSelected* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `rowSelected: function (args){}`<br> `});`
|Triggers before the row is being selected| **Event:** *rowSelecting* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `rowSelecting: function (args){}` <br> `});`| **Event:** *rowSelecting* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `rowSelecting: function (args){}`<br> `});`
|Triggers when the <br>row is deselected| **Event:** *rowDeselected* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `rowDeselected: function (args){}` <br> `});`| **Event:** *rowDeselected* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `rowDeselected: function (args){}`<br> `});`
|Triggers before the row is being deselected| **Event:** *rowDeselecting* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `rowDeselecting: function (args){}` <br> `});`| **Event:** *rowDeselecting* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `rowDeselecting: function (args){}`<br> `});`
|Triggers when the column is selected| **Event:** *columnSelected* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `columnSelected: function (args){}` <br> `});`| Not Applicable
|Triggers before the column is being selected | **Event:** *columnSelecting* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `columnSelecting: function (args){}` <br> `});`| Not Applicable
|Triggers when the column is deselected| **Event:** *columnDeselected* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `columnDeselected: function (args){}` <br> `});`| Not Applicable
|Triggers before the column is being deselected| **Event:** *columnDeselecting* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `columnDeselecting: function (args){}` <br> `});`| Not Applicable

## Editing

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|   Default           | **Property:** *editSettings* <br><br> `$("#Grid").ejGrid({`<br>  &nbsp;&nbsp;`editSettings : { allowEditing: true,`<br>&nbsp;&nbsp;`allowAdding: true, allowDeleting: true}`<br>`});` | **Property:** *editSettings* <br><br> `var gridObj = new ej.grids.Grid({`<br>&nbsp;&nbsp;`editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true }`<br>`});`<br>`gridObj.appendTo('#Grid');`
|   Inline Editing           | **Property:** *editSettings.editMode* <br><br> `$("#Grid").ejGrid({`<br>  &nbsp;&nbsp;`editSettings : { allowEditing: true,`<br>&nbsp;&nbsp;`allowAdding: true, allowDeleting: true, editMode : "normal"}`<br>`});` | **Property:** *editSettings.mode* <br><br> `var gridObj = new ej.grids.Grid({`<br>&nbsp;&nbsp;`editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' }`<br>`});`<br>`gridObj.appendTo('#Grid');`
|   Dialog Editing           | **Property:** *editSettings.editMode* <br><br> `$("#Grid").ejGrid({`<br>  &nbsp;&nbsp;`editSettings : { allowEditing: true,`<br>&nbsp;&nbsp;`allowAdding: true, allowDeleting: true, editMode : "dialog"}`<br>`});` | **Property:** *editSettings.mode* <br><br> `var gridObj = new ej.grids.Grid({`<br>&nbsp;&nbsp;`editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Dialog' }`<br>`});`<br>`gridObj.appendTo('#Grid');`
|   Batch Editing           | **Property:** *editSettings.editMode* <br><br> `$("#Grid").ejGrid({`<br>  &nbsp;&nbsp;`editSettings : { allowEditing: true,`<br>&nbsp;&nbsp;`allowAdding: true, allowDeleting: true, editMode : "batch"}`<br>`});` | **Property:** *editSettings.mode* <br><br> `var gridObj = new ej.grids.Grid({`<br>&nbsp;&nbsp;`editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Batch' }`<br>`});`<br>`gridObj.appendTo('#Grid');`
|Add a new Record | **Method:** *addRecord([data,[serverChange]])* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.addRecord({"OrderID":12333});`| **Method:** *addRecord(data(optional), index(optional))* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.addRecord();`
|Batch Cancel | **Method:** *batchCancel()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.batchCancel();`| Not Applicable
|Batch Save | **Method:** *batchSave()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.batchSave();`| **Method:** *batchSave()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.editModule.batchSave()`
|Save a Cell - If *preventSaveEvent* is true, then it <br>will prevent the client side cellSave event| **Method:** *saveCell([preventSaveEvent])* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.saveCell();`| **Method:** *saveCell()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.editModule.saveCell()`
|End Edit | **Method:** *endEdit()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.endEdit();`| **Method:** *endEdit()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.endEdit()`
|Cancel Edit | **Method:** *cancelEdit()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.cancelEdit();`| **Method:** *closeEdit()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.closeEdit()`
|Delete Record | **Method:** *deleteRecord(fieldName, data)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.deleteRecord("OrderID", { OrderID: 10249, EmployeeID: 3 });`| **Method:** *deleteRecord(field, data)- Field and*<br>* data are optional* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.deleteRecord()`
|Delete Row | **Method:** *deleteRow($tr)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.deleteRow($(".gridcontent tr").first());`| **Method:** *deleteRow(tr)* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `grid.deleteRow(grid.getContentTable()`<br>`.querySelector("tbody").firstChild)`
|Edit a cell in Batch edit mode| **Method:** *editCell(index, fieldName)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.editCell(2, "OrderID");`| **Method:** *startEdit(tr)* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br>`gridObj.editModule.editCell(0,gridObj`<br>`.columns[0].field)`
|Edit Form Validation | **Method:** *editFormValidate()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.editFormValidate();`| **Method:** *editModule.formObj.validate()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br>`gridObj.editModule.formObj.validate()`
|Get Batch Changes | **Method:** *getBatchChanges()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getBatchChanges();`| **Method:** *editModule.getBatchChanges()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br>`gridObj.editModule.getBatchChanges()`
|Refresh Batch Edit Changes | **Method:** *refreshBatchEditChanges()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.refreshBatchEditChanges();`| Not Applicable
|Set Default Data for adding| **Method:** *setDefaultData(defaultData)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `var defaultData = {OrderID:"10000"};` <br> `gridObj.setDefaultData(defaultData);`| **Method:** *editModule.addRecord()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.editModule.addRecord({OrderID:10000})`
|Start Edit | **Method:** *startEdit($tr)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.startEdit($(".gridcontent tr").first());`| **Method:** *startEdit()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.startEdit(gridObj.selectRow(0))`
|Update Record | **Method:** *updateRecord(fieldName, data)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.updateRecord("OrderID", { OrderID: 10249, EmployeeID: 3 });`| Not Applicable
|Set Cell value | **Method:** *setCellText()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.setCellText(0, 1, "France");`| **Method:** *setCellValue(key, field, value)* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.setCellValue(10248,"CustomerID","A")`
|Get Currently edited cell value| **Method:** *getCurrentEditCellData()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getCurrentEditCellData();`| **Method:** *getCurrentEditCellData()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.`<br>`editModule.getCurrentEditCellData();`
|Triggers when adding a <br>record in batch editing| **Event:** *batchAdd* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `batchAdd: function (args){}` <br> `});`| **Event:** *batchAdd* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `batchAdd: function (args){}`<br> `});`
|Triggers when deleting a <br>record in batch editing| **Event:** *batchDelete* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `batchDelete: function (args){}` <br> `});`| **Event:** *batchDelete* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `batchDelete: function (args){}`<br> `});`
|Triggers before adding a record in batch editing| **Event:** *beforeBatchAdd* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `beforeBatchAdd: function (args){}` <br> `});`| **Event:** *beforeBatchAdd* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `beforeBatchAdd: function (args){}`<br> `});`
|Triggers before deleting a record in batch editing| **Event:** *beforeBatchDelete* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `beforeBatchDelete: function (args){}` <br> `});`| **Event:** *beforeBatchDelete* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `beforeBatchDelete: function (args){}`<br> `});`
|Triggers before saving a record in batch editing| **Event:** *beforeBatchSave* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `beforeBatchSave: function (args){}` <br> `});`| **Event:** *beforeBatchSave* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `beforeBatchSave: function (args){}`<br> `});`
|Triggers before the <br>record in being edited| **Event:** *beginEdit* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `beginEdit: function (args){}` <br> `});`| **Event:** *beginEdit* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `beginEdit: function (args){}`<br> `});`
|Triggers when the <br>cell is being edited| **Event:** *cellEdit* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `cellEdit: function (args){}` <br> `});`| **Event:** *cellEdit* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `cellEdit: function (args){}`<br> `});`
|Triggers when the <br>cell is saved| **Event:** *cellSave* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `cellSave: function (args){}` <br> `});`| **Event:** *cellSave* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `cellSave: function (args){}`<br> `});`
|Triggers when the record is added| **Event:** *endAdd* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `endAdd: function (args){}` <br> `});`| **Event:** *actionComplete* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `actionComplete: function (args){}`<br> `});`
|Triggers when the record is deleted| **Event:** *endDelete* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `endDelete: function (args){}` <br> `});`| **Event:** *actionComplete* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `actionComplete: function (args){}`<br> `});`
|Triggers after the record is edited| **Event:** *endEdit* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `endEdit: function (args){}` <br> `});`| **Event:** *actionComplete* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `actionComplete: function (args){}`<br> `});`

## Resizing

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Default | **Property:** *allowResizing* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `allowResizing: true` <br> `});`| **Property:** *allowResizing* <br><br>`var gridObj = new ej.grids.Grid({` &nbsp;`allowResizing: true` <br>`});`<br>`gridObj.appendTo('#Grid');` |
|Resize a column by using the method| **Method:** *resizeColumns(column,width)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.resizeColumns("OrderID",width);`| **Property:** *columns.width* <br><br>To resize a column, set width to that particular column and then refresh the grid by using the refresh method.<br>`var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.columns[1].width = 100;`<br> `gridObj.refresh();`
|Triggers when a column resize starts| **Event:** *resizeStart* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `resizeStart: function (args){}` <br> `});`| **Event:** *resizeStart* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `resizeStart: function (args){}`<br> `});`
|Triggers when a column is resized| **Event:** *resized* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `resized: function (args){}` <br> `});`| **Event:** *resizeStop* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `resizeStop: function (args){}`<br> `});`
|Triggers when a column resize stops| **Event:** *resizeEnd* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `resizeEnd: function (args){}` <br> `});`| Not Applicable

## Reordering

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Default | **Property:** *allowReordering* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `allowReordering: true` <br> `});`| **Property:** *allowReordering* <br><br>`var gridObj = new ej.grids.Grid({` &nbsp;`allowReordering: true` <br>`});`<br>`gridObj.appendTo('#Grid');` |
|Reorder Columns| **Method:** *reorderColumns(fromFieldName, toFieldName)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.reorderColumns("OrderID", "CustomerID");`| **Method:** *reorderColumns(fromFieldName, toFieldName)* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.reorderColumns("OrderID", "CustomerID");`
|Reorder Rows| **Method:** *reorderRows(indexes, toIndex)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.reorderRows([0,1],3);`| Not Applicable

## Context Menu

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|   Default           | **Property:** *contextMenuSettings.enableContextMenu* <br><br> `$("#Grid").ejGrid({`<br>  &nbsp;&nbsp;`contextMenuSettings: { enableContextMenu: true }`<br>`});` | **Property:** *contextMenuItems* <br><br> `var gridObj = new ej.grids.Grid({`<br>&nbsp;&nbsp;`contextMenuItems: ['AutoFit', 'AutoFitAll']`<br>`});`<br>`gridObj.appendTo('#Grid');`
|Triggers when context menu item is clicked| **Event:** *contextClick* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `contextClick: function (args){}` <br> `});`| **Event:** *contextMenuClick* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `contextMenuClick: function (args){}`<br> `});`
|Triggers when context menu opens| **Event:** *contextOpen* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `contextOpen: function (args){}` <br> `});`| **Event:** *contextMenuOpen* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `contextMenuOpen: function (args){}`<br> `});`

## Toolbar

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|   Print           | **Property:** *toolbarSettings.toolbarItems* <br><br> `$("#Grid").ejGrid({`<br>&nbsp;&nbsp;`showToolbar: true,`<br>  &nbsp;&nbsp;`toolbarItems: [ej.Grid.ToolBarItems.PrintGrid]`<br>`});` | **Property:** *toolbar* <br><br> `var gridObj = new ej.grids.Grid({`<br>&nbsp;`toolbar: ['Print']`<br>`});`<br>`gridObj.appendTo('#Grid');`
|   Add           | **Property:** *toolbarSettings.toolbarItems* <br><br> `$("#Grid").ejGrid({`<br>&nbsp;&nbsp;`showToolbar: true,`<br>  &nbsp;&nbsp;`toolbarItems: [ej.Grid.ToolBarItems.Add]`<br>`});` | **Property:** *toolbar* <br><br> `var gridObj = new ej.grids.Grid({`<br>&nbsp;`toolbar: ['Add']`<br>`});`<br>`gridObj.appendTo('#Grid');`
|   Edit           | **Property:** *toolbarSettings.toolbarItems* <br><br> `$("#Grid").ejGrid({`<br>&nbsp;&nbsp;`showToolbar: true,`<br>  &nbsp;&nbsp;`toolbarItems: [ej.Grid.ToolBarItems.Edit]`<br>`});` | **Property:** *toolbar* <br><br> `var gridObj = new ej.grids.Grid({`<br>&nbsp;`toolbar: ['Edit']`<br>`});`<br>`gridObj.appendTo('#Grid');`
|   Delete           | **Property:** *toolbarSettings.toolbarItems* <br><br> `$("#Grid").ejGrid({`<br>&nbsp;&nbsp;`showToolbar: true,`<br>  &nbsp;&nbsp;`toolbarItems: [ej.Grid.ToolBarItems.Delete]`<br>`});` | **Property:** *toolbar* <br><br> `var gridObj = new ej.grids.Grid({`<br>&nbsp;`toolbar: ['Delete']`<br>`});`<br>`gridObj.appendTo('#Grid');`
|   Update           | **Property:** *toolbarSettings.toolbarItems* <br><br> `$("#Grid").ejGrid({`<br>&nbsp;&nbsp;`showToolbar: true,`<br>  &nbsp;&nbsp;`toolbarItems: [ej.Grid.ToolBarItems.Update]`<br>`});` | **Property:** *toolbar* <br><br> `var gridObj = new ej.grids.Grid({`<br>&nbsp;`toolbar: ['Update']`<br>`});`<br>`gridObj.appendTo('#Grid');`
|   Cancel           | **Property:** *toolbarSettings.toolbarItems* <br><br> `$("#Grid").ejGrid({`<br>&nbsp;&nbsp;`showToolbar: true,`<br>  &nbsp;&nbsp;`toolbarItems: [ej.Grid.ToolBarItems.Cancel]`<br>`});` | **Property:** *toolbar* <br><br> `var gridObj = new ej.grids.Grid({`<br>&nbsp;`toolbar: ['Cancel']`<br>`});`<br>`gridObj.appendTo('#Grid');`
|   ExcelExport           | **Property:** *toolbarSettings.toolbarItems* <br><br> `$("#Grid").ejGrid({`<br>&nbsp;&nbsp;`showToolbar: true,`<br>  &nbsp;&nbsp;`toolbarItems: [ej.Grid.ToolBarItems.ExcelExport]`<br>`});` | **Property:** *toolbar* <br><br> `var gridObj = new ej.grids.Grid({`<br>&nbsp;`toolbar: ['ExcelExport']`<br>`});`<br>`gridObj.appendTo('#Grid');`
|   WordExport           | **Property:** *toolbarSettings.toolbarItems* <br><br> `$("#Grid").ejGrid({`<br>&nbsp;&nbsp;`showToolbar: true,`<br>  &nbsp;&nbsp;`toolbarItems: [ej.Grid.ToolBarItems.WordExport]`<br>`});` | Not Applicable
|   PdfExport           | **Property:** *toolbarSettings.toolbarItems* <br><br> `$("#Grid").ejGrid({`<br>&nbsp;&nbsp;`showToolbar: true,`<br>  &nbsp;&nbsp;`toolbarItems: [ej.Grid.ToolBarItems.PdfExport]`<br>`});` | **Property:** *toolbar* <br><br> `var gridObj = new ej.grids.Grid({`<br>&nbsp;`toolbar: ['PdfExport']`<br>`});`<br>`gridObj.appendTo('#Grid');`
|Refresh Toolbar| **Method:** *refreshToolbar()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.refreshToolbar();`| Not Applicable
|Triggers when toolbar item is clicked| **Event:** *toolbarClick* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `toolbarClick: function (args){}` <br> `});`| **Event:** *toolbarClick* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `toolbarClick: function (args){}`<br> `});`

## GridLines

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Default | **Property:** *gridLines* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `gridLines: ej.Grid.GridLines.Both` <br> `});`| **Property:** *gridLines* <br><br>`var gridObj = new ej.grids.Grid({` <br>`gridLines: 'Default'` <br>`});`<br>`gridObj.appendTo('#Grid');` |

## Templates

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Detail Template | **Property:** *detailsTemplate* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `detailsTemplate : "#detailsTemplate"` <br> `});`| **Property:** *detailTemplate* <br><br>`var gridObj = new ej.grids.Grid({` <br>&nbsp;`detailTemplate: '#detailtemplate',` <br>`});`<br>`gridObj.appendTo('#Grid');` |
|Row Template | **Property:** *rowTemplate* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `rowTemplate : "#rowTemplate"` <br> `});`| **Property:** *rowTemplate* <br><br>`var gridObj = new ej.grids.Grid({` <br>&nbsp;`rowTemplate: '#rowtemplate'',` <br>`});`<br>`gridObj.appendTo('#Grid');` |
|Refresh Template| **Method:** *refreshTemplate()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.refreshTemplate();`| Not Applicable
|Triggers when detail template row is clicked to collapse| **Event:** *detailsCollapse* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `detailsCollapse: function (args){}` <br> `});`| Not Applicable
|Triggers when detail template row is initialized| **Event:** *detailsDataBound* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `detailsDataBound: function (args){}` <br> `});`| Not Applicable
|Triggers when detail template<br>row is clicked to expand| **Event:** *detailsExpand* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `detailsExpand: function (args){}` <br> `});`| **Event:** *detailDataBound* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `detailDataBound: function (args){}`<br> `});`
|Triggers when refresh the template column elements in the Grid| **Event:** *templateRefresh* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `templateRefresh: function (args){}` <br> `});`| Not Applicable

## Row/Column Drag and Drop

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Default | **Property:** *allowRowDragAndDrop* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `allowRowDragAndDrop: true` <br> `});`| **Property:** *allowRowDragAndDrop* <br><br>`var gridObj = new ej.grids.Grid({` <br>&nbsp;`allowRowDragAndDrop: true,` <br>&nbsp;`rowDropSettings: { targetID: 'DestGrid' }` <br>`});`<br>`gridObj.appendTo('#Grid');` |
|Triggers when the row is<br>being dragged| **Event:** *rowDrag* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `rowDrag: function (args){}` <br> `});`| **Event:** *rowDrag* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `rowDrag: function (args){}`<br> `});`
|Triggers when the row drag begins| **Event:** *rowDragStart* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `rowDragStart: function (args){}` <br> `});`| **Event:** *rowDragStart* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `rowDragStart: function (args){}`<br> `});`
|Triggers when the row is dropped| **Event:** *rowDrop* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `rowDrop: function (args){}` <br> `});`| **Event:** *rowDrop* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `rowDrop: function (args){}`<br> `});`
|Triggers before the row is being dropped| **Event:** *beforeRowDrop* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `beforeRowDrop: function (args){}` <br> `});`| Not Applicable
|Triggers when the <br>column is being dragged| **Event:** *columnDrag* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `columnDrag: function (args){}` <br> `});`| Not Applicable
|Triggers when the <br>column drag begins| **Event:** *columnDragStart* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `columnDragStart: function (args){}` <br> `});`| Not Applicable
|Triggers when the <br>column is dropped| **Event:** *columnDrop* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `columnDrop: function (args){}` <br> `});`| Not Applicable

## Frozen Rows and Columns

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Default | **Property:** *scrollSettings.frozenRows* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `allowScrolling: true,` <br>&nbsp; `scrollSettings:{frozenRows:2,`<br>`frozenColumns: 2 }` <br> `});`| **Property:** *frozenColumns* <br><br>`var gridObj = new ej.grids.Grid({` <br>&nbsp;`frozenColumns : 2,` <br>&nbsp;`frozenRows:2` <br>`});`<br>`gridObj.appendTo('#Grid');` |
|isFrozen | **Property:** *columns.isFrozen* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `columns : [{ field: "ShipCity", isFrozen:true}` <br> `});`| **Property:** *columns.isFrozen* <br><br>`var gridObj = new ej.grids.Grid({` <br>&nbsp;`columns : [{ field: "ShipCity", isFrozen: true}` <br>`});`<br>`gridObj.appendTo('#Grid');` |

## ForeignKey

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Default | **Property:** *columns.foreignKeyValue* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `columns : [{ field: "EmployeeID", foreignKeyField: "EmployeeID", foreignKeyValue: "FirstName", dataSource: window.employeeView, headerText: "First Name"}` <br> `});`| **Property:** *columns.foreignKeyValue* <br><br>`var gridObj = new ej.grids.Grid({` <br>&nbsp;`columns : [{ field: 'EmployeeID', headerText: 'Employee Name', width: 150, foreignKeyValue: 'FirstName', dataSource: employeeData}` <br>`});`<br>`gridObj.appendTo('#Grid');` |

## Auto Wrap

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Default | **Property:** *allowTextWrap* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `allowTextWrap : true`<br> `});`| **Property:** *allowTextWrap* <br><br>`var gridObj = new ej.grids.Grid({` <br>&nbsp;`allowTextWrap: true,` <br>`});`<br>`gridObj.appendTo('#Grid');` |
|Both | **Property:** *allowTextWrap* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `allowTextWrap : true`<br>&nbsp;`textWrapSettings: {wrapMode: "both"},` <br> `});`| **Property:** *allowTextWrap* <br><br>`var gridObj = new ej.grids.Grid({` <br>&nbsp;`allowTextWrap: true,` <br>&nbsp;`textWrapSettings: { wrapMode: 'Both' }` <br>`});`<br>`gridObj.appendTo('#Grid');` |
|Header | **Property:** *allowTextWrap* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `allowTextWrap : true`<br>&nbsp;`textWrapSettings: {wrapMode: "header"},` <br> `});`| **Property:** *allowTextWrap* <br><br>`var gridObj = new ej.grids.Grid({` <br>&nbsp;`allowTextWrap: true,` <br>&nbsp;`textWrapSettings: { wrapMode: 'Header' }` <br>`});`<br>`gridObj.appendTo('#Grid');` |
|Content | **Property:** *allowTextWrap* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `allowTextWrap : true`<br>&nbsp;`textWrapSettings: {wrapMode: "content"},` <br> `});`| **Property:** *allowTextWrap* <br><br>`var gridObj = new ej.grids.Grid({` <br>&nbsp;`allowTextWrap: true,` <br>&nbsp;`textWrapSettings: { wrapMode: 'Content' }` <br>`});`<br>`gridObj.appendTo('#Grid');` |

## Responsive

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|   Default           | **Property:** *isResponsive* <br><br> `$("#Grid").ejGrid({`<br>&nbsp;&nbsp;`isResponsive: true,enableResponsiveRow: true`<br>`});` | Not Applicable

## State Persistence

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Default | **Property:** *enablepersistence* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `enablepersistence: true` <br> `});`| **Property:** *enablepersistence* <br><br>`var gridObj = new ej.grids.Grid({` <br>&nbsp;`enablepersistence: true` <br>`});`<br>`gridObj.appendTo('#Grid');` |

## Right to Left - RTL

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Default | **Property:** *enableRTl* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `enableRTl: true` <br> `});`| **Property:** *enableRtl* <br><br>`var gridObj = new ej.grids.Grid({` <br>&nbsp;`enableRtl: true` <br>`});`<br>`gridObj.appendTo('#Grid');` |

## ToolTip

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Default | **Property:** *clipMode* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `columns : [{ field: "ShipCity", clipMode: ej.Grid.ClipMode.EllipsisWithTooltip}` <br>&nbsp;`{ field: "ShipCountry", clipMode: ej.Grid.ClipMode.Ellipsis}`<br>&nbsp;`{ field: "ShipName", clipMode: ej.Grid.ClipMode.Clip}]`<br> `});`| **Property:** *clipMode* <br><br>`var gridObj = new ej.grids.Grid({` <br>&nbsp;`columns : [{ field: "ShipCity", clipMode: 'EllipsisWithTooltip'},` <br>&nbsp;`{ field: "ShipCountry", clipMode: 'Ellipsis'},`<br>&nbsp;`{ field: "ShipName", clipMode: 'Clip'}` <br>`});`<br>`gridObj.appendTo('#Grid');` |

## Aggregate/Summary

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Footer Aggregate | **Property:** *showSummary* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `showSummary: true` <br>&nbsp;&nbsp;`summaryRows: [{`<br>&nbsp;&nbsp;&nbsp;`title: "Sum",`<br>&nbsp;&nbsp;&nbsp;`summaryColumns: [{` <br>&nbsp;&nbsp;&nbsp;`summaryType: ej.Grid.SummaryType.Sum,` <br>&nbsp;&nbsp;&nbsp;`displayColumn: "Freight",`<br>&nbsp;&nbsp;&nbsp;`dataMember: "Freight",` <br>&nbsp;&nbsp;&nbsp;`format: "{0:C2}"}]}]`<br> `});`| **Property:** *aggregates* <br><br>`var gridObj = new ej.grids.Grid({` <br>&nbsp;`aggregates: [{` <br>&nbsp;&nbsp;`columns: [{`<br>&nbsp;&nbsp;`type: 'Sum',`<br>&nbsp;&nbsp;`field: 'Freight',`<br>&nbsp;&nbsp;`footerTemplate: 'Sum: ${Sum}'}]}` <br>`});`<br>`gridObj.appendTo('#Grid');` |
|Caption Aggregate | **Property:** *showSummary* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `showSummary: true` <br>&nbsp;&nbsp;`summaryRows: [{`<br>&nbsp;&nbsp;`showCaptionSummary: true,`<br>&nbsp;&nbsp;&nbsp;`title: "Sum",`<br>&nbsp;&nbsp;&nbsp;`summaryColumns: [{` <br>&nbsp;&nbsp;&nbsp;`summaryType: ej.Grid.SummaryType.Sum,` <br>&nbsp;&nbsp;&nbsp;`displayColumn: "Freight",`<br>&nbsp;&nbsp;&nbsp;`dataMember: "Freight",` <br>&nbsp;&nbsp;&nbsp;`format: "{0:C2}"}]}]`<br> `});`| **Property:** *aggregates* <br><br>`var gridObj = new ej.grids.Grid({` <br>&nbsp;`aggregates: [{` <br>&nbsp;&nbsp;`columns: [{`<br>&nbsp;&nbsp;`type: 'Sum',`<br>&nbsp;&nbsp;`field: 'Freight',`<br>&nbsp;&nbsp;`groupCaptionTemplate: 'Max: ${Max}'}]}` <br>`});`<br>`gridObj.appendTo('#Grid');` |
|Get Summary values | **Method:** *getSummaryValues(summaryCol, summaryData)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getSummaryValues(summaryCol, window.gridData);`| Not Applicable

## Grid Export

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Adds a grid model property which is <br>to be ignored on exporting grid | **Method:** *addIgnoreOnExport(propertyNames)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.addIgnoreOnExport("filterSettings");`| Not Applicable |

## Columns

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Add or Remove Columns | **Method:** *columns(columnDetails, [action])()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.columns("OrderID", "remove");` <br> `gridObj.columns("CustomerID", "add");`| **Property:** *columns* <br><br> Grid is initially rendered with `OrderID` and `CustomerId` columns.Then if you want to add `ShipAddress` column, you have to reset the value for `column` property as `gridObj.columns = [{field:"OrderID"}, {field:"CustomerId"}, {field:"ShipAddress"}];` Then to remove the `CustomerId` column, reset the `column` property as, `gridObj.columns = [{field:"OrderID"}, {field:"ShipAddress"}];`
|Get Column By Field | **Method:** *getColumnByField(fieldName)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getColumnByField("OrderID");`| **Method:** *getColumnByField(fieldName)* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br>`gridObj.getColumnByField("OrderID")`
|Get Column By HeaderText | **Method:** *getColumnByHeaderText(headerText)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getColumnByHeaderText("Order ID");`| Column object for a corresponding headerText can able to get by iterating the gridObj.columns with the headerText
|Get Column By Index | **Method:** *getColumnByIndex(columnIndex)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getColumnByIndex(1);`| **Method:** *getColumnByIndex(columnIndex)* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br>`gridObj.getColumnByIndex(1)`
|Get Column Fieldnames | **Method:** *getColumnFieldNames()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getColumnFieldNames();`| **Method:** *getColumnFieldNames()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br>`gridObj.getColumnFieldNames()`
|Get Column Index By Field | **Method:** *getColumnIndexByField(fieldName)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getColumnIndexByField("OrderID");`| **Method:** *getColumnIndexByField(fieldName)* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br>`gridObj.getColumnIndexByField("OrderID");`
|Get Column Index By headerText | **Method:** *getColumnIndexByHeaderText(headerText, [field])* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getColumnIndexByHeaderText("Order ID");`| The Column Index for a corresponding headerText can be get by iterating the gridObj.columns with the headerText
|Set Width to columns | **Method:** *setWidthToColumns()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.setWidthToColumns();`| **Method:** *widthService.setWidthToColumns()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br>`gridObj.widthService.setWidthToColumns()`
|Get HeaderText By FieldName | **Method:** *getHeaderTextByFieldName()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getHeaderTextByFieldName("OrderID");`| Not Applicable
|Get Hidden Columnname | **Method:** *getHiddenColumnNames()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getHiddenColumnNames();`| Not Applicable
|Get Visible Columns/Names| **Method:** *getVisibleColumnNames()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getVisibleColumnNames();`| **Method:** *getVisibleColumns()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.getVisibleColumns();`
|Select Columns | **Method:** *selectColumns(fromIndex)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.selectColumns(1,4);`| Not Applicable
|Select Specific Columns based on Index | **Method:** *selectColumns(columnIndex,[toIndex])* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.selectColumns(1,4);`| Not Applicable

## Row

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|EnableHover | **Property:** *enableRowHover* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `enableRowHover : false` <br> `});`| **Property:** *enableHover* <br><br>`var gridObj = new ej.grids.Grid({` <br>&nbsp;`enableHover: false,` <br>`});`<br>`gridObj.appendTo('#Grid');` |
|Get Row Height | **Method:** *getRowHeight()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getRowHeight();`| **Method:** *getRowHeight()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.getRowHeight();`
|Refresh Row Height| **Method:** *rowHeightRefresh()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.rowHeightRefresh();`| Not Applicable
|Get index by Row Element | **Method:** *getIndexByRow($tr)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getIndexByRow($(".gridcontent tr").first());`| Not Applicable
|Get Row by its Index | **Method:** *getRowByIndex(from, to)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getRowByIndex(3, 6);`| **Method:** *getRowByIndex()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.getRowByIndex(1);`
|Get rendered rows | **Method:** *getRows()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getRows();`| **Method:** *getRows()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.getRows();`
|Triggers while hover the grid row| **Event:** *rowHover* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `rowHover: function (args){}` <br> `});`| Not Applicable

## Show/Hide Columns

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Hide Columns by using method| **Method:** *hideColumns(headerText)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.hideColumns("Order ID");`| **Method:** *hideColumns(headerText)* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.hideColumns("Order ID");`
|Show Columns by using method| **Method:** *showColumns(headerText)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.showColumns("Order ID");`| **Method:** *showColumns(headerText)* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.showColumns("Order ID");`

## Column Chooser

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Default | **Property:** *showColumnChooser* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `showColumnChooser : true` <br> `columns: [` <br>&nbsp; `{ field: 'CustomerID', showInColumnChooser: false },` <br>&nbsp; `{ field: 'Name', showInColumnChooser: true },` <br> `]});`| **Property:** *showColumnChooser* <br><br>`var gridObj = new ej.grids.Grid({` <br>&nbsp;`showColumnChooser: true,` <br>&nbsp;`toolbar: ['ColumnChooser'],` <br>&nbsp; `columns: [{`<br>`{ field: 'CustomerID', showInColumnChooser: false },` <br>&nbsp; `{ field: 'Name', showInColumnChooser: true },`<br>`]});`<br>`gridObj.appendTo('#Grid');` |

## Header

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Refresh Header| **Method:** *refreshHeader()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.refreshHeader();`| **Method:** *refreshHeader()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.refreshHeader();`
|Triggers every time a request is made to access particular header cell information, element and data.| **Event:** *mergeHeaderCellInfo* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `mergeHeaderCellInfo: function (args){}` <br> `})`| Not Applicable
|Triggers every time a request is made to access particular cell information, element and data | **Event:** *mergeCellInfo* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `mergeCellInfo: function (args){}` <br> `})`| Not Applicable

## DataSource

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
| DataSource | **Method:** *dataSource(datasource,[templateRefresh])* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.dataSource(newdataSource);`| **Property:** *dataSource* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.datasource = newdataSource`

## Print

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Print the grid| **Method:** *print()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.print();`| **Method:** *print()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.print();`
|Triggers before printing the grid| **Event:** *beforePrint* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `beforePrint: function (args){}` <br> `});`| **Event:** *beforePrint* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `beforePrint: function (args){}`<br> `});`

## Scrolling

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Get ScrollObject | **Method:** *getScrollObject()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getScrollObject();`| **Property:** *grid.scrollModule* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `var scrollObj = gridObj.scrollModule;`

## PrimaryKey

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Set PrimaryKey Column| **Property:** *columns.isPrimaryKey* <br><br> `$("#Grid").ejGrid({` <br> `columns: [` <br> `{ field: "OrderID", isPrimaryKey: true}]`  `});`| **Property:** *columns.isPrimaryKey* <br><br> `var gridObj = new ej.grids.Grid({` <br> `columns: [` <br> `{ field: "OrderID", isPrimaryKey: true}]`<br> `});`
|Get the PrimaryKey fieldnames | **Method:** *getPrimaryKeyFieldNames()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getPrimaryKeyFieldNames();`| **Method:** <br>*getPrimaryKeyFieldNames()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.getPrimaryKeyFieldNames();`

## Grid

|Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--------- | ----------- | ----------- |
|Get the Browser Details| **Method:** *getBrowserDetails()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getBrowserDetails();`| In Essential JS 2, it can be <br>achieved by using `Browser` class of `ej2-base`
|Set dimension for the grid | **Method:** *setDimension(height, width)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.setDimension(300,400);`| Not Applicable
|set maximum width for mobile | **Method:** *setPhoneModeMaxWidth(value)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.setPhoneModeMaxWidth(500);`| Not Applicable
|Render the grid| **Method:** *render()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.render();`| **Method:** *render()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.render();`
|Reset the model collections like pageSettings, <br>groupSettings, filterSettings, sortSettings and summaryRows.| **Method:** *resetModelCollections()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.resetModelCollections();`| Not Applicable
|Destroy the grid| **Method:** *destroy()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.destroy();`| **Method:** *destroy()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.destroy()`
|Get Content Element| **Method:** *getContent()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getContent();`| **Method:** *getContent()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.getContent();`
|Get Content Table | **Method:** *getContentTable()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getContentTable();`| **Method:** *getContentTable()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.getContentTable();`
|Get Current View Data | **Method:** *getCurrentViewData()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getCurrentViewData();`| **Method:** *getCurrentViewRecords()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.getCurrentViewRecords();`
|Get Data Row| **Method:** *getDataByIndex(rowIndex)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getDataByIndex(0);`| **Method:** *getDataRows()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.getDataRows();`
|Get Fieldname by using the headertext| **Method:** *getFieldNameByHeaderText(headerText)* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getFieldNameByHeaderText("Order ID");`| Not Applicable
|Get FooterContent | **Method:** *getFooterContent()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getFooterContent();`| **Method:** *getFooterContent()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.getFooterContent();`
|Get FooterContent Table | **Method:** *getFooterTable()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getFooterTable();`| **Method:** *getFooterContentTable()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.getFooterContentTable();`
|Get HeaderContent | **Method:** *getHeaderContent()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getHeaderContent();`| **Method:** *getHeaderContent()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.getHeaderContent();`
|Get HeaderContent Table | **Method:** *getHeaderTable()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.getHeaderTable();`| **Method:** *getHeaderTable()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.getHeaderTable();`
|Refresh Content| **Method:** *refreshContent()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.refreshContent();`| **Method:**<br> *contentModule.refreshContentRows()* <br><br> `var gridObj = document.getElementById('Grid')`<br>`.ej2_instances[0]` <br> `gridObj.`<br>`contentModule.refreshContentRows();`
|Refresh Data| **Method:** *refreshData()* <br><br> `var gridObj = $("#Grid").data("ejGrid");` <br> `gridObj.refreshData();`| Not Applicable
|Triggers every time a request is <br>made to access particular cell <br>information, element and data| **Event:** *queryCellInfo* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `queryCellInfo: function (args){}` <br> `});`| **Event:** *queryCellInfo* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `queryCellInfo: function (args){}`<br> `});`
|Triggers every time a request is <br>made to access row information, <br>element and data| **Event:** *rowDataBound* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `rowDataBound: function (args){}` <br> `});`| **Event:** *rowDataBound* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `rowDataBound: function (args){}`<br> `});`
|Triggers for every grid <br>action before it get started| **Event:** *actionBegin* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `actionBegin: function (args){}` <br> `});`| **Event:** *actionBegin* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `actionBegin: function (args){}`<br> `});`
|Triggers for every grid <br>action success event| **Event:** *actionComplete* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `actionComplete: function (args){}` <br> `});`| **Event:** *actionComplete* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `actionComplete: function (args){}`<br> `});`
|Triggers for every grid <br>server failure event| **Event:** *actionFailure* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `actionFailure: function (args){}` <br> `});`| **Event:** *actionFailure* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `actionFailure: function (args){}`<br> `});`
|Triggers when the grid is bound <br>with data during rendering| **Event:** *dataBound* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `dataBound: function (args){}` <br> `});`| **Event:** *dataBound* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `dataBound: function (args){}`<br> `});`
|Triggers when the grid is<br>going to destroy| **Event:** *destroy* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `destroy: function (args){}` <br> `});`| **Event:** *destroyed* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `destroyed: function (args){}`<br> `});`
|Triggers when initial load of the grid| **Event:** *load* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `load: function (args){}` <br> `});`| **Event:** *load* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `load: function (args){}`<br> `});`
|Triggers when the grid is rendered completely| **Event:** *create* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `create: function (args){}` <br> `});`| **Event:** *created* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `created: function (args){}`<br> `});`
|Triggers when the record is clicked| **Event:** *recordClick* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `recordClick: function (args){}` <br> `});`| Not Applicable
|Triggers when right clicked on grid element| **Event:** *rightClick* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `rightClick: function (args){}` <br> `});`| Not Applicable
|Triggers when the <br>record is double clicked| **Event:** *recordDoubleClick* <br><br> `$("#Grid").ejGrid({` <br>&nbsp; `recordDoubleClick: function (args){}` <br> `});`| **Event:** *recordDoubleClick* <br><br> `var gridObj = new ej.grids.Grid({` <br>&nbsp; `recordDoubleClick: function (args){}`<br> `});`