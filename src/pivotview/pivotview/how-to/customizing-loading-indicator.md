# Customizing loading indicator

You can customize the appearance of the loading indicator in the pivot table by using the [`spinnerTemplate`](https://ej2.syncfusion.com/documentation/api/pivotview/#spinnertemplate) property. This property accepts an HTML string which can be used for appearance customization.

> You can also disable the loading indicator by setting [`spinnerTemplate`](https://ej2.syncfusion.com/documentation/api/pivotview/#spinnertemplate) to empty string.

{% tab template="pivot-table/pivot-table", es5Template="spinner-template", sourceFiles="index.ts,index.html,index.css" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { DataManager, WebApiAdaptor, Query, ReturnOption } from '@syncfusion/ej2-data';

let data: DataManager = new DataManager({
    url: 'https://bi.syncfusion.com/northwindservice/api/orders',
    adaptor: new WebApiAdaptor,
    crossDomain: true
});

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: data,
        expandAll: true,
        filters: [],
        columns: [{ name: 'ProductName', caption: 'Product Name' }],
        rows: [{ name: 'ShipCountry', caption: 'Ship Country' }, { name: 'ShipCity', caption: 'Ship City' }],
        formatSettings: [{ name: 'UnitPrice', format: 'C0' }],
        values: [{ name: 'Quantity' }, { name: 'UnitPrice', caption: 'Unit Price' }]
    },
    height: 350,
    spinnerTemplate: '<i class="fa fa-cog fa-spin fa-3x fa-fw"></i>'
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}
