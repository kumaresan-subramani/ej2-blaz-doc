# Migration from Essential JS 1

This article describes the API migration process of  AutoComplete component from Essential JS 1 to Essential JS 2.
> MultiSelect concept is not present in EJ2-AutoComplete.  If you want to use multiselection support in autocomplete, we suggest you to use MultiSelect component.

## DataBinding

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **Default** | **Property:** *datasource* <br/>`$('#autocomplete').ejAutocomplete({ dataSource: countriesField,});`| **Property:** *dataSource*<br/>`var groupObj = new ej.dropdowns.AutoComplete({dataSource: vegetableData,});groupObj.appendTo('#vegetables');`|
| **Fields for mapping** | **Property:** *fields*<br/>`$('#autocomplete').ejAutocomplete({fields: { key: "index", text: "name" },});`| **Property:** *fields*<br/>`var groupObj = new ej.dropdowns.AutoComplete({fields: { groupBy: 'Category', value: 'Vegetable' },});groupObj.appendTo('#vegetables');` |
| **Query** | **Property**: *query*<br/>`$('#autocomplete').ejAutocomplete({query: query,});`| **Property**: *query*<br/>`var groupObj = new ej.dropdowns.AutoComplete({query: ej.Query().requiresCount(),});groupObj.appendTo('#vegetables');`|
| **Begin event** | **Event**: *actionBegin*<br/>`$('#autocomplete').ejAutocomplete({actionBegin: "actionBegin",});`|**Event**: *actionBegin*<br/> `var groupObj = new ej.dropdowns.AutoComplete({actionBegin: "actionBegin",});groupObj.appendTo('#vegetables');`|
| **Complete event** | **Event**: *actionComplete*<br/>`$('#autocomplete').ejAutocomplete({actionComplete: "actionComplete",});`|**Event**: *actionComplete* <br/> `var groupObj = new ej.dropdowns.AutoComplete({actionComplete: "actionComplete",});groupObj.appendTo('#vegetables');`|
| **Failure event** | **Event**: *actionFailure*<br/>`$('#autocomplete').ejAutocomplete({actionFailure: "actionFailure",});` |**Event**: *actionFailure* <br/> `var groupObj = new ej.dropdowns.AutoComplete({actionFailure: "actionFailure",});groupObj.appendTo('#vegetables');`|
| **Success event** | **Event**: *actionSuccess* <br/>`$('#autocomplete').ejAutocomplete({actionSuccess: "actionSuccess",});` |**Not Applicable** |

## Filtering

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **Case sensitivity** | **Property**: *caseSensitiveSearch*<br/>`$('#autocomplete').ejAutocomplete({ caseSensitiveSearch: true,});`|**Property:** *ignoreCase*<br/>`var groupObj = new ej.dropdowns.AutoComplete({ignoreCase: true,});groupObj.appendTo('#vegetables');`|
| **Accent effective search** | **Not applicable** | **Property** : *ignoreAccent* <br/>`var groupObj = new ej.dropdowns.AutoComplete({ignoreAccent: true,});groupObj.appendTo('#vegetables');`|
| **Filtering Type** | **Property:** *filterType*<br/>`$('#autocomplete').ejAutocomplete({ filterType: "Contains",});`| **Property**: *filterType*<br/>`var groupObj = new ej.dropdowns.AutoComplete({filterType: filtertype,});groupObj.appendTo('#vegetables');` |
| **Autofill** | **Property:** *enableAutoFill*<br/>`$('#autocomplete').ejAutocomplete({ enableAutoFill: true,});` | **Property:**: *autoFill* <br/>`var groupObj = new ej.dropdowns.AutoComplete({autoFill: true,});groupObj.appendTo('#vegetables');`|
| **Highlight the search word** | **Property**: *highlightSearch* `$('#autocomplete').ejAutocomplete({ highlightSearch: true,});`|**Property:** *highlight* <br/>`var groupObj = new ej.dropdowns.AutoComplete({highlight: true,});groupObj.appendTo('#vegetables');`|
| **No of items to be shown** | **Property:** *itemsCount*<br/>`$('#autocomplete').ejAutocomplete({ itemsCount: 3,});` |**Property:** *suggestionCount*<br/>`var groupObj = new ej.dropdowns.AutoComplete({suggestionCount: 5,});groupObj.appendTo('#vegetables');` |
| **Minimum characters to enter** | **Property:** *minCharacter*<br/> `$('#autocomplete').ejAutocomplete({ minCharacter: 3,});` |**Property:** *minLength* <br/>`var groupObj = new ej.dropdowns.AutoComplete({minLength: 4,});groupObj.appendTo('#vegetables');` |
| **Search** | **Method:** *search* <br/>`$("#autocomplete").ejAutocomplete("search");` | **Not applicable** |

