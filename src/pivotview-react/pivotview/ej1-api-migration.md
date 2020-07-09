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
| Data source | **property:** dataSource<br/><br/>`<EJ.PivotGrid id="PivotGrid" dataSource= {pivotdataSource}></EJ.PivotGrid>`<br/><br/>`var  pivotdataSource = {`<br/>`data: []`<br/>`};`| **property:** dataSourceSettings<br/><br/>`<PivotViewComponent id='PivotView' dataSourceSettings={dataSourceSettings}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`dataSource: [] as IDataSet[]` <br/>`};`|
| Rows |**property:** rows<br/><br/>`<EJ.PivotGrid id="PivotGrid" dataSource= {pivotdataSource}></EJ.PivotGrid>`<br/><br/>`var  pivotdataSource = {`<br/>`rows: [{`<br/>`fieldName: "Country", fieldCaption: "Country"}]`<br/>`};` | **property:** rows<br/><br/>`<PivotViewComponent id='PivotView' dataSourceSettings={dataSourceSettings}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`row: [{`<br/> `name: 'company', caption: 'Industry' }]` <br/>`};`|
| Columns |**property:** columns<br/><br/>`<EJ.PivotGrid id="PivotGrid" dataSource= {pivotdataSource}></EJ.PivotGrid>`<br/><br/>`var  pivotdataSource = {`<br/>`columns: [{`<br/>`fieldName: "Country", fieldCaption: "Country"}]`<br/>`};` | **property:** columns<br/><br/>`<PivotViewComponent id='PivotView' dataSourceSettings={dataSourceSettings}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`columns: [{`<br/> `name: 'company', caption: 'Industry' }]` <br/>`};`|
| Values |**property:** values<br/><br/>`<EJ.PivotGrid id="PivotGrid" dataSource= {pivotdataSource}></EJ.PivotGrid>`<br/><br/>`var  pivotdataSource = {`<br/>`values: [ {`<br/> `fieldName: "balance", fieldCaption: "Balance($)"}]`<br/> `};` | **property:** values<br/><br/>`<PivotViewComponent id='PivotView' dataSourceSettings={dataSourceSettings}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`values: [{`<br/> `name: 'balance', caption: 'Balance($)' }]`<br/>`};`|
|Filters |**property:** filters<br/><br/>`<EJ.PivotGrid id="PivotGrid" dataSource= {pivotdataSource}></EJ.PivotGrid>`<br/><br/>`var  pivotdataSource = {`<br/>`filters: [{`<br/>`fieldName: "Country",  fieldCaption: "Country" }]`<br/>`};`|**property:** filters<br/><br/>`<PivotViewComponent id='PivotView' dataSourceSettings={dataSourceSettings}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`filters: [{`<br/> `name: 'company', caption: 'Industry'}]`<br/>`};`|
|Value axis position|Not Applicable|**property:** valueAxis<br/><br/>`<PivotViewComponent id='PivotView' dataSourceSettings={dataSourceSettings}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`valueAxis: 'row'`<br/>`};`|

## Aggregation

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Summary Type|**property:** summaryType<br/><br/>`<EJ.PivotGrid id="PivotGrid" dataSource= {pivotdataSource}></EJ.PivotGrid>`<br/><br/>`var  pivotdataSource = {`<br/>`values: [{`<br/> `fieldName: "balance",`<br/>`fieldCaption: "Balance($)",`<br/>`summaryType: ej.PivotAnalysis.SummaryType.Count }]`<br/>`};`|**property:** type<br/><br/>`<PivotViewComponent id='PivotView' dataSourceSettings={dataSourceSettings}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`values: [{`<br/>`name: 'balance', caption: 'Balance($)', type: 'Count' }]`<br/>`};`|

## Number Format

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Format settings|**property:** format<br/><br/>`<EJ.PivotGrid id="PivotGrid" dataSource= {pivotdataSource}></EJ.PivotGrid>`<br/><br/>`var  pivotdataSource = {`<br/>`values: [{`<br/> `fieldName: "balance",`<br/>`fieldCaption: "Balance($)",`<br/>`format: "currency" }]`<br/>`};`|**property:** formatSettings<br/><br/>`<PivotViewComponent id='PivotView' dataSourceSettings={dataSourceSettings}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`formatSettings: [{`<br/>`name: 'balance', format: 'C' },`<br/>`{ name: 'date', format: 'dd/MM/yyyy-hh:mm', type: 'date' }]`<br/>`};`|

