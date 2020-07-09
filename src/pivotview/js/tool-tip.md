---
title: "Tooltip"
component: "Pivot Table"
description: "Describes about enabling and disabling tooltip in pivot table"
---

# Tooltip

The tooltip can be enabled or disabled by setting the [`showTooltip`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/#showtooltip) property to **true**. By default, tooltip is enabled in the pivot table.

{% tab template="pivot-table/pivot-table", es5Template="tooltip", sourceFiles="index.ts,index.html" %}

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
    showTooltip: false,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Tooltip Template

User can design their own tooltip by setting the property [`tooltipTemplate`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#tooltiptemplate) with own HTML elements. The property accepts both HTML string and ID attribute. The following place holders are available to display its dynamic values inside the HTML elements.

`${rowHeaders}` – Row headers of the selected value cell.

`${columnHeaders}`  – Column headers of the selected value cell.

`${rowFields}` – Row fields of the selected value cell.

`${columnFields}` – Column fields of the selected value cell.

`${valueField}` – Field name of the selected value cell.

`${aggregateType}` – Aggregate type of the selected value cell.

`${value}` - Formatted value of the selected value cell.

The tooltip customization is common for both pivot table and pivot chart or it can be done individually as well. To customize the pivot table tooltip, the above procedure needs to be followed. To customize the pivot chart tooltip alone use `template` property of tooltip under [`chartSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/chartSettings).

In the below sample, the pivot table and pivot chart shows customized tooltip layouts.

{% tab template="pivot-table/tooltip-template", es5Template="tooltip-template", sourceFiles="index.ts,index.html" %}

```typescript

import {
    PivotView, Toolbar, IDataSet
} from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';
PivotView.Inject(Toolbar)
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        filters: []
    },
    height: 350,
    displayOption: { view: 'Both' },
    chartSettings: {
        value: 'Amount',chartSeries: { type: 'Column', animation: { enable: false } },
        tooltip: { template:'<span class="wrap">${aggregateType} of ${valueField}: ${value}</span>' }
    },
    toolbar: ['Grid', 'Chart'],
    showToolbar: true,
    tooltipTemplate: "#Template"
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}