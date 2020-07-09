# Apply condition based hyperlink for specific row or column

You can apply conditions for specific row or column using `label` option to show hyperlink option in the pivot table. It can be configured using the `conditionalSettings` option through code behind, during initial rendering. The required settings are:

* `label`: Specifies the header name to get visibility of hyperlink option for row or column.
* `conditions`: Specifies the operator type such as equals, greater than, less than, etc.
* `value1`: Specifies the start value.
* `value2`: Specifies the end value.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { HyperLinkSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/hypderlinksettings';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    enableSorting: true,
    drilledMembers: [{ name: 'Year', items: ['FY 2015'] }, { name: 'Country', items: ['France'] }],
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    filters: []
  }
  public hyperlinkSettings: HyperLinkSettings = {
    conditionalSettings: [{
        label: 'Germany',
        conditions: 'GreaterThan',
        value1: 500
    }],
    cssClass: 'e-custom-class'
  } as HyperLinkSettings;
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' dataSourceSettings={this.dataSourceSettings} hyperlinkSettings={this.hyperlinkSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}
