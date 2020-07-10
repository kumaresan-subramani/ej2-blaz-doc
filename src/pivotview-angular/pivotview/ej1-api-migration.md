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
| DataSource | **property:** dataSource<br/><br/>`<ej-pivotgrid [dataSource.data]="data" [dataSource.rows]="rows" [dataSource.columns]="columns" [dataSource.values]="values"> </ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`public data; rows; columns;values;filters;`<br/>`constructor() {`<br/>`this.data = [{ Amount: 100, Country: "Canada", Date: "FY 2005", Product: "Bike", Quantity: 2, State: "Alberta" }];`<br/>`this.rows= [{ fieldName: "Country", fieldCaption: "Country" }];`<br/>`this.columns= [{ fieldName:"Product", fieldCaption: "Product" }];`<br/>`this.values= [{ fieldName: "Amount", fieldCaption: "Amount" }];`<br/>`}}` | **property:** dataSourceSettings<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions;`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`dataSource: this.pivotData,`<br/>`columns: [{ name: 'Year', caption: 'Production Year' }, { name:'Quarter' }],`<br/>`values: [{ name: 'Sold', caption: 'Units Sold' }, {name: 'Amount', caption: 'Sold Amount' }],`<br/>`rows: [{ name: 'Country' },{ name: 'Products' }]};`<br/>`}}`|
| Rows |**property:** rows<br/><br/>`<ej-pivotgrid [dataSource.rows]="rows"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`public rows;`<br/>`constructor() {`<br/>`this.rows= [{ fieldName: "Country", fieldCaption: "Country" }];`<br/>`}}` | **property:** rows<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions;`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`rows: [{ name: 'Country' },{ name: 'Products' }]};`<br/>`}}`|
|Columns |**property:** columns<br/><br/>`<ej-pivotgrid [dataSource.columns]="columns"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`public columns;`<br/>`constructor() {`<br/>`this.columns= [{ fieldName: "Product", fieldCaption: "Product" }];`<br/>`}}` | **property:** columns<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions;`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`columns: [{ name: 'Year' },{ name: 'Production Year' }]};`<br/>`}}`|
| Values |**property:** values<br/><br/>`<ej-pivotgrid [dataSource.values]="values"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`public values;`<br/>`constructor() {`<br/>`this.values= [{ fieldName: "Amount", fieldCaption: "Amount" }];`<br/>`}}`| **property:** values<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions;`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`values: [{ name: 'Amount' }]};`<br/>`}}`
|Filters |**property:** filters<br/><br/>`<ej-pivotgrid [dataSource.filters]="filters"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`public filters;`<br/>`constructor() {`<br/>`this.filters= [{ fieldName: "Product", fieldCaption: "Product" }];`<br/>`}}`|**property:** filters<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`filters: [{ name: 'Year' },{ name: 'Production Year' }]};`<br/>`}}`|
|Value axis position|Not Applicable|**property:** valueAxis<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`valueAxis: 'row';`<br/>`}}`|

## Aggregation

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Summary Type|**property:** summaryType<br/><br/>`<ej-pivotgrid [dataSource.values]="values"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`public values;`<br/>`constructor() {`<br/>`this.values= [{ fieldName: "Amount", fieldCaption: "Amount", summaryType: ej.PivotAnalysis.SummaryType.Count }];`<br/>`}}`|**property:** type<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions;`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`values: [{ name: 'Amount', type: 'Count' }]};`<br/>`}}`|

## Number Format

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Format settings|**property:** format<br/><br/>`<ej-pivotgrid [dataSource.values]="values"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`public values;`<br/>`constructor() {`<br/>`this.values= [{ fieldName: "Amount", fieldCaption: "Amount", format: "currency" }];`<br/>`}}`|**property:** formatSettings<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions;`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`formatSettings: [{ name: 'balance', format: 'C' },`<br/>`{ name: 'date', format: 'dd/MM/yyyy-hh:mm', type: 'date' }]};`<br/>`}}`|

## Summary Customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide grand totals|**property:** enableGrandTotal<br/><br/>`<ej-pivotgrid [dataSource.enableGrandTotal]="false"></ej-pivotgrid>`|**property:** showGrandTotals<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions;`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`showGrandTotals: false};`<br/>`}}`|
|Show/hide row grand totals|**property:** enableRowGrandTotal<br/><br/>`<ej-pivotgrid [dataSource.enableRowGrandTotal]="false"></ej-pivotgrid>`|**property:** showRowGrandTotals<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions;`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`showRowGrandTotals: false};`<br/>`}}`|
|Show/hide column grand totals|**property:** enableColumnGrandTotal<br/><br/>`<ej-pivotgrid [dataSource.enableColumnGrandTotal]="false"></ej-pivotgrid>`|**property:** showColumnGrandTotals<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions;`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`showColumnGrandTotals: false};`<br/>`}}`|
|Show/hide sub-totals|Not Applicable|**property:** showSubTotals<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions;`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`showSubTotals: false};`<br/>`}}`|
|Show/hide row sub-totals|Not Applicable|**property:** showRowSubTotals<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions;`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`showRowSubTotals: false};`<br/>`}}`|
|Show/hide column sub-totals|Not Applicable|**property:** showColumnSubTotals<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions;`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`showColumnSubTotals: false};`<br/>`}}`|
| Show/hide sub-totals for specific field|**property:** showSubTotal<br/><br/>`<ej-pivotgrid [dataSource.rows]="rows"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`public rows;`<br/>`constructor() {`<br/>`this.rows= [{ name: 'company', showSubTotal: false }];`<br/>`}}` <br/>`};` | **property:** showSubTotals<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions;`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`rows: [{ name: 'company', showSubTotals: false }]`<br/>`};`<br/>`}}`|

## Drill operation

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Expand All|**property:** enableCollapseByDefault<br/><br/>`<ej-pivotgrid [enableCollapseByDefault]="true"></ej-pivotgrid>`|**property:** expandAll<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`expandAll: false;`<br/>`}}`|
|Drill Up/Down|**property:** collapsedMembers<br/><br/>`<ej-pivotgrid [collapsedMembers]="collapsedMembers"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`public collapsedMembers;`<br/>`constructor() {`<br/>`collapsedMembers: { Country: ["Canada", "France"] };`<br/>`}}`|**property:** drilledMembers<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`drilledMembers: [{ name: 'Country', items: ['France'] }];`<br/>`}}`|

