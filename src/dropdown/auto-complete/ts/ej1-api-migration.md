# Migration from Essential JS 1

This article describes the API migration process of  AutoComplete component from Essential JS 1 to Essential JS 2.
> MultiSelect concept is not present in EJ2-AutoComplete.  If you want to use multiselection support in autocomplete, we suggest you to use MultiSelect component.

## DataBinding

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **Default** | **Property:** *datasource* <br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), { dataSource: countriesField,});`| **Property:** *dataSource*<br/>`let groupObj: AutoComplete = new AutoComplete({dataSource: vegetableData,});groupObj.appendTo('#vegetables');`|
| **Fields for mapping** | **Property:** *fields*<br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {fields: { key: "index", text: "name" },});`| **Property:** *fields*<br/>`let groupObj: AutoComplete = new AutoComplete({fields: { groupBy: 'Category', value: 'Vegetable' },});groupObj.appendTo('#vegetables');` |
| **Query** | **Property**: *query*<br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {query: query,});`| **Property**: *query*<br/>`let groupObj: AutoComplete = new AutoComplete({query: ej.Query().requiresCount(),});groupObj.appendTo('#vegetables');`|
| **Begin event** | **Event**: *actionBegin*<br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {actionBegin: "actionBegin",});`|**Event**: *actionBegin*<br/> `let groupObj: AutoComplete = new AutoComplete({actionBegin: "actionBegin",});groupObj.appendTo('#vegetables');`|
| **Complete event** | **Event**: *actionComplete*<br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {actionComplete: "actionComplete",});`|**Event**: *actionComplete* <br/> `let groupObj: AutoComplete = new AutoComplete({actionComplete: "actionComplete",});groupObj.appendTo('#vegetables');`|
| **Failure event** | **Event**: *actionFailure*<br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {actionFailure: "actionFailure",});` |**Event**: *actionFailure* <br/> `let groupObj: AutoComplete = new AutoComplete({actionFailure: "actionFailure",});groupObj.appendTo('#vegetables');`|
| **Success event** | **Event**: *actionSuccess* <br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {actionSuccess: "actionSuccess",});` |**Not Applicable** |

## Filtering

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **Case sensitivity** | **Property**: *caseSensitiveSearch*<br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), { caseSensitiveSearch: true,});`|**Property:** *ignoreCase*<br/>`let groupObj: AutoComplete = new AutoComplete({ignoreCase: true,});groupObj.appendTo('#vegetables');`|
| **Accent effective search** | **Not applicable** | **Property** : *ignoreAccent* <br/>`let groupObj: AutoComplete = new AutoComplete({ignoreAccent: true,});groupObj.appendTo('#vegetables');`|
| **Filtering Type** | **Property:** *filterType*<br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), { filterType: "Contains",});`| **Property**: *filterType*<br/>`let groupObj: AutoComplete = new AutoComplete({filterType: filtertype,});groupObj.appendTo('#vegetables');` |
| **Autofill** | **Property:** *enableAutoFill*<br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), { enableAutoFill: true,});` | **Property:**: *autoFill* <br/>`let groupObj: AutoComplete = new AutoComplete({autoFill: true,});groupObj.appendTo('#vegetables');`|
| **Highlight the search word** | **Property**: *highlightSearch* `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), { highlightSearch: true,});`|**Property:** *highlight* <br/>`let groupObj: AutoComplete = new AutoComplete({highlight: true,});groupObj.appendTo('#vegetables');`|
| **No of items to be shown** | **Property:** *itemsCount*<br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), { itemsCount: 3,});` |**Property:** *suggestionCount*<br/>`let groupObj: AutoComplete = new AutoComplete({suggestionCount: 5,});groupObj.appendTo('#vegetables');` |
| **Minimum characters to enter** | **Property:** *minCharacter*<br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), { minCharacter: 3,});` |**Property:** *minLength* <br/>`let groupObj: AutoComplete = new AutoComplete({minLength: 4,});groupObj.appendTo('#vegetables');` |
| **Search** | **Method:** *search* <br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), { });`<br/><br/>`$("#autocomplete").ejAutocomplete("search");` | **Not applicable** |

## Placeholder

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **Watermark text** | **Property:** *watermarkText* <br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {watermarkText:"select" });`| **Property:** *placeholder* <br/>`let groupObj: AutoComplete = new AutoComplete({placeholder: "Select",});groupObj.appendTo('#vegetables');`|
| **Floating  of watermark Text** | **Not applicable**   | **Property:** *floatLabelType* <br/>`let groupObj: AutoComplete = new AutoComplete({floatLabelType: floatLabelType,});groupObj.appendTo('#vegetables');`|

