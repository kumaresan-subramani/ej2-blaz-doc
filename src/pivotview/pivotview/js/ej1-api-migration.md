---
title: "Migration from Essential JS 1"
component: "Pivot Table"
description: "Explains the common steps for migrating from Essential JS 1 application to Essential JS 2 components especially, pivot table component."
---

# Migration from Essential JS 1

This article describes the API migration process of pivot table component from Essential JS 1 to Essential JS 2.

## Data Binding

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Data source | **property:** dataSource<br/><br/>$("#PivotGrid").ejPivotGrid({<br/>dataSource: {<br/>data: []<br/>}); | **property:** dataSourceSettings<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>dataSourceSettings: {<br/>dataSource: []<br/>}});<br/>pivotGridObj.appendTo('#PivotGrid');|
| Rows |**property:** rows<br/><br/>$("#PivotGrid").ejPivotGrid({<br/>dataSource: {<br/>rows: [{fieldName: "Country",fieldCaption: "Country"}] }<br/>}); | **property:** rows<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> dataSourceSettings: {<br/>rows: [{ name: 'company', caption: 'Industry' }]}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Columns |**property:** columns<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> dataSource: {<br/>columns: [  {  fieldName: "Country",fieldCaption: "Country" } ]  }<br/>}); | **property:** columns<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> dataSourceSettings: {<br/>    columns: [{ name: 'company', caption: 'Industry' }]}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
| Values |**property:** values<br/><br/>$("#PivotGrid").ejPivotGrid({<br/>  dataSource: {<br/>  values: [ { fieldName: "balance", fieldCaption: "Balance($)" } ] }<br/> }); | **property:** values<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>dataSourceSettings: {<br/>values: [{ name: 'balance', caption: 'Balance($)' }]}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Filters |**property:** filters<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> dataSource: {<br/>filters: [ {   fieldName: "Country",  fieldCaption: "Country" } ]  }<br/> });|**property:** filters<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> dataSourceSettings: {<br/>filters:  [{ name: 'company', caption: 'Industry' }]}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Value axis position|Not Applicable|**property:** valueAxis<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>dataSourceSettings: { valueAxis: 'row'}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Aggregation

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Summary Type|**property:** summaryType<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> dataSource: {<br/>values: [ {<br/> fieldName: "balance",<br/>fieldCaption: "Balance($)",<br/>summaryType: ej.PivotAnalysis.SummaryType.Count<br/> } ] }<br/> });|**property:** type<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>    dataSourceSettings: {<br/> values: [{ name: 'balance', caption: 'Balance($)', type: 'Count' }]}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Number Format

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Format settings|**property:** format<br/><br/>$("#PivotGrid").ejPivotGrid({<br/>  dataSource: {<br/>  values: [ { fieldName: "balance", fieldCaption: "Balance($)", format: "currency" } ] }<br/> }); |**property:** formatSettings<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> dataSourceSettings: {<br/>formatSettings: [{ name: 'balance', format: 'C' },<br/> { name: 'date', format: 'dd/MM/yyyy-hh:mm', type: 'date' }]}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Summary Customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide grand totals|**property:** enableGrandTotal<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> enableGrandTotal: false<br/> });|**property:** showGrandTotals<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>dataSourceSettings: {<br/>showGrandTotals: false<br/> }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide row grand totals|**property:** enableRowGrandTotal<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> enableRowGrandTotal: false<br/> });|**property:** showRowGrandTotals<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>dataSourceSettings: {<br/>showRowGrandTotals: false<br/> }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide column grand totals|**property:** enableColumnGrandTotal<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> enableColumnGrandTotal: false<br/> });|**property:** showColumnGrandTotals<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>dataSourceSettings: {<br/>showColumnGrandTotals: false<br/> }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide sub-totals|Not Applicable|**property:** showSubTotals<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>dataSourceSettings: {<br/>showSubTotals: false<br/> }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide row sub-totals|Not Applicable|**property:** showRowSubTotals<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>dataSourceSettings: {<br/>showRowSubTotals: false<br/> }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide column sub-totals|Not Applicable|**property:** showColumnSubTotals<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>dataSourceSettings: {<br/>showColumnSubTotals: false<br/> }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
| Show/hide sub-totals for specific field|**property:** showSubTotal<br/><br/>new ej.PivotGrid($("#PivotGrid"){<br/>dataSource: {<br/>rows: [{ fieldName: "Country", showSubTotal : false}] }<br/>}); | **property:** showSubTotals<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> dataSourceSettings: {<br/>rows: [{ name: 'company', showSubTotals: false }]}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Drill operation

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Expand All|**property:** enableCollapseByDefault<br/><br/>$("#PivotGrid").ejPivotGrid({<br/>  enableCollapseByDefault:true<br/> });|**property:** expandAll<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>dataSourceSettings: {<br/>expandAll: false<br/> }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Drill Up/Down|**property:** collapsedMembers<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> collapsedMembers: { Country: ["Canada", "France"] }<br/>});|**property:** drilledMembers<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> dataSourceSettings: {<br/> drilledMembers: [{ name: 'Country', items: ['France'] }]<br/> }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Field List

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide field list pop-up button on pivot table|Not Applicable|**property:** showFieldList<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> showFieldList: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Defer update|**property:** enableDeferUpdate<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> enableDeferUpdate: true<br/>});|Not Applicable|
|Control initialization|**component:** PivotSchemaDesigner<br/><br/>$("#PivotSchemaDesigner").ejPivotSchemaDesigner({});<br/>|**component:** PivotFieldList<br/><br/>var fieldlistObj = new ej.pivotview.PivotFieldList({});<br/>fieldlistObj.appendTo('#FieldList');|
|Render mode|Not Applicable|**property:** renderMode<br/><br/>var fieldlistObj = new ej.pivotview.PivotFieldList({<br/>renderMode: 'Fixed'});<br/>fieldlistObj.appendTo('#FieldList');|
|Show/hide calculated field button|Not Applicable|**property:** allowCalculatedField<br/><br/>var fieldlistObj = new ej.pivotview.PivotFieldList({<br/>  allowCalculatedField: true<br/>});<br/>fieldlistObj.appendTo('#FieldList');|
|Show/hide value group button|Not Applicable|**property:** showValuesButton<br/><br/>var fieldlistObj = new ej.pivotview.PivotFieldList({<br/>showValuesButton: true<br/>});<br/>fieldlistObj.appendTo('#FieldList');|