## Summary Customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide grand totals|**property:** enableGrandTotal<br/><br/>`<EJ.PivotGrid id="PivotGrid" dataSource= {pivotdataSource}></EJ.PivotGrid>`<br/><br/>`var  pivotdataSource = {`<br/>`enableGrandTotal: false`<br/>`};`|**property:** showGrandTotals<br/><br/>`<PivotViewComponent id='PivotView' dataSourceSettings={dataSourceSettings}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`showGrandTotals: false`<br/>`};`|
|Show/hide row grand totals|**property:** enableRowGrandTotal<br/><br/>`<EJ.PivotGrid id="PivotGrid" dataSource= {pivotdataSource}></EJ.PivotGrid>`<br/><br/>`var  pivotdataSource = {`<br/>`enableRowGrandTotal: false`<br/>`};`|**property:** showRowGrandTotals<br/><br/>`<PivotViewComponent id='PivotView' dataSourceSettings={dataSourceSettings}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`showRowGrandTotals: false`<br/>`};`|
|Show/hide column grand totals|**property:** enableColumnGrandTotal<br/><br/>`<EJ.PivotGrid id="PivotGrid" dataSource= {pivotdataSource}></EJ.PivotGrid>`<br/><br/>`var  pivotdataSource = {`<br/>`enableColumnGrandTotal: false`<br/>`};`|**property:** showColumnGrandTotals<br/><br/>`<PivotViewComponent id='PivotView' dataSourceSettings={dataSourceSettings}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`showColumnGrandTotals: false`<br/>`};`|
|Show/hide sub-totals|Not Applicable|**property:** showSubTotals<br/><br/>`<PivotViewComponent id='PivotView' dataSourceSettings={dataSourceSettings}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`showSubTotals: false`<br/>`};`|
|Show/hide row sub-totals|Not Applicable|**property:** showRowSubTotals<br/><br/>`<PivotViewComponent id='PivotView' dataSourceSettings={dataSourceSettings}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`showRowSubTotals: false`<br/>`};`|
|Show/hide column sub-totals|Not Applicable|**property:** showColumnSubTotals<br/><br/>`<PivotViewComponent id='PivotView' dataSourceSettings={dataSourceSettings}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`showColumnSubTotals: false`<br/>`};`|
| Show/hide sub-totals for specific field|**property:** showSubTotal<br/><br/>`<EJ.PivotGrid id="PivotGrid" dataSource= {pivotdataSource}></EJ.PivotGrid>`<br/><br/>`var  pivotdataSource = {`<br/>`rows: [{ name: 'company', showSubTotal: false }]`<br/>`};` | **property:** showSubTotals<br/><br/>`<PivotViewComponent id='PivotView' dataSourceSettings={dataSourceSettings}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`rows: [{ name: 'company', showSubTotals: false }]`<br/>`};`|

## Drill operation

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Expand All|**property:** enableCollapseByDefault<br/><br/>`<EJ.PivotGrid id="PivotGrid" enableCollapseByDefault= {true}></EJ.PivotGrid>`|**property:** expandAll<br/><br/>`<PivotViewComponent id='PivotView' dataSourceSettings={dataSourceSettings}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`expandAll: false`<br/>`};`|
|Drill Up/Down|**property:** collapsedMembers<br/><br/>`<EJ.PivotGrid id="PivotGrid" collapsedMembers= {collapsedMembers}></EJ.PivotGrid>`<br/><br/>`var  collapsedMembers = {`<br/>`Country: ["Canada", "France"]`<br/>`};`|**property:** drilledMembers<br/><br/>`<PivotViewComponent id='PivotView' dataSourceSettings={dataSourceSettings}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`drilledMembers: [{`<br/>`name: 'Country',`<br/>`items: ['France'] }]`<br/>`};`|

## Field List

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide field list pop-up button on pivot table|Not Applicable|**property:** showFieldList<br/><br/>`<PivotViewComponent id='PivotView' showFieldList={true}></PivotViewComponent>`|
|Defer update|**property:** enableDeferUpdate<br/><br/>`<EJ.PivotGrid id="PivotGrid" enableDeferUpdate= {true}></EJ.PivotGrid>`|Not Applicable|
|Control initialization|**component:** PivotSchemaDesigner<br/><br/>`<EJ.PivotSchemaDesigner id="PivotSchemaDesigner"></EJ.PivotSchemaDesigner>`|**component:** PivotFieldListComponent<br/><br/>`<PivotFieldListComponent id='PivotFieldList'>    </PivotFieldListComponent>`|
|Render mode|Not Applicable|**property:** renderMode<br/><br/>`<PivotFieldListComponent id='PivotFieldList' renderMode= {'Fixed'}></PivotFieldListComponent>`|
|Show/hide calculated field button|Not Applicable|**property:** allowCalculatedField<br/><br/>`<PivotFieldListComponent id='PivotFieldList' allowCalculatedField={true}></PivotFieldListComponent>`|
|Show/hide value group button|Not Applicable|**property:** showValuesButton<br/><br/>>`<PivotFieldListComponent id='PivotFieldList' showValuesButton={true}></PivotFieldListComponent>`|

