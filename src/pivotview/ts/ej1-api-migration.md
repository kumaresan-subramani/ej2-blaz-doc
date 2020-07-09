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
| Data source | **property:** dataSource<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/>dataSource: {<br/>data: []<br/>}); | **property:** dataSourceSettings<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>dataSourceSettings: {<br/>dataSource: []<br/>}});<br/>pivotGridObj.appendTo('#PivotGrid');|
| Rows |**property:** rows<br/><br/>new ej.PivotGrid($("#PivotGrid"),{<br/>dataSource: {<br/>rows: [{fieldName: "Country",fieldCaption: "Country"}] }<br/>}); | **property:** rows<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> dataSourceSettings: {<br/>rows: [{ name: 'company', caption: 'Industry' }]}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Columns |**property:** columns<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> dataSource: {<br/>columns: [  {  fieldName: "Country",fieldCaption: "Country" } ]  }<br/>}); | **property:** columns<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> dataSourceSettings: {<br/>    columns: [{ name: 'company', caption: 'Industry' }]}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
| Values |**property:** values<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/>  dataSource: {<br/>  values: [ { fieldName: "balance", fieldCaption: "Balance($)" } ] }<br/> }); | **property:** values<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>dataSourceSettings: {<br/>values: [{ name: 'balance', caption: 'Balance($)' }]}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Filters |**property:** filters<br/><br/>new ej.PivotGrid($("#PivotGrid"),{<br/> dataSource: {<br/>filters: [ {   fieldName: "Country",  fieldCaption: "Country" } ]  }<br/> });|**property:** filters<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> dataSourceSettings: {<br/>filters:  [{ name: 'company', caption: 'Industry' }]}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Value axis position|Not Applicable|**property:** valueAxis<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>dataSourceSettings: { valueAxis: 'row'}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Aggregation

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Summary Type|**property:** summaryType<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> dataSource: {<br/>values: [ {<br/> fieldName: "balance",<br/>fieldCaption: "Balance($)",<br/>summaryType: ej.PivotAnalysis.SummaryType.Count<br/> } ] }<br/> });|**property:** type<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>    dataSourceSettings: {<br/> values: [{ name: 'balance', caption: 'Balance($)', type: 'Count' }]}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Number Format

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Format settings|**property:** format<br/><br/>$new ej.PivotGrid($("#PivotGrid"), {<br/>  dataSource: {<br/>  values: [ { fieldName: "balance", fieldCaption: "Balance($)", format: "currency" } ] }<br/> }); |**property:** formatSettings<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> dataSourceSettings: {<br/>formatSettings: [{ name: 'balance', format: 'C' },<br/> { name: 'date', format: 'dd/MM/yyyy-hh:mm', type: 'date' }]}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Summary Customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide grand totals|**property:** enableGrandTotal<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> enableGrandTotal: false<br/> });|**property:** showGrandTotals<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>dataSourceSettings: {<br/>showGrandTotals: false<br/> }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide row grand totals|**property:** enableRowGrandTotal<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> enableRowGrandTotal: false<br/> });|**property:** showRowGrandTotals<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>dataSourceSettings: {<br/>showRowGrandTotals: false<br/> }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide column grand totals|**property:** enableColumnGrandTotal<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> enableColumnGrandTotal: false<br/> });|**property:** showColumnGrandTotals<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>dataSourceSettings: {<br/>showColumnGrandTotals: false<br/> }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide sub-totals|Not Applicable|**property:** showSubTotals<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>dataSourceSettings: {<br/>showSubTotals: false<br/> }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide row sub-totals|Not Applicable|**property:** showRowSubTotals<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>dataSourceSettings: {<br/>showRowSubTotals: false<br/> }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide column sub-totals|Not Applicable|**property:** showColumnSubTotals<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>dataSourceSettings: {<br/>showColumnSubTotals: false<br/> }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
| Show/hide sub-totals for specific field|**property:** showSubTotal<br/><br/>new ej.PivotGrid($("#PivotGrid"),{<br/>dataSource: {<br/>rows: [{ fieldName: "Country", showSubTotal : false}] }<br/>}); | **property:** showSubTotals<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> dataSourceSettings: {<br/>rows: [{ name: 'company', showSubTotals: false }]}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Drill operation

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Expand All|**property:** enableCollapseByDefault<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/>  enableCollapseByDefault:true<br/> });|**property:** expandAll<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>dataSourceSettings: {<br/>expandAll: false<br/> }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Drill Up/Down|**property:** collapsedMembers<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> collapsedMembers: { Country: ["Canada", "France"] }<br/>});|**property:** drilledMembers<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> dataSourceSettings: {<br/> drilledMembers: [{ name: 'Country', items: ['France'] }]<br/> }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Field List

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide field list pop-up button on pivot table|Not Applicable|**property:** showFieldList<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> showFieldList: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Defer update|**property:** enableDeferUpdate<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> enableDeferUpdate: true<br/>});|Not Applicable|
|Control initialization|**component:** PivotSchemaDesigner<br/><br/>new ej.PivotSchemaDesigner($("#PivotSchemaDesigner"), {});<br/>|**component:** PivotFieldList<br/><br/>let fieldlistObj: PivotFieldList = new PivotFieldList({});<br/>fieldlistObj.appendTo('#FieldList');|
|Render mode|Not Applicable|**property:** renderMode<br/><br/>let fieldlistObj: PivotFieldList = new PivotFieldList({<br/>renderMode: 'Fixed'});<br/>fieldlistObj.appendTo('#FieldList');|
|Show/hide calculated field button|Not Applicable|**property:** allowCalculatedField<br/><br/>let fieldlistObj: PivotFieldList = new PivotFieldList({<br/>  allowCalculatedField: true<br/>});<br/>fieldlistObj.appendTo('#FieldList');|
|Show/hide value group button|Not Applicable|**property:** showValuesButton<br/><br/>let fieldlistObj: PivotFieldList = new PivotFieldList({<br/>showValuesButton: true<br/>});<br/>fieldlistObj.appendTo('#FieldList');|

