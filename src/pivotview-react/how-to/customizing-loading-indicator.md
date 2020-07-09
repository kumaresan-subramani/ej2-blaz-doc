# Customizing loading indicator

You can customize the appearance of the loading indicator in the pivot table by using the [`spinnerTemplate`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#spinnertemplate) property. This property accepts an HTML string which can be used for appearance customization.

> You can also disable the loading indicator by setting [`spinnerTemplate`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#spinnertemplate) to empty string.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import { DataManager, WebApiAdaptor, Query, ReturnOption } from '@syncfusion/ej2-data';
import * as React from 'react';
import * as ReactDOM from 'react-dom';

class App extends React.Component<{}, {}>{
  public dataSourceSettings: IDataOptions;
  public pivotObj: PivotViewComponent;
  public dataSource: Promise<void> = new DataManager({
    url: 'https://bi.syncfusion.com/northwindservice/api/orders',
    adaptor: new WebApiAdaptor,
    crossDomain: true
  }).executeQuery(new Query().take(8)).then((e: ReturnOption) => {
    this.pivotObj.dataSourceSettings = {
      dataSource: e.result as IDataSet[],
      expandAll: true,
      filters: [],
      columns: [{ name: 'ProductName', caption: 'Product Name' }],
      rows: [{ name: 'ShipCountry', caption: 'Ship Country' }, { name: 'ShipCity', caption: 'Ship City' }],
      formatSettings: [{ name: 'UnitPrice', format: 'C0' }],
      values: [{ name: 'Quantity' }, { name: 'UnitPrice', caption: 'Unit Price' }]
    }
  });

  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} spinnerTemplate={'<i class="fa fa-cog fa-spin fa-3x fa-fw"></i>'} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}
