---
title: "Member Filtering"
component: "Pivot Table"
description: "Member filtering allows user to view pivot table with particular records based on selected members."
---

<!-- markdownlint-disable MD012 -->

# Filtering

Filtering allows to view the pivot table with selective records based on members that can be either included or excluded through UI and code-behind.

The following are the three different types of filtering:

* Member filtering
* Label filtering
* Value filtering

> When all the above filtering options are disabled via code-behind, then the filter icon would be disabled in the field list or grouping bar UI.

## Member filtering

Allows to view the pivot table with selective records based on included and excluded members in each field. By default, member filter option is enabled by the [`allowMemberFilter`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#allowmemberfilter) boolean property in [`dataSourceSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/). This UI option helps end user to filter members by clicking the filter icon besides any field in the row, column and filter axes available in the field list or grouping bar UI at runtime.

![output](images/fieldlist_filtericon.png "Member filter icon in field list")
<br/>
![output](images/filter_icon_gb.png "Member filter icon in grouping bar")
<br/>
![output](images/filter_dialog_gb.png "Member filter dialog with checked and unchecked members")
<br/>
![output](images/filter_grid_gb.png "Resultant pivot table on member filter")

Meanwhile filtering can also be configured at code behind using the [`filterSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/) while initial rendering of the component. The basic settings required to add filter criteria are:

* [`name`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#name): It allows to set the appropriate field name.
* [`type`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#type): It allows to set the filter type as **Include** or **Exclude** to include or exclude field members respectively.
* [`items`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#items): It allows to set the members which needs to be either included or excluded from display.
* [`levelCount`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filterModel/#levelcount): It allows to set level count of the field to fetch data from the cube. **NOTE: This property applicable only for OLAP data source.**

> When specifying unavailable or inappropriate members to include or exclude filter items collection, they will be ignored.

{% tab template="pivot-table/pivot-table", es5Template="filtering", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        filterSettings: [{ name: 'Country', type: 'Exclude', items: ['United States'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        filters: []
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

### Option to select and unselect all members

The member filter dialog comes with an option "All", which on checked selects all members and on unchecked deselects all members. The option "All" would appear in intermediate state mentioning that both selected and unselected child members are available.

![output](images/editor_inter.png)

When all members are deselected, the "Ok" button in member filter dialog would be disabled, meaning, at least one member should be selected and bound to the pivot table component.

![output](images/editor_alluncheck.png)

### Provision to search specific member(s)

By default, search option is available to quickly navigate to the desired members. It can be done by entering the starting character(s) of the actual members.

![output](images/search.png)

### Option to sort members

User can sort members within the member editor either to ascending (or) descending using the built-in sort icons. When both ascending and descending options are not chosen, then members will be shown in the default order (retrieved as such from data source).

![output](images/member-sort.png)

### Performance Tips

In member filter dialog, end user can set the limit to display members while loading large data. Based on this limit, initial loading will get completed quickly without any performance constraint. Also, a message with remaining member count, which are not part of the UI, will be displayed in the member editor.

The data limit can be set using the [`maxNodeLimitInMemberEditor`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#maxnodelimitinmembereditor) property in pivot table. By default, the property holds the numeric value **1000**.


{% tab template="pivot-table/pivot-table", es5Template="filtering-maxnode", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { FieldList, GroupingBar, VirtualScroll } from '@syncfusion/ej2-pivotview';


let names: string[] = ['TOM', 'Hawk', 'Jon', 'Chandler', 'Monica', 'Rachel', 'Phoebe', 'Gunther',
    'Ross', 'Geller', 'Joey', 'Bing', 'Tribbiani', 'Janice', 'Bong', 'Perk', 'Green', 'Ken', 'Adams'];
let city: string[] = ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Philadelphia', 'Phoenix', 'San Antonio', 'Austin',
    'San Francisco', 'Columbus', 'Washington', 'Portland', 'Oklahoma', 'Las Vegas', 'Virginia', 'St. Louis', 'Birmingham']
let hours: number[] = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
let rating: number[] = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
let designation: string[] = ['Manager', 'Engineer 1', 'Engineer 2', 'Developer', 'Tester'];
let status: string[] = ['Completed', 'Open', 'In Progress', 'Review', 'Testing'];
let data: Function = (count: number) => {
    let result: Object[] = [];
    for (let i = 0; i < count; i++) {
        result.push({
            TaskID: i + 1,
            Engineer: names[Math.round(Math.random() * names.length)] || names[0],
            City: names[Math.round(Math.random() * city.length)] || city[0],
            Designation: designation[Math.round(Math.random() * designation.length)] || designation[0],
            Estimation: hours[Math.round(Math.random() * hours.length)] || hours[0],
            Rating: hours[Math.round(Math.random() * rating.length)] || rating[0],
            Status: status[Math.round(Math.random() * status.length)] || status[0]
        });
    }
    return result;
};

PivotView.Inject(VirtualScroll, FieldList, GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: data(5000),
        expandAll: false,
        formatSettings: [{ name: 'Estimation', format: 'C' }],
        rows: [{ name: 'TaskID' }, { name: 'Status' }],
        columns: [{ name: 'Designation' }],
        values: [{ name: 'Estimation' }, { name: 'Rating' }],
    },
    width: 800,
    height: 300,
    enableVirtualization: true,
    showFieldList: true,
    showGroupingBar: true,
    maxNodeLimitInMemberEditor:500
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

Meanwhile, end user can utilize the search option to refine the members from the exceeded limit. For example, consider that there are 5000 members in the name "Node 1", "Node 2", "Node 3", and so on... and user has set the property [`maxNodeLimitInMemberEditor`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#maxnodelimitinmembereditor) to **500**. In this case, only the initial 500 members will be displayed by default leaving a message "4500 more items. Search to refine further.". To get the member(s) between 501 to 5000, enter the starting character(s) in search option to bring the desired member(s) from the exceeded limit to the UI. Now, end user can either check or uncheck to continue with the filtering process.

### Loading members on-demand

> This property is applicable only for OLAP data sources.

Allows to load members inside the filter dialog on-demand by setting the [`loadOnDemandInMemberEditor`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#loadondemandinmembereditor) property to **true**. By default, first level is loaded in the member editor from the OLAP cube. So, the member editor will be opened quickly, without any performance constraints. By default, this property is set to **true** and the search will only be applied to the level members that are loaded. In the meantime, the next level members can be added using either of the following methods.

* By clicking on the expander button of the respective member, only its child members will be loaded.
* Select a level from the drop-down list that will load all members up to the chosen level from the cube.

This will help to avoid performance lags when opening a member editor whose hierarchy has a large number of members. Once level members are queried and added one after the other, they will be maintained internally (for all operations like dialog re-opening, drag and drop, etc...) and will not be removed until the web page is refreshed.

{% tab template="pivot-table/pivot-table", es5Template="olap-ondemand-member", sourceFiles="index.ts,index.html" %}

```typescript

var pivotTableObj = new ej.pivotview.PivotView({
    dataSourceSettings: {
            catalog: 'Adventure Works DW 2008 SE',
            cube: 'Adventure Works',
            providerType: 'SSAS',
            enableSorting: true,
            url: 'https://bi.syncfusion.com/olap/msmdpump.dll',
            localeIdentifier: 1033,
            rows: [
                { name: '[Customer].[Customer Geography]', caption: 'Customer Geography' },
            ],
            columns: [
                { name: '[Product].[Product Categories]', caption: 'Product Categories' },
                { name: '[Measures]', caption: 'Measures' },
            ],
            values: [
                { name: '[Measures].[Customer Count]', caption: 'Customer Count' },
                { name: '[Measures].[Internet Sales Amount]', caption: 'Internet Sales Amount' }
            ],
            filters: [
                { name: '[Date].[Fiscal]', caption: 'Date Fiscal' },
            ],
            calculatedFieldSettings: [
                {
                    name: 'BikeAndComponents',
                    formula: '([Product].[Product Categories].[Category].[Bikes] + [Product].[Product Categories].[Category].[Components] )',
                    hierarchyUniqueName: '[Product].[Product Categories]',
                    formatString: 'Standard'
                },
                {
                    name: 'Order on Discount',
                    formula: '[Measures].[Order Quantity] + ([Measures].[Order Quantity] * 0.10)',
                    formatString: 'Currency'
                }
            ]
    },
    loadOnDemandInMemberEditor: true,
    showFieldList: true,
    showGroupingBar: true,
    allowCalculatedField: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

![output](images/ondemand_member.png)

In the example above, "Customer Geography" dimension is loaded with first level (Country) during initial loading. The search will therefore be applied on the members of the "Country" level alone. After that, you can load members to the next level (State-Province) on-demand by expanding the "Australia" node (or) by selecting the "State-Province" level from the drop down list.

* When you expand "Australia", the "State-Province" members will be loaded to "Australia" alone.
* If you load the members by selecting the "State-Province" level from the drop-down list means, the "State-Province" members will be loaded across all countries like Australia, Canada, France, etc...

Once members are loaded, they are maintained internally and will not be removed until the page is refreshed.

If the property is set to **false**, all members of all levels will be queried and added during initial loading itself. Only one query is executed here to retrieve all members from all levels. Since it fetches large number of members, you can feel the performance difference while opening the member editor. But still, expand and search operation is quick here because the members have already been retrieved and populated.

![output](images/initial_member.png)

### Loading members based on level number

> This property is applicable only for OLAP data sources.

Allows user to load the members on the basis of the level number set in the [`levelCount`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filterModel/#levelcount) property in the [`filterSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettingsModel/#filtersettings). By default, this property is set to **1** and the search will only take place within the members of the first level.

{% tab template="pivot-table/pivot-table", es5Template="olap-level-count", sourceFiles="index.ts,index.html" %}

```typescript

var pivotTableObj = new ej.pivotview.PivotView({
    dataSourceSettings: {
            catalog: 'Adventure Works DW 2008 SE',
            cube: 'Adventure Works',
            providerType: 'SSAS',
            enableSorting: true,
            url: 'https://bi.syncfusion.com/olap/msmdpump.dll',
            localeIdentifier: 1033,
            rows: [
                { name: '[Customer].[Customer Geography]', caption: 'Customer Geography' },
            ],
            columns: [
                { name: '[Product].[Product Categories]', caption: 'Product Categories' },
                { name: '[Measures]', caption: 'Measures' },
            ],
            values: [
                { name: '[Measures].[Customer Count]', caption: 'Customer Count' },
                { name: '[Measures].[Internet Sales Amount]', caption: 'Internet Sales Amount' }
            ],
            filters: [
                { name: '[Date].[Fiscal]', caption: 'Date Fiscal' },
            ],
            calculatedFieldSettings: [
                {
                    name: 'BikeAndComponents',
                    formula: '([Product].[Product Categories].[Category].[Bikes] + [Product].[Product Categories].[Category].[Components] )',
                    hierarchyUniqueName: '[Product].[Product Categories]',
                    formatString: 'Standard'
                },
                {
                    name: 'Order on Discount',
                    formula: '[Measures].[Order Quantity] + ([Measures].[Order Quantity] * 0.10)',
                    formatString: 'Currency'
                }
            ],
            filterSettings: [
                {
                    name: '[Customer].[Customer Geography]', items: ['[Customer].[Customer Geography].[State-Province].&[NSW]&[AU]'], type: 'Exclude',
                    levelCount: 2
                }
            ]
    },
    showFieldList: true,
    showGroupingBar: true,
    allowCalculatedField: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

![output](images/level-count.png)

In the example above, we set [`levelCount`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filterModel/#levelcount) as **2** for the "Customer Geography" dimension in [`filterSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettingsModel/#filtersettings). So, the "Customer Geography" dimension is loaded with the "Country" and "State-Province" levels during initial loading itself. The search will therefore be applied only to the members of the "Country" and "State-Province" levels. After that, you can load members to the next level on-demand by expanding the respective "State-Province" node (or) by selecting the "City" level from the drop-down list.

## Label filtering

The label filtering helps to view the pivot table with selective header text in fields across row and column axes based on the applied filter criteria. The following are the three different types of label filtering available:

* Filtering string data type
* Filtering number data type
* Filtering date data type

The label filtering dialog can be enabled by setting the [`allowLabelFilter`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#allowlabelfilter) property in [`dataSourceSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/) to **true**. After enabling this API, click the filter icon besides any field in row or column axis available in field list or grouping bar UI. Now a filtering dialog will appear and navigate to "Label" tab to perform label filtering operations.

### Filtering string data type through code

This type of filtering is exclusively applicable for fields with members in string data type. The filtering can be configured using the [`filterSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/) through code-behind. The properties required for label filter are:

* [`name`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#name): Sets the field name.
* [`type`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#type): Sets the filter type as **Label** to the field.
* [`condition`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#condition): Sets the operator type such as **Equals**, **GreaterThan**, **LessThan**, etc.
* [`value1`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#value1): Sets the start value.
* [`value2`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#value2): Sets the end value. It is applicable only for the operator such as 'Between' and 'NotBetween'.
* [`selectedField`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filterModel/#selectedfield): Sets level name of a dimension, where the filter settings are to be applied. **NOTE: This property applicable only for OLAP data source.**

Operators that can be used in label filtering are:

| Operator | Description |
|------|-------------|
| Equals| Displays the pivot table that matches with the text.|
| DoesNotEquals| Displays the pivot table that does not match with the given text.|
| BeginWith| Displays the pivot table that begins with text.|
| DoesNotBeginWith| Displays the pivot table that does not begins with text.|
| EndsWith| Displays the pivot table that ends with text.|
| DoesNotEndsWith| Displays the pivot table that does not ends with text.|
| Contains| Displays the pivot table that contains text.|
| DoesNotContains| Displays the pivot table that does not contain text.|
| GreaterThan| Displays the pivot table when the text is greater.|
| GreaterThanOrEqualTo| Displays the pivot table when the text is greater than or equal.|
| LessThan| Displays the pivot table when the text is lesser.|
| LessThanOrEqualTo| Displays the pivot table when the text is lesser than or equal.|
| Between| Displays the pivot table that records between the start and end text.|
| NotBetween| Displays the pivot table that does not record between the start and end text.|

{% tab template="pivot-table/pivot-table", es5Template="label-filtering", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        allowLabelFilter: true,
        filterSettings: [{ name: 'Country', type: 'Label', condition: 'GreaterThan', value1: 'United Kingdom' }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        filters: []
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

### Filtering number data type through code

This type of filtering is exclusively applicable for fields with members in number data type. The filtering can be configured in a similar way explained in the previous section - "Filtering string data type through code", except the [`type`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#type) property setting. For number data type, set the [`type`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#type) property to **Number**.

For example, to show only the groups less than the value 40000, set [`Value1`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#value1) to **40000** with filter operator **LessThan** on the amount field.
<!-- markdownlint-disable MD028 -->
> Operators like **Equals**, **DoesNotEquals**, **GreaterThan**, **GreaterThanOrEqualTo**, **LessThan**, **LessThanOrEqualTo**, **Between** and **NotBetween** are alone applicable for number data type.

> Number filtering option is enabled only when the field contains the **number** format.

{% tab template="pivot-table/pivot-table", es5Template="number-filtering", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        allowLabelFilter: true,
        filterSettings: [{ name: 'Amount', type: 'Number', condition: 'LessThan', value1: '40000' }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }],
        rows: [{ name: 'Amount', caption: 'Sold Amount' }],
        filters: [{ name: 'Country' }, { name: 'Products' }]
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

### Filtering date data type through code

This type of filtering is exclusively applicable for fields with members in date data type. The filtering can be configured in a similar way explained in the prior section - "Filtering string data type through code", except the [`type`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#type) property setting. For date data type, set the [`type`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#type) property to **Date**.

For example, in a "Date" field, to show the records before the year 2016, then set [`Value1`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#value1) as **2016** and [`condition`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#condition) to **Equals** for desired output in pivot table.

Date filtering can be configured using the [`filterSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/) option through code-behind. The settings required to filter at initial rendering are:

* [`name`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#name): Sets the field name.
* [`type`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#type): Sets the filter type as **Date** to the field.
* [`condition`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#condition): Sets the operator type such as **Equals**, **Before**, **After**, etc.
* [`value1`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#value1): Sets the start date.
* [`value2`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#value2): Sets the end date. It is applicable only for the operator such as 'Between' and 'NotBetween'.
* [`selectedField`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filterModel/#selectedfield): Sets level name of a dimension, where the filter settings are to be applied. **NOTE: This property applicable only for OLAP data source.**

> Operators like **Equals**, **DoesNotEquals**, **Before**, **BeforeOrEqualTo**, **After**, **AfterOrEqualTo**, **Between**, and **NotBetween** are alone applicable for date data type.

> Date filtering option is enabled only when the field has **date** type `formatsettings`.

{% tab template="pivot-table/pivot-table", es5Template="date-filtering", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        allowLabelFilter: true,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        formatSettings: [{ name: 'Year', format: 'dd/MM/yyyy-hh:mm', type: 'date' }],
        filterSettings: [{ name: 'Year', type: 'Date', condition: 'Before', value1: new Date('2016') }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        filters: []
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

### Clearing the existing label filter

End user can clear the applied label filter by simply click the "Clear" option at the bottom of the filter dialog under "Label" tab.

![output](images/clearfilter.png)

## Value Filtering

The value filtering helps to perform filter operation based only on value fields and its resultant aggregated values over other fields defined in row and column axes.

The value filtering dialog can be enabled by setting the [`allowValueFilter`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#allowlabelfilter) property in [`dataSourceSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/) to **true**. After enabling this API, click the filter icon besides any field in row or column axis available in field list or grouping bar UI. Now a filtering dialog will appear and navigate to "Value" tab to perform value filtering operations.

Value filtering can be configured using the [`filterSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/) option through the code-behind. The settings required to filter at initial rendering are:

* [`name`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#name): Sets the normal field name.
* [`type`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#type): Sets the filter type as **Value** to the field.
* [`measure`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#measure): Sets the value field name.
* [`condition`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#condition): Sets the operator type such as equals, greater than, less than, etc.
* [`value1`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#value1): Sets the start value.
* [`value2`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/#value2): Sets the end value. It is applicable only for the operator such as 'Between' and 'NotBetween'.
* [`selectedField`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filterModel/#selectedfield): Sets level name of a dimension, where the filter settings are to be applied. **NOTE: This property applicable only for OLAP data source.**

Operators that can be used in value filtering are:

| Operator | Description |
|------|-------------|
| Equals| Displays the pivot table that matches with the value.|
| DoesNotEquals| Displays the pivot table that does not match with the given value.|
| GreaterThan| Displays the pivot table when the value is greater.|
| GreaterThanOrEqualTo| Displays the pivot table when the value is greater than or equal.|
| LessThan| Displays the pivot table when the value is lesser.|
| LessThanOrEqualTo| Displays the pivot table when the value is lesser than or equal.|
| Between| Displays the pivot table that records between start and end values.|
| NotBetween| Displays the pivot table that does not record between start and end values.|

{% tab template="pivot-table/pivot-table", es5Template="value-filtering", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        allowValueFilter: true,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        filterSettings: [{ name: 'Country', measure: 'Sold', type: 'Value', condition: 'GreaterThan', value1: '2000' }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        filters: []
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

### Clearing the existing value filter

End user can clear the applied value filter by simply click the "Clear" option at the bottom of the filter dialog under "Value" tab.

![output](images/clearvaluefilter.png)

## Event

The event [`memberFiltering`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#memberfiltering) triggers before applying filter using the dialog, that is, specifically while clicking the **"OK"** button. Using this event user can view or modify the applied [filter settings](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/) such as filter items, type of filter, conditions, etc. It has following parameters:

* `cancel` - Boolean property, when the parameter `cancel` is set to **true**, applied filtering will not be updated
* [`filterSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/) - It holds current [filter settings](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/filter/).
* `dataSourceSettings` - It holds updated datasource settings.

{% tab template="pivot-table/pivot-table", es5Template="filtering-event", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, GroupingBar, MemberFilteringEventArgs } from '@syncfusion/ej2-pivotview';
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
    memberFiltering: (args: MemberFilteringEventArgs) => {
        args.cancel = true;
        //triggers every while applying filtering in ui dialog
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

### MemberEditorOpen

The event [`memberEditorOpen`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#membereditoropen) fires while opening member editor dialog. It allows to customize the field members to be displayed in the dialog. It has the following parameters

* `fieldName`: It holds the name of the appropriate field.

* `fieldMembers`: It holds the members of a field.

* `cancel`: It is a boolean property and by setting this to true, dialog won’t be created.

In the below sample, the member editor of field "Country" shows only the selected Item.

{% tab template="pivot-table/pivot-table", es5Template="memberEditorOpen-event", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, GroupingBar, memberEditorOpenEventArgs } from '@syncfusion/ej2-pivotview';
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
    memberEditorOpen: (args: memberEditorOpenEventArgs) => {
       if (args.fieldName == 'Country') {
            args.fieldMembers = args.fieldMembers.filter((key) => {
                return (key.id == 'France' || key.id == 'Germany')
            });
       }
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}