## Grouping Bar

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide Grouping bar|**property:** enableGroupingBar<br/><br/>`<EJ.PivotGrid id="PivotGrid" enableGroupingBar= {true}></EJ.PivotGrid>`|**property:** showGroupingBar<br/><br/>`<PivotViewComponent id='PivotView' showGroupingBar={true}></PivotViewComponent>`|
|Grouping Bar Settings|Not Applicable|**property:** groupingBarSettings<br/><br/>`<PivotViewComponent id='PivotView' groupingBarSettings={groupingBarSettings}></PivotViewComponent>`<br/><br/>`let groupingBarSettings: GroupingBarSettings = {`<br/>`showFilterIcon: false,`<br/>`showSortIcon: true,`<br/>`showRemoveIcon: false`<br/>`};`|
|Show/hide value group button|Not Applicable|**property:** showValuesButton<br/><br/>`<PivotFieldListComponent id='PivotFieldList' showValuesButton={true}></PivotFieldListComponent>`|

## Filtering

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Filter settings|**property:** filterItems<br/><br/>`<EJ.PivotGrid id="PivotGrid" dataSource= {pivotdataSource}></EJ.PivotGrid>`<br/><br/>`var  pivotdataSource = {`<br/>`rows: [{`<br/>`fieldName: "Country", fieldCaption: "Country",`<br/>`filterItems : {`<br/> `filterType: ej.PivotAnalysis.FilterType.Exclude,`<br/>`values: ["Canada", "France"] }`<br/>`}]};`|**property:** filterSettings<br/><br/>`<PivotViewComponent id="PivotGrid" dataSource= {dataSource}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`filterSettings: [{`<br/>`name: 'eyeColor',`<br/>`type: 'Exclude',`<br/>`items: ['blue'] }]`<br/>`};`|

## Maximum node limit in member editor

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Max node limit in member editor|**property:** maxNodeLimitInMemberEditor<br/><br/>`<EJ.PivotGrid id="PivotGrid" maxNodeLimitInMemberEditor= {100}></EJ.PivotGrid>`|**property:** maxNodeLimitInMemberEditor<br/><br/>`<PivotViewComponent id='PivotView' maxNodeLimitInMemberEditor={100}></PivotViewComponent>`|

## No Data Items

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide "no data" items|Not Applicable|**property:** showNoDataItems<br/><br/>`<PivotViewComponent id='PivotView' dataSourceSettings={dataSourceSettings}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`rows: [{ name: 'company', showNoDataItems: true }]`<br/>`};`|

## Excel-like filtering

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Label filtering|**property:** enableAdvancedFilter<br/><br/>`<EJ.PivotGrid id="PivotGrid" enableAdvancedFilter={true} dataSource= {pivotdataSource}></EJ.PivotGrid>`<br/><br/>`var  pivotdataSource = {`<br/>`rows: [{`<br/>`fieldName: "Country", fieldCaption: "Country",`<br/>`advancedFilter : [{`<br/>`labelFilterOperator: ej.olap.LabelFilterOptions.EndsWith,`<br/>`values: ["es"] ]}`<br/>`}]};`|**property:** allowLabelFilter<br/><br/>`<PivotViewComponent id="PivotGrid"  allowLabelFilter= {true} dataSource= {dataSource}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`filterSettings: [{`<br/>`name: 'product',`<br/>`type: 'Label',`<br/>`condition: 'Between',`<br/>`value1: 'e', value2: 'v' }]`<br/>`};`|
|Value filtering|**property:** enableAdvancedFilter<br/><br/>`<EJ.PivotGrid id="PivotGrid" enableAdvancedFilter={true} dataSource= {pivotdataSource}></EJ.PivotGrid>`<br/><br/>`var  pivotdataSource = {`<br/>`rows: [{`<br/>`fieldName: "Country", fieldCaption: "Country",`<br/>`advancedFilter : [{`<br/>`measure: "balance",`<br/>`valueFilterOperator: ej.olap.ValueFilterOptions.GreaterThan,`<br/>`values: ["200"] ]}`<br/>`}]};`|**property:** allowValueFilter<br/><br/>`<PivotViewComponent id="PivotGrid"  allowValueFilter= {true} dataSource= {dataSource}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`filterSettings: [{`<br/>`name: 'product',`<br/>`measure: 'quantity',`<br/>`type: 'Value',`<br/>`condition: 'Between',`<br/>`value1: '3250',`<br/>`value2: '5000' }]`<br/>`};`|

