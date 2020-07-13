# Configure data grid options on editing mode

You can access the data grid options such as sort, group, filter on editing mode using the `beginDrillThrough` event in the pivot table. The event occurs in every value cell on double click and provides the data grid information before display the drill through grid pop-up.

> Grid features are segregated into individual feature-wise modules. For example, to use sorting feature, you should inject `Sort` using the `Grid.Inject(Sort)` section.

{% tab template="pivot-table/pivot-table", es5Template="custom-editing", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, BeginDrillThroughEventArgs } from '@syncfusion/ej2-pivotview';
import { Grid, Sort, Filter, Group } from '@syncfusion/ej2-grids';
import { pivotData } from './datasource.ts';

Grid.Inject(Sort, Filter, Group);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    height: 350,
    editSettings: { allowAdding: true, allowDeleting: true, allowEditing: true, mode: 'Normal' },
    beginDrillThrough: (args: BeginDrillThroughEventArgs) => {
        if (args.gridObj) {
            let gridObj: Grid = args.gridObj;
            gridObj.allowGrouping = true;
            gridObj.allowSorting = true;
            gridObj.allowFiltering = true;
            gridObj.filterSettings = { type: 'CheckBox' };
        }
    }
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}