## Popup

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **No records text** | **Property:** *emptyResultText* <br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {emptyResultText:"no records" });`| **Property:** *noRecordsTemplate*<br/> `let groupObj: AutoComplete = new AutoComplete({noRecordsTemplate: noRecordsTemplate,});groupObj.appendTo('#vegetables');`|
| **No records showing** | **Property:** *showEmptyResultText<br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {showEmptyResultText:true })` | **Not applicable** |
| **Popupbutton** | **Property:** *showPopupButton*<br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {ShowPopupButton:true })` | **Property:** *showPopupButton*<br/>  `let groupObj: AutoComplete = new AutoComplete({showPopupButton: true,});groupObj.appendTo('#vegetables');`|
| **Clear button** | **Property:** *showResetIcon* <br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {showResetIcon:true })` | **Property:** *showClearButton* <br/>`let groupObj: AutoComplete = new AutoComplete({showClearButton: true,});groupObj.appendTo('#vegetables');` |
| **Animation** | **Property:** *animateType* <br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {animateType:animateType })` | **Not Applicable** |
| **Focusing the list item** | **Property:** *autoFocus*<br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {autoFocus:true })` |**Not applicable** |
| **Delaying the popup open time** | **Property:** *delaySuggestionTimeout*<br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {delaySuggestionTimeout:300 })` | **Not applicable** |
| **Popup text when there is no popup items** | **Property:** *emptyResultText*<br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {emptyResultText:"no Records" })`  |<https://ej2.syncfusion.com/demos/#/material/auto-complete/template.html> |
| **Enable/disable the duplicate option** | **Property:** *enableDistinct*<br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {enableDistinct:true })`|**Not applicable**  |
| **Popup height** | **Property:** *popupHeight*<br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {popupHeight:300px })` |**Property:** *popupHeight* <br/> `let groupObj: AutoComplete = new AutoComplete({popupHeight: 300px,});groupObj.appendTo('#vegetables');` |
| **Popup Width** | **Property:** *popupWidth*<br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {popupWidth:300px })` |**Property:** *popupWidth* <br/> `let groupObj: AutoComplete = new AutoComplete({popupWidth: 300px,});groupObj.appendTo('#vegetables');`|
| **Open popup** | **Method:** *open*<br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), { })`<br/><br/>`$("#autocomplete").ejAutocomplete("open");` | **Method:** *showPopup*<br/>`let groupObj: AutoComplete = new AutoComplete({});groupObj.appendTo('#vegetables');`<br/><br/>`groupObj.showPopup();` |
| **Close event** | **Event:** *close*<br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {close:"onClose" })` | **Event**: *close* <br/> `let groupObj: AutoComplete = new AutoComplete({close:"close",});groupObj.appendTo('#vegetables');`|
| **Open event** | **Event:** *open*<br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {open:"onopen" })`| **Event:** *open* <br/> `let groupObj: AutoComplete = new AutoComplete({open:"open",});groupObj.appendTo('#vegetables');`|

## CSS

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **Default** | **Property:** *cssClass* <br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {cssClass:"cssClass" })` | **Property:** *cssClass* <br/> `let groupObj: AutoComplete = new AutoComplete({cssClass:"cssClass",});groupObj.appendTo('#vegetables');`|
| **Height** | **Property:** *height* <br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {height:"300px" })`| **Acheivable through the [cssClass](https://ej2.syncfusion.com/documentation/auto-complete/api-autoComplete.html?lang=typescript#cssclass) property.** |
| **showRoundedCorner**   | **Property:** *showRoundedCorner*<br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {showRoundedCorner:true })` | **Acheivable through the [cssClass](https://ej2.syncfusion.com/documentation/auto-complete/api-autoComplete.html?lang=typescript#cssclass) property.** |
| **Width** | **Property:** *width* <br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {width:300px })`| **Property:** *width* <br/> `let groupObj: AutoComplete = new AutoComplete({width:"300px",});groupObj.appendTo('#vegetables');`|
| **Visibility** | **Property:** *visible* <br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {visible:true })` | **Acheivable through the [cssClass](https://ej2.syncfusion.com/documentation/auto-complete/api-autoComplete.html?lang=typescript#cssclass) property.** |

## Grouping

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **Default** | **Property:** *fields*<br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {fields: { key: "index", groupBy: "name" },});`|**Property:** *fields* `let groupObj: AutoComplete = new AutoComplete({fields: { groupBy: 'Category', value: 'Vegetable' },});groupObj.appendTo('#vegetables');`|