## Drill Through

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide drill though feature|**property:** enableDrillThrough<br/><br/>`<EJ.PivotGrid id="PivotGrid" enableDrillThrough= {true}></EJ.PivotGrid>`|**property:** allowDrillThrough<br/><br/>`<PivotViewComponent id='PivotView' allowDrillThrough={true}></PivotViewComponent>`|
|Event Triggers when cell clicked in pivot table control|**event:** drillThrough<br/><br/>`<EJ.PivotGrid id="PivotGrid" drillThrough= "onDrillThrough"></EJ.PivotGrid>`<br/><br/>`function onDrillThrough(){ }`|**event:** drillThrough<br/><br/>`<PivotViewComponent id="PivotGrid" drillThrough= this.onDrillThrough.bind(this)></PivotViewComponent>`<br/><br/>`onDrillThrough(): void { }`|

## Cell Editing

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Edit settings|Not Applicable|**property:** editSettings<br/><br/>`<PivotViewComponent id='PivotView' editSettings={}></PivotViewComponent>`|
|Show/hide cell editing feature|**property:** enableCellEditing<br/><br/>`<EJ.PivotGrid id="PivotGrid" enableCellEditing= {true}></EJ.PivotGrid>`|**property:** allowEditing<br/><br/>`<PivotViewComponent id='PivotView' editSettings={editSettings}></PivotViewComponent>`<br/><br/>`let editSettings: CellEditSettings = {`<br/>`allowAdding: true, allowDeleting: true, allowEditing: true, mode: 'Normal'`<br/>`};`|

