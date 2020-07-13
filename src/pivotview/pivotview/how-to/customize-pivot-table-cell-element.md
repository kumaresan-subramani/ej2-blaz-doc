# Customize pivot table cell element

You can customize the pivot table cell element by using the `cellTemplate` property.
The cellTemplate property accepts either an HTML string or the element's ID, which can be used to append additional HTML elements to showcase each cell with custom format.

In this demo, the revenue cost for each year is represented with trend icons.

{% tab template="pivot-table/pivot-table", es5Template="cell-template", sourceFiles="index.ts,index.html,index.css" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { renewableEnergy } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
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
    },
    gridSettings: {
        columnWidth: 140
    },
    height: 350,
    cellTemplate: '<span class="tempwrap sb-icon-neutral pv-icons"></span>',
    dataBound(): void {
        let cTable: HTMLElement[] = [].slice.call(document.getElementsByClassName("e-table"));
        let colLen: number = pivotTableObj.pivotValues[3].length;
        let cLen: number = cTable[3].children[0].children.length;
        let rLen: number = cTable[3].children[1].children.length;
        let rowIndx: number;

        for (let k = 0; k < rLen; k++) {
            if (pivotTableObj.pivotValues[k] && pivotTableObj.pivotValues[k][0] !== undefined) {
                rowIndx = ((pivotTableObj.pivotValues[k][0]) as IAxisSet).rowIndex;
                break;
            }
        }
        var rowHeaders = [].slice.call(cTable[2].children[1].querySelectorAll('td'));
        var rows = pivotTableObj.dataSourceSettings.rows;
        if (rowHeaders.length > 1) {
            for (var i = 0, Cnt = rows; i < Cnt.length; i++) {
                var fields = {};
                var fieldHeaders = [];
                for (var j = 0, Lnt = rowHeaders; j < Lnt.length; j++) {
                    var header = rowHeaders[j];
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
                            for (var j = 0, ci = 1; j < cLen && ci < colLen; j++ , ci++) {
                                let node: HTMLElement = cTable[3].children[1].children[row].childNodes[j] as HTMLElement;
                                let prevNode: HTMLElement = cTable[3].children[1].children[prevRow].childNodes[j] as HTMLElement;
                                let ri: string = undefined;
                                let prevRi: string = undefined;
                                if (node) {
                                    ri = node.getAttribute("index");
                                }
                                if (prevNode) {
                                    prevRi = prevNode.getAttribute("index");
                                }
                                if (ri && ri < [].slice.call(pivotTableObj.pivotValues).length) {
                                    if ((pivotTableObj.pivotValues[prevRi][ci]).value > (pivotTableObj.pivotValues[ri][ci]).value && node.querySelector('.tempwrap')) {
                                        let trendElement: HTMLElement = node.querySelector('.tempwrap');
                                        trendElement.className = trendElement.className.replace('sb-icon-neutral', 'sb-icon-loss');
                                    } else if ((pivotTableObj.pivotValues[prevRi][ci]).value < (pivotTableObj.pivotValues[ri][ci]).value && node.querySelector('.tempwrap')) {
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
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}
