# Customizing loading indicator

You can customize the appearance of the loading indicator in the pivot table by using the [`spinnerTemplate`](https://ej2.syncfusion.com/angular/documentation/api/pivotview/#spinnertemplate) property. This property accepts an HTML string which can be used for appearance customization.

> You can also disable the loading indicator by setting [`spinnerTemplate`](https://ej2.syncfusion.com/angular/documentation/api/pivotview/#spinnertemplate) to empty string.

{% tab template="pivot-grid/getting-started", sourceFiles="app/app.component.ts,app/app.module.ts" %}

```typescript
import { Component, OnInit } from '@angular/core';
import { IDataOptions, IDataSet, PivotView } from '@syncfusion/ej2-angular-pivotview';
import { DataManager, WebApiAdaptor, Query, ReturnOption } from '@syncfusion/ej2-data';

@Component({
  selector: 'app-container',
  template: `<ejs-pivotview #pivotview id='PivotView' height='350' [dataSourceSettings]=dataSourceSettings width=width spinnerTemplate="<i class='fa fa-cog fa-spin fa-3x fa-fw'></i>"></ejs-pivotview>`
})
export class AppComponent implements OnInit {
  public dataSourceSettings: IDataOptions;
  public data: DataManager;
  public width: string;

    ngOnInit(): void {

        this.data = new DataManager({
            url: 'https://bi.syncfusion.com/northwindservice/api/orders',
            adaptor: new WebApiAdaptor,
            crossDomain: true
        });
        this.width = '100%';
        this.dataSourceSettings = {
            dataSource: this.data,
            expandAll: true,
            filters: [],
            columns: [{ name: 'ProductName', caption: 'Product Name' }],
            rows: [{ name: 'ShipCountry', caption: 'Ship Country' }, { name: 'ShipCity', caption: 'Ship City' }],
            formatSettings: [{ name: 'UnitPrice', format: 'C0' }],
            values: [{ name: 'Quantity' }, { name: 'UnitPrice', caption: 'Unit Price' }]
        };
    }
}

```

{% endtab %}
