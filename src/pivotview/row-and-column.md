---
title: "Row and Column"
component: "Pivot Table"
description: "Miscellaneous aspects of customizing the pivot table."
---

<!-- markdownlint-disable MD012 -->

# Row and Column

## Width and Height

Allows end user to set the pivot table's height and width by using [`height`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#height) and [`width`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#width) properties in pivot table respectively. The supported formats to set [`Height`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#height) and [`Width`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#width) properties are,

* Pixel: For example - 100, 200, "100px", "200px".
* Percentage: For example - "100%", "200%".
* Auto: It is applicable for [`Height`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#height) property alone in-order to render the pivot table beyond its parent container height without vertical scrollbar. The parent container here would show its vertical scrollbar as soon as the component reaches beyond its dimension.

> The pivot table will not be displayed less than **400px**, since it's the minimum width of the component.

{% tab template="pivot-table/pivot-table", es5Template="scroll", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    height: '340px',
    width: 550,
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Row Height

Allows end user to set the height of each pivot table rows commonly using the [`rowHeight`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/gridSettings/#rowheight) property in [`gridSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/gridSettings/).

> By default, the [`rowHeight`](https://ej2.syncfusion.com/documentation/api/pivotview/gridSettings/#rowheight) property is set as **36** pixels for desktop layout and **48** pixels for mobile layout.
> The height of the column headers alone may vary when grouping bar feature is enabled.

In the below code sample, the [`rowHeight`](https://ej2.syncfusion.com/documentation/api/pivotview/gridSettings/#rowheight) property is set as **60** pixels.

{% tab template="pivot-table/pivot-table", es5Template="row-height", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    height: 350,
    gridSettings: {
        rowHeight: 60
    }
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Column Width

Allows end user to set the width of each pivot table columns commonly using the [`ColumnWidth`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/gridSettings/#columnwidth) property in [`gridSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/gridSettings/).

> By default, the [`columnWidth`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/gridSettings/#columnwidth) property is set as **110** pixels to each columns except the first column. For first column, **250** pixels and **200** pixels are set respectively with and without grouping bar.

In the below example, the [`columnWidth`](https://ej2.syncfusion.com/documentation/api/pivotview/gridSettings/#columnwidth) property is set as **120** pixels.

{% tab template="pivot-table/pivot-table", es5Template="column-width", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    gridSettings: {
        columnWidth: 120
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Reorder

Allows end user to reorder a particular column header from one index to another index within the pivot table through drag-and-drop option. It can be enabled by setting the [`allowReordering`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/gridSettings/#allowreordering) property in [`gridSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/gridSettings/) to **true**.

{% tab template="pivot-table/pivot-table", es5Template="re-order", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    gridSettings: {
        allowReordering: true
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');
```

{% endtab %}

## Column Resizing

Allows end user to resize the columns by clicking and dragging the right edge of the column header. While dragging, the width of the respective column will be resized immediately. To enable column resizing option, set the [`allowResizing`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/gridSettings/#allowresizing) property in [`gridSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/gridSettings/) to **true**.

> By default, the column resizing option is enabled.
> In RTL mode, user can click and drag the left edge of the header cell to resize the column.

{% tab template="pivot-table/pivot-table", es5Template="column-resizing", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    gridSettings: {
        allowResizing: true
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');
```

{% endtab %}

## Text Wrap

Allows end user to wrap the cell content to the next line when it exceeds the boundary of the cell width. To enable text wrap, set the [`allowTextWrap`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/gridSettings/#allowtextwrap) property in [`gridSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/gridSettings/) to **true**.

{% tab template="pivot-table/pivot-table", es5Template="auto-wrap", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    gridSettings: {
        allowTextWrap: true
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');
```

{% endtab %}

## Grid Lines

Allows end user to display cell border for each cells using [`gridLines`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/gridSettings/#gridlines) property in [`gridSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/gridSettings/).

Available mode of grid lines are:

| Modes | Actions |
|-------|---------|
| Both | Displays both the horizontal and vertical grid lines.|
| None | No grid lines are displayed.|
| Horizontal | Displays the horizontal grid lines only.|
| Vertical | Displays the vertical grid lines only.|
| Default | Displays grid lines based on the theme.|

> By default, pivot table renders grid lines in **Both** mode.

{% tab template="pivot-table/pivot-table", es5Template="grid-lines", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
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
        gridLines: 'Vertical'
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');
```

{% endtab %}

## Selection

Selection provides an option to highlight a row or a column or a cell. It can be done through simple mouse down or arrow keys. To enable selection in the pivot table, set the [`allowSelection`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/gridSettings/#allowselection) property in [`gridSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/gridSettings/) to **true**.

The pivot table supports two types of selection that can be set using [`type`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotSelectionSettings/#type) property in [`selectionSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotSelectionSettings/). The selection types are:

* **`Single`**: It is set by default, and it only allows selection of a single row or a column or a cell.
* **`Multiple`**: Allows you to select multiple rows or columns or cells.
To perform multi-selection, press and hold "CTRL" key and click the desired rows or cells. To select range of rows or cells, press and hold the "SHIFT" key and click the rows or columns or cells.

{% tab template="pivot-table/pivot-table", es5Template="selection", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    gridSettings: {
        allowSelection: true,
        selectionSettings: { type: 'Multiple' }
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');
```

{% endtab %}

### Selection Mode

The pivot table supports four types of selection mode that can be set using [`mode`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotSelectionSettings/#mode) in [`selectionSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotSelectionSettings/). The selection modes are:

* **`Row`**:It is set by default, and allows user to select only rows.
* **`Column`**: Allows you to select only columns.
* **`Cell`**: Allows you to select only cells.
* **`Both`**: Allows you to select rows and columns at the same time.

{% tab template="pivot-table/pivot-table", es5Template="selection-mode", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    gridSettings: {
        allowSelection: true,
        selectionSettings: { mode: 'Both' }
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');
```

{% endtab %}

### Cell Selection Mode

The pivot table supports two types of cell selection mode that can be set using [`cellSelectionMode`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotSelectionSettings/#cellselectionmode) in [`selectionSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotSelectionSettings/). The cell selection modes are:

* **`Flow`**: The `Flow` value is set by default. The range of cells are selected between the start index and end index that includes in between cells of rows.
* **`Box`**: Range of cells are selected from the start and end column indexes that includes in between cells of rows within the range.

{% tab template="pivot-table/pivot-table", es5Template="cell-selection", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    gridSettings: {
        allowSelection: true,
        selectionSettings: { cellSelectionMode: 'Box', type: 'Multiple', mode: 'Cell' }
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');
```

{% endtab %}

> Cell selection requires `selectionSettings.mode` property to be `Cell` or `Both`, and `selectionSettings.type` property should be `Multiple`.

### Event

The event `cellSelected` is triggered when cell selection gets completed. It provides selected cells information with its corresponding column and row headers. It has following parameters - `selectedCellsInfo`, `currentCell` and `target`. This event allows user to view selected cells information and user can pass those selected cells information to any external component for data binding.

{% tab template="pivot-table/pivot-table", es5Template="cell-selection-event", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    gridSettings: {
        allowSelection: true,
        selectionSettings: { cellSelectionMode: 'Box', type: 'Multiple', mode: 'Cell' }
    },
    cellSelected: (args: PivotCellSelectedEventArgs) => {
        //args.SelectedCellsInfo -> get selected cells information
    }
    height: 350
});
pivotTableObj.appendTo('#PivotTable');
```

{% endtab %}

## Clip Mode

The clip mode provides options to display its overflow cell content in the pivot table. It can be configured using the [`clipMode`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/gridSettings/#clipmode) property in [`gridSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/gridSettings/). The pivot table supports three types of clip modes which are:

* **`Clip`**: Truncates the cell content when it overflows its area.
* **`Ellipsis`**: Displays ellipsis when the cell content overflows its area.
* **`EllipsisWithTooltip`**: Displays ellipsis when the cell content overflows its area, also it will display the tooltip while hover on ellipsis is applied.

>By default, `clipMode` value is set to `Ellipsis`.

{% tab template="pivot-table/pivot-table", es5Template="clip-mode", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    gridSettings: {
        clipMode: 'Clip'
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');
```

{% endtab %}

## Cell Template

User can customize the pivot table cell element by using the `cellTemplate` property in pivot table. The `cellTemplate` property accepts either an HTML string or the element's ID, which can be used to append additional HTML elements to showcase each cell with custom format.