## Grouping Bar

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide Grouping bar|**property:** enableGroupingBar<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> enableGroupingBar: true<br/>});|**property:** showGroupingBar<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> showGroupingBar: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Grouping Bar Settings|Not Applicable|**property:** groupingBarSettings<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> groupingBarSettings: {<br/>        showFilterIcon: false,<br/>showSortIcon: true,<br/>showRemoveIcon: false}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide value group button|Not Applicable|**property:** showValuesButton<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>showValuesButton: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Filtering

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Filter settings|**property:** filterItems<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> dataSource: {<br/> rows: [ {fieldName: "country",<br/>                    filterItems : {<br/> filterType: ej.PivotAnalysis.FilterType.Exclude,<br/>  values: ["Canada", "France"] }<br/> } ] }<br/>});|**property:** filterSettings<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> dataSourceSettings: {<br/> filterSettings: [{<br/> name: 'eyeColor',<br/> type: 'Exclude', items: ['blue'] }]<br/>}});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Maximum node limit in member editor

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Max node limit in member editor|**property:** maxNodeLimitInMemberEditor<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> maxNodeLimitInMemberEditor: 100<br/>});|**property:** maxNodeLimitInMemberEditor<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> maxNodeLimitInMemberEditor: 100<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## No Data Items

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide "no data" items|Not Applicable|**property:** showNoDataItems<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> dataSourceSettings: {<br/> rows: [{<br/> name: 'eyeColor', showNoDataItems: true }]<br/>}});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Excel-like filtering

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Label filtering|**property:** enableAdvancedFilter<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> enableAdvancedFilter: true,<br/> dataSource: {<br/> rows: [ {      fieldName: "country",<br/> advancedFilter : [{<br/> labelFilterOperator: ej.olap.LabelFilterOptions.EndsWith,<br/> values:  ["es"] }]<br/> }  ] }<br/> });|**property:** allowLabelFilter<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>dataSourceSettings: {<br/> allowLabelFilter: true,<br/> filterSettings: [{ <br/> name: 'product',<br/> type: 'Label', <br/> condition: 'Between',<br/> value1: 'e', <br/>value2: 'v' }]<br/>}});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Value filtering|**property:** enableAdvancedFilter<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> enableAdvancedFilter: true,<br/> dataSource: {<br/> rows: [{ {<br/> rows: [{ fieldName: "country",<br/> advancedFilter : [{<br/> measure: "balance",<br/>valueFilterOperator: ej.olap.ValueFilterOptions.GreaterThan,<br/> values:  ["200"] }]<br/> } ]}<br/> });|**property:** allowValueFilter<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>dataSourceSettings: {<br/>allowValueFilter: true,<br/>filterSettings: [{ <br/> name: 'product',<br/> measure: 'quantity',<br/> type: 'Value', <br/>condition: 'Between',<br/> value1: '3250',<br/>value2: '5000' }]<br/>}});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Sorting

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Enable/disable sorting|Not Applicable|**property:** enableSorting<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> dataSourceSettings: {<br/> enableSorting: false<br/>}});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Sort settings|**property:** sortOrder<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/>dataSource: { <br/>      rows: [{<br/> fieldName: "Country",<br/> sortOrder : ej.PivotAnalysis.SortOrder.Descending }]<br/> } });<br/>|**property:** sortSettings<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> dataSourceSettings: {<br/> sortSettings: [{<br/> name: 'company',<br/>order: 'Descending' }]<br/> }});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Value Sorting

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Enable/disable value sorting|Not Applicable|**property:** enableValueSorting<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> enableValueSorting: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Value sort settings|**property:** valueSortSettings<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/>valueSortSettings: {<br/> headerText: "Bike##Quantity",<br/>       headerDelimiters: "##",<br/>sortOrder: ej.PivotAnalysis.SortOrder.Descending }<br/>});|**property:** valueSortSettings<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> dataSourceSettings: {<br/>valueSortSettings: {<br/>headerText: 'FY 2015##Sold Amount',<br/>headerDelimiter: '##',<br/> sortOrder: 'Descending' }<br/> }});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Calculated Field

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide calculated field|Not Applicable|**property:** allowCalculatedField<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> allowCalculatedField: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Calculated field settings|**property:** values<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> dataSource: {<br/>values: [ {<br/> fieldName: "Amount", fieldCaption: "Amount"<br/>}, {<br/> fieldName: "Price",<br/>fieldCaption: "Price",<br/> isCalculatedField: true,<br/> formula: "Amount*15" }] }<br/>});|**property:** calculatedFieldSettings<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>dataSourceSettings: {<br/>values: [{<br/> name: 'Total', type: 'CalculatedField' }],<br/>    calculatedFieldSettings: [{<br/> name: 'Total', <br/> formula: '"Sum(Amount)"+"Sum(Sold)"' }]<br/>}});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Paging

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Paging|**property:** enablePaging<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> enablePaging : true<br/>});|Not Applicable|
|Virtual scrolling|**property:** enableVirtualScrolling<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> enableVirtualScrolling : true<br/> });|**property:** enableVirtualization<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> enableVirtualization: true});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Conditional Formatting

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide conditional formatting|**property:** enableConditionalFormatting<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> enableConditionalFormatting: true<br/>    });|**property:** allowConditionalFormatting<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> allowConditionalFormatting: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Conditional formatting settings|**property:** conditionalFormatSettings<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/>conditionalFormatSettings: [{<br/>name: "Format2",<br/> style: { <br/>"color": "#000000",<br/> "backgroundcolor": "#0000FF",<br/> "bordercolor": "#000000",<br/>"borderstyle": "Dashed",<br/> "borderwidth": "5",<br/> "fontsize": "12",<br/> "fontstyle": "Algerian" },<br/>condition: ej.PivotGrid.ConditionalOptions.LessThan,<br/> value: "200",<br/> measures: "Amount,Quantity" }]<br/>});|**property:** conditionalFormatSettings<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>    dataSourceSettings: {<br/>conditionalFormatSettings: [{<br/> measure: 'In Stock',<br/>value1: 5000,<br/> conditions: 'LessThan',<br/> style: {<br/>              backgroundColor: '#80cbc4',<br/> color: 'black',<br/> fontFamily: 'Tahoma',<br/>fontSize: '12px' }<br/> }]<br/>}});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Exporting

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Excel Export|Not Applicable|**property:** allowExcelExport<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> allowExcelExport: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Pdf Export|Not Applicable|**property:** allowPdfExport<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>allowPdfExport: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Grid Customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Set width for pivot table|Not Applicable|**property:** width<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>width: '800'<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Set height for pivot table|Not Applicable|**property:** height<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>height: '400'<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Set row height for pivot table|Not Applicable|**property:** rowHeight<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> gridSettings: { rowHeight: 60 }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Set column width for pivot table|Not Applicable|**property:** columnWidth<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> gridSettings: {        columnWidth: 120 }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Drag and drop column headers in pivot table|Not Applicable|**property:** allowReordering<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> gridSettings: {     allowReordering: true}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Resizing the column headers in pivot table|**property:** enableColumnResizing<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> enableColumnResizing: true<br/>});|**property:** allowResizing<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> gridSettings: { allowResizing: true }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Wrap the cell content in pivot table|Not Applicable|**property:** allowTextWrap<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> gridSettings: {       allowTextWrap: true }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Display cell border in pivot table|Not Applicable|**property:** gridLines<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> gridSettings: { gridLines:'Vertical' }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Cell selection|**property:** enableCellSelection<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> enableCellSelection: true<br/> });|**property:** allowSelection<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>gridSettings: { allowSelection: true,<br/> selectionSettings: {<br/> cellSelectionMode: 'Box',<br/> type: 'Multiple',<br/> mode: 'Cell' } }});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Display overflow cell content in pivot table|Not Applicable|**property:** clipMode<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>gridSettings: {  clipMode: 'Clip' }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Cell Editing|**property:** enableCellEditing<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> enableCellEditing:true<br/> });|Not Applicable|
|Cell double click|**property:** enableCellDoubleClick<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> enableCellDoubleClick: true<br/> });|Not Applicable|
|Cell context|**property:** enableCellContext<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/>enableCellContext: true<br/> });|Not Applicable|

