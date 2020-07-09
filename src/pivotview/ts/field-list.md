---
title: "Field List"
component: "Pivot Table"
description: "Field list allows the user to add or remove fields and also re-arrange them between different axes."
---

# Field List

The pivot table provides a built-in Field List similar to Microsoft Excel. It allows to add or remove fields and also rearrange them between different axes, including column, row, value, and filter along with sort and filter options dynamically at runtime.

The field list can be displayed in two different formats to interact with pivot table. They are:

* **In-built Field List (Popup)**: To display the field list icon in pivot table UI to invoke the built-in dialog.
* **Stand-alone Field List (Fixed)**: To display the field list in a static position within a web page.

## In-built Field List (Popup)

To enable the field list in pivot table UI, set the [`showFieldList`](https://ej2.syncfusion.com/documentation/api/pivotview/#showfieldlist) property in pivot table to **true**. A small icon will appear on the top left corner of the pivot table and clicking on this icon, field list dialog will appear.

> The field list icon will be displayed at the top right corner of the pivot table, when grouping bar is enabled.

To use field list, you need to inject the `FieldList` module in pivot table.

{% tab template="pivot-table/pivot-table", es5Template="fieldlist", sourceFiles="index.ts,index.html" %}

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
    showFieldList: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Stand-alone Field List (Fixed)

The field list can be rendered in a static position, anywhere in web page layout, like a separate component. To do so, you need to set [`renderMode`](https://ej2.syncfusion.com/documentation/api/pivotfieldlist/#rendermode) property to **Fixed** in [`pivotFieldList`](https://ej2.syncfusion.com/documentation/api/pivotfieldlist/).

> To make field list interact with pivot table, you need to use the [**updateView**](https://ej2.syncfusion.com/documentation/api/pivotfieldlist/#updateview) and [**update**](https://ej2.syncfusion.com/documentation/api/pivotfieldlist/#update) methods for data source update in both field list and pivot table simultaneously.

{% tab template="pivot-table/field-list", es5Template="static-fieldlist", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, PivotFieldList } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
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
    renderMode: 'Fixed',
    enginePopulated: (): void => {
        fieldlistObj.updateView(pivotTableObj);
    }
});
fieldlistObj.appendTo('#Static_FieldList');

```

{% endtab %}

## Add or remove fields

Using check box besides each field, end user can select or unselect to add or remove fields respectively from the report at runtime.

![output](images/fieldlist_treeview.png)

## Remove specific field(s) from displaying

When a data source is bound to the component, fields will be automatically populated inside the Field List. In such case, user can also restrict specific field(s) from displaying. To do so, set the appropriate field name(s) in [`excludeFields`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#excludefields) property belonging to [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/).

{% tab template="pivot-table/pivot-table", es5Template="exclude-fields", sourceFiles="index.ts,index.html" %}

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
        columns: [{ name: 'Year', caption: 'Production Year' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: [],
        excludeFields:['Quarter']
    },
    showFieldList: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Re-arranging fields

In-order to re-arrange, drag any field from the field list and drop it into the column, row, value, or filter axis using the drag-and-drop holder. It helps end user to alter the report at runtime.

![output](images/fieldlist_axes.png)

## Filtering members

Using the filter icon besides each field in row, column and filter axes, members can be either included or excluded at runtime. To know more about member filtering, [`refer`](./filtering) here.

![output](images/fieldlist_filtericon.png "Filter icon besides each field")
<br/>
![output](images/fieldlist_editor.png "Filter dialog to either include or exclude members")
<br/>
![output](images/fieldlist_filteringgrid.png "Resultant pivot table on filtering members")

## Sorting members

Using the sort icon besides each field in row and column axes, members can be arranged either in ascending or descending order at runtime. To know more about member sorting, [`refer`](./sorting) here.

![output](images/fieldlist_sorticon.png "Sort icon besides each field")
<br/>
![output](images/fieldlist_sortgrid.png "Resultant pivot table showing countries in descending order")

## Calculated fields

The calculated field support allows end user to add a new calculated field based on the available fields from the bound data source using basic arithmetic operators. To enable this support in Field List UI, set the [`allowCalculatedField`](https://ej2.syncfusion.com/documentation/api/pivotview/#allowcalculatedfield) property to **true** in pivot table. Now a button will be seen automatically inside the field list UI which will invoke the calculated field dialog on click. To know more about calculated field, [`refer`](./calculated-field) here.

![output](images/gs_calc_button.png "Enabling calculated field in field list UI")
<br/>
![output](images/gs_calc_dialog.png "Creating new calculated field")
<br/>
![output](images/gs_calc_grid.png "New calculated field 'Total Amount' added in pivot table")

## Changing aggregation type of value fields at runtime

End user can perform calculations over a group of values using the aggregation option. The value fields bound to the field list, appears with a dropdown icon, helps to select an appropriate aggregation type at runtime. On selection, the values in the Pivot Table will be changed dynamically. To know more about aggregation, [`refer`](./aggregation) here.

![output](images/aggregation_fl_icon.png "Icon to change aggregation type")
<br/>
<br/>
![output](images/fieldlist_aggregation_avg.png "List of pre-defined aggregation types")
<br/>
![output](images/fieldlist_aggregation_grid.png "Resultant pivot table showing average aggregation type applied in 'Unit Sold' value field")

## Defer layout update

Defer layout update support to update the pivot table only on demand and not during every user action. To enable this support in Field List UI, set the [`allowDeferLayoutUpdate`](https://ej2.syncfusion.com/documentation/api/pivotview/#allowdeferlayoutupdate) property to **true** in pivot table. Now a check box inside Field List UI will be seen in checked state, allowing pivot table to update only on demand. To know more about defer layout, [`refer`](./defer-update) here.

![output](images/fieldlist_deferupdate.png)

## Show field list using toolbar

It can also be viewed in toolbar by setting [`showFieldList`](https://ej2.syncfusion.com/documentation/api/pivotview/#allowdeferlayoutupdate) and [`showToolbar`](https://ej2.syncfusion.com/documentation/api/pivotview/#allowdeferlayoutupdate) properties in pivot table to **true**. Also, include the item **FieldList** within the [`toolbar`](https://ej2.syncfusion.com/documentation/api/pivotview/#allowdeferlayoutupdate) property in pivot table. When toolbar is enabled, field list icon will be automatically added into the toolbar and the icon won't appear on top left corner in the pivot table component.

{% tab template="pivot-table/pivot-table", es5Template="toolbar-fieldlist", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, FieldList, Toolbar } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(FieldList,Toolbar);
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
    showToolbar: true,
    toolbar:['FieldList'],
    showFieldList: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Invoking dynamic Field List (Customized)

Also, you can display the field list dialog independently through other means. For example, you can invoke the field list dialog on an external button click. To do so, set `renderMode` property to `Popup` and  since on button click, field list dialog will be invoked.

> * Meanwhile, you can display the field list dialog over specific target element within a webpage using `target` property. By default, the `target` value is "null", which by default refers the `document.body` element.
> * To make field list interact with pivot table, you need to use the **updateView** and **update** methods for data source update in both field list and pivot table simultaneously.

The below sample code illustrates the field list dialog invoked on an external button click.

{% tab template="pivot-table/popup", es5Template="popup-fieldlist", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, PivotFieldList } from '@syncfusion/ej2-pivotview';
import { Button } from '@syncfusion/ej2-buttons';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
    enginePopulated: () => {
        if (fieldlistObj) {
            fieldlistObj.update(pivotTableObj);
        }
    },
    height: 320
});
pivotTableObj.appendTo('#PivotTable');
let fieldlistObj: PivotFieldList = new PivotFieldList({
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
    renderMode: 'Popup',
    target: '#PivotFieldList',
    enginePopulated: (): void => {
        fieldlistObj.updateView(pivotTableObj);
    }
});
fieldlistObj.appendTo('#PivotFieldList');

let fieldListBtn: Button = new Button({ isPrimary: true });
fieldListBtn.appendTo('#fieldlistbtn');

document.getElementById('fieldlistbtn').onclick = function () {
    fieldlistObj.dialogRenderer.fieldListDialog.show();
};

```

{% endtab %}

## Set caption to fields which isn’t bound to the report

One can set the caption to all fields from the data source even if it is not bound to the actual report. It can be achieved using the [`enginePopulated`](https://ej2.syncfusion.com/javascript/documentation/api/pivotfieldlist#enginepopulated) event. On doing so, caption of the respective field will be displayed in both grouping bar and field list.

In the sample, we have set caption to the fields `Year` and `Quarter` dynamically.

{% tab template="pivot-table/popup-field-list", es5Template="fieldlist", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, FieldList } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(FieldList);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Products' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showFieldList: true,
    height: 350,
    enginePopulated: (): void => {
         Object.keys(pivotTableObj.engineModule.fieldList).forEach((key, index) => {
                if (key === 'Quarter') {
                    pivotTableObj.engineModule.fieldList[key].caption = 'Production Quarter Year';
                }
                else if (key === 'Year') {
                    pivotTableObj.engineModule.fieldList[key].caption = 'Production Year';
                }
        });
    }
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Events

### EnginePopulated

The [`enginePopulated`](https://ej2.syncfusion.com/documentation/api/pivotfieldlist#enginepopulated) event is available in both Pivot Table and Field List.

* The event [`enginePopulated`](https://ej2.syncfusion.com/documentation/api/pivotfieldlist#enginepopulated) is triggered in field list whenever the report gets modified. The updated report is passed to the pivot table via [`updateView`](https://ej2.syncfusion.com/documentation/api/pivotfieldlist#updateview) method written within this event to refresh the same.

* Likewise, [`enginePopulated`](https://ej2.syncfusion.com/documentation/api/pivotview#enginepopulated) event is triggered in pivot table whenever the report gets modified. The updated report is passed to the field list via [`update`](https://ej2.syncfusion.com/documentation/api/pivotfieldlist#update) method written within this event to refresh the same.

The event [`enginePopulated`](https://ej2.syncfusion.com/documentation/api/pivotview#enginepopulated) is triggered after engine is populated. It has following parameters - `dataSourceSettings`, `pivotFieldList` and `pivotValues`.

> Note: This event is not required for Popup field list since it is a in built one.

{% tab template="pivot-table/field-list", es5Template="static-fieldlist", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, PivotFieldList } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
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
    renderMode: 'Fixed',
    enginePopulated: (): void => {
        fieldlistObj.updateView(pivotTableObj);
    }
});
fieldlistObj.appendTo('#Static_FieldList');

```

{% endtab %}

### FieldListRefreshed

The event [`FieldListRefreshed`](https://ej2.syncfusion.com/documentation/api/pivotview/#fieldlistrefreshed) is triggered whenever there is any change done in the field list UI. It has following parameter - `dataSourceSettings` and `pivotValues`. It allows user to identify each field list update. This event is applicable only for static field list.

For example, if we perform a sort operation within the field list, the field list will be refreshed. The [`fieldListRefreshed`](https://ej2.syncfusion.com/documentation/api/pivotview/#fieldlistrefreshed) event will be triggered at that time and the user can perform custom operation inside that event.

{% tab template="pivot-table/pivot-table", es5Template="fieldlist-refresh", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, FieldList, FieldListRefreshedEventArgs } from '@syncfusion/ej2-pivotview';
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
        filters: []
    },
    fieldListRefreshed: function (args: FieldListRefreshedEventArgs) {
        //Triggers, whenever field list get refreshed.
    },
    showFieldList: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

### FieldDropped

The event [`onFieldDropped`](https://ej2.syncfusion.com/documentation/api/pivotfieldlist#onfielddropped) fires whenever a field is dropped in an axis. It has following parameters - `droppedAxis`, `droppedField` and `dataSourceSettings`. In this illustration, we have modified the `droppedField` caption through this event at runtime.

{% tab template="pivot-table/pivot-table", es5Template="field-dropped", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, FieldList, FieldListRefreshedEventArgs } from '@syncfusion/ej2-pivotview';
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
        filters: []
    },
    onFieldDropped: function (args: FieldDroppedEventArgs) {
        args.droppedField.caption = args.droppedField.name + " --> " + args.droppedAxis;
    },
    showFieldList: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## See Also

* [Customize the icons for pivot table](./how-to/customize-the-icons-for-pivot-table)