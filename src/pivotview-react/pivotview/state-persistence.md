---
title: "State Persistence"
component: "Pivot Table"
description: "Describes about persistence in pivot table"
---

# State Persistence

State persistence allows user to maintain the current state of the component along with its report bounded in the browser local storage (cookie). Even if the browser is refreshed or if you move to the next page within the browser, components state will be persisted. State persistence stores the Pivot Table object in the local storage when [`enablePersistence`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#enablepersistence) property is set to **true**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
        dataSource: pivotData,
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Country', items: ['France', 'Germany'] }],
        columns: [{ name: 'Year' }, { name: 'Order_Source', caption: 'Order Source' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        values: [{ name: 'In_Stock', caption: 'In Stock' },
        { name: 'Sold', caption: 'Units Sold' }],
        filters: [{ name: 'Product_Categories', caption: 'Product Categories' }]
  }
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} enablePersistence={true} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

# Save and Load Pivot Layout

You can save the current layout of the pivot table by using [`getPersistData`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#getpersistdata) in string format. The saved layout can be loaded to pivot table any time by passing the saved data as a parameter to [`loadPersistData`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#loadpersistdata) method.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
        dataSource: pivotData,
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Country', items: ['France', 'Germany'] }],
        columns: [{ name: 'Year' }, { name: 'Order_Source', caption: 'Order Source' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        values: [{ name: 'In_Stock', caption: 'In Stock' },
        { name: 'Sold', caption: 'Units Sold' }],
        filters: [{ name: 'Product_Categories', caption: 'Product Categories' }]
  }
  public pivotObj: PivotViewComponent;
  public report: string;
  render() {
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent></div><div className='col-lg-3 property-section'><div><ButtonComponent cssClass='e-primary' onClick={this.save.bind(this)}>Save</ButtonComponent></div><br/><div><ButtonComponent cssClass='e-primary' onClick={this.load.bind(this)}>Load</ButtonComponent></div></div>
    </div>
  }
  save(): void {
    this.report = this.pivotObj.getPersistData();
  }
  load(): void {
    this.pivotObj.loadPersistData(this.report);
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}