## Placeholder

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **Watermark text** | **Property:** *watermarkText* <br/>`$('#autocomplete').ejAutocomplete({watermarkText:"select" });`| **Property:** *placeholder* <br/>`var groupObj = new ej.dropdowns.AutoComplete({placeholder: "Select",});groupObj.appendTo('#vegetables');`|
| **Floating  of watermark text** | **Not applicable**   | **Property:** *floatLabelType* <br/>`var groupObj = new ej.dropdowns.AutoComplete({floatLabelType: floatLabelType,});groupObj.appendTo('#vegetables');`|

## Popup

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **No records text** | **Property:** *emptyResultText* <br/> `$('#autocomplete').ejAutocomplete({emptyResultText:"no records" });`| **Property:** *noRecordsTemplate*<br/> `var groupObj = new ej.dropdowns.AutoComplete({noRecordsTemplate: noRecordsTemplate,});groupObj.appendTo('#vegetables');`|
| **No records showing** | **Property:** *showEmptyResultText*<br/> `$('#autocomplete').ejAutocomplete({showEmptyResultText:true })` | **Not applicable** |
| **Popupbutton** | **Property:** *showPopupButton*<br/> `$('#autocomplete').ejAutocomplete({ShowPopupButton:true })` | **Property:** *showPopupButton*<br/>  `var groupObj = new ej.dropdowns.AutoComplete({showPopupButton: true,});groupObj.appendTo('#vegetables');`|
| **Clear button** | **Property:** *showResetIcon* <br/> `$('#autocomplete').ejAutocomplete({showResetIcon:true })` | **Property:** *showClearButton* <br/>`var groupObj = new ej.dropdowns.AutoComplete({showClearButton: true,});groupObj.appendTo('#vegetables');` |
| **Animation** | **Property:** *animateType* <br/> `$('#autocomplete').ejAutocomplete({animateType:animateType })` | **Not Applicable** |
| **Focusing the list item** | **Property:** *AutoFocus*<br/> `@Html.EJ().Autocomplete("selectCar").AutoFocus("true")` |**Not applicable** |
| **Delaying the popup open time** | **Property:** *delaySuggestionTimeout*<br/> `$('#autocomplete').ejAutocomplete({delaySuggestionTimeout:300 })` | **Not applicable** |
| **Popup text when there is no popup items** | **Property:** *emptyResultText*<br/> `$('#autocomplete').ejAutocomplete({emptyResultText:"no Records" })`  |<https://ej2.syncfusion.com/javascript/demos/#/material/auto-complete/template.html> |
| **Enable/disable the duplicate option** | **Property:** *enableDistinct*<br/> `$('#autocomplete').ejAutocomplete({enableDistinct:true })`|**Not applicable**  |
| **Popup height** | **Property:** *popupHeight*<br/> `$('#autocomplete').ejAutocomplete({popupHeight:300px })` |**Property:** *popupHeight* <br/> `var groupObj = new ej.dropdowns.AutoComplete({popupHeight: 300px,});groupObj.appendTo('#vegetables');` |
| **Popup Width** | **Property:** *popupWidth*<br/> `$('#autocomplete').ejAutocomplete({popupWidth:300px })` |**Property:** *popupWidth* <br/> `var groupObj = new ej.dropdowns.AutoComplete({popupWidth: 300px,});groupObj.appendTo('#vegetables');`|
| **Open popup** | **Method:** *open*<br/> `$("#autocomplete").ejAutocomplete("open");` | **Method:** *showPopup*<br/>`var groupObj = new ej.dropdowns.AutoComplete({});groupObj.appendTo('#vegetables');`<br/><br/>`groupObj.showPopup();` |
| **Close event** | **Event:** *close*<br/>`$('#autocomplete').ejAutocomplete({close:"onClose" })` | **Event**: *close* <br/> `var groupObj = new ej.dropdowns.AutoComplete({close:"close",});groupObj.appendTo('#vegetables');`|
| **Open event** | **Event:** *open*<br/> `$('#autocomplete').ejAutocomplete({open:"onopen" })`| **Event:** *open* <br/> `var groupObj = new ej.dropdowns.AutoComplete({open:"open",});groupObj.appendTo('#vegetables');`|

