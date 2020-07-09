# Hide empty headers

If the raw data for a particular field is not defined, it will be shown as 'Undefined' in the pivot table headers. You can hide those headers by setting the [`showHeaderWhenEmpty`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#showheaderwhenempty) property to **false** in the pivot table.

For example, if the raw data for the field 'Country' is defined as **"United Kingdom"** and **"State"** is not defined means, it will be shown as **"United Kingdom >> Undefined"** in the header section. Here, you can hide those 'Undefined' header using the [`showHeaderWhenEmpty`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#showheaderwhenempty) property.

> By default, this property is set as **true**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { FieldList, IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotNullData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
        dataSource: pivotNullData as IDataSet[],
        expandAll: false,
        rows: [{ name: 'Country' }, { name: 'State'}],
        columns: [{ name: 'Product', showNoDataItems: true }, { name: 'Date' }],
        values: [{ name: 'Amount' }, { name: 'Quantity' }],
        showHeaderWhenEmpty: false
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} showFieldList={true}><Inject services={[FieldList]} /></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}