## Drill Through

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide drill though feature|**property:** enableDrillThrough<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> enableDrillThrough: true<br/>});|**property:** allowDrillThrough<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> allowDrillThrough: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers when cell clicked in pivot table widget|**event:** drillThrough<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/>drillThrough: function() {}<br/>});|**event:** drillThrough<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> drillThrough: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Cell Editing

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Edit settings|Not Applicable|**property:** editSettings<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> editSettings: { }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide cell editing feature|**property:** enableCellEditing<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> enableCellEditing: true<br/>});|**property:** allowEditing<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> editSettings: {<br/>allowAdding: true, allowDeleting: true, allowEditing: true, mode: 'Normal'<br/>}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Hyperlink

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Hyperlink settings|**property:** hyperlinkSettings<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> hyperlinkSettings:  { }<br/>});|**property:** hyperlinkSettings<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> hyperlinkSettings: { }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide hyperlink to all cells|Not Applicable|**property:** showHyperlink<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> hyperlinkSettings: {<br/>showHyperlink: true }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide hyperlink to row headers|**property:** enableRowHeaderHyperlink<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> hyperlinkSettings:  {<br/>enableRowHeaderHyperlink: true }<br/>});|**property:** showRowHeaderHyperlink<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> hyperlinkSettings: {<br/>showRowHeaderHyperlink: true }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide hyperlink to column headers|**property:** enableColumnHeaderHyperlink<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> hyperlinkSettings:  {<br/>enableColumnHeaderHyperlink: true }<br/>});|**property:** showColumnHeaderHyperlink<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> hyperlinkSettings: {<br/>showColumnHeaderHyperlink: true }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide hyperlink to value cells|**property:** enableValueCellHyperlink<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> hyperlinkSettings:  {<br/>enableValueCellHyperlink: true }<br/>});|**property:** showValueCellHyperlink<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> hyperlinkSettings: {<br/>showValueCellHyperlink: true }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide hyperlink to summary cells|**property:** enableSummaryCellHyperlink<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> hyperlinkSettings:  {<br/>enableSummaryCellHyperlink: true }<br/>});|**property:** showSummaryCellHyperlink<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> hyperlinkSettings: {<br/>showSummaryCellHyperlink: true }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide hyperlink using specific conditions|Not Applicable|**property:** conditionalSettings<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> hyperlinkSettings: {<br/>conditionalSettings: [{<br/> measure: 'Units Sold', conditions: 'Between', value1: 150, value2: 200<br/>}] }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Show/hide hyperlink for row or column|Not Applicable|**property:** headerText<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> hyperlinkSettings: {<br/>headerText: 'FY 2015.Q1.Units Sold' }<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers when row headers clicked in pivot table widget|**event:** rowHeaderHyperlinkClick<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/>rowHeaderHyperlinkClick: function() {}<br/>});|**event:** hyperlinkCellClick<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> hyperlinkCellClick: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers when column headers clicked in pivot table widget|**event:** columnHeaderHyperlinkClick<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/>columnHeaderHyperlinkClick: function() {}<br/>});|**event:** hyperlinkCellClick<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> hyperlinkCellClick: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers when value cells clicked in pivot table widget|**event:** valueCellHyperlinkClick<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/>valueCellHyperlinkClick: function() {}<br/>});|**event:** hyperlinkCellClick<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> hyperlinkCellClick: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers when summary cells clicked in pivot table widget|**event:** summaryCellHyperlinkClick<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/>summaryCellHyperlinkClick: function() {}<br/>});|**event:** hyperlinkCellClick<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> hyperlinkCellClick: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Defer Layout Update

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide defer layout update|**property:** enableDeferUpdate<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> enableDeferUpdate: true<br/>});|**property:** allowDeferLayoutUpdate<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> allowDeferLayoutUpdate: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Accessibility

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Localization|**property:** locale<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/>locale: 'es-ES'<br/> });|**property:** locale<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>locale: 'es-ES'<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Right to left|**property:** enableRTL<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> enableRTL: true<br/>});|**property:** enableRtl<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> enableRtl: true<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|