## Localization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **Default** | **Property:** *Locale* <br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {lcoale: "fr-FE",});`| **Property:** *Locale* <br/>`let groupObj: AutoComplete = new AutoComplete({locale: "fr-FE"});groupObj.appendTo('#vegetables');`|

## Template

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **Default** | **Property:** *template* <br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {template: "<span><span class='name'>${FirstName}</span><span class ='city'>${City}</span></span>"})`|**Property:** *itemTemplate*<br/> `let groupObj: AutoComplete = new AutoComplete({itemTemplate: "<span><span class='name'>${FirstName}</span><span class ='city'>${City}</span></span>"});groupObj.appendTo('#vegetables');` |
| **Group Template** | **Not Applicable**  | **Property:** *groupTemplate* <br/>`let groupObj: AutoComplete = new AutoComplete({groupTemplate: "<strong>${City}</strong>"});groupObj.appendTo('#vegetables');`|
| **ValueTemplate** | **Not applicable** | **Property:** *valueTemplate* <br/>`let groupObj: AutoComplete = new AutoComplete({valueTemplate: "<span>${FirstName} - ${City}</span>"});groupObj.appendTo('#vegetables');`|
| **Header Template** | **Not applicable** | **Property:** *headerTemplate* <br/> `let groupObj: AutoComplete = new AutoComplete({headerTemplate: "<span class='head'><span class='name'>Name</span><span class='city'>City</span></span>",});groupObj.appendTo('#vegetables');`|
| **FooterTemplate** | **Not applicable** | **Property:** *footerTemplate* <br/>`let groupObj: AutoComplete = new AutoComplete({footerTemplate:"<span class='foot'> Total list items: "+ sportsData.length +"</span>"});groupObj.appendTo('#vegetables');` |
| **No records Template** | **Not applicable** | **Property:** *noRecordsTemplate* <br/>`let groupObj: AutoComplete = new AutoComplete({noRecordsTemplate:"<span class='norecord'> NO DATA AVAILABLE</span>"});groupObj.appendTo('#vegetables');` |
| **Action failure Template** | **Not applicable** | **Property:** *actionFailureTemplate* <br/>`let groupObj: AutoComplete = new AutoComplete({actionFailureTemplate:"<span class='action-failure'> Data fetch get fails</span>"});groupObj.appendTo('#vegetables');` |

## Sorting

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **Default** | **Property:** *allowSorting* <br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {allowSorting: true,});` |  **Acheivable through [sortOrder](https://ej2.syncfusion.com/documentation/auto-complete/api-autoComplete.html?lang=typescript#sortorder) property** |
| **Order of sorting** | **Property:** *sortOrder* <br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {sortOrder: "Ascending",});`|**Property:** *sortOrder*<br/> `let groupObj: AutoComplete = new AutoComplete({sortOrder: "sortOrder"});groupObj.appendTo('#vegetables');` |

## Accessibility

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **RTL support** | **Property:** *enableRtl* <br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {enableRtl: true,});` | **Property:** *enableRtl* <br/>`let groupObj: AutoComplete = new AutoComplete({enableRtl: true});groupObj.appendTo('#vegetables');`|

## Selection

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| ------------ | ------------ | ----------- |
|**Selecting particular value**| **Property**: *selectValueByKey* <br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {selectValueByKey: 1,});`|**Acheivable through the [cssClass](https://ej2.syncfusion.com/documentation/auto-complete/api-autoComplete.html?lang=typescript#cssclass) property.** |
| **Selecting particular value** | **Property**: *value*<br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {value: data,});` | **Property:** *value*<br/> `let groupObj: AutoComplete = new AutoComplete({value: "data"});groupObj.appendTo('#vegetables');`|
| **Selecting particular text** | **Property:** *text*<br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {text: "data",});` | **Not applicable** |
| **Selecting particular value** |**Method:** *selectValueByKey*<br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {});`<br/><br/> `$("#autocomplete").selectValueByKey("key")`| **Acheivable through the [value](https://ej2.syncfusion.com/documentation/auto-complete/api-autoComplete.html?lang=typescript#value) property.**   |
| **Selecting particular text** |**Method:** *selectValueByText* <br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {});`<br/><br/> `$("#autocomplete").selectValueByText("key")`|**Not applicable** |
| **Select event** |**Event**: *select*<br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {select: "onSelect",});` | **Event:** *select* <br/> `let groupObj: AutoComplete = new AutoComplete({select: "onSelect"});groupObj.appendTo('#vegetables');`|

