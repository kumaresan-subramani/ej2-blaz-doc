---
title: "Sorting"
component: "Pivot Table"
description: "Sorting allows user to order the field headers either in ascending or descending."
---

# Sorting

## Member Sorting

Allows to order field members in rows and columns either in ascending or descending order. By default, field members in rows and columns are in ascending order.

Member sorting can be enabled by setting the [`enableSorting`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#enablesorting) property in [`dataSourceSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/) to **true**. After enabling this API, click the sort icon besides each field in row or column axis, available in field list or grouping bar UI for re-arranging members either in ascending or descending order.

> By default the [`enableSorting`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#enablesorting) property in [`dataSourceSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/) set as **true**. If we set it as **false**, then the field members arrange in pivot table as its data source order. And, the sort icons in grouping bar and field list buttons will be removed.

![output](images/sorting_fl.png "Member sorting icon in field list")
<br/>
![output](images/sorting_gb.png "Member sorting icon in grouping bar")
<br/>
![output](images/sorting_grid.png "Resultant pivot table on member sort")

Member sorting can also be configured using the [`sortSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/sort/) through code behind, during initial rendering. The settings required to sort are:

* [`name`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/sort/#name): It allows to set the field name.
* [`order`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/sort/#order): It allows to set the sort direction either to ascending or descending of the respective field.

> By default the [`order`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/sort/#order) property in the [`sortSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/sort/) set as **Ascending**. Meanwhile, we can arrange the field members as its order in data source by setting it as **None** where the sort icons in grouping bar and field list buttons for the corresponding field will be removed.

{% tab template="pivot-table/pivot-table", es5Template="sorting", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        sortSettings: [{ name: 'Country', order: 'Descending' }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        filters: []
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Value sorting

> This property is applicable only for the relational data source.

Allows to sort individual value field and its aggregated values either in row or column axis in both ascending and descending order. It can been enabled by setting the [`enableValueSorting`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#enablevaluesorting) property in pivot table to **true**. On enabling, end user can sort the values by directly clicking the value field header positioned either in row or column axis of the pivot table component.

The value sorting can also be configured using the [`valueSortSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/valueSortSettings/) option through code behind. The settings required to sort value fields are:

* [`headerText`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/valueSortSettings/#headertext): It allows to set the header names with delimiters, that is used for value sorting. The header names are arranged from Level 1 to Level N, down the hierarchy with a delimiter for better specification.
* [`headerDelimiter`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/valueSortSettings/#headerdelimiter): It allows to set the delimiters string to separate the header text between levels.
* [`sortOrder`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/valueSortSettings/#sortorder): It allows to set the sort direction of the value field.

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