## Field List

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide field list|Not Applicable|**property:** showFieldList<br/><br/>`<ejs-pivotview #pivotview id='PivotView' showFieldList='true'></ejs-pivotview>`|
|Defer update|**property:** enableDeferUpdate<br/><br/>`<ej-pivotgrid [enableDeferUpdate]="true"></ej-pivotgrid>`|Not Applicable|
|Control initialization|**component:** PivotSchemaDesigner<br/><br/>`<ej-pivotschemadesigner id="PivotSchemaDesigner1"></ej-pivotschemadesigner>`|**component:** PivotFieldList<br/><br/>`<ejs-pivotfieldlist #pivotfieldlist id='PivotFieldList' [dataSourceSettings]=dataSourceSettings></ejs-pivotfieldlist>`|
|Render mode|Not Applicable|**property:** renderMode<br/><br/>`<ejs-pivotfieldlist #pivotfieldlist id='PivotFieldList' [dataSourceSettings]=dataSourceSettings renderMode="Fixed"></ejs-pivotfieldlist>`|
|Show/hide calculated field button|Not Applicable|**property:** allowCalculatedField<br/><br/>`<ejs-pivotfieldlist #pivotfieldlist id='PivotFieldList' [dataSourceSettings]=dataSourceSettings allowCalculatedField="true"></ejs-pivotfieldlist>`|
|Show/hide values button|Not Applicable|**property:** showValuesButton<br/><br/>`<ejs-pivotfieldlist #pivotfieldlist id='PivotFieldList' [dataSourceSettings]=dataSourceSettings showValuesButton="true"></ejs-pivotfieldlist>`|

