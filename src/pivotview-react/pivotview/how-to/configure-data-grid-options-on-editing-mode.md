# Configure data grid options on editing mode

You can access the data grid options such as sort, group, filter, etc on editing mode using `beginDrillThrough` event in the pivot table. The event fires on every value cell click and provides the data grid information before it displays.

> To access the data grid options, you need to inject module for the provided options in data grid itself.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, CellEditSettings, IDataSet, Inject, PivotViewComponent, BeginDrillThroughEventArgs } from '@syncfusion/ej2-react-pivotview';
import { Grid, Sort, Filter, Group } from '@syncfusion/ej2-grids';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public editSettings: CellEditSettings = {
    allowAdding: true, allowDeleting: true, allowEditing: true, mode: 'Normal'
  } as CellEditSettings

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }

  beginDrillThrough(args: BeginDrillThroughEventArgs): void {
    if (args.gridObj) {
          Grid.Inject(Sort, Filter, Group);
          let gridObj: Grid = args.gridObj;
          gridObj.allowGrouping = true;
          gridObj.allowSorting = true;
          gridObj.allowFiltering = true;
          gridObj.filterSettings = { type: 'CheckBox' };
      }
  }

  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} editSettings={this.editSettings} beginDrillThrough={this.beginDrillThrough.bind(this)}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}
