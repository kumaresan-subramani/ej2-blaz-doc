# Customize pivot table Cell Element

You can customize the pivot table cell element by using the `cellTemplate` property.
The cellTemplate property accepts either an HTML string or the element's ID, which can be used to append additional HTML elements to showcase each cell with custom format.

In this demo, the revenue cost for each year is represented with trend icons.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { renewableEnergy } from './datasource';

class App extends React.Component<{}, {}>{

private cellTemplate(props): JSX.Element {
    return (<span className="tempwrap e-pivot-trend-neutral pv-icons"></span>);
}

  public dataSourceSettings: IDataOptions = {
    dataSource: renewableEnergy as IDataSet[],
    expandAll: true,
    enableSorting: true,
    drilledMembers: [{ name: 'Year', items: ['FY 2015', 'FY 2017', 'FY 2018'] }],
    formatSettings: [{ name: 'ProCost', format: 'C0' }],
    rows: [
        { name: 'Year', caption: 'Production Year' }
    ],
    columns: [
        { name: 'EnerType', caption: 'Energy Type' },
        { name: 'EneSource', caption: 'Energy Source' }
    ],
    values: [
        { name: 'ProCost', caption: 'Revenue Growth' }
    ],
    filters: []
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} cellTemplate={this.cellTemplate.bind(this)} dataBound={this.trend.bind(this)}></PivotViewComponent>
  }

    trend(): void {
        let cTable: HTMLElement[] = [].slice.call(document.getElementsByClassName("e-table"));
        let colLen: number = this.pivotObj.pivotValues[3].length;
        let cLen: number = cTable[3].children[0].children.length;
        let rLen: number = cTable[3].children[1].children.length;
        let rowIndx: number;

        for (let k: number = 0; k < rLen; k++) {
            if (this.pivotObj.pivotValues[k] && this.pivotObj.pivotValues[k][0] !== undefined) {
                rowIndx = ((this.pivotObj.pivotValues[k][0]) as IAxisSet).rowIndex;
                break;
            }
        }
        let rowHeaders: HTMLElement[] = [].slice.call(cTable[2].children[1].querySelectorAll('td'));
        let rows: IFieldOptions[] = this.pivotObj.dataSourceSettings.rows as IFieldOptions[];
        if (rowHeaders.length > 1) {
            for (let i: number = 0, Cnt = rows; i < Cnt.length; i++) {
                let fields: any = {};
                let fieldHeaders: any = [];
                for (let j: number = 0, Lnt = rowHeaders; j < Lnt.length; j++) {
                    let header: any = rowHeaders[j];
                    if (header.className.indexOf('e-gtot') === -1 && header.className.indexOf('e-rowsheader') > -1 && header.getAttribute('fieldname') === rows[i].name) {
                        var headerName = rowHeaders[j].getAttribute('fieldname') + '_' + rowHeaders[j].textContent;
                        fields[rowHeaders[j].textContent] = j;
                        fieldHeaders.push(rowHeaders[j].textContent);
                    }
                }
                if (i === 0) {
                    for (let rnt: number = 0, Lnt = fieldHeaders; rnt < Lnt.length; rnt++) {
                        if (rnt !== 0) {
                            let row: number = fields[fieldHeaders[rnt]];
                            let prevRow: number = fields[fieldHeaders[rnt - 1]];
                            for (let j: number = 0, ci = 1; j < cLen && ci < colLen; j++ , ci++) {
                                let node: HTMLElement = cTable[3].children[1].children[row].childNodes[j] as HTMLElement;
                                let prevNode: HTMLElement = cTable[3].children[1].children[prevRow].childNodes[j] as HTMLElement;
                                let ri: any = undefined;
                                let prevRi: any = undefined;
                                if (node) {
                                    ri = node.getAttribute("index");
                                }
                                if (prevNode) {
                                    prevRi = prevNode.getAttribute("index");
                                }
                                if (ri && ri < [].slice.call(this.pivotObj.pivotValues).length) {
                                    if ((this.pivotObj.pivotValues[prevRi][ci] as IAxisSet).value > (this.pivotObj.pivotValues[ri][ci]  as IAxisSet).value &&
                                     node.querySelector('.tempwrap')) {
                                        let trendElement: HTMLElement = node.querySelector('.tempwrap');
                                        trendElement.className = trendElement.className.replace('sb-icon-neutral', 'sb-icon-loss');
                                    } else if ((this.pivotObj.pivotValues[prevRi][ci]  as IAxisSet).value < (this.pivotObj.pivotValues[ri][ci]  as IAxisSet).value &&
                                     node.querySelector('.tempwrap')) {
                                        let trendElement: HTMLElement = node.querySelector('.tempwrap');
                                        trendElement.className = trendElement.className.replace('sb-icon-neutral', 'sb-icon-profit');
                                    }
                                }
                            }
                        }
                    }
                }
            }
        }
    }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}