## Miscellaneous

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **Enable/disable** | **Property:** *enabled*<br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {enabled: true,});` | **Property:** *enabled* <br/>`let groupObj: AutoComplete = new AutoComplete({enabled: true});groupObj.appendTo('#vegetables');`|
| **Enable persistence** | **Property:** *enablePersistence*<br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {enablePersistence: true,});` | **Property:** *enablePersistence* <br/> `let groupObj: AutoComplete = new AutoComplete({enablePersistence: true});groupObj.appendTo('#vegetables');`|
| **Loading icon** | **Property:** *showLoadingIcon* <br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {showLoadingIcon: true,});` | **By default,it is showing** |
| **Read only** | **Property:** *readOnly* <br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {readOnly: true,});` | **Property:** *readOnly*  `let groupObj: AutoComplete = new AutoComplete({readOnly: true});groupObj.appendTo('#vegetables');`  |
| **Disable** | **Method:** *disable*<br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {});`<br/><br/>`$("#autocomplete").ejAutoComplete("disable");` | **Achievable through [enabled](https://ej2.syncfusion.com/documentation/auto-complete/api-autoComplete.html?lang=typescript#enabled) property**  |

## Common

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| **Addition of new option watermark text** | **Property:** *addNewText*<br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {addNewText:"text"});`|**Not applicable** |
| **Addition of new item** | **Property:**  *allowAddNew* <br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {allowAddNew: true});`|**Property:** *allowCustom*<br/> `let groupObj: AutoComplete = new AutoComplete({allowCustom: true});groupObj.appendTo('#vegetables');`|
| **Reset the autocomplete** | **Property:** *showResetIcon* <br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {showResetIcon: true});`|**Property:** *showClearIcon* <br/> `let groupObj: AutoComplete = new AutoComplete({allowCustom: true});groupObj.appendTo('#vegetables');`|
| **Destroy** | **Method:** *destroy*<br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {});`<br/><br/>`$("#autocomplete").ejAutoComplete("destroy");`| **Method:** *destroy* <br/>`let groupObj: AutoComplete = new AutoComplete({allowCustom: true});groupObj.appendTo('#vegetables');``<br/><br/>`groupObj.destroy();`|
| **Reset the autocomplete** | **Method:** *clearText*<br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {});`<br/><br/>`$("#autocomplete").ejAutoComplete("clearText");`  | **By passing empty value to the value property, you can acheive this**   |
| **Multicolumn** | **Property:** *multiColumnSettings*<br/> `var autocompleteInstance =new ej.Autocomplete($("#selectCar"), {multiColumnSettings:{enable:true,showHeader:true,stringFormat:"{1}",searchColumnIndices[0,1,2],`<br/> `columns:[{"field": "EmployeeID" ,"headerText":"EmployeeID"},{"field": "FirstName" , "headerText":"FirstName"},{"field": "City" , "headerText":"City"}]}});` |**Not applicable** |
| **Hide the Autocomplete** | **Method:** *hide*<br/><br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {});`<br/><br/>`$("#autocomplete").ejAutoComplete("hide");` | **By using *css-class* property, you can acheive this.**
| **Getting particular text** | **Method:** *getActiveText* <br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {});`<br/><br/>`$("#autocomplete").ejAutoComplete("getActiveText");`|**By using text property, you can get it.** |
| **Getting particular value** | **Method:** *getValue*<br/> `var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {});`<br/><br/>`$("#autocomplete").ejAutoComplete("getValue");` |**By using value property, you can get it.** |
| **Change event** | **Event:** *change*<br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {change:"change"});`|**Event:** *change* <br/>`let groupObj: AutoComplete = new AutoComplete({change: "change"});groupObj.appendTo('#vegetables');`|
| **Create eventf** | **Event:** *create* <br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {create:"create"});`|**Event:** *created* <br/>`let groupObj: AutoComplete = new AutoComplete({created: "created"});groupObj.appendTo('#vegetables');`|
| **Destroy event** | **Event:** *destroy* <br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {destroy:"destroy"});` |**Event:** *destroyed* <br/>`let groupObj: AutoComplete = new AutoComplete({destroyed: "destroyed"});groupObj.appendTo('#vegetables');`|
| **Focus out event** | **Event**: *focusOut*<br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {focusOut:"focusOut"});`| **Event:** *blur* <br/>`let groupObj: AutoComplete = new AutoComplete({blur: "blur"});groupObj.appendTo('#vegetables');` |
| **Focus in event** | **Event** : *focusIn*<br/>`var autocompleteInstance =new ej.Autocomplete($("#autocomplete"), {focusIn:"focusIn"});` | **Event:** *focus* <br/>`let groupObj: AutoComplete = new AutoComplete({focus: "focus"});groupObj.appendTo('#vegetables');` |
