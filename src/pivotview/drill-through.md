---
title: "Drill Through"
component: "Pivot Table"
description: "Drill Through allows to view the detailed data of the summarized cell."
---

# Drill Through

Allows to view the underlying raw data of a summarized cell in the pivot table. It can be enabled by setting the [`allowDrillThrough`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#allowdrillthrough) property to **true**. By double-clicking on any value cell, user can view the detailed raw data in a data grid inside a new window. In the new window, row header, column header and measure name of the clicked cell will be shown at the top. Also, user can include or exclude fields available in the data grid using column chooser option.

To use drill-through feature, You need to inject the `DrillThrough` module in pivot table.

{% tab template="pivot-table/pivot-table", es5Template="drill-through", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, DrillThrough } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(DrillThrough);
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
    allowDrillThrough: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}