## Common

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Adding custom class to wrapper element|**property:** cssClass<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> cssClass: 'custom-class'<br/> });|**property:** cssClass<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/>cssClass: 'custom-class'<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Keeping the model values in cookies|Not Applicable|**property:**enablePersistence<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> enablePersistence: true});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event triggers when control initializing|**event:** load<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> load: function() {}<br/>});|**event:** load<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> load: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers before the pivot engine starts|**event:** beforePivotEnginePopulate<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> beforePivotEnginePopulate: function() {}<br/> });|**event:** enginePopulating<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> enginePopulating: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers after the pivot engine populated|**event:** afterPivotEnginePopulate<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> afterPivotEnginePopulate: function() {}<br/> });|**event:** enginePopulated<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> enginePopulated: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers after the control populated with data source|**event:** renderSuccess<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/> renderSuccess: function() {}<br/> });|**event:** dataBound<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> dataBound: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers after the control created|Not Applicable|**event:** created<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> created: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers when destroy the control|Not Applicable|**event:** destroyed<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> destroyed: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
|Event Triggers the cell clicked in pivot table widget|**event:** cellClick<br/><br/>new ej.PivotGrid($("#PivotGrid"), {<br/>cellClick: function() {}<br/>});|**event:** cellClick<br/><br/>let pivotGridObj: PivotView = new PivotView({<br/> cellClick: function() {}<br/>});<br/>pivotGridObj.appendTo('#PivotGrid');|