## Hyperlink

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Hyperlink settings|**property:** hyperlinkSettings<br/><br/>`<EJ.PivotGrid id="PivotGrid" hyperlinkSettings= {}></EJ.PivotGrid>`|**property:** hyperlinkSettings<br/><br/>`<PivotViewComponent id='PivotView' hyperlinkSettings={}></PivotViewComponent>`|
|Show/hide hyperlink to all cells|Not Applicable|**property:** showHyperlink<br/><br/>`<PivotViewComponent id='PivotView' hyperlinkSettings={hyperlinkSettings}></PivotViewComponent>`<br/><br/>`let hyperlinkSettings: HyperLinkSettings = {`<br/>`showHyperlink: 'true'`<br/>`};`|
|Show/hide hyperlink to row headers|**property:** enableRowHeaderHyperlink<br/><br/>`<EJ.PivotGrid id="PivotGrid" hyperlinkSettings= {`<br/>`enableRowHeaderHyperlink: true`<br/>`}></EJ.PivotGrid>`|**property:** showRowHeaderHyperlink<br/><br/>`<PivotViewComponent id='PivotView' hyperlinkSettings={hyperlinkSettings}></PivotViewComponent>`<br/><br/>`let hyperlinkSettings: HyperLinkSettings = {`<br/>`showRowHeaderHyperlink: 'true'`<br/>`};`|
|Show/hide hyperlink to column headers|**property:** enableColumnHeaderHyperlink<br/><br/>`<EJ.PivotGrid id="PivotGrid" hyperlinkSettings= {`<br/>`enableColumnHeaderHyperlink: true`<br/>`}></EJ.PivotGrid>`|**property:** showColumnHeaderHyperlink<br/><br/>`<PivotViewComponent id='PivotView' hyperlinkSettings={hyperlinkSettings}></PivotViewComponent>`<br/><br/>`let hyperlinkSettings: HyperLinkSettings = {`<br/>`showColumnHeaderHyperlink: 'true'`<br/>`};`|
|Show/hide hyperlink to value cells|**property:** enableValueCellHyperlink<br/><br/>`<EJ.PivotGrid id="PivotGrid" hyperlinkSettings= {`<br/>`enableValueCellHyperlink: true`<br/>`}></EJ.PivotGrid>`|**property:** showValueCellHyperlink<br/><br/>`<PivotViewComponent id='PivotView' hyperlinkSettings={hyperlinkSettings}></PivotViewComponent>`<br/><br/>`let hyperlinkSettings: HyperLinkSettings = {`<br/>`showValueCellHyperlink: 'true'`<br/>`};`|
|Show/hide hyperlink to summary cells|**property:** enableSummaryCellHyperlink<br/><br/>`<EJ.PivotGrid id="PivotGrid" hyperlinkSettings= {`<br/>`enableSummaryCellHyperlink: true`<br/>`}></EJ.PivotGrid>`|**property:** showSummaryCellHyperlink<br/><br/>`<PivotViewComponent id='PivotView' hyperlinkSettings={hyperlinkSettings}></PivotViewComponent>`<br/><br/>`let hyperlinkSettings: HyperLinkSettings = {`<br/>`showSummaryCellHyperlink: 'true'`<br/>`};`|
|Show/hide hyperlink using specific conditions|Not Applicable|**property:** conditionalSettings<br/><br/>`<PivotViewComponent id='PivotView' hyperlinkSettings={hyperlinkSettings}></PivotViewComponent>`<br/><br/>`let hyperlinkSettings: HyperLinkSettings = {`<br/>`conditionalSettings: [{`<br/>`measure: 'Units Sold', conditions: 'Between', value1: 150, value2: 200`<br/>`}] };`|
|Show/hide hyperlink for row or column|Not Applicable|**property:** headerText<br/><br/>`<PivotViewComponent id='PivotView' hyperlinkSettings={hyperlinkSettings}></PivotViewComponent>`<br/><br/>`let hyperlinkSettings: HyperLinkSettings = {`<br/>`headerText: 'FY 2015.Q1.Units Sold'`<br/>`};`|
|Event Triggers when row headers clicked in pivot table|**event:** rowHeaderHyperlinkClick<br/><br/>`<EJ.PivotGrid id="PivotGrid" rowHeaderHyperlinkClick= "onRowHeaderHyperlinkClick"></EJ.PivotGrid>`<br/><br/>`function onRowHeaderHyperlinkClick(){ }`|**event:** hyperlinkCellClick<br/><br/>`<PivotViewComponent id="PivotGrid" hyperlinkCellClick= this.onHyperlinkCellClick.bind(this)></PivotViewComponent>`<br/><br/>`onHyperlinkCellClick(): void { }`|
|Event Triggers when column headers clicked in pivot table|**event:** columnHeaderHyperlinkClick<br/><br/>`<EJ.PivotGrid id="PivotGrid" columnHeaderHyperlinkClick= "onColumnHeaderHyperlinkClick"></EJ.PivotGrid>`<br/><br/>`function onColumnHeaderHyperlinkClick(){ }`|**event:** hyperlinkCellClick<br/><br/>`<PivotViewComponent id="PivotGrid" hyperlinkCellClick= this.onHyperlinkCellClick.bind(this)></PivotViewComponent>`<br/><br/>`onHyperlinkCellClick(): void { }`|
|Event Triggers when value cells clicked in pivot table|**event:** valueCellHyperlinkClick<br/><br/>`<EJ.PivotGrid id="PivotGrid" valueCellHyperlinkClick= "onValueCellHyperlinkClick"></EJ.PivotGrid>`<br/><br/>`function onValueCellHyperlinkClick(){ }`|**event:** hyperlinkCellClick<br/><br/>`<PivotViewComponent id="PivotGrid" hyperlinkCellClick= this.onHyperlinkCellClick.bind(this)></PivotViewComponent>`<br/><br/>`onHyperlinkCellClick(): void { }`|
|Event Triggers when summary cells clicked in pivot table|**event:** summaryCellHyperlinkClick<br/><br/>`<EJ.PivotGrid id="PivotGrid" summaryCellHyperlinkClick= "onSummaryCellHyperlinkClick"></EJ.PivotGrid>`<br/><br/>`function onSummaryCellHyperlinkClick(){ }`|**event:** hyperlinkCellClick<br/><br/>`<PivotViewComponent id="PivotGrid" hyperlinkCellClick= this.onHyperlinkCellClick.bind(this)></PivotViewComponent>`<br/><br/>`onHyperlinkCellClick(): void { }`|