## Grouping Bar

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide Grouping bar|**property:** enableGroupingBar<br/><br/>`<ej-pivotgrid [enableGroupingBar]="true"></ej-pivotgrid>`|**property:** showGroupingBar<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings showGroupingBar='true'></ejs-pivotview>`|
|Grouping Bar Settings|Not Applicable|**property:** groupingBarSettings<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings showGroupingBar='true'[groupingBarSettings]='groupingSettings'></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public groupingSettings: GroupingBarSettings;`<br/>`ngOnInit(): void {`<br/>`this.groupingSettings = {`<br/>`showFilterIcon: false`<br/>`} as GroupingBarSettings;`<br/>`}}`|
|Show/hide values button|Not Applicable|**property:** showValuesButton<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings showValuesButton='true'></ejs-pivotview>`|

## Filtering

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Filter settings|**property:** filterItems<br/><br/>`<ej-pivotgrid [dataSource.columns]="columns"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`public columns;`<br/>`constructor() {`<br/>`this.columns= [{ fieldName: "Product", fieldCaption: "Product", filterItems: {`<br/>`filterType: ej.PivotAnalysis.FilterType.Include,`<br/>`values: ["Bike", "Car"]} }];`<br/>`}}`|**property:** filterSettings<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions;`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`filterSettings: [{ name: 'Country', type: 'Exclude', items: ['United States'] }]};`<br/>`}}`|

## Maximum node limit in member editor

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Max node limit in member editor|**property:** maxNodeLimitInMemberEditor<br/><br/>`<ej-pivotgrid [maxNodeLimitInMemberEditor]="100"></ej-pivotgrid>`|**property:** maxNodeLimitInMemberEditor<br/><br/>`<ejs-pivotview #pivotview id='PivotView' maxNodeLimitInMemberEditor='100'></ejs-pivotview>`|

## No Data Items

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide "no data" items|Not Applicable|**property:** showNoDataItems<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions;`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`rows: [{ name: 'company', showNoDataItems: true }]};`<br/>`}}`|

## Advanced filtering

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Label filtering|**property:** enableAdvancedFilter<br/><br/>`<ej-pivotgrid [dataSource.rows]="rows" [enableAdvancedFilter]="true"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`public rows;`<br/>`constructor() {`<br/>`this.rows= [{ fieldName: "Country", fieldCaption: "Country", advancedFilter : [{`<br/>`labelFilterOperator: ej.olap.LabelFilterOptions.EndsWith,`<br/>`values: ["es"] }]`<br/>`}];`<br/>`}}`|**property:** allowLabelFilter<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions;`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`allowLabelFilter: true,`<br/>`filterSettings: [{`<br/>`name: 'product',`<br/>`type: 'Label',`<br/>`condition: 'Between',`<br/>`value1: 'e',`<br/>`value2: 'v' }]`<br/>`}}`|
|Value filtering|**property:** enableAdvancedFilter<br/><br/>`<ej-pivotgrid [dataSource.rows]="rows" [enableAdvancedFilter]="true"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`public rows;`<br/>`constructor() {`<br/>`this.rows= [{ fieldName: "Country", fieldCaption: "Country", advancedFilter:[{`<br/>`valueFilterOperator: ej.olap.ValueFilterOptions.GreaterThan,`<br/>`values:  ["200"] }]`<br/>`}];`<br/>`}}`|**property:** allowValueFilter<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions;`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`allowValueFilter: true,`<br/>`filterSettings: [{`<br/>`name: 'product',`<br/>`measure: 'quantity',`<br/>`type: 'Value',`<br/>`condition: 'Between',`<br/>`value1: '3250' }]`<br/>`}}`|

## Drill Through

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide drill though feature|**property:** enableDrillThrough<br/><br/>`<ej-pivotgrid [enableDrillThrough]="true"></ej-pivotgrid>`|**property:** allowDrillThrough<br/><br/>`<ejs-pivotview #pivotview id='PivotView' allowDrillThrough='true'></ejs-pivotview>`|
|Event Triggers when cell clicked in pivot table widget|**event:** drillThrough<br/><br/>`<ej-pivotgrid (drillThrough)="onDrillThrough($event)"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`onDrillThrough(args) {}`<br/>`}`|**event:** drillThrough<br/><br/>`<ejs-pivotview #pivotview id='PivotView' (drillThrough)='onDrillThrough($event)'></ejs-pivotview>`<br/><br/>`export class AppComponent {`<br/>`onDrillThrough(args): void {}`<br/>`}`|

