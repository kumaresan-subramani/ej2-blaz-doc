---
title: "State Persistence"
component: "Pivot Table"
description: "Describes about persistence in pivot table"
---

# State Persistence

State persistence allows user to maintain the current state of the component along with its report bounded in the browser local storage (cookie). Even if the browser is refreshed or if you move to the next page within the browser, components state will be persisted. State persistence stores the Pivot Table object in the local storage when [`enablePersistence`](https://ej2.syncfusion.com/documentation/api/pivotview#enablepersistence) property in pivot table is set to **true**.

{% tab template="pivot-table/state-persistence", es5Template="state-persistence", sourceFiles="index.ts,index.html" %}

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
        filters: [],
    },
    enablePersistence: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

# Save and Load Pivot Layout

You can save the current layout of the pivot table by using `getPersistData` in string format. The saved layout can be loaded to pivot table any time by passing the saved data as a parameter to `loadPersistData` method in the pivot table.

{% tab template="pivot-table/state-persistence", es5Template="save-load", sourceFiles="index.ts,code-behind.html" %}

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
        filters: [],
    },
    enablePersistence: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}