## Defer Layout Update

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide defer layout update|**property:** enableDeferUpdate<br/><br/>`<EJ.PivotGrid id="PivotGrid" enableDeferUpdate= {true}></EJ.PivotGrid>`|**property:** allowDeferLayoutUpdate<br/><br/>`<PivotViewComponent id='PivotView' allowDeferLayoutUpdate={true}></PivotViewComponent>`|

## Sorting

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Enable/disable sorting|Not Applicable|**property:** enableSorting<br/><br/>`<PivotViewComponent id="PivotGrid" dataSource= {dataSource}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`enableSorting: false`<br/>`};`|
|Sort settings|**property:** sortOrder<br/><br/>`<EJ.PivotGrid id="PivotGrid" dataSource= {pivotdataSource}></EJ.PivotGrid>`<br/><br/>`var  pivotdataSource = {`<br/>`rows: [{`<br/>`fieldName: "Country",`<br/>`sortOrder : ej.PivotAnalysis.SortOrder.Descending}]`<br/>`};`|**property:** sortSettings<br/><br/>`<PivotViewComponent id="PivotGrid" dataSource= {dataSource}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`sortSettings: [{`<br/>`name: 'company',`<br/>`order: 'Descending'}]`<br/>`};`|

## Value Sorting

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Enable/disable value sorting|Not Applicable|**property:** enableSorting<br/><br/>`<PivotViewComponent id="PivotGrid" enableValueSorting= {true}></PivotViewComponent>`|
|Value sort settings|**property:** valueSortSettings<br/><br/>`<EJ.PivotGrid id="PivotGrid" valueSortSettings= {valueSortSettings}></EJ.PivotGrid>`<br/><br/>`var  valueSortSettings = {`<br/>`headerText: "Bike##Quantity",`<br/>`headerDelimiters: "##",`<br/>`sortOrder: ej.PivotAnalysis.SortOrder.Descending`<br/>`};`|**property:** valueSortSettings<br/><br/>`<PivotViewComponent id="PivotGrid" dataSource= {dataSource}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`valueSortSettings: {`<br/>`headerText: 'FY 2015##Sold Amount',`<br/>`headerDelimiter: '##',`<br/>`sortOrder: 'Descending' }`<br/>`};`|

## Calculated Field

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide calculated field|Not Applicable|**property:** allowCalculatedField<br/><br/>`<PivotViewComponent id="PivotGrid" allowCalculatedField= {true}></PivotViewComponent>`|
|Calculated field settings|**property:** values<br/><br/>`<EJ.PivotGrid id="PivotGrid" dataSource= {pivotdataSource}></EJ.PivotGrid>`<br/><br/>`var  pivotdataSource = {`<br/>`values: [`<br/>`{ fieldName: "Amount", fieldCaption: "Amount"},`<br/>`{ fieldName: "Price",`<br/>`fieldCaption: "Price",`<br/>`isCalculatedField: true,`<br/>`formula: "Amount*15" }]`<br/> `};` |**property:** calculatedFieldSettings<br/><br/>`<PivotViewComponent id="PivotGrid" dataSource= {dataSource}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`values: [{`<br/> `name: 'Total', type: 'CalculatedField' }],`<br/>`calculatedFieldSettings: [{`<br/>`name: 'Total',`<br/>`formula: '"Sum(Amount)"+"Sum(Sold)"' }]`<br/>`};`|

## Paging

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Paging|**property:** enablePaging<br/><br/>`<EJ.PivotGrid id="PivotGrid" enablePaging= {true}></EJ.PivotGrid>`|Not Applicable|
|Virtual scrolling|**property:** enableVirtualScrolling<br/><br/>`<EJ.PivotGrid id="PivotGrid" enableVirtualScrolling= {true}></EJ.PivotGrid>`|**property:** enableVirtualization<br/><br/>`<PivotViewComponent id="PivotGrid" enableVirtualization= {true}></PivotViewComponent>`|