## Cell Editing

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Edit settings|Not Applicable|**property:** editSettings<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [editSettings]=editSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public editSettings: CellEditSettings;`<br/>`ngOnInit(): void {`<br/>`this.editSettings = {};`<br/>`}}`|
|Show/hide cell editing feature|**property:** enableCellEditing<br/><br/>`<ej-pivotgrid [enableCellEditing]="true"></ej-pivotgrid>`|**property:** allowEditing<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [editSettings]=editSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public editSettings: CellEditSettings;`<br/>`ngOnInit(): void {`<br/>`this.editSettings = {`<br/>`allowAdding: true, allowDeleting: true, allowEditing: true, mode: 'Normal'`<br/>`};`<br/>`}}`|

## Hyperlink

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Hyperlink settings|**property:** hyperlinkSettings<br/><br/>`<ej-pivotgrid [hyperlinkSettings]="hyperlinkSettings"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`public hyperlinkSettings;`<br/>`constructor() {`<br/>`this.hyperlinkSettings= {};`<br/>`}}` |**property:** hyperlinkSettings<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [hyperlinkSettings]=hyperlinkSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public hyperlinkSettings: HyperLinkSettings;`<br/>`ngOnInit(): void {`<br/>`this.hyperlinkSettings = {};`<br/>`}}`|
|Show/hide hyperlink to all cells|Not Applicable|**property:** showHyperlink<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [hyperlinkSettings]=hyperlinkSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public hyperlinkSettings: HyperLinkSettings;`<br/>`ngOnInit(): void {`<br/>`this.hyperlinkSettings = {`<br/>`showHyperlink: 'true'`<br/>`};`<br/>`}}`|
|Show/hide hyperlink to row headers|**property:** enableRowHeaderHyperlink<br/><br/>`<ej-pivotgrid [hyperlinkSettings]="hyperlinkSettings"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`public hyperlinkSettings;`<br/>`constructor() {`<br/>`this.hyperlinkSettings= { enableRowHeaderHyperlink: "true"};`<br/>`}}` |**property:** showRowHeaderHyperlink<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [hyperlinkSettings]=hyperlinkSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public hyperlinkSettings: HyperLinkSettings;`<br/>`ngOnInit(): void {`<br/>`this.hyperlinkSettings = {`<br/>`showRowHeaderHyperlink: 'true'`<br/>`};`<br/>`}}`|
|Show/hide hyperlink to column headers|**property:** enableColumnHeaderHyperlink<br/><br/>`<ej-pivotgrid [hyperlinkSettings]="hyperlinkSettings"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`public hyperlinkSettings;`<br/>`constructor() {`<br/>`this.hyperlinkSettings= { enableColumnHeaderHyperlink: "true"};`<br/>`}}` |**property:** showColumnHeaderHyperlink<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [hyperlinkSettings]=hyperlinkSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public hyperlinkSettings: HyperLinkSettings;`<br/>`ngOnInit(): void {`<br/>`this.hyperlinkSettings = {`<br/>`showColumnHeaderHyperlink: 'true'`<br/>`};`<br/>`}}`|
|Show/hide hyperlink to value cells|**property:** enableValueCellHyperlink<br/><br/>`<ej-pivotgrid [hyperlinkSettings]="hyperlinkSettings"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`public hyperlinkSettings;`<br/>`constructor() {`<br/>`this.hyperlinkSettings= { enableValueCellHyperlink: "true"};`<br/>`}}` |**property:** showValueCellHyperlink<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [hyperlinkSettings]=hyperlinkSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public hyperlinkSettings: HyperLinkSettings;`<br/>`ngOnInit(): void {`<br/>`this.hyperlinkSettings = {`<br/>`showValueCellHyperlink: 'true'`<br/>`};`<br/>`}}`|
|Show/hide hyperlink to summary cells|**property:** enableSummaryCellHyperlink<br/><br/>`<ej-pivotgrid [hyperlinkSettings]="hyperlinkSettings"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`public hyperlinkSettings;`<br/>`constructor() {`<br/>`this.hyperlinkSettings= { enableSummaryCellHyperlink: "true"};`<br/>`}}` |**property:** showSummaryCellHyperlink<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [hyperlinkSettings]=hyperlinkSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public hyperlinkSettings: HyperLinkSettings;`<br/>`ngOnInit(): void {`<br/>`this.hyperlinkSettings = {`<br/>`showSummaryCellHyperlink: 'true'`<br/>`};`<br/>`}}`|
|Show/hide hyperlink using specific conditions|Not Applicable|**property:** conditionalSettings<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [hyperlinkSettings]=hyperlinkSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public hyperlinkSettings: HyperLinkSettings;`<br/>`ngOnInit(): void {`<br/>`this.hyperlinkSettings = {`<br/>`conditionalSettings: [{`<br/>`measure: 'Units Sold', conditions: 'Between', value1: 150, value2: 200`<br/>`}]};`<br/>`}}`|
|Show/hide hyperlink for row or column|Not Applicable|**property:** headerText<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [hyperlinkSettings]=hyperlinkSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public hyperlinkSettings: HyperLinkSettings;`<br/>`ngOnInit(): void {`<br/>`this.hyperlinkSettings = {`<br/>`headerText: 'FY 2015.Q1.Units Sold'`<br/>`};`<br/>`}}`|
|Event Triggers when row headers clicked in pivot table widget|**event:** rowHeaderHyperlinkClick<br/><br/>`<EJ.PivotGrid id="PivotGrid" rowHeaderHyperlinkClick= "onRowHeaderHyperlinkClick"></EJ.PivotGrid>`<br/><br/>`function onRowHeaderHyperlinkClick(){ }`|**event:** hyperlinkCellClick<br/><br/>`<ejs-pivotview #pivotview id='PivotView' (hyperlinkCellClick)='onHyperlinkCellClick($event)'></ejs-pivotview>`<br/><br/>`export class AppComponent {`<br/>`onHyperlinkCellClick(args): void {}`<br/>`}`|
|Event Triggers when column headers clicked in pivot table widget|**event:** columnHeaderHyperlinkClick<br/><br/>`<ej-pivotgrid [dataSource]="dataSource" (columnHeaderHyperlinkClick)="onColumnHeaderHyperlinkClick($event)"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`onColumnHeaderHyperlinkClick(args) {}`<br/>`}`|**event:** hyperlinkCellClick<br/><br/>`<ejs-pivotview #pivotview id='PivotView' (hyperlinkCellClick)='onHyperlinkCellClick($event)'></ejs-pivotview>`<br/><br/>`export class AppComponent {`<br/>`onHyperlinkCellClick(args): void {}`<br/>`}`|
|Event Triggers when value cells clicked in pivot table widget|**event:** valueCellHyperlinkClick<br/><br/>`<ej-pivotgrid [dataSource]="dataSource" (valueCellHyperlinkClick)="onValueCellHyperlinkClick($event)"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`onValueCellHyperlinkClick(args) {}`<br/>`}`|**event:** hyperlinkCellClick<br/><br/>`<ejs-pivotview #pivotview id='PivotView' (hyperlinkCellClick)='onHyperlinkCellClick($event)'></ejs-pivotview>`<br/><br/>`export class AppComponent {`<br/>`onHyperlinkCellClick(args): void {}`<br/>`}`|
|Event Triggers when summary cells clicked in pivot table widget|**event:** summaryCellHyperlinkClick<br/><br/>`<ej-pivotgrid [dataSource]="dataSource" (summaryCellHyperlinkClick)="onSummaryCellHyperlinkClick($event)"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`onSummaryCellHyperlinkClick(args) {}`<br/>`}`|**event:** hyperlinkCellClick<br/><br/>`<ejs-pivotview #pivotview id='PivotView' (hyperlinkCellClick)='onHyperlinkCellClick($event)'></ejs-pivotview>`<br/><br/>`export class AppComponent {`<br/>`onHyperlinkCellClick(args): void {}`<br/>`}`|

