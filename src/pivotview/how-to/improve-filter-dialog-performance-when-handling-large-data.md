# Improve filter dialog performance when handling large data

In the filter dialog, you can set the limit to display the field values while loading large data. Based on this limit, the initial loading will complete quickly without any performance constraint. You can use the search option to refine the field values from the exceeded limit and refine the data further. A message with the remaining data count will be displayed in the member editor. The data limit can be set in the `maxNodeLimitInMemberEditor` property.

By default, the property holds the value 1000.

> The property is available in both pivot table and field list components.

In the following example, the limit of data in the member editor is set to 100. So, the member editor of the `ProductID` field shows only its first 100 members from its 1000 members.

{% tab template="pivot-table/pivot-table", es5Template="limit-data", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, VirtualScroll, GroupingBar, IDataSet } from '@syncfusion/ej2-pivotview';

let data: Function = (count: number) => {
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
            Sold: Math.round(Math.random() * 80) + 10,
        });
        if (dt / 4 == 1) {
            dt = 0;
        }
    }
    return result;
};

PivotView.Inject(VirtualScroll, GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: data(1000) as IDataSet[],
        enableSorting: false,
        rows: [{ name: 'ProductID' }],
        columns: [{ name: 'Year' }],
        values: [{ name: 'Sold', caption: 'Unit Sold' }]
    },
    height: 350,
    enableVirtualization: true,
    showGroupingBar: true,
    maxNodeLimitInMemberEditor: 100
});

pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}