## Conditional Formatting

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide conditional formatting|**property:** enableConditionalFormatting<br/><br/>`<EJ.PivotGrid id="PivotGrid" enableConditionalFormatting= {true}></EJ.PivotGrid>`|**property:** allowConditionalFormatting<br/><br/>`<PivotViewComponent id="PivotGrid" allowConditionalFormatting= {true}></PivotViewComponent>`|
|Conditional formatting settings|**property:** conditionalFormatSettings<br/><br/>`<EJ.PivotGrid id="PivotGrid" conditionalFormatSettings= {conditionalFormatSettings}></EJ.PivotGrid>`<br/><br/>`var  conditionalFormatSettings = [{`<br/>`name: "Format2",`<br/>`style: {`<br/>`"color": "#000000",`<br/>`"backgroundcolor": "#0000FF",`<br/>`"bordercolor": "#000000",`<br/>`"borderstyle": "Dashed",`<br/>`"borderwidth": "5",`<br/>`"fontsize": "12",`<br/>`"fontstyle": "Algerian" },`<br/>`condition: ej.PivotGrid.ConditionalOptions.LessThan,`<br/>`value: "200",`<br/>`measures: "Amount,Quantity" }];`|**property:** conditionalFormatSettings<br/><br/>`<PivotViewComponent id="PivotGrid" dataSource= {dataSource}></PivotViewComponent>`<br/><br/>`let dataSourceSettings: IDataOptions = {`<br/>`conditionalFormatSettings: [{`<br/>`measure: 'In Stock',`<br/>`value1: 5000,`<br/>`conditions: 'LessThan',`<br/>`style: {`<br/>`backgroundColor: '#80cbc4',`<br/> `color: 'black',`<br/> `fontFamily: 'Tahoma',`<br/>`fontSize: '12px' } }]`<br/>`};`|

## Exporting

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Excel Export|Not Applicable|**property:** allowExcelExport<br/><br/>`<PivotViewComponent id="PivotGrid" allowExcelExport= {true}></PivotViewComponent>`|
|Pdf Export|Not Applicable|**property:** allowPdfExport<br/><br/>`<PivotViewComponent id="PivotGrid" allowPdfExport= {true}></PivotViewComponent>`|

{% raw %}

## Grid Customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Set width for pivot table|Not Applicable|**property:** width<br/><br/>`<PivotViewComponent id="PivotGrid" width= {800}></PivotViewComponent>`|
|Set height for pivot table|Not Applicable|**property:** height<br/><br/>`<PivotViewComponent id="PivotGrid" height= {400}></PivotViewComponent>`|
|Set row height for pivot table|Not Applicable|**property:** rowHeight<br/><br/>`<PivotViewComponent id="PivotGrid" gridSettings= {{rowHeight: 60}}></PivotViewComponent>`|
|Set column width for pivot table|Not Applicable|**property:** columnWidth<br/><br/>`<PivotViewComponent id="PivotGrid" gridSettings= {{columnWidth: 120}}></PivotViewComponent>`|
|Drag and drop column headers in pivot table|Not Applicable|**property:** allowReordering<br/><br/>`<PivotViewComponent id="PivotGrid" gridSettings= {{allowReordering: true}}></PivotViewComponent>`|
|Resizing the column headers in pivot table|**property:** enableColumnResizing<br/><br/>`<EJ.PivotGrid id="PivotGrid" enableColumnResizing= {true}></EJ.PivotGrid>`|**property:** allowResizing<br/><br/>`<PivotViewComponent id="PivotGrid" gridSettings= {{allowResizing: true}}></PivotViewComponent>`|
|Wrap the cell content in pivot table|Not Applicable|**property:** allowTextWrap<br/><br/>`<PivotViewComponent id="PivotGrid" gridSettings= {{allowTextWrap: true}}></PivotViewComponent>`|
|Display cell border in pivot table|Not Applicable|**property:** gridLines<br/><br/>`<PivotViewComponent id="PivotGrid" gridSettings= {{gridLines:'Vertical'}}></PivotViewComponent>`|
|Cell selection|**property:** enableCellSelection<br/><br/>`<EJ.PivotGrid id="PivotGrid" enableCellSelection= {true}></EJ.PivotGrid>`|**property:** allowSelection<br/><br/>`<PivotViewComponent id="PivotGrid" gridSettings= {gridSettings}></PivotViewComponent>`<br/><br/>`let gridSettings: GridSettings = {`<br/>`allowSelection: true,`<br/>`selectionSettings: {`<br/> `cellSelectionMode: 'Box',`<br/> `type: 'Multiple',`<br/> `mode: 'Cell' }`<br/>`};`|
|Display overflow cell content in pivot table|Not Applicable|**property:** clipMode<br/><br/>`<PivotViewComponent id="PivotGrid" gridSettings= {{clipMode: 'Clip'}}></PivotViewComponent>`|
|Cell Editing|**property:** enableCellEditing<br/><br/>`<EJ.PivotGrid id="PivotGrid" enableCellEditing= {true}></EJ.PivotGrid>`|Not Applicable|
|Cell double click|**property:** enableCellDoubleClick<br/><br/>`<EJ.PivotGrid id="PivotGrid" enableCellDoubleClick= {true}></EJ.PivotGrid>`|Not Applicable|
|Cell context|**property:** enableCellContext<br/><br/>`<EJ.PivotGrid id="PivotGrid" enableCellContext= {true}></EJ.PivotGrid>`|Not Applicable|

