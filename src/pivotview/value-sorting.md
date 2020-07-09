---
title: "Value Sorting"
component: "Pivot Table"
description: "Value sorting allows user to sort individual column based on the measure values."
---

# Value sorting

Value sorting allows you to sort individual column based on it's values either in ascending or descending order. It can been enabled by setting the `enableValueSorting` property to **true**. You can sort the column values by clicking the column header.

Value sorting can be configured using the `valueSortSettings` option through code behind. The settings required to sort value fields at initial rendering are:
* `headerText`: It allows to set the column header names with delimiters, that is used for value sorting.
* `headerDelimiter`: It allows to set the delimiters string to separate the given header text.
* `sortOrder`: It allows to set the sort direction of the value field.

{% tab template="pivot-table/pivot-table", es5Template="value-sorting", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        valueSortSettings: {
            headerText: 'FY 2015##Sold Amount',
            headerDelimiter: '##',
            sortOrder: 'Descending'
        },
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        filters: [],
    },
    enableValueSorting: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## See Also

* [Sorting](./sorting)