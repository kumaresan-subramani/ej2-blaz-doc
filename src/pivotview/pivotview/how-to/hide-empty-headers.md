# Hide empty headers

If the raw data for a particular field is not defined, it will be shown as 'Undefined' in the pivot table headers. You can hide those headers by setting the [`showHeaderWhenEmpty`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettingsModel/#showheaderwhenempty) property to **false** in the pivot table.

For example, if the raw data for the field 'Country' is defined as **"United Kingdom"** and **"State"** is not defined means, it will be shown as **"United Kingdom >> Undefined"** in the header section. Here, you can hide those 'Undefined' header using the [`showHeaderWhenEmpty`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettingsModel/#showheaderwhenempty) property.

> By default, this property is set as **true**.

{% tab template="pivot-table/pivot-table", es5Template="hide-member", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotNullData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotNullData as IDataSet[],
        expandAll: false,
        rows: [{ name: 'Country' }, { name: 'State'}],
        columns: [{ name: 'Product', showNoDataItems: true }, { name: 'Date' }],
        values: [{ name: 'Amount' }, { name: 'Quantity' }],
        showHeaderWhenEmpty: false
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}
