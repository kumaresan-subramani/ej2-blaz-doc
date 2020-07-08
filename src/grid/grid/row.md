---
title: "Row"
component: "Grid"
description: "Documentation for row templates (custom row content), detail templates, and DataGrid row styles."
---

# Row

The row represents record details fetched from data source.

## Row template

The [`rowTemplate`](../api/grid/#rowtemplate) has an option to customise the look and behavior of the grid rows. The [`rowTemplate`](../api/grid/#rowtemplate) property accepts either
the [template string](../common/template-engine) or HTML element ID.
{% tab template="grid/row-template", sourceFiles="index.ts,index.html,index.css",es5Template="rowtemplate" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { employeeData } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: employeeData,
    rowTemplate: '#rowtemplate',
    columns: [
        { headerText: 'Employee Image', width: 150, textAlign: 'Center', field: 'OrderID' },
        { headerText: 'Employee Details', width: 300, field: 'EmployeeID' }
    ],
    height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}

>The [`rowTemplate`](../api/grid/#rowtemplate) property accepts only the TR element.

### Row template with formatting

If the [`rowTemplate`](../api/grid/#rowtemplate) is used, the value cannot be  formatted  inside the template using the [`columns.format`](../api/grid/column/#format) property. In that case, a function should be defined globally to format the value and invoke it inside the template.

{% tab template="grid/row-template-format", sourceFiles="index.ts,index.html,index.css",es5Template="format" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { employeeData } from './datasource.ts';
import { Internationalization } from '@syncfusion/ej2-base';

let intl: Internationalization = new Internationalization();

let dFormatter: Function = intl.getDateFormat({ skeleton: 'yMd', type: 'date' });

(<IWindow>window).formatDate = (date: Date) => dFormatter(date);

let grid: Grid = new Grid({
    dataSource: employeeData,
    rowTemplate: '#rowtemplate',
    columns: [
        { headerText: 'Employee Image', width: 150, textAlign: 'Center', field: 'OrderID' },
        { headerText: 'Employee Details', width: 300, field: 'EmployeeID' }
    ],
    height: 315
});
grid.appendTo('#Grid');

interface IWindow extends Window {
    formatDate?: Function;
}

```

{% endtab %}

### Limitations

Row template feature is not compatible with all the features which are available in grid and it has limited features support. Here we have listed out the features which are compatible with row template feature.

* Filtering
* Paging
* Sorting
* Scrolling
* Searching
* Rtl
* Export
* Context Menu
* State Persistence

## Detail template

The detail template provides additional information about a particular row by expanding or collapsing detail content. The [`detailTemplate`](../api/grid/#detailtemplate) property accepts either
the [template string](../common/template-engine) or HTML element ID.

To use detail template, inject the [`DetailRow`](../api/grid/detailRow)) module in the grid.

{% tab template="grid/detail-template", sourceFiles="index.ts,index.html,index.css",es5Template="detail" %}

```typescript
import { Grid, DetailRow } from '@syncfusion/ej2-grids';
import { employeeData } from './datasource.ts';

Grid.Inject(DetailRow);

let grid: Grid = new Grid({
    dataSource: employeeData,
    detailTemplate: '#detailtemplate',
    columns: [
        { field: 'FirstName', headerText: 'First Name', width: 140 },
        { field: 'LastName', headerText: 'Last Name', width: 140 },
        { field: 'Title', headerText: 'Title', width: 150 },
        { field: 'Country', headerText: 'Country', width: 150 }
    ],
    height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}

### Rendering custom component

To render the custom component inside the detail row, define the template in the [`detailTemplate`](../api/grid/#detailtemplate) and render the
component in the [`detailDataBound`](../api/grid/#detaildatabound-emittypedetaildataboundeventargs) event.

For example, to render grid inside the detail row, place an HTML div element as the [`detailTemplate`](../api/grid/#detailtemplate) and render the DIV element as grid component in the [`detailDataBound`](../api/grid/#detaildatabound-emittypedetaildataboundeventargs) event.

{% tab template="grid/detail-template-childgrid", sourceFiles="index.ts,index.html",es5Template="custom" %}

```typescript
import { Grid, DetailRow, DetailDataBoundEventArgs } from '@syncfusion/ej2-grids';
import { employeeData, data } from './datasource.ts';

Grid.Inject(DetailRow);

let grid: Grid = new Grid({
    dataSource: employeeData.slice(2, 5),
    detailTemplate: '#detailtemplate',
    columns: [
        { field: 'FirstName', headerText: 'First Name', width: 140 },
        { field: 'LastName', headerText: 'Last Name', width: 140 },
        { field: 'Title', headerText: 'Title', width: 150 },
        { field: 'Country', headerText: 'Country', width: 150 }
    ],
    detailDataBound: (e: DetailDataBoundEventArgs) => {
        let detail = new Grid({
            dataSource: data.filter((item: Object) => item['EmployeeID'] === e.data['EmployeeID']).slice(0, 3),
            columns: [
                { field: 'OrderID', headerText: 'Order ID', width: 110 },
                { field: 'CustomerID', headerText: 'Customer Name', width: 140 },
                { field: 'ShipCountry', headerText: 'Ship Country', width: 150 }
            ]
        });
        detail.appendTo(<HTMLElement>e.detailElement.querySelector('.custom-grid'));
    }
});
grid.appendTo('#Grid');

```

{% endtab %}

### Expand by external button

By default, detail rows render in collapsed state. You can expand a detail row by invoking the [`expand`](../api/grid/detailRow/#expand) method using the external button.

{% tab template="grid/detail-template-method", sourceFiles="index.ts,index.html,index.css", es5Template="expand" %}

```typescript
import { Grid, DetailRow } from '@syncfusion/ej2-grids';
import { Button } from '@syncfusion/ej2-buttons';
import { employeeData } from './datasource.ts';

Grid.Inject(DetailRow);

let expandBtn: Button = new Button();
expandBtn.appendTo('#expand');

let grid: Grid = new Grid({
    dataSource: employeeData,
    detailTemplate: '#detailtemplate',
    columns: [
        { field: 'FirstName', headerText: 'First Name', width: 140 },
        { field: 'LastName', headerText: 'Last Name', width: 140 },
        { field: 'Title', headerText: 'Title', width: 150 },
        { field: 'Country', headerText: 'Country', width: 150 }
    ],
    height: 260
});
grid.appendTo('#Grid');

document.getElementById('expand').addEventListener('click', () => {
    let inputElem: HTMLInputElement = (document.getElementsByClassName('rowindex')[0] as HTMLInputElement);
    let rowIndex: number = parseInt(inputElem.value, 10);
    grid.detailRowModule.expand(rowIndex);
});

```

{% endtab %}

> * You can expand all the rows by using [`expandAll`](../api/grid/detailRow/#expandall) method.
> * If you want to expand all the rows at initial Grid rendering, then use [`expandAll`](../api/grid/detailRow/#expandall) method in [`dataBound`](../api/grid/#databound) event of the Grid.

## Drag and drop

The grid row drag and drop allows you to drag and drop grid rows to another grid or custom component. To enable row drag and drop, set the [`allowRowDragAndDrop`](../api/grid/#allowrowdraganddrop) to true.
The target component where the grid rows are to be dropped can be set by using
the [`targetID`](../api/grid/rowDropSettings/#targetid).

To use row drag and drop, inject the **RowDD** module in the grid.

{% tab template="grid/draganddrop",es5Template="dragdrop" %}

```typescript
import { Grid, Page, RowDD, Selection } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Page, RowDD, Selection);

let grid: Grid = new Grid({
    dataSource: data.slice(0, 5),
    allowRowDragAndDrop: true,
    rowDropSettings: { targetID: 'DestGrid' },
    selectionSettings: { type: 'Multiple' },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ]
});
grid.appendTo('#Grid');

let destGrid: Grid = new Grid({
    dataSource: [],
    allowRowDragAndDrop: true,
    rowDropSettings: { targetID: 'Grid' },
    selectionSettings: { type: 'Multiple' },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ]
});
destGrid.appendTo('#DestGrid');

```

{% endtab %}

> * Selection feature must be enabled for row drag and drop.
> * Multiple rows can be selected by clicking and dragging inside the grid.
For multiple row selection, the [`type`](../api/grid/selectionSettings/#type) property must be set to **multiple**.

### Drag and drop events

The following events are triggered while drag and drop the grid rows.

[`rowDragStartHelper`](../api/grid/#rowdragstarthelper) - Triggers when click the drag icon or grid row and this event is used to customize the drag element based on user criteria.<br/>
[`rowDragStart`](../api/grid/#rowdragstart) -Triggers when starts to drag the grid row. <br/>
[`rowDrag`](../api/grid/#rowdrag) - Triggers while dragging the grid row. <br/>
[`rowDrop`](../api/grid/#rowdrop) - Triggers when a drag element is dropped on the target element. <br/>

### Drag and drop the grid rows to custom component

You can drag and drop the grid rows to any custom component. To enable row drag and drop, set the [`allowRowDragAndDrop`](../api/grid/#allowrowdraganddrop) as true and define the custom component id in [`targetID`](../api/grid/rowDropSettings/#targetid) property of rowDropSettings.

In the below example, the selected grid row is dragged and dropped in to the TreeView component by using [`rowDrop`](../api/grid/#rowdrop) event. Once the row is dropped into the TreeView component, we have removed the corresponding grid row from grid and its data inserted in custom component. To know more information about the drag and drop events check [`here`](https://ej2.syncfusion.com/documentation/grid/row/?no-cache=1#drag-and-drop-events).

{% tab template="grid/draganddrop-custom",es5Template="dragdrop-custom" %}

```typescript
import { Grid, Page, RowDD, Selection } from '@syncfusion/ej2-grids';
import { TreeView } from '@syncfusion/ej2-navigations';
import { data } from './datasource.ts';

Grid.Inject(Page, RowDD, Selection);
let hierarchicalData: { [key: string]: Object }[];
let grid: Grid = new Grid({
    dataSource: data.slice(0, 5),
    allowRowDragAndDrop: true,
    rowDropSettings: { targetID: 'tree' },
    selectionSettings: { type: 'Multiple' },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
    rowDrop: function(args:any){
            let currLi: Element = args.target.closest('li');
            let gridData: any = args.data;
            if(currLi !=null && closest(currLi, '.' + 'e-control').classList.contains('e-treeview')){
                if(gridData != null){
                    let grid: any = (<any>document.getElementById('Grid')).ej2_instances[0];
                    let tree: any = (<any>document.getElementById('tree')).ej2_instances[0];
                    for(let i:number = 0, len = gridData.length; i < len; i++){
                        let obj: any = [{ nodeId:gridData[i].OrderID,nodeText:gridData[i].CustomerID }];
                        (grid as any).deleteRow(args.rows[i]);
                        tree.addNodes(obj,currLi);
                    }
                    args.cancel=true;
                }
            }
        }  
});
grid.appendTo('#Grid');

let treeObj: TreeView = new TreeView({
    fields: { dataSource: hierarchicalData, id: 'nodeId', text: 'nodeText',  
            child: 'nodeChild'
        },
    });
    treeObj.appendTo('#tree');

```

{% endtab %}

## Drag and drop within Grid

The grid row drag and drop allows you to drag and drop grid rows on the same grid using drag icon. To enable row drag and drop, set the [`allowRowDragAndDrop`](../api/grid/#allowrowdraganddrop) to true.

{% tab template="grid/draganddrop-single",es5Template="dragdrop" %}

```typescript
import { Grid, RowDD, Selection } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(RowDD, Selection);

let grid: Grid = new Grid({
    dataSource: data,
    allowRowDragAndDrop: true,
    heigth:300,
    selectionSettings: { type: 'Multiple' },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', isPrimaryKey: true, textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ]
});
grid.appendTo('#Grid');

```

{% endtab %}

> * Multiple rows can be drag and drop in the row selections basis.
> * Single row is able to drag and drop in same grid without enable the row selection.
> * Row drag and drop feature is not having built in support with sorting, filtering and grouping features of grid. However we can achieve sorting and filtering behavior by sample side customization which will be explained in the next topic.

### Drag and drop with Sorting and Filtering

In the following demo, you can achieve the grid row drag and drop support with filtering and sorting using [`rowDrop`](../api/grid/rowDragEventArgs) event.

{% tab template="grid/draganddrop-single-filter-sort",es5Template="dragdrop" %}

```typescript
import { Grid, Page, RowDD, Selection, Filter, Sort } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Page, RowDD, Selection, Filter, Sort);

let grid: Grid = new Grid({
    dataSource: data.slice(0, 10),
    allowRowDragAndDrop: true,
    selectionSettings: { type: 'Multiple' },
    height:300,
    allowFiltering:true,
    allowSorting:true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', isPrimaryKey: true, textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
     rowDrop: function (args: any) {
        let gObj: any = (<any>document.getElementById('Grid')).ej2_instances[0];
        let seletedRowIndexes: number[] = gInstance.getSelectedRowIndexes();
        if (gObj.sortSettings.columns.length > 0 || gObj.filterSettings.columns.length > 0) {
            let startedRow: HTMLTableRowElement = args.rows[0];
            let startRowIndex: number = startedRow.rowIndex;
            if (!args.target) {
                return
            }
            let targetRow: HTMLTableRowElement = args.target.closest('tr');
            let targetRowIndex: number = targetRow.rowIndex;
            gInstance.getContentTable().querySelector('tbody').insertBefore(startedRow, targetRow);

            if (!isNullOrUndefined(targetRow.nextElementSibling)) {
                let currentIndex: number = targetRow.rowIndex;
                if (currentIndex <= startedRow.rowIndex) {
                    gObj.getContentTable().querySelector('tbody').insertBefore(startedRow, targetRow);
                } else {
                    gObj.getContentTable().querySelector('tbody').insertBefore(startedRow, targetRow.nextElementSibling);
                }
            } else {
                gObj.getContentTable().querySelector('tbody').insertBefore(targetRow, startedRow);
            }

            let startRowObj: any = gObj.getRowObjectFromUID(startedRow.getAttribute('data-uid'));
            let targetRowObj: any = gObj.getRowObjectFromUID(targetRow.getAttribute('data-uid'))
            for (let i: number = 0, len: number = gObj.currentViewData.length; i < len; i++) {
                let getDataByField = gObj.currentViewData[i];
                if (gObj.sortSettings.columns.length > 0 || gObj.filterSettings.columns.length > 0) {
                    filteredCurrentViewData = gObj.currentViewData;
                    filteredCurrentViewData.splice(targetRowIndex, 0, filteredCurrentViewData.splice(startRowIndex, 1)[0]);
                    gObj.rowDragAndDropModule.removeBorder(targetRow);
                    gObj.contentModule.refreshContentRows();
                    dropSelectedRowIndx.push(targetRowIndex);
                    if (gObj.sortSettings.columns.length > 0) {
                        args.cancel = true;
                    }
                    if (dropSelectedRowIndx.length > 0) {
                        gObj.clearSelection();
                        gObj.selectRows(dropSelectedRowIndx);
                    }
                    return;
                }
            }
        }
    }
  
});
grid.appendTo('#Grid');

```

{% endtab %}

> * You can enable/disable the drag icon by using **disableRowDD** method which is achieved in the [`actionComplete`](../api/grid/actionEventArgs) event.

```typescript
    actionComplete: function (args) {
        if (this.filterSettings.columns.length) {
            this.disableRowDD(true);
        }
        else {
            this.disableRowDD(false);
        }
    }

```

## Row spanning

The grid has option to span row cells. To achieve this, You need to define the [`rowSpan`](../api/grid/queryCellInfoEventArgs/#rowspan) attribute to span cells in the [`QueryCellInfo`](../api/grid/queryCellInfoEventArgs) event.

In the following demo, **Davolio** cell is spanned to two rows in the **EmployeeName** column.

Also Grid supports the spanning of rows and columns for same cells. **Lunch Break** cell is spanned to two rows and three columns in the **1:00** column.

{% tab template="grid/row-spanning", sourceFiles="index.ts,index.html", es5Template="span" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { columnSpanData, ColumnSpanDataType  } from './datasource.ts';

let grid: Grid = new Grid({
            dataSource: columnSpanData,
            queryCellInfo: QueryCellEvent,
            gridLines: 'Both',
            columns: [
                { field: 'EmployeeID', headerText: 'Employee ID', isPrimaryKey: true, textAlign: 'Right', width: 120 },
                { field: 'EmployeeName', headerText: 'Employee Name', width: 200 },
                { field: '9:00', headerText: '9.00 AM', width: 100 },
                { field: '9:30', headerText: '9.30 AM', width: 100 },
                { field: '10:00', headerText: '10.00 AM', width: 100 },
                { field: '10:30', headerText: '10.30 AM', width: 100 },
                { field: '11:00', headerText: '11.00 AM', width: 100 },
                { field: '11:30', headerText: '11.30 AM', width: 100 },
                { field: '12:00', headerText: '12.00 PM', width: 100 },
                { field: '12:30', headerText: '12.30 PM', width: 100 },
                { field: '1:00', headerText: '1.00 PM', width: 120 },
                { field: '1:30', headerText: '1.30 PM', width: 120 },
                { field: '2:00', headerText: '2.00 PM', width: 120 },
                { field: '2:30', headerText: '2.30 PM', width: 120 },
                { field: '3:00', headerText: '3.00 PM', width: 120 },
                { field: '3:30', headerText: '3.30 PM', width: 120 },
                { field: '4:00', headerText: '4.00 PM', width: 100 },
                { field: '4:30', headerText: '4.30 PM', width: 100 },
                { field: '5:00', headerText: '5.00 PM', width: 100 }
            ],
            width: 'auto',
            height: 300,
            allowTextWrap: true
});
grid.appendTo('#Grid');

function QueryCellEvent(args: QueryCellInfoEventArgs): void {
    let data: ColumnSpanDataType = args.data as ColumnSpanDataType;
    // Prevent the spanning in second page
    if (this.pageSettings.currentPage != 2 && (!args.requestType || args.requestType === 'paging')) {
    switch (data.EmployeeID) {
        case 10001:
            if (args.column.field === '9:00' || args.column.field === '2:30' || args.column.field === '4:30') {
                args.colSpan = 2;
            } else if (args.column.field === '11:00') {
                args.colSpan = 3;
            } else if (args.column.field === 'EmployeeName') {
                args.rowSpan = 2;
            } else if (args.column.field === '1:00') {
                args.colSpan = 3;
                args.rowSpan = 2;
            }
            break;
        case 10002:
            if (args.column.field === '9:30' || args.column.field === '2:30' ||
                args.column.field === '4:30') {
                args.colSpan = 3;
            } else if (args.column.field === '11:00') {
                args.colSpan = 4;
            }
            break;
        case 10003:
            if (args.column.field === '9:00' || args.column.field === '11:30') {
                args.colSpan = 3;
            } else if (args.column.field === '10:30' || args.column.field === '3:30' ||
                args.column.field === '4:30' || args.column.field === '2:30') {
                args.colSpan = 2;
            }
            break;
        case 10004:
            if (args.column.field === '9:00') {
                args.colSpan = 3;
            } else if (args.column.field === '11:00') {
                args.colSpan = 4;
            } else if (args.column.field === '4:00' || args.column.field === '2:30') {
                args.colSpan = 2;
            }
            break;
        case 10005:
            if (args.column.field === '9:00') {
                args.colSpan = 4;
            } else if (args.column.field === '11:30') {
                args.colSpan = 3;
            } else if (args.column.field === '3:30' || args.column.field === '4:30' || args.column.field === '2:30') {
                args.colSpan = 2;
            }
            break;
        case 10006:
            if (args.column.field === '9:00' || args.column.field === '4:30' ||
                args.column.field === '2:30' || args.column.field === '3:30') {
                args.colSpan = 2;
            } else if (args.column.field === '10:00' || args.column.field === '11:30') {
                args.colSpan = 3;
            }
            break;
        case 10007:
            if (args.column.field === '9:00' || args.column.field === '3:00' || args.column.field === '10:30') {
                args.colSpan = 2;
            } else if (args.column.field === '11:30' || args.column.field === '4:00') {
                args.colSpan = 3;
            }
            break;
        case 10008:
            if (args.column.field === '9:00' || args.column.field === '10:30' || args.column.field === '2:30') {
                args.colSpan = 3;
            } else if (args.column.field === '4:00') {
                args.colSpan = 2;
            }
            break;
        case 10009:
            if (args.column.field === '9:00' || args.column.field === '11:30') {
                args.colSpan = 3;
            } else if (args.column.field === '4:30' || args.column.field === '2:30') {
                args.colSpan = 2;
            }
            break;
        case 100010:
            if (args.column.field === '9:00' || args.column.field === '2:30' ||
                args.column.field === '4:00' || args.column.field === '11:30') {
                args.colSpan = 3;
            } else if (args.column.field === '10:30') {
                args.colSpan = 2;
            }
            break;
        }
    }
}

```

{% endtab %}

> When paging is enabled in grid, you can disable the rows and columns spanning for any particular page. To achieve this, we need to check **requestType** as paging `<code class='language-text'> string</code>` in [`queryCellInfo`](../api/grid/queryCellInfoEventArgs) event of grid.

## Customize rows

You can customize the appearance of a row by using the [`rowDataBound`](../api/grid/#rowdatabound) event.
The [`rowDataBound`](../api/grid/#rowdatabound) event triggers for every row. In the event handler, you can get the
[`RowDataBoundEventArgs`](../api/grid/rowDataBoundEventArgs) that contains details of the row.

{% tab template="grid/custom-row", sourceFiles="index.ts,index.css,index.html",es5Template="custom" %}

```typescript
import { Grid, RowDataBoundEventArgs } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: data,
    enableHover: false,
    allowSelection: false,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipCity', headerText: 'Ship City', width: 100 },
        { field: 'Freight', headerText: 'Freight', width: 100, format: 'C2' },
        { field: 'ShipName', headerText: 'Ship Name', width: 100 }
    ],
    rowDataBound: rowBound,
    height: 280
});
grid.appendTo('#Grid');

function rowBound(args: RowDataBoundEventArgs) {
    if (args.data['Freight'] < 30) {
        args.row.classList.add('below-30');
    } else if (args.data['Freight'] < 80) {
        args.row.classList.add('below-80');
    } else {
        args.row.classList.add('above-80');
    }
}

```

{% endtab %}

## Styling alternate rows

 You can change the grid's alternative rows' background color by overriding the **.e-altrow** class.

```css
.e-grid .e-altrow {
    background-color: #fafafa;
}
```

Please refer to the following example.

{% tab template="grid/how-to-alt-row", isDefaultActive=true,es5Template="altrow" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: data.slice(0, 8),
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
        { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd' }
    ]
});

grid.appendTo('#Grid');


```

{% endtab %}

## Row height

You can customize the row height of grid rows through the [`rowHeight`](../api/grid/#rowheight) property. The **rowHeight** property
is used to change the row height of entire grid rows.

In the below example, the **rowHeight** is set as '60px'.

{% tab template="grid/custom-row", sourceFiles="index.ts,index.css,index.html",es5Template="height" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { data, RowDataBoundEventArgs } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: data.slice(0, 8),
    columns: [
            { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
            { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
            { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
            { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd' }
    ],
    rowHeight: 60
});

grid.appendTo('#Grid');

```

{% endtab %}

### Customize row height for particular row

Grid row height for particular row can be customized using the [`rowDataBound`](../api/grid/#rowdatabound)
event by setting the **rowHeight** in arguments for each row based on the requirement.

In the below example, the row height for the row with OrderID as '10249' is set as '90px' using the **rowDataBound** event.

{% tab template="grid/custom-row", sourceFiles="index.ts,index.css,index.html",es5Template="particular" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { Query, DataManager } from '@syncfusion/ej2-data';
import { data, RowDataBoundEventArgs } from './datasource.ts';

let gridData: Object = new DataManager(data).executeLocal(new Query().take(8));

let grid: Grid = new Grid({
    dataSource: gridData,
    columns: [
            { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
            { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
            { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
            { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd' }
    ],
    rowDataBound: rowDataBound
});

function rowDataBound(args: RowDataBoundEventArgs) {
    if((args.data as OrderDetails).OrderID === 10249){
        args.rowHeight = 90;
    }
}

interface OrderDetails {
    OrderID ?: number;
}

grid.appendTo('#Grid');

```

{% endtab %}

> * In virtual scrolling mode, it is not applicable to set the **rowHeight** using the **rowDataBound** event.
