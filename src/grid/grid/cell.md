---
title: "Cell"
component: "Grid"
description: "Learn how to customize the Essential JS 2 DataGrid cells with styling, text wrapping, adding custom attributes and tooltips."
---

# Cell

## Displaying the HTML content

The HTML tags can be displayed in the Grid header and content by enabling the [`disableHtmlEncode`](../api/grid/column/#disablehtmlencode) property.

{% tab template="grid/cell-html", sourceFiles="index.ts,index.html,datasource.ts",es5Template="htmlcontent" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
        { field: 'OrderID', headerText: '<span> Order ID </span>', disableHtmlEncode: true, textAlign: 'Right', width: 140 },
        { field: 'CustomerID', headerText: '<span> Customer ID </span>', disableHtmlEncode: false, width: 120 },
        { field: 'OrderDate', headerText: 'Order Date', width: 100, format: 'yMd' },
        { field: 'ShipCity', headerText: 'Ship City', width: 100 },
    ],
    height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}

## Customize cell styles

The appearance of cells can be customized by using the [`queryCellInfo`](../api/grid/#querycellinfo) event.
The [`queryCellInfo`](../api/grid/#querycellinfo) event triggers for every cell. In that event handler, you can get
[`QueryCellInfoEventArgs`](../api/grid/queryCellInfoEventArgs) that contains the details of the cell.

{% tab template="grid/custom-cell", sourceFiles="index.ts,index.html,index.css",es5Template="customcell" %}

```typescript
import { Grid, QueryCellInfoEventArgs } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: data,
    enableHover: false,
    allowSelection: false,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'OrderDate', headerText: 'Order Date', width: 100, format: 'yMd'},
        { field: 'Freight', headerText: 'Freight', width: 100, format: 'C2'},
        { field: 'ShipCity', headerText: 'Ship City', width: 100 },
    ],
    height: 315,
    queryCellInfo: customiseCell
});
grid.appendTo('#Grid');

function customiseCell(args: QueryCellInfoEventArgs) {
    if(args.column.field === 'Freight') {
        if (args.data['Freight'] < 30){
            args.cell.classList.add('below-30');
        } else if(args.data['Freight'] < 80 ) {
            args.cell.classList.add('below-80');
        } else {
            args.cell.classList.add('above-80');
        }
    }
}

```

{% endtab %}

## Auto wrap

The auto wrap allows the cell content of the grid to wrap to the next line when it exceeds the boundary of the cell width. The Cell Content wrapping works based on the position of white space between words.
To enable auto wrap, set the [`allowTextWrap`](../api/grid/#allowtextwrap) property to `true`.
You can configure the auto wrap mode by setting the [`textWrapSettings.wrapMode`](../api/grid/textWrapSettings) property.

There are three types of [`wrapMode`](../api/grid/textWrapSettings/#wrapmode). They are:

* **Both**: **Both** value is set by default. Auto wrap will be enabled for both the content and the header.
* **Header**: Auto wrap will be enabled only for the header.
* **Content**: Auto wrap will be enabled only for the content.

Note: When a column width is not specified, then auto wrap of columns will be adjusted with respect to the grid's width.

In the following example, the [`textWrapSettings.wrapMode`](../api/grid/textWrapSettings/#wrapmode) is set to **Content**.

{% tab template="grid/autowrap", es5Template="autowrap" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: data,
    gridLines: 'Default',
    allowTextWrap: true,
    textWrapSettings: { wrapMode: 'Content' },
    columns: [
        { field: 'RoolNo', headerText: 'Rool No', width: 120 },
        { field: 'Name', headerText: 'Name of the inventor', width: 100 },
        { field: 'patentfamilies', headerText: 'No of patentfamilies', width: 100 },
        { field: 'Country', headerText: 'country', width: 130 },
        { field: 'mainfields', headerText: 'Main fields of Invention', width: 150 },
    ],
    height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}

## Custom Attributes

You can customize the grid cells by adding a CSS class to the [`customAttribute`](../api/grid/column#customattributes) property of the column.

```CSS
.e-attr {
    background: '#d7f0f4';
}
```

```typescript
{
    field: "ShipCity", headerText: "Ship City", customAttributes: {class: "e-attr"}, width: "120"
}
```

In the below example, we have customized the cells of **OrderID** and **ShipCity** columns.

{% tab template="grid/custom-attribute", es5Template="cellstyle" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', customAttributes: {class: "e-attr"}, textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipCity', headerText: 'Ship City', customAttributes: {class: "e-attr"}, width: 100 },
        { field: 'ShipName', headerText: 'Ship Name', width: 100 }
    ],
    height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}

## Grid Lines

The [`gridLines`](../api/grid/#gridlines) have option to display cell border and it can be defined by the
[`gridLines`](../api/grid/#gridlines) property.

The available modes of grid lines are:

| Modes | Actions |
|-------|---------|
| Both | Displays both the horizontal and vertical grid lines.|
| None | No grid lines are displayed.|
| Horizontal | Displays the horizontal grid lines only.|
| Vertical | Displays the vertical grid lines only.|
| Default | Displays grid lines based on the theme.|

{% tab template="grid/row-template", es5Template="gridlines" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: data,
    gridLines: 'Both',
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipCity', headerText: 'Ship City', width: 100 },
        { field: 'ShipName', headerText: 'Ship Name', width: 100 }
    ],
    height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}

>By default, the grid renders with **Default** mode.

## Clip Mode

The clip mode provides options to display its overflow cell content and it can be defined by the [`columns.clipMode`](../api/grid/column/#clipmode) property.

There are three types of [`clipMode`](../api/grid/column/#clipmode). They are:

* **Clip**: Truncates the cell content when it overflows its area.
* **Ellipsis**: Displays ellipsis when the cell content overflows its area.
* **EllipsisWithTooltip**: Displays ellipsis when the cell content overflows its area, also it will display the tooltip while hover on ellipsis is applied.

{% tab template="grid/clipmode", es5Template="clipmode" %}

```typescript
import { Grid, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Page);

let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    columns: [
        { field: 'RoolNo', headerText: 'Rool No', width: 100 },
        { field: 'Name', headerText: 'Name of the inventor', clipMode: 'Clip', width: 100 },
        { field: 'patentfamilies', headerText: 'No of patent families', clipMode: 'Ellipsis', width: 100 },
        { field: 'Country', headerText: 'Country', width: 80 },
        { field: 'mainfields', headerText: 'Main fields of Invention', clipMode: 'EllipsisWithTooltip', width: 100 },
    ]
});
grid.appendTo('#Grid');

```

{% endtab %}

>By default, [`columns.clipMode`](../api/grid/column/#clipmode) value is **Ellipsis**.
