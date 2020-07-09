# Improve filter dialog performance when handling large data

In the filter dialog, you can set the limit to display the field values while loading large data. Based on this limit, the initial loading will complete quickly without any performance constraint. You can use the search option to refine the field values from the exceeded limit and refine the data further. A message with the remaining data count will be displayed in the member editor. The data limit can be set in the `maxNodeLimitInMemberEditor` property.

By default, the property holds the value 1000.

> The property is available in both pivot table and field list components.

In the following example, the limit of data in the member editor is set to 100. So, the member editor of the `ProductID` field shows only its first 100 members from its 1000 members.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { GroupingBar, IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
let date1: number;
let date2: number;
function data(count: number) {
    let result: Object[] = [];
    let dt: number = 0;
    for (let i: number = 1; i < (count + 1); i++) {
        dt++;
        let round: string;
        let toString: string = i.toString();
        if (toString.length === 1) {
            round = '0000' + (i);
        }
        else if (toString.length === 2) {
            round = '000' + i;
        }
        else if (toString.length === 3) {
            round = '00' + i;
        } else if (toString.length === 4) {
            round = '0' + i;
        } else {
            round = toString;
        }
        result.push({
            ProductID: 'PRO-' + round,
            Year: "FY " + (dt + 2013),
            Price: Math.round(Math.random() * 5000) + 5000,
            Sold: Math.round(Math.random() * 80) + 10,
        });
        if (dt / 4 == 1) {
            dt = 0;
        }
    }
    return result;
};
class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    dataSource: data(1000),
    enableSorting: false,
    expandAll: true,
    formatSettings: [{ name: 'Price', format: 'C0' }],
    rows: [{ name: 'ProductID' }],
    columns: [{ name: 'Year' }],
    values: [{ name: 'Price', caption: 'Unit Price' }, { name: 'Sold', caption: 'Unit Sold' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} showGroupingBar={true} maxNodeLimitInMemberEditor={100}><Inject services={[GroupingBar]}/></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}