## CSS

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **Default** | **Property:** *cssClass* <br/> `$('#autocomplete').ejAutocomplete({cssClass:"cssClass" })` | **Property:** *cssClass* <br/> `var groupObj = new ej.dropdowns.AutoComplete({cssClass:"cssClass",});groupObj.appendTo('#vegetables');`|
| **Height** | **Property:** *height* <br/> `$('#autocomplete').ejAutocomplete({height:"300px" })`| **Acheivable through the [cssClass](https://ej2.syncfusion.com/documentation/auto-complete/api-autoComplete.html?lang=typescript#cssclass) property** |
| **showRoundedCorner**   | **Property:** *showRoundedCorner*<br/> `$('#autocomplete').ejAutocomplete({showRoundedCorner:true })` | **Acheivable through the [cssClass](https://ej2.syncfusion.com/documentation/auto-complete/api-autoComplete.html?lang=typescript#cssclass) property**. |
| **Width** | **Property:** *width* <br/> `$('#autocomplete').ejAutocomplete({width:300px })`| **Property:** *width* <br/> `var groupObj = new ej.dropdowns.AutoComplete({width:"300px",});groupObj.appendTo('#vegetables');`|
| **Visibility** | **Property:** *visible* <br/>`$('#autocomplete').ejAutocomplete({visible:true })` | **Acheivable through the [cssClass](https://ej2.syncfusion.com/documentation/auto-complete/api-autoComplete.html?lang=typescript#cssclass) property**. |

## Grouping

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **Default** | **Property:** *fields*<br/> `$('#autocomplete').ejAutocomplete({fields: { key: "index", groupBy: "name" },});`|**Property:** *fields*<br/> `var groupObj = new ej.dropdowns.AutoComplete({fields: { groupBy: 'Category', value: 'Vegetable' },});groupObj.appendTo('#vegetables');`|

## Localization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **Default** | **Property:** *Locale* <br/>`$('#autocomplete').ejAutocomplete({lcoale: "fr-FE",});`| **Property:** *Locale* <br/>`var groupObj = new ej.dropdowns.AutoComplete({locale: "fr-FE"});groupObj.appendTo('#vegetables');`|

## Template

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **Default** | **Property:** *template* `$('#autocomplete').ejAutocomplete({template: "<span><span class='name'>${FirstName}</span><span class ='city'>${City}</span></span>"})`|**Property:** *itemTemplate*<br/> `var groupObj = new ej.dropdowns.AutoComplete({itemTemplate: "<span><span class='name'>${FirstName}</span><span class ='city'>${City}</span></span>"});groupObj.appendTo('#vegetables');` |
| **Group Template** | **Not Applicable**  | **Property:** *groupTemplate* <br/>`var groupObj = new ej.dropdowns.AutoComplete({groupTemplate: "<strong>${City}</strong>"});groupObj.appendTo('#vegetables');`|
| **ValueTemplate** | **Not applicable** | **Property:** *valueTemplate* <br/>`var groupObj = new ej.dropdowns.AutoComplete({valueTemplate: "<span>${FirstName} - ${City}</span>"});groupObj.appendTo('#vegetables');`|
| **Header Template** | **Not applicable** | **Property:** *headerTemplate* <br/> `var groupObj = new ej.dropdowns.AutoComplete({headerTemplate: "<span class='head'><span class='name'>Name</span><span class='city'>City</span></span>",});groupObj.appendTo('#vegetables');`|
| **FooterTemplate** | **Not applicable** | **Property:** *footerTemplate* <br/>`var groupObj = new ej.dropdowns.AutoComplete({footerTemplate:"<span class='foot'> Total list items: "+ sportsData.length +"</span>"});groupObj.appendTo('#vegetables');` |
| **No records Template** | **Not applicable** | **Property:** *noRecordsTemplate* <br/>`var groupObj = new ej.dropdowns.AutoComplete({noRecordsTemplate:"<span class='norecord'> NO DATA AVAILABLE</span>"});groupObj.appendTo('#vegetables');` |
| **Action failure Template** | **Not applicable** | **Property:** *actionFailureTemplate* <br/>`var groupObj = new ej.dropdowns.AutoComplete({actionFailureTemplate:"<span class='action-failure'> Data fetch get fails</span>"});groupObj.appendTo('#vegetables');` |

## Sorting

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **Default** | **Property:** *allowSorting* <br/> `$('#autocomplete').ejAutocomplete({allowSorting: true,});` | **Acheivable through [sortOrder](https://ej2.syncfusion.com/documentation/auto-complete/api-autoComplete.html?lang=typescript#sortorder) property** |
| **Order of sorting** | **Property:** *sortOrder* <br/>`$('#autocomplete').ejAutocomplete({sortOrder: "Ascending",});`|**Property:** *sortOrder*<br/> `var groupObj = new ej.dropdowns.AutoComplete({sortOrder: "sortOrder"});groupObj.appendTo('#vegetables');` |

## Accessibility

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **RTL support** | **Property:** *enableRtl* <br/>`$('#autocomplete').ejAutocomplete({enableRtl: true,});` | **Property:** *enableRtl* <br/>`var groupObj = new ej.dropdowns.AutoComplete({enableRtl: true});groupObj.appendTo('#vegetables');`|

## Selection

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| ------------ | ------------ | ----------- |
|**Selecting particular value**| **Property**: *selectValueByKey* <br/>`$('#autocomplete').ejAutocomplete({selectValueByKey: 1,});`|**Achievable through [value](https://ej2.syncfusion.com/documentation/auto-complete/api-autoComplete.html?lang=typescript#value) property** |
| **Selecting particular value** | **Property**: *value*<br/>`$('#autocomplete').ejAutocomplete({value: data,});` | **Property:** *value*<br/> `var groupObj = new ej.dropdowns.AutoComplete({value: "data"});groupObj.appendTo('#vegetables');`|
| **Selecting particular text** | **Property:** *text*<br/> `$('#autocomplete').ejAutocomplete({text: "data",});` | **Not Applicable** |
| **Selecting particular value** |**Method:** *selectValueByKey*<br/> `$("#autocomplete").selectValueByKey("key")`| **Achievable through [value](https://ej2.syncfusion.com/documentation/auto-complete/api-autoComplete.html?lang=typescript#value) property**   |
| **Selecting particular text** |**Method:** *selectValueByText* <br/> `$("#autocomplete").selectValueByText("key")`|**Not Applicable** |
| **Select event** |**Event**: *select*<br/>`$('#autocomplete').ejAutocomplete({select: "onSelect",});` | **Event:** *select* <br/> `var groupObj = new ej.dropdowns.AutoComplete({select: "onSelect"});groupObj.appendTo('#vegetables');`|

## Miscellaneous

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **Enable/disable** | **Property:** *enabled*<br/>`$('#autocomplete').ejAutocomplete({enabled: true,});` | **Property:** *enabled* <br/>`var groupObj = new ej.dropdowns.AutoComplete({enabled: true});groupObj.appendTo('#vegetables');`|
| **Enable persistence** | **Property:** *enablePersistence*<br/> `$('#autocomplete').ejAutocomplete({enablePersistence: true,});` | **Property:** *enablePersistence* <br/> `var groupObj = new ej.dropdowns.AutoComplete({enablePersistence: true});groupObj.appendTo('#vegetables');`|
| **Loading icon** | **Property:** *showLoadingIcon* <br/>`$('#autocomplete').ejAutocomplete({showLoadingIcon: true,});` | **By default,it is showing** |
| **Read only** | **Property:** *readOnly* <br/> `$('#autocomplete').ejAutocomplete({readOnly: true,});` | **Property:** *readOnly* <br/> `var groupObj = new ej.dropdowns.AutoComplete({readOnly: true});groupObj.appendTo('#vegetables');`  |
| **Disable** | **Method:** *disable*<br/> `$("#autocomplete").ejAutoComplete("disable");` | **Achievable through [enabled](https://ej2.syncfusion.com/documentation/auto-complete/api-autoComplete.html?lang=typescript#enabled) property**  |

## Common

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **Addition of new option watermark text** | **Property:** *addNewText*<br/> `$('#autocomplete').ejAutocomplete({addNewText:"text"});`|**Not applicable** |
| **Addition of new item** | **Property:**  *allowAddNew* <br/>`$('#autocomplete').ejAutocomplete({allowAddNew: true});`|**Property:** *allowCustom*<br/> `var groupObj = new ej.dropdowns.AutoComplete({allowCustom: true});groupObj.appendTo('#vegetables');`|
| **Reset the autocomplete** | **Property:** *showResetIcon* <br/>`$('#autocomplete').ejAutocomplete({showResetIcon: true});`|**Property:** *showClearIcon* <br/> `var groupObj = new ej.dropdowns.AutoComplete({allowCustom: true});groupObj.appendTo('#vegetables');`|
| **Destroy** | **Method:** *destroy*<br/> `$("#autocomplete").ejAutoComplete("destroy");`| **Method:** *destroy* <br/>`var groupObj = new ej.dropdowns.AutoComplete({allowCustom: true});groupObj.appendTo('#vegetables');`<br/><br/>`groupObj.destroy();`|
| **Reset the autocomplete** | **Method:** *clearText*<br/>`$("#autocomplete").ejAutoComplete("clearText");`  | **Property:** *value*<br/> `var groupObj = new ej.dropdowns.AutoComplete({value: ""});groupObj.appendTo('#vegetables');` |
| **Multicolumn** | **Property:** *multiColumnSettings*<br/> `var autocompleteInstance =new ej.Autocomplete($("#selectCar"), {multiColumnSettings:{enable:true,showHeader:true,stringFormat:"{1}",searchColumnIndices[0,1,2],`<br/> `columns:[{"field": "EmployeeID" ,"headerText":"EmployeeID"},{"field": "FirstName" , "headerText":"FirstName"},{"field": "City" , "headerText":"City"}]}});` |**Not applicable** |
| **Hide the Autocomplete** | **Method:** *hide*<br/>`$("#autocomplete").ejAutoComplete("hide");` | **Acheivable through the [cssClass](https://ej2.syncfusion.com/documentation/auto-complete/api-autoComplete.html?lang=typescript#cssclass) property.**|
| **Getting particular text** | **Method:** *getActiveText* <br/>`$("#autocomplete").ejAutoComplete("getActiveText");`|**Not Applicable** |
| **Getting particular value** | **Method:** *getValue*<br/> `$("#autocomplete").ejAutoComplete("getValue");` |**Acheivable through the [value](https://ej2.syncfusion.com/documentation/auto-complete/api-autoComplete.html?lang=typescript#value) property**. |
| **Change event** | **Event:** *change*<br/>`$('#autocomplete').ejAutocomplete({change:"change"});`|**Event:** *change* <br/>`var groupObj = new ej.dropdowns.AutoComplete({change: "change"});groupObj.appendTo('#vegetables');`|
| **Create event** | **Event:** *create* <br/>`$('#autocomplete').ejAutocomplete({create:"create"});`|**Event:** *created* <br/>`var groupObj = new ej.dropdowns.AutoComplete({created: "created"});groupObj.appendTo('#vegetables');`|
| **Destroy event** | **Event:** *destroy* <br/>`$('#autocomplete').ejAutocomplete({destroy:"destroy"});` |**Event:** *destroyed* <br/>`var groupObj = new ej.dropdowns.AutoComplete({destroyed: "destroyed"});groupObj.appendTo('#vegetables');`|
| **Focus out event** | **Event**: *focusOut*<br/>`$('#autocomplete').ejAutocomplete({focusOut:"focusOut"});`| **Event:** *blur* <br/>`var groupObj = new ej.dropdowns.AutoComplete({blur: "blur"});groupObj.appendTo('#vegetables');` |
| **Focus in event** | **Event** : *focusIn*<br/>`$('#autocomplete').ejAutocomplete({focusIn:"focusIn"});` | **Event:** *focus* <br/>`var groupObj = new ej.dropdowns.AutoComplete({focus: "focus"});groupObj.appendTo('#vegetables');` |