## Defer Layout Update

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide defer layout update|**property:** enableDeferUpdate<br/><br/>`<ej-pivotgrid [enableDeferUpdate]="true"></ej-pivotgrid>`|**property:** allowDeferLayoutUpdate<br/><br/>`<ejs-pivotview #pivotview id='PivotView' allowDeferLayoutUpdate='true'></ejs-pivotview>`|

## Sorting

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Enable/disable sorting|Not Applicable|**property:** enableSorting<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`enableSorting: false;`<br/>`}}`|
|Sort settings|**property:** sortOrder<br/><br/>`<ej-pivotgrid [dataSource.rows]="rows"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`public rows;`<br/>`constructor() {`<br/>`this.rows= [{`<br/>`fieldName: "Country",`<br/>`fieldCaption: "Country",`<br/>`sortOrder: ej.PivotAnalysis.SortOrder.Descending`<br/>`}];`<br/>`}}`<br/>|**property:** sortSettings<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions;`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`sortSettings: [{`<br/>`name: 'company',`<br/>`order: 'Descending' }]};`<br/>`}}`|

## Value Sorting

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Enable/disable value sorting|Not Applicable|**property:** enableValueSorting<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings enableValueSorting='true'></ejs-pivotview>`|
|Value sort settings|**property:** valueSortSettings<br/><br/>`<ej-pivotgrid [valueSortSettings]="valueSortSettings"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`public valueSortSettings;`<br/>`constructor() {`<br/>`this.valueSortSettings= {`<br/>`headerText: "Bike##Quantity",`<br/>`headerDelimiters: "##",`<br/>`sortOrder: ej.PivotAnalysis.SortOrder.Descending`<br/>`};`<br/>`}}`|**property:** valueSortSettings<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions;`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`valueSortSettings: {`<br/>`headerText: 'FY 2015##Sold Amount',`<br/>`headerDelimiter: '##',`<br/>`sortOrder: 'Descending' }};`<br/>`}}`|

## Calculated Field

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide calculated field|Not Applicable|**property:** allowCalculatedField<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings allowCalculatedField='true'></ejs-pivotview>`|
|Calculated field settings|**property:** values<br/><br/>`<ej-pivotgrid [dataSource.values]="values"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`public values;`<br/>`constructor() {`<br/>`this.values=[{`<br/>`fieldName:"Amount",`<br/>`fieldCaption:"Amount"`<br/>`},`<br/>`{`<br/>`fieldName:"Price",`<br/>`fieldCaption: "Price",`<br/>`isCalculatedField: true,`<br/>`formula: "Amount*15"}],`<br/>`}}`|**property:** calculatedFieldSettings<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings showFieldList='true' allowCalculatedField='true'></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions;`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`values: [{`<br/>`name: 'price', type: 'CalculatedField' }],`<br/>`calculatedFieldSettings: [{`<br/>`name: 'Total',`<br/>`formula: '"Sum(Amount)"+"Sum(Sold)"' }]`<br/>`};`<br/>`}}`|

