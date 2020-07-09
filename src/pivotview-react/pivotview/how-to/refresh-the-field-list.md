# Refresh the field list while change the data source

You can refresh pivot table and field list with new data source dynamically.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { IDataOptions, IDataSet, PivotViewComponent, FieldList, Inject } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }],
    dataSource: [
  { 'Sold': 31, 'Amount': 52824, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q1' },
  { 'Sold': 51, 'Amount': 86904, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q2' },
  { 'Sold': 90, 'Amount': 153360, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q3' },
  { 'Sold': 25, 'Amount': 42600, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q4' },
  { 'Sold': 27, 'Amount': 46008, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2016', 'Quarter': 'Q1' }] as IDataSet[],
    expandAll: false,
    filters: [],
    rows: [{ name: 'Country' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }]
  };
  public pivotObj: PivotViewComponent;
  render() {
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} showFieldList={true}><Inject services={[FieldList]} /></PivotViewComponent></div><div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Refresh</ButtonComponent></div></div>
  }

  btnClick(): void {
    this.pivotObj.engineModule.fieldList = {};
    this.pivotObj.dataSourceSettings.dataSource = [
            { 'Sold': 31, 'Amount': 52824, 'Country': 'France', 'Year': 'FY 2015' },
            { 'Sold': 51, 'Amount': 86904, 'Country': 'France', 'Year': 'FY 2015' },
            { 'Sold': 90, 'Amount': 153360, 'Country': 'France', 'Year': 'FY 2015' },
            { 'Sold': 25, 'Amount': 42600, 'Country': 'France', 'Year': 'FY 2015' },
            { 'Sold': 27, 'Amount': 46008, 'Country': 'France', 'Year': 'FY 2016' }];
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}
