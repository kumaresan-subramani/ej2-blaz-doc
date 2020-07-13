---
title: "Grouping Bar"
component: "Pivot Table"
description: "Grouping bar allows the user to drag and drop fields between different axes at runtime."
---

# Grouping Bar

The Grouping Bar option in pivot table automatically populates fields from the bound data source and allows end users to drag fields between different axes such as columns, rows, values, and filters, and create pivot table at runtime. It can be enabled by setting the [`showGroupingBar`](https://ej2.syncfusion.com/documentation/api/pivotview#showgroupingbar) property in pivot to **true**.

Similar to Field List, Grouping Bar UI also comes with basic interactions like,

* Re-arranging fields through drag-and-drop operation between row, column, value and filter axes.
* Remove fields from the existing report using remove icon.
* Filtering members of specific fields using filter icon.
* Sorting members of specific fields using sort icon.

To use grouping bar, user need to inject the `GroupingBar` module in pivot table.

{% tab template="pivot-table/pivot-table", es5Template="groupingbar", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, GroupingBar } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        allowLabelFilter: true,
        allowValueFilter: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    height: 340
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

The grouping bar provides some additional options to customize it's UI using [`groupingBarSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/groupingBarSettings/) property.

## Show or hide all filter icon

The Grouping Bar has an option to filter members of particular fields at runtime in pivot table. In-order to filter members in a field, click the filter icon and check/uncheck members that needs to be displayed. By default, filter icon besides each field is enabled in the grouping bar. To disable the filter icon, set the property [`showFilterIcon`](https://ej2.syncfusion.com/documentation/api/pivotview/groupingBarSettings/#showfiltericon) in [`groupingBarSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/groupingBarSettings/) to **false**.

> By default, the filter icon is enabled in the grouping bar.

{% tab template="pivot-table/pivot-table", es5Template="show-filter", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, GroupingBar } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    groupingBarSettings: {
        showFilterIcon: false
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Show or hide specific filter icon

To disable the filter icon for a specific field, set the property [`showFilterIcon`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptions/#showfiltericon) to **false** to the corresponding field in [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/).

In the below sample, the filter icon of "Quarter" and "Products" fields have been hidden.

{% tab template="pivot-table/pivot-table", es5Template="show-filter-specific", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, GroupingBar } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter', showFilterIcon: false }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' , showFilterIcon: false }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Show or hide all sort icon

The Grouping Bar has an option to order members of a particular fields either in ascending or descending at runtime. In order to sort a field, click the sort icon and to reverse its sort direction, once again click the same sort icon. By default, the sort icon besides each field is enabled in the grouping bar and members will be arranged in ascending order. To disable the sort option, set the property [`showSortIcon`](https://ej2.syncfusion.com/documentation/api/pivotview/groupingBarSettings/#showsorticon) in [`groupingBarSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/groupingBarSettings/) to **false**.

> By default, the sort icon is enabled in the grouping bar.

{% tab template="pivot-table/pivot-table", es5Template="show-sort", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, GroupingBar } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    groupingBarSettings: {
        showSortIcon: false
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Show or hide specific sort icon

To disable the sort icon for a specific button, set the property [`showSortIcon`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptions/#showsorticon) to **false** to the corresponding field in [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/).

In the below sample, the sort icon of "Quarter" and "Country" fields have been hidden.

{% tab template="pivot-table/pivot-table", es5Template="show-sort-specific", sourceFiles="index.ts,index.html" %}

```typescript

import { PivotView, IDataSet, GroupingBar } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter', showSortIcon: false }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country', showSortIcon:false }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Show or hide all remove icon

The Grouping Bar has an option to remove any field at runtime. To remove a field, just click the remove icon. By default, the remove icon besides each field is enabled in the grouping bar. To disable the remove icon, set the property [`showRemoveIcon`](https://ej2.syncfusion.com/documentation/api/pivotview/groupingBarSettings/#showremoveicon) in [`groupingBarSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/groupingBarSettings/) to **false**.

> By default, the remove icon is enabled in the grouping bar.

{% tab template="pivot-table/pivot-table", es5Template="show-remove", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, GroupingBar } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    groupingBarSettings: {
        showRemoveIcon: false
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Show or hide specific remove icon

To disable the remove icon for a specific button, set the property [`showRemoveIcon`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptions/#showremoveicon) to **false** to the corresponding field in [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/).

In the below sample, the remove icon of fields "Year", "Sold" and "Products" have been hidden.

{% tab template="pivot-table/pivot-table", es5Template="show-remove-specific", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, GroupingBar } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        columns: [{ name: 'Year', caption: 'Production Year', showRemoveIcon: false }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold', showRemoveIcon: false }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products', showRemoveIcon: false }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Disable all fields from dragging

The Grouping Bar has an option to drag-and-drop fields between row, column, value and filter axes in-order to change report at runtime. By default, all fields are available for drag-and-drop operation in the grouping bar. To disable these fields, set the property [`allowDragAndDrop`](https://ej2.syncfusion.com/documentation/api/pivotview/groupingBarSettings/#allowdraganddrop) in [`groupingBarSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/groupingBarSettings/) to false. This will prevent end user from changing the current report.

{% tab template="pivot-table/pivot-table", es5Template="allow-drag", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, GroupingBar } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    groupingBarSettings: {
        allowDragAndDrop: false
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Disable specific field from dragging

To disable dragging for a specific button, set the property [`allowDragAndDrop`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptions/#allowdraganddrop) to **false** to the corresponding  field in [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/).

In the below sample, the drag and drop of the fields "Year" and "Products" have been restricted.

{% tab template="pivot-table/pivot-table", es5Template="allow-drag-specific", sourceFiles="index.ts,index.html" %}

```typescript

import { PivotView, IDataSet, GroupingBar } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        columns: [{ name: 'Year', caption: 'Production Year', allowDragAndDrop: false }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products', allowDragAndDrop: false }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Changing aggregation type of value fields at runtime

End user can perform calculations over a group of values using the aggregation option. The value fields bound to the field list, appears with a dropdown icon, helps to select an appropriate aggregation type at runtime. On selection, the values in the Pivot Table will be changed dynamically. By default, the icon to set aggregation type is enabled in the grouping bar. To disable this icon, set the property [`showValueTypeIcon`](https://ej2.syncfusion.com/documentation/api/pivotview/groupingBarSettings/#showvaluetypeicon) in [`groupingBarSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/groupingBarSettings/) to false. To know more about aggregation,[`refer`](./aggregation) here.
{% tab template="pivot-table/pivot-table", es5Template="groupingbar-aggregation", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, GroupingBar } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    groupingBarSettings: {
        showValueTypeIcon: true
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Show or hide specific dropdown icon

To disable the dropdown icon for a specific button, set the property [`showValueTypeIcon`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptions/#showvaluetypeicon) to **false** to the corresponding field in [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/).

In the below sample, the dropdown icon of field "Sold" is hidden.

{% tab template="pivot-table/pivot-table", es5Template="show-dropdown-specific",sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, GroupingBar } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold', showValueTypeIcon: false }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

 >The property [`showFilterIcon`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptions/#showfiltericon), [`showSortIcon`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptions/#showsorticon), [`showValueTypeIcon`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptions/#showvaluetypeicon) and [`allowDragAndDrop`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptions/#allowdraganddrop) in fields of [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/) are applicable for both grouping bar and field list.

## Event

### OnFieldDropped

The event `onFieldDropped` fires on whenever a field is dropped over an axis. It has following parameters - `droppedAxis`, `droppedField` and `dataSourceSettings`. In this sample we have modified the `droppedField` caption based on the `droppedAxis`.

{% tab template="pivot-table/pivot-table", es5Template="groupingbar-dropped", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, GroupingBar } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    onFieldDropped: function (args: FieldDroppedEventArgs) {
        args.droppedField.caption = args.droppedField.name + " --> " + args.droppedAxis;
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

### FieldDragStart

The event [`fieldDragStart`](https://ej2.syncfusion.com/documentation/api/pivotview#fielddragstart) fires whenever a field drag starts from its axis. It allows the user to restrict the drag operation based on its parameters. It has the following parameters  

* `fieldName`: It holds the name of the appropriate field.

* `fieldItem`: It holds the complete definition of the appropriate field mentioned in data source settings.

* `axis`: It holds the axis name where the draggable field lies.

* `cancel`: It is a boolean property and by setting this to true, user can restrict the field from dragging.

In the below sample, the drag operation for the fields in row axis alone is restricted.

{% tab template="pivot-table/pivot-table", es5Template="fieldDragStart-event", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, GroupingBar } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    fieldDragStart: function (args: FieldDragStartEventArgs) {
        if(args.axis === 'rows') {
            args.cancel = true;
        }
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

### FieldDrop

The event  [`fieldDrop`](https://ej2.syncfusion.com/documentation/api/pivotview#fielddrop) fires whenever a field is dropped into an axis. It allows the user to restrict the drop operation based on its parameters. It has the following parameters  

* `fieldName`: It holds the name of the appropriate field.

* `fieldItem`: It holds the complete definition of the appropriate field mentioned in data source settings.

* `draggedAxis`: It holds the axis name from where dragging was started.

* `dropAxis`: It holds the axis name where the field is dropped.

* `dropPosition`: It holds the dropped index among other existing fields in the axis.

* [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/): It holds complete pivot report.

* `cancel`: It is a boolean property and by setting this to true, user can restrict the field from being dropped.

In the below sample, dropping of any fields in value axis alone is restricted.

{% tab template="pivot-table/pivot-table", es5Template="FieldDrop-event", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, GroupingBar } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    fieldDrop: function (args: fieldDropEventArgs ) {
        if(args.dropAxis === 'values') {
            args.cancel = true;
        }
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

### FieldRemove

The event [`fieldRemove`](https://ej2.syncfusion.com/documentation/api/pivotview#fieldremove) fires when removing any field from their axis. It helps the user to limit the elimination of a field based on its parameters. It has the following parameters  

* `fieldName`: It holds the name of the field to be removed.

* `fieldItem`: It holds the complete definition of the appropriate field mentioned in data source settings.

* `axis`: It holds the name of the axis from where it is to remove the field.

* [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/): It holds complete pivot report.

* `cancel`: It is a boolean property and by setting this to true, user can restrict the field from removing.

In the below sample, the field "Country" could not be removed from report by any UI operations.

{% tab template="pivot-table/pivot-table", es5Template="fieldRemove-event", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, GroupingBar } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    fieldRemove: function (args: FieldRemoveEventArgs ) {
        if(args.fieldName === 'Country') {
            args.cancel = true;
        }
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

### AggregateMenuOpen

The event [`aggregateMenuOpen`](https://ej2.syncfusion.com/documentation/api/pivotview#aggregatemenuopen) fires while clicking dropdown icon of the value field button UI. It allows to customize the aggregate types to be displayed in the dropdown menu. It has the following parameters

* `fieldName`: It holds the name of the field that opens the aggregate menu.

* [`aggregateTypes`](https://ej2.syncfusion.com/documentation/api/pivotview/#aggregatetypes): It holds the aggregation types set for a field.

* `cancel`: It is a boolean property and by setting this to true, dropdown menu won’t be displayed.

In the below sample, the aggregate types of the field "Amount" has been customized in it's dropdown menu.

{% tab template="pivot-table/pivot-table", es5Template="aggregateMenuOpen-event", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, GroupingBar } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    aggregateMenuOpen: function (args: AggregateMenuOpenEventArgs ) {
        if(args.fieldName === 'Amount') {
            args.aggregateTypes = ['Sum', 'Avg', 'Max'];
        }
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

 >The events [`aggregateMenuOpen`](https://ej2.syncfusion.com/documentation/api/pivotview#aggregatemenuopen), [`fieldRemove`](https://ej2.syncfusion.com/documentation/api/pivotview#fieldremove), [`fieldDrop`](https://ej2.syncfusion.com/documentation/api/pivotview#fielddrop), [`fieldDragStart`](https://ej2.syncfusion.com/documentation/api/pivotview#fielddragstart) and [`onFieldDropped`](https://ej2.syncfusion.com/documentation/api/pivotview#onfielddropped) are applicable for both grouping bar and field list.

## See Also

* [Customize the icons for pivot table](./how-to/customize-the-icons-for-pivot-table)