## Paging

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Paging|**property:** enablePaging<br/><br/>`<ej-pivotgrid id="PivotGrid1" [enablePaging]="true"></ej-pivotgrid>`|Not Applicable|
|Virtual scrolling|**property:** enableVirtualScrolling<br/><br/>`<ej-pivotgrid id="PivotGrid1" [enableVirtualScrolling]="true">`|**property:** enableVirtualization<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings enableVirtualization='true'></ejs-pivotview>`|

## Conditional Formatting

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show/hide conditional formatting|**property:** enableConditionalFormatting<br/><br/>`<ej-pivotgrid [enableConditionalFormatting]="true"></ej-pivotgrid>`|**property:** allowConditionalFormatting<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings allowConditionalFormatting='true'></ejs-pivotview>`|
|Conditional formatting settings|**property:** conditionalFormatSettings<br/><br/>`<ej-pivotgrid [conditionalFormatSettings]="conditionalFormatSettings"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`public conditionalFormatSettings;`<br/>`constructor() {`<br/>`this.conditionalFormatSettings: [{`<br/>`name: "Format2",`<br/>`style: {`<br/>`"color": "#000000",`<br/>`"backgroundcolor": "#0000FF",`<br/>`"bordercolor": "#000000",`<br/>`"borderstyle": "Dashed",`<br/>`"borderwidth": "5",`<br/>`"fontsize": "12",`<br/>`"fontstyle": "Algerian" },`<br/>`condition: ej.PivotGrid.ConditionalOptions.LessThan,`<br/>`value: "200",`<br/>`measures: "Amount,Quantity" }];`<br/>`}}`|**property:** conditionalFormatSettings<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public dataSourceSettings: IDataOptions;`<br/>`ngOnInit(): void {`<br/>`this.dataSourceSettings = {`<br/>`conditionalFormatSettings: [{`<br/>`measure: 'In Stock',`<br/>`value1: 5000,`<br/>`conditions: 'LessThan',`<br/>`style: {`<br/>`backgroundColor: '#80cbc4',`<br/>`color: 'black',`<br/>`fontFamily: 'Tahoma',`<br/>`fontSize: '12px' }`<br/>`}]};`<br/>`}}`|

