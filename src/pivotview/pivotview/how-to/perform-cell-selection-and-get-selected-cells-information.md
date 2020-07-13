# Perform cell selection and get selected cells information

To select any cell or row using mouse or arrow keys, set the `gridSettings.allowSelection` property to true. The selected cells will be highlighted.

## Selection mode

The Pivot Table control supports the following four types of selection modes, which can be set by using the `gridSettings.selectionSettings.mode` property:

* **`Row`**: The `Row` value is set by default, and allows you to select only rows.
* **`Column`**: Allows you to select only columns.
* **`Cell`**: Allows you to select only cells.
* **`Both`**: Allows you to select rows and columns at the same time.

## Selection type

It supports two types of selection that can be set by the property `gridSettings.selectionSettings.type`. They are,

* **`Single`**: The `Single` value is set by default, and it only allows selection of a single row or a column or a cell.
* **`Multiple`**: Allows you to select multiple rows or cells.
To perform the multi-selection, press and hold CTRL key and click the desired rows or columns or cells. To select range of rows or cells, press and hold the SHIFT key and click the rows or columns or cells.

## Event

The event `cellSelected` fires on every cell/row/column on selected/deselected operations and it provides the selected cells information with its corresponding column and row headers.

{% tab template="pivot-table/pivot-table", es5Template="pivot-selection", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, PivotCellSelectedEventArgs } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    gridSettings: {
        allowSelection: true,
        selectionSettings: { mode: 'Both', type: 'Multiple' }
    },
    cellSelected: (args: PivotCellSelectedEventArgs) => {
        //args.selectedCellsInfo -> get selected cells information.
        //args.pivotValues -> get the pivot values of the pivot table.
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}