{% endraw %}

## Accessibility

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Localization|**property:** locale<br/><br/>`<EJ.PivotGrid id="PivotGrid" locale= {'es-ES'}></EJ.PivotGrid>`|**property:** locale<br/><br/>`<PivotViewComponent id="PivotGrid" locale= {'es-ES'}></PivotViewComponent>`|
|Right to left|**property:** enableRTL<br/><br/>`<EJ.PivotGrid id="PivotGrid" enableRTL= {true}></EJ.PivotGrid>`|**property:** enableRtl<br/><br/>`<PivotViewComponent id="PivotGrid" enableRTL= {true}></PivotViewComponent>`|

## Common

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Adding custom class to wrapper element|**property:** cssClass<br/><br/>`<EJ.PivotGrid id="PivotGrid" cssClass= {"custom-class"}></EJ.PivotGrid>`|**property:** cssClass<br/><br/>`<PivotViewComponent id="PivotGrid" cssClass= {'custom-class'}></PivotViewComponent>`|
|Keeping the model values in cookies|Not Applicable|**property:** enablePersistence<br/><br/>`<PivotViewComponent id="PivotGrid" enablePersistence= {true}></PivotViewComponent>`|
|Event triggers when control initializing|**event:** load<br/><br/>`<EJ.PivotGrid id="PivotGrid" load= "onLoad"></EJ.PivotGrid>`<br/><br/>`function onLoad(){ }`|**event:** load<br/><br/>`<PivotViewComponent id="PivotGrid" load= this.onLoad.bind(this)></PivotViewComponent>`<br/><br/>`onLoad(): void { }`|
|Event Triggers before the pivot engine starts|**event:** beforePivotEnginePopulate<br/><br/>`<EJ.PivotGrid id="PivotGrid" beforePivotEnginePopulate= "onBeforePivotEnginePopulate"></EJ.PivotGrid>`<br/><br/>`function onBeforePivotEnginePopulate(){ }`|**event:** enginePopulating<br/><br/>`<PivotViewComponent id="PivotGrid" enginePopulating= this.onEnginePopulating.bind(this)></PivotViewComponent>`<br/><br/>`onEnginePopulating(): void { }`|
|Event Triggers after the pivot engine populated|**event:** afterPivotEnginePopulate<br/><br/>`<EJ.PivotGrid id="PivotGrid" afterPivotEnginePopulate= "onAfterPivotEnginePopulate"></EJ.PivotGrid>`<br/><br/>`function onAfterPivotEnginePopulate(){ }`|**event:** enginePopulated<br/><br/>`<PivotViewComponent id="PivotGrid" enginePopulated= this.onEnginePopulated.bind(this)></PivotViewComponent>`<br/><br/>`onEnginePopulated(): void { }`|
|Event Triggers after the control populated with data source|**event:** renderSuccess<br/><br/>`<EJ.PivotGrid id="PivotGrid" renderSuccess= "onRenderSuccess"></EJ.PivotGrid>`<br/><br/>`function onRenderSuccess(){ }`|**event:** dataBound<br/><br/>`<PivotViewComponent id="PivotGrid" dataBound= this.onDataBound.bind(this)></PivotViewComponent>`<br/><br/>`onDataBound(): void { }`|
|Event Triggers after the control created|Not Applicable|**event:** created<br/><br/>`<PivotViewComponent id="PivotGrid" created= this.created.bind(this)></PivotViewComponent>`<br/><br/>`created(): void { }`|
|Event Triggers when destroy the control|Not Applicable|**event:** destroyed<br/><br/>`<PivotViewComponent id="PivotGrid" destroyed= this.destroyed.bind(this)></PivotViewComponent>`<br/><br/>`destroyed(): void { }`|
|Event Triggers the cell clicked in pivot table|**event:** cellClick<br/><br/>`<EJ.PivotGrid id="PivotGrid" cellClick= "onCellClick"></EJ.PivotGrid>`<br/><br/>`function onCellClick(){ }`|**event:** cellClick<br/><br/>`<PivotViewComponent id="PivotGrid" cellClick= this.onCellClick.bind(this)></PivotViewComponent>`<br/><br/>`onCellClick(): void { }`|
