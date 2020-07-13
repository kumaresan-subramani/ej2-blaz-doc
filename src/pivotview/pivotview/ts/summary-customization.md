---
title: "Show or hide totals"
component: "Pivot Table"
description: "Show/hide sub-totals and grand totals for the pivot table"
---

# Show or hide totals

## Show or hide grand totals

Allows to show or hide grand totals in rows and columns using the [`showGrandTotals`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#showgrandtotals) property. To hide the grand totals in rows and columns, set the property [`showGrandTotals`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#showgrandtotals) in [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/) to **false**.
End user can also hide grand totals for row or columns separately by setting the property [`showRowGrandTotals`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#showrowgrandtotals) or [`showColumnGrandTotals`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#showcolumngrandtotals) in [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/) to **false** respectively.

> By default, [`showGrandTotals`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#showgrandtotals), [`showRowGrandTotals`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#showrowgrandtotals) and [`showColumnGrandTotals`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#showrowgrandtotals) properties in [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/) are set as **true**.

{% tab template="pivot-table/pivot-table", es5Template="grand-total", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, FieldList } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(FieldList);
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
        filters: [],
        showGrandTotals: false
    },
    showFieldList: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Show or hide sub-totals

Allows to show or hide sub-totals in rows and columns using the [`showSubTotals`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#showsubtotals) property. To hide all the sub-totals in rows and columns, set the property [`showSubTotals`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#showsubtotals) in [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/) to **false**. End user can also hide sub-totals for rows or columns separately by setting the property [`showRowSubTotals`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#showrowsubtotals) or [`showColumnSubTotals`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#showcolumnsubtotals) in [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/) to **false** respectively.

> By default, [`showSubTotals`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#showsubtotals), [`showRowSubTotals`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#showrowsubtotals) and [`showColumnSubTotals`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#showcolumnsubtotals) properties in [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/) are set as **true**.

{% tab template="pivot-table/pivot-table", es5Template="sub-total", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, FieldList } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(FieldList);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        allowLabelFilter: true,
        allowValueFilter: true,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: [],
        showSubTotals: false
    },
    showFieldList: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Show or hide sub-totals for specific fields

Allows to show or hide sub-totals for specific fields in rows and columns using the [`showSubTotals`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#showsubtotals) property. To hide sub-totals for a specific field in row or column axis, set the property [`showSubTotals`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#showsubtotals) in [`rows`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptionsModel/) or [`columns`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptionsModel/) to **false** respectively.

> By default, [`showSubTotals`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#showsubtotals) property in [`rows`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptionsModel/) or [`columns`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptionsModel/) is set as **true**.

{% tab template="pivot-table/pivot-table", es5Template="sub-total-specific", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, FieldList } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(FieldList);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year', showSubTotals: false }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country', showSubTotals: false }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showFieldList: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Show or hide totals using toolbar

It can also be achieved using built-in toolbar options by setting the [`showToolbar`](https://ej2.syncfusion.com/documentation/api/pivotview#showtoolbar) property in pivot table to **true**. Also, include the items **GrandTotal** and **SubTotal** within the [`toolbar`](https://ej2.syncfusion.com/documentation/api/pivotview#toolbar) property in pivot table. End user can now see "Show/Hide Grand totals" and "Show/Hide Sub totals" icons in toolbar UI automatically.

{% tab template="pivot-table/pivot-table", es5Template="summary-toolbar", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, Toolbar, IDataSet } from '@syncfusion/ej2-pivotview';
import { Button } from '@syncfusion/ej2-buttons';
import { pivotData } from './datasource.ts';

PivotView.Inject(Toolbar);
let pivotTableObj: PivotView = new PivotView({
           dataSourceSettings: {
            dataSource: pivotData,
            expandAll: false,
            enableSorting: true,
            drilledMembers: [{ name: 'Country', items: ['France', 'Germany'] }],
            columns: [{ name: 'Year' }],
            rows: [{ name: 'Country' }, { name: 'Products' }],
            values: [{ name: 'Amount', caption: 'Sold Amount' },
            { name: 'Sold', caption: 'Units Sold' }],
            filters: []
        },
        showToolbar:true,
        toolbar:['GrandTotal','SubTotal'],
        height: 350
});

pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}