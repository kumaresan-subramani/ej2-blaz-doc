---
title: "CSS Customization"
component: "Pivot Table"
description: "CSS Customization allows user to hide axis for the pivot by overriding the styles."
---

# CSS Customization

## Hiding Axis

The visibility of row, column, value and filter axis in Field List and Grouping Bar can be changed using custom CSS setting. To do so, please refer the code sample below:

```html
#PivotTable .e-group-columns {
  display: none;
}
#PivotTable .e-group-filters {
  height: 71px !important;
}

#PivotTable_PivotFieldList_Wrapper .e-field-list-columns{
  display: none;
}
#PivotTable_PivotFieldList_Wrapper .e-field-list-values{
  margin-top: 0px;
  height: 338px;
}
```

{% tab template="pivot-table/css", es5Template="css", sourceFiles="index.ts,index.html,index.css" %}

```typescript
import { PivotView, IDataSet, GroupingBar, FieldList } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar,FieldList);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    showFieldList: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Text Alignment

The alignment of text inside row headers, column headers, value cells and summary cells can be changed using custom CSS setting. To do so, please refer the code sample below:

```html

.e-pivotview .e-valuescontent {
  text-align: center !important;
}

```

{% tab template="pivot-table/css", es5Template="css", sourceFiles="index.ts,index.html,index.css" %}

```typescript
import { PivotView, IDataSet, GroupingBar, FieldList } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar,FieldList);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    showFieldList: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Customize header, value and summary cell style

The elements in pivot table like header cell, value cell and summary cell style can be customized using built-in CSS names. To do so, please refer the code sample below:

{% tab template="pivot-table/pivottable-css", es5Template="pivottable-css", sourceFiles="index.ts,index.html,index.css" %}

```typescript
import { PivotView, IDataSet, GroupingBar, FieldList } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar,FieldList);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    showFieldList: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}