## Exporting

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Excel Export|Not Applicable|**property:** allowExcelExport<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings allowExcelExport='true'></ejs-pivotview>`|
|Pdf Export|Not Applicable|**property:** allowPdfExport<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings allowPdfExport='true'></ejs-pivotview>`|

## Grid Customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Set width for pivot table|Not Applicable|**property:** width<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings width='100%'></ejs-pivotview>`|
|Set height for pivot table|Not Applicable|**property:** height<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings height='500'></ejs-pivotview>`|
|Set row height for pivot table|Not Applicable|**property:** rowHeight<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings [gridSettings]='gridSettings'></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public gridSettings: GridSettings;`<br/>`ngOnInit(): void {`<br/>`this.gridSettings = {`<br/>`rowHeight: 60;`<br/>`} as GridSettings;`<br/>`}}`|
|Set column width for pivot table|Not Applicable|**property:** columnWidth<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings [gridSettings]='gridSettings'></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public gridSettings: GridSettings;`<br/>`ngOnInit(): void {`<br/>`this.gridSettings = {`<br/>`columnWidth: 120;`<br/>`} as GridSettings;`<br/>`}}`|
|Drag and drop column headers in pivot table|Not Applicable|**property:** allowReordering<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings [gridSettings]='gridSettings'></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public gridSettings: GridSettings;`<br/>`ngOnInit(): void {`<br/>`this.gridSettings = {`<br/>`allowReordering: true;`<br/>`} as GridSettings;`<br/>`}}`|
|Resizing the column headers in pivot table|**property:** enableColumnResizing<br/><br/>`<ej-pivotgrid [enableColumnResizing]="true"></ej-pivotgrid>`|**property:** allowResizing<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings [gridSettings]='gridSettings'></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public gridSettings: GridSettings;`<br/>`ngOnInit(): void {`<br/>`this.gridSettings = {`<br/>`allowResizing: true;`<br/>`} as GridSettings;`<br/>`}}`|
|Wrap the cell content in pivot table|Not Applicable|**property:** allowTextWrap<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings [gridSettings]='gridSettings'></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public gridSettings: GridSettings;`<br/>`ngOnInit(): void {`<br/>`this.gridSettings = {`<br/>`allowTextWrap: true;`<br/>`} as GridSettings;`<br/>`}}`|
|Display cell border in pivot table|Not Applicable|**property:** gridLines<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings [gridSettings]='gridSettings'></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public gridSettings: GridSettings;`<br/>`ngOnInit(): void {`<br/>`this.gridSettings = {`<br/>`gridLines: 'Vertical';`<br/>`} as GridSettings;`<br/>`}}`|
|Cell selection|**property:** enableCellSelection<br/><br/>`<ej-pivotgrid [enableCellSelection]="true"></ej-pivotgrid>`|**property:** allowSelection<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings [gridSettings]='gridSettings'></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public gridSettings: GridSettings;`<br/>`ngOnInit(): void {`<br/>`this.gridSettings = {`<br/>`allowSelection: true,`<br/>`selectionSettings: {`<br/>`cellSelectionMode: 'Box',`<br/>`type: 'Multiple',`<br/>`mode: 'Cell'}`<br/>`} as GridSettings;`<br/>`}}`|
|Display overflow cell content in pivot table|Not Applicable|**property:** clipMode<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings [gridSettings]='gridSettings'></ejs-pivotview>`<br/><br/>`export class AppComponent implements OnInit {`<br/>`public gridSettings: GridSettings;`<br/>`ngOnInit(): void {`<br/>`this.gridSettings = {`<br/>`clipMode: 'Clip';`<br/>`} as GridSettings;`<br/>`}}`|
|Cell Editing|**property:** enableCellEditing<br/><br/>`<ej-pivotgrid [enableCellEditing]="true"></ej-pivotgrid>`|Not Applicable|
|Cell double click|**property:** enableCellDoubleClick<br/><br/>`<ej-pivotgrid [enableCellDoubleClick]="true"></ej-pivotgrid>`|Not Applicable|
|Cell context|**property:** enableCellContext<br/><br/>`<ej-pivotgrid [enableCellContext]="true"></ej-pivotgrid>`|Not Applicable|

## Accessibility

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Localization|**property:** locale<br/><br/>`<ej-pivotgrid id="PivotGrid1" locale="fr-FR"></ej-pivotgrid>`|**property:** locale<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings locale='de-DE'></ejs-pivotview>`|
|Right to left|**property:** enableRTL<br/><br/>`<ej-pivotgrid [enableRTL]="true"></ej-pivotgrid>`|**property:** enableRtl<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings enableRtl=true></ejs-pivotview>`|

## Common

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Adding custom class to wrapper element|**property:** cssClass<br/><br/>`<ej-pivotgrid [cssClass]="custom-class"></ej-pivotgrid>`|**property:** cssClass<br/><br/>`<ejs-pivotview #pivotview id='PivotView' [dataSourceSettings]=dataSourceSettings cssClass='custom-class'></ejs-pivotview>`|
|Event triggers when control initializing|**event:** load<br/><br/>`<ej-pivotgrid [dataSource]="dataSource" (load)="onLoad($event)"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`onLoad(args) {}`<br/>`}`|**event:** load<br/><br/>`<ejs-pivotview #pivotview id='PivotView' (load)='onLoad($event)'></ejs-pivotview>`<br/><br/>`export class AppComponent {`<br/>`onLoad(): void {}`<br/>`}`|
|Event Triggers before the pivot engine starts|**event:** beforePivotEnginePopulate<br/><br/>`<ej-pivotgrid [dataSource]="dataSource" (beforePivotEnginePopulate)="onbeforePivotEnginePopulate($event)"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`onbeforePivotEnginePopulate(args) {}`<br/>`}`|**event:** enginePopulating<br/><br/>`<ejs-pivotview #pivotview id='PivotView' (load)='onLoad($event)'></ejs-pivotview>`<br/><br/>`export class AppComponent {`<br/>`onLoad(): void {}`<br/>`}`|
|Event Triggers after the pivot engine populated|**event:** afterPivotEnginePopulate<br/><br/>`<ej-pivotgrid [dataSource]="dataSource" (afterPivotEnginePopulate)="onafterPivotEnginePopulate($event)"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`onafterPivotEnginePopulate(args) {}`<br/>`}`|**event:** enginePopulated<br/><br/>`<ejs-pivotview #pivotview id='PivotView' (load)='onLoad($event)'></ejs-pivotview>`<br/><br/>`export class AppComponent {`<br/>`onLoad(): void {}`<br/>`}`|
|Event Triggers after the control populated with data source|**event:** renderSuccess<br/><br/>`<ej-pivotgrid [dataSource]="dataSource" (renderSuccess)="onrenderSuccess($event)"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`onrenderSuccess(args) {}`<br/>`}`|**event:** dataBound<br/><br/>`<ejs-pivotview #pivotview id='PivotView' (dataBound)='ondataBound($event)'></ejs-pivotview>`<br/><br/>`export class AppComponent {`<br/>`ondataBound(): void {}`<br/>`}`|
|Event Triggers after the control created|Not Applicable|**event:** created<br/><br/>`<ejs-pivotview #pivotview id='PivotView' (created)='oncreated($event)'></ejs-pivotview>`<br/><br/>`export class AppComponent {`<br/>`oncreated(): void {}`<br/>`}`|
|Event Triggers when destroy the control|Not Applicable|**event:** destroyed<br/><br/>`<ejs-pivotview #pivotview id='PivotView'(destroyed)='ondestroyed($event)'></ejs-pivotview>`<br/><br/>`export class AppComponent {`<br/>`ondestroyed(): void {}`<br/>`}`|
|Event Triggers the cell clicked in pivot table widget|**event:** cellClick<br/><br/>`<ej-pivotgrid [dataSource]="dataSource" (cellClick)="oncellClick($event)"></ej-pivotgrid>`<br/><br/>`export class PivotGridComponent {`<br/>`oncellClick(args) {}`<br/>`}`|**event:** cellClick<br/><br/>`<ejs-pivotview #pivotview id='PivotView' (cellClick)='oncellClick($event)'></ejs-pivotview>`<br/><br/>`export class AppComponent {`<br/>`oncellClick(): void {}`<br/>`}`|
|Keeping the model values in cookies|Not Applicable|**property:** enablePersistence<br/><br/>`<ejs-pivotview #pivotview id='PivotView' enablePersistence='true'></ejs-pivotview>`|