## Grouping Bar

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide Grouping bar|**property:** enableGroupingBar<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> enableGroupingBar: true<br/>});|**property:** showGroupingBar<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> showGroupingBar: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Grouping Bar Settings|Not Applicable|**property:** groupingBarSettings<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> groupingBarSettings: {<br/>        showFilterIcon: false,<br/>showSortIcon: true,<br/>showRemoveIcon: false}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide value group button|Not Applicable|**property:** showValuesButton<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>showValuesButton: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Filtering

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Filter settings|**property:** filterItems<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> dataSource: {<br/> rows: [ {fieldName: "country",<br/>                    filterItems : {<br/> filterType: ej.PivotAnalysis.FilterType.Exclude,<br/>  values: ["Canada", "France"] }<br/> } ] }<br/>});|**property:** filterSettings<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> dataSourceSettings: {<br/> filterSettings: [{<br/> name: 'eyeColor',<br/> type: 'Exclude', items: ['blue'] }]<br/>}});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Maximum node limit in member editor

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Max node limit in member editor|**property:** maxNodeLimitInMemberEditor<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> maxNodeLimitInMemberEditor: 100<br/>});|**property:** maxNodeLimitInMemberEditor<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> maxNodeLimitInMemberEditor: 100<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## No Data Items

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide "no data" items|Not Applicable|**property:** showNoDataItems<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> dataSourceSettings: {<br/> rows: [{<br/> name: 'eyeColor', showNoDataItems: true }]<br/>}});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Excel-like filtering

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Label filtering|**property:** enableAdvancedFilter<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> enableAdvancedFilter: true,<br/> dataSource: {<br/> rows: [ {      fieldName: "country",<br/> advancedFilter : [{<br/> labelFilterOperator: ej.olap.LabelFilterOptions.EndsWith,<br/> values:  ["es"] }]<br/> }  ] }<br/> });|**property:** allowLabelFilter<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>dataSourceSettings: {<br/> allowLabelFilter: true,<br/> filterSettings: [{ <br/> name: 'product',<br/> type: 'Label', <br/> condition: 'Between',<br/> value1: 'e', <br/>value2: 'v' }]<br/>}});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Value filtering|**property:** enableAdvancedFilter<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> enableAdvancedFilter: true,<br/> dataSource: {<br/> rows: [{ fieldName: "country",<br/> advancedFilter : [{<br/> measure: "balance",<br/>valueFilterOperator: ej.olap.ValueFilterOptions.GreaterThan,<br/> values:  ["200"] }]<br/> } ]}<br/> });|**property:** allowValueFilter<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>dataSourceSettings: {<br/>allowValueFilter: true,<br/>filterSettings: [{ <br/>        name: 'product',<br/> measure: 'quantity',<br/> type: 'Value', <br/>condition: 'Between',<br/> value1: '3250',<br/>value2: '5000' }]<br/>}});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Sorting

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Enable/disable sorting|Not Applicable|**property:** enableSorting<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> dataSourceSettings: {<br/> enableSorting: false<br/>}});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Sort settings|**property:** sortOrder<br/><br/>$("#PivotGrid").ejPivotGrid({<br/>dataSource: { <br/>      rows: [{<br/> fieldName: "Country",<br/> sortOrder : ej.PivotAnalysis.SortOrder.Descending }]<br/> } });<br/>|**property:** sortSettings<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> dataSourceSettings: {<br/> sortSettings: [{<br/> name: 'company',<br/>order: 'Descending' }]<br/> }});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Value Sorting

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Enable/disable value sorting|Not Applicable|**property:** enableValueSorting<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> enableValueSorting: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Value sort settings|**property:** valueSortSettings<br/><br/>$("#PivotGrid").ejPivotGrid({<br/>valueSortSettings: {<br/> headerText: "Bike##Quantity",<br/>       headerDelimiters: "##",<br/>sortOrder: ej.PivotAnalysis.SortOrder.Descending }<br/>});|**property:** valueSortSettings<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> dataSourceSettings: {<br/>valueSortSettings: {<br/>headerText: 'FY 2015##Sold Amount',<br/>headerDelimiter: '##',<br/> sortOrder: 'Descending' }<br/> }});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Calculated Field

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide calculated field|Not Applicable|**property:** allowCalculatedField<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> allowCalculatedField: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Calculated field settings|**property:** values<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> dataSource: {<br/>values: [ {<br/> fieldName: "Amount", fieldCaption: "Amount"<br/>}, {<br/> fieldName: "Price",<br/>fieldCaption: "Price",<br/> isCalculatedField: true,<br/> formula: "Amount*15" }] }<br/>});|**property:** calculatedFieldSettings<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>dataSourceSettings: {<br/>values: [{<br/> name: 'Total', type: 'CalculatedField' }],<br/>    calculatedFieldSettings: [{<br/> name: 'Total', <br/> formula: '"Sum(Amount)"+"Sum(Sold)"' }]<br/>}});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Paging

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Paging|**property:** enablePaging<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> enablePaging : true<br/>});|Not Applicable|
|Virtual scrolling|**property:** enableVirtualScrolling<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> enableVirtualScrolling : true<br/> });|**property:** enableVirtualization<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> enableVirtualization: true});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Conditional Formatting

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide conditional formatting|**property:** enableConditionalFormatting<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> enableConditionalFormatting: true<br/>    });|**property:** allowConditionalFormatting<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> allowConditionalFormatting: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Conditional formatting settings|**property:** conditionalFormatSettings<br/><br/>$("#PivotGrid").ejPivotGrid({<br/>conditionalFormatSettings: [{<br/>name: "Format2",<br/> style: { <br/>"color": "#000000",<br/> "backgroundcolor": "#0000FF",<br/> "bordercolor": "#000000",<br/>"borderstyle": "Dashed",<br/> "borderwidth": "5",<br/> "fontsize": "12",<br/> "fontstyle": "Algerian" },<br/>condition: ej.PivotGrid.ConditionalOptions.LessThan,<br/> value: "200",<br/> measures: "Amount,Quantity" }]<br/>});|**property:** conditionalFormatSettings<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>    dataSourceSettings: {<br/>conditionalFormatSettings: [{<br/> measure: 'In Stock',<br/>value1: 5000,<br/> conditions: 'LessThan',<br/> style: {<br/>              backgroundColor: '#80cbc4',<br/> color: 'black',<br/> fontFamily: 'Tahoma',<br/>fontSize: '12px' }<br/> }]<br/>}});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Exporting

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Excel Export|Not Applicable|**property:** allowExcelExport<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> allowExcelExport: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Pdf Export|Not Applicable|**property:** allowPdfExport<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>allowPdfExport: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Grid Customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Set width for pivot table|Not Applicable|**property:** width<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>width: '800'<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Set height for pivot table|Not Applicable|**property:** height<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>height: '400'<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Set row height for pivot table|Not Applicable|**property:** rowHeight<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> gridSettings: { rowHeight: 60 }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Set column width for pivot table|Not Applicable|**property:** columnWidth<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> gridSettings: {        columnWidth: 120 }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Drag and drop column headers in pivot table|Not Applicable|**property:** allowReordering<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> gridSettings: {     allowReordering: true}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Resizing the column headers in pivot table|**property:** enableColumnResizing<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> enableColumnResizing: true<br/>});|**property:** allowResizing<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> gridSettings: { allowResizing: true }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Wrap the cell content in pivot table|Not Applicable|**property:** allowTextWrap<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> gridSettings: {       allowTextWrap: true }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Display cell border in pivot table|Not Applicable|**property:** gridLines<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> gridSettings: { gridLines:'Vertical' }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Cell selection|**property:** enableCellSelection<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> enableCellSelection: true<br/> });|**property:** allowSelection<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>gridSettings: { allowSelection: true,<br/> selectionSettings: {<br/> cellSelectionMode: 'Box',<br/> type: 'Multiple',<br/> mode: 'Cell' } }});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Display overflow cell content in pivot table|Not Applicable|**property:** clipMode<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>gridSettings: {  clipMode: 'Clip' }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Cell Editing|**property:** enableCellEditing<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> enableCellEditing:true<br/> });|Not Applicable|
|Cell double click|**property:** enableCellDoubleClick<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> enableCellDoubleClick: true<br/> });|Not Applicable|
|Cell context|**property:** enableCellContext<br/><br/>$("#PivotGrid").ejPivotGrid({<br/>enableCellContext: true<br/> });|Not Applicable|

