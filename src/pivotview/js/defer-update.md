---
title: "Defer Layout Update"
component: "Pivot Table"
description: "Defer update allows users to update the pivot table only on demand."
---

# Defer Layout Update

Defer layout update support allows to update the pivot table component only on demand. On enabling this feature, end user can drag-and-drop fields between row, column, value and filter axes, apply sorting and filtering inside the Field List, resulting in change of pivot report alone but not the pivot table values. Once all operations are performed and on clicking the "Apply" button in the Field List, pivot table will start to update with the last modified report. This also helps in bringing better performance in pivot table component rendering.

The field list can be displayed in two different formats to interact with pivot table. They are:

* **In-built Field List (Popup)**: To display the field list icon in pivot table UI to invoke the built-in dialog.
* **Stand-alone Field List (Fixed)**: To display the field list in a static position within a web page.

## In-built Field List (Popup)

To enable deferred updates in the pivot table, set the property [`allowDeferLayoutUpdate`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#allowdeferlayoutupdate) in pivot table as **true**. To make a note, the defer update option can be controlled only via Field List during runtime.

{% tab template="pivot-table/pivot-table", es5Template="defer-update", sourceFiles="index.ts,index.html" %}

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
        filters: []
    },
    allowDeferLayoutUpdate: true,
    showFieldList: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Stand-alone Field List (Fixed)

The field list can be rendered in a static position, anywhere in web page layout, like a separate component. To do so, you need to set [`renderMode`](https://ej2.syncfusion.com/javascript/documentation/api/pivotfieldlist/#rendermode) property to **Fixed** in [`pivotFieldList`](https://ej2.syncfusion.com/javascript/documentation/api/pivotfieldlist/).

To enable deferred updates in the static fieldlist, set the property [`allowDeferLayoutUpdate`](https://ej2.syncfusion.com/javascript/documentation/api/pivotfieldlist/#allowdeferlayoutupdate) in [`pivotFieldlist`](https://ej2.syncfusion.com/javascript/documentation/api/pivotfieldlist/) as **true**. To make a note, the defer update option can be controlled only via Field List during runtime.

> To make field list interact with pivot table, you need to use the **updateView** and **update** methods for data source update in both field list and pivot table simultaneously.

{% tab template="pivot-table/field-list", es5Template="defer-update-static", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, PivotFieldList } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
    allowDeferLayoutUpdate: true,
    enginePopulated: () => {
        if (fieldlistObj) {
            fieldlistObj.update(pivotTableObj);
        }
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');
let fieldlistObj: PivotFieldList = new PivotFieldList({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        allowLabelFilter: true,
        allowValueFilter: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    allowDeferLayoutUpdate: true,
    renderMode: 'Fixed',
    enginePopulated: (): void => {
        if (fieldlistObj.isRequiredUpdate) {
            fieldlistObj.updateView(pivotTableObj);
        }
        pivotTableObj.notify('ui-update', pivotTableObj);
        fieldlistObj.notify('tree-view-update', fieldlistObj);
    }
});
fieldlistObj.appendTo('#Static_FieldList');

```

{% endtab %}