## Drill Through

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide drill though feature|**property:** enableDrillThrough<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> enableDrillThrough: true<br/>});|**property:** allowDrillThrough<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> allowDrillThrough: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers when cell clicked in pivot table widget|**event:** drillThrough<br/><br/>$("#PivotGrid").ejPivotGrid({<br/>drillThrough: function() {}<br/>});|**event:** drillThrough<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> drillThrough: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Cell Editing

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Edit settings|Not Applicable|**property:** editSettings<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> editSettings: { }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide cell editing feature|**property:** enableCellEditing<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> enableCellEditing: true<br/>});|**property:** allowEditing<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> editSettings: {<br/>allowAdding: true, allowDeleting: true, allowEditing: true, mode: 'Normal'<br/>}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Hyperlink

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Hyperlink settings|**property:** hyperlinkSettings<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> hyperlinkSettings:  { }<br/>});|**property:** hyperlinkSettings<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> hyperlinkSettings: { }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide hyperlink to all cells|Not Applicable|**property:** showHyperlink<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> hyperlinkSettings: {<br/>showHyperlink: true }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide hyperlink to row headers|**property:** enableRowHeaderHyperlink<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> hyperlinkSettings:  {<br/>enableRowHeaderHyperlink: true }<br/>});|**property:** showRowHeaderHyperlink<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> hyperlinkSettings: {<br/>showRowHeaderHyperlink: true }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide hyperlink to column headers|**property:** enableColumnHeaderHyperlink<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> hyperlinkSettings:  {<br/>enableColumnHeaderHyperlink: true }<br/>});|**property:** showColumnHeaderHyperlink<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> hyperlinkSettings: {<br/>showColumnHeaderHyperlink: true }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide hyperlink to value cells|**property:** enableValueCellHyperlink<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> hyperlinkSettings:  {<br/>enableValueCellHyperlink: true }<br/>});|**property:** showValueCellHyperlink<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> hyperlinkSettings: {<br/>showValueCellHyperlink: true }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide hyperlink to summary cells|**property:** enableSummaryCellHyperlink<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> hyperlinkSettings:  {<br/>enableSummaryCellHyperlink: true }<br/>});|**property:** showSummaryCellHyperlink<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> hyperlinkSettings: {<br/>showSummaryCellHyperlink: true }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide hyperlink using specific conditions|Not Applicable|**property:** conditionalSettings<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> hyperlinkSettings: {<br/>conditionalSettings: [{<br/> measure: 'Units Sold', conditions: 'Between', value1: 150, value2: 200<br/>}] }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide hyperlink for row or column|Not Applicable|**property:** headerText<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> hyperlinkSettings: {<br/>headerText: 'FY 2015.Q1.Units Sold' }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers when row headers clicked in pivot table widget|**event:** rowHeaderHyperlinkClick<br/><br/>$("#PivotGrid").ejPivotGrid({<br/>rowHeaderHyperlinkClick: function() {}<br/>});|**event:** hyperlinkCellClick<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> hyperlinkCellClick: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers when column headers clicked in pivot table widget|**event:** columnHeaderHyperlinkClick<br/><br/>$("#PivotGrid").ejPivotGrid({<br/>columnHeaderHyperlinkClick: function() {}<br/>});|**event:** hyperlinkCellClick<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> hyperlinkCellClick: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers when value cells clicked in pivot table widget|**event:** valueCellHyperlinkClick<br/><br/>$("#PivotGrid").ejPivotGrid({<br/>valueCellHyperlinkClick: function() {}<br/>});|**event:** hyperlinkCellClick<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> hyperlinkCellClick: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers when summary cells clicked in pivot table widget|**event:** summaryCellHyperlinkClick<br/><br/>$("#PivotGrid").ejPivotGrid({<br/>summaryCellHyperlinkClick: function() {}<br/>});|**event:** hyperlinkCellClick<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> hyperlinkCellClick: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Defer Layout Update

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide defer layout update|**property:** enableDeferUpdate<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> enableDeferUpdate: true<br/>});|**property:** allowDeferLayoutUpdate<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> allowDeferLayoutUpdate: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Accessibility

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Localization|**property:** locale<br/><br/>$("#PivotGrid").ejPivotGrid({<br/>locale: 'es-ES'<br/> });|**property:** locale<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>locale: 'es-ES'<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Right to left|**property:** enableRTL<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> enableRTL: true<br/>});|**property:** enableRtl<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> enableRtl: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Common

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Adding custom class to wrapper element|**property:** cssClass<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> cssClass: 'custom-class'<br/> });|**property:** cssClass<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/>cssClass: 'custom-class'<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Keeping the model values in cookies|Not Applicable|**property:** enablePersistence<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> enablePersistence: true});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event triggers when control initializing|**event:** load<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> load: function() {}<br/>});|**event:** load<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> load: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers before the pivot engine starts|**event:** beforePivotEnginePopulate<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> beforePivotEnginePopulate: function() {}<br/> });|**event:** enginePopulating<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> enginePopulating: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers after the pivot engine populated|**event:** afterPivotEnginePopulate<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> afterPivotEnginePopulate: function() {}<br/> });|**event:** enginePopulated<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> enginePopulated: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers after the control populated with data source|**event:** renderSuccess<br/><br/>$("#PivotGrid").ejPivotGrid({<br/> renderSuccess: function() {}<br/> });|**event:** dataBound<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> dataBound: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers after the control created|Not Applicable|**event:** created<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> created: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers when destroy the control|Not Applicable|**event:** destroyed<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> destroyed: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers the cell clicked in pivot table widget|**event:** cellClick<br/><br/>$("#PivotGrid").ejPivotGrid({<br/>cellClick: function() {}<br/>});|**event:** cellClick<br/><br/>var pivotGridObj = new ej.pivotview.PivotView({<br/> cellClick: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
