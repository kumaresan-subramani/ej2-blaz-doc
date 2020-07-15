# Migration from Essential JS 1

This article describes the API migration process of  DropDownList component from Essential JS 1 to Essential JS 2.

## DataBinding

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Default** | **Property**: *dataSource* <br/>`$('#dropdown1').ejDropDownList({dataSource: List});` | **Property**: *dataSource* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({dataSource: sportsData,});dropDownListObject.appendTo('#ddlelement');`|
| **Fields for mapping** | **Property**: *fields* <br/>`$('#dropdown1').ejDropDownList({fields: {text: "text",value: "country",},});`| **Property**: *fields* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({fields: { text: 'Game', value: 'Id' },});dropDownListObject.appendTo('#ddlelement');`|
| **Query** | **Property**: *query* <br/>`$('#dropdown1').ejDropDownList({query: ej.Query().requiresCount();});`| **Property**: *query*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({query: new Query().from('Customers').select(['ContactName', 'CustomerID']).take(6),});dropDownListObject.appendTo('#ddlelement');`|
| **Begin event** | **Event** :*actionBegin* <br/>`$('#dropdown1').ejDropDownList({actionBegin : function (args) {/*Do your changes */}});` | **Event** : *actionBegin* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({actionBegin: "actionBegin"});dropDownListObject.appendTo('#ddlelement');`|
| **Complete event** | **Event**: *actionComplete* <br/>`$('#dropdown1').ejDropDownList({actionComplete : function (args) {/*Do your changes */}});` | **Event**: *actionComplete* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({actionComplete: "actionComplete"});dropDownListObject.appendTo('#ddlelement');`|
| **Failure event** | **Event**: *actionFailure* <br/>`$('#dropdown1').ejDropDownList({actionFailure : function (args) {/*Do your changes */}});`| **Event**: *actionFailure* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({actionFailure: "actionFailure"});dropDownListObject.appendTo('#ddlelement');`|
| **Success event**| **Event**: *actionSuccess* <br/>`$('#dropdown1').ejDropDownList({actionSuccess : function (args) {/*Do your changes */}});`| **Not Applicable** |
| **Data binding event** | **Event**: *dataBound* <br/> `$('#dropdown1').ejDropDownList({dataBound : function (args) {/*Do your changes */}});`| **Event**: *dataBind* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({dataBind: "dataBind"});dropDownListObject.appendTo('#ddlelement');`|

## Filtering

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Default** |	**Property**: *enableFilterSearch* <br/>`$('#dropdown1').ejDropDownList({enableFilterSearch : true,});`| **Property**: *allowFiltering* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({allowFiltering: true});dropDownListObject.appendTo('#ddlelement');` |
| **Server filtering** | **Property**: *enableServerFiltering* <br/>`$('#dropdown1').ejDropDownList({enableServerFiltering : true,});`| **Property**: *allowFiltering* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({allowFiltering: true});dropDownListObject.appendTo('#ddlelement');` |
| **Filter type** | **Property**: *filterType* <br/>`$('#dropdown1').ejDropDownList({fiterType : ej.FilterType.Contains,});` |<https://ej2.syncfusion.com/javascript/demos/#/material/drop-down-list/filtering.html> |
| **No Records Template** |	**Not Applicable** | **Property**: *noRecordsTemplate* <br/> `var dropDownListObject = new ej.dropdowns.DropDownList({noRecordsTemplate: "<span class='norecord'> NO DATA AVAILABLE</span>"});dropDownListObject.appendTo('#ddlelement');` |
| **Filter Bar watermark text** | **Not Applicable** | **Property**: *filterBarPlaceholder* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({filterBarPlaceholder: "search"});dropDownListObject.appendTo('#ddlelement');` |
| **Ignore casing and diacritics** | **Not Applicable** |**Property**: *ignoreAccent*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({ignoreAccent: true});dropDownListObject.appendTo('#ddlelement');` |
| **Incremental search**| **Property**: *enableIncrementalSearch*<br/>`$('#dropdown1').ejDropDownList({enableIncrementalSearch : true,});` | **By default it is true** |
| **Case sensitivity** | **Property**: *caseSensitiveSearch*<br/>`$('#dropdown1').ejDropDownList({caseSensitiveSearch : true,});` | <https://ej2.syncfusion.com/javascript/demos/#/material/drop-down-list/filtering.html> |
| **Search event** | **Event**: *search* <br/>`$('#dropdown1').ejDropDownList({search : function (args) {/*Do your changes */}});` | **Event**: *filtering* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({filtering: "search"});dropDownListObject.appendTo('#ddlelement');` |

## Template

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Default** | **Property**: *template* <br/>`$("#dropdown").ejDropDownList({template: '<div class="flag ${flag}"> </div>' + '<div class="txt"> ${text} </div>', width: "200px"});` |**Property**: *itemTemplate*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({itemTemplate: "<span><span class='name'>${FirstName}</span><span class ='city'>${City}</span></span>"});dropDownListObject.appendTo('#ddlelement');`|
| **Group Template** | **Not Applicable** | **Property**: *groupTemplate* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({ groupTemplate: "<strong>${City}</strong>"});dropDownListObject.appendTo('#ddlelement');`|
| **ValueTemplate** | **Not Applicable** | **Property**: *valueTemplate* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({valueTemplate: "<span>${FirstName} - ${City}</span>"});dropDownListObject.appendTo('#ddlelement');`|
| **Header Template** | **Property**: *headerTemplate* <br/>`$("#dropdown").ejDropDownList({ headerTemplate: "<div class='header'><span class='flag-head'>Flag</span> <span class='con-head'>Countries</span> </div>"});`| **Property**: *headerTemplate* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({headerTemplate: "<span class='head'><span class='name'>Name</span><span class='city'>City</span></span>",});dropDownListObject.appendTo('#ddlelement');`|
| **FooterTemplate** | **Not applicable** |	**Property**: *footerTemplate* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({footerTemplate: "<span class='foot'> Total list items: " + sportsData.length + "</span>"});dropDownListObject.appendTo('#ddlelement');`|
| **No records Template** | **Not applicable** | **Property**: *noRecordsTemplate* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({noRecordsTemplate: "<span class='norecord'> NO DATA AVAILABLE</span>"});dropDownListObject.appendTo('#ddlelement');`|
| **Action failure Template** | **Not applicable** | **Property**: *actionFailureTemplate* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({actionFailureTemplate: "<span class='action-failure'> Data fetch get fails</span>"});dropDownListObject.appendTo('#ddlelement');`|

## Virtual Scrolling

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Default** |	**Property**: *allowVirtualScrolling* <br/>`$('#dropdown1').ejDropDownList({allowVirtualScrolling : true,});` | **Not applicable** |

## Applying CSS

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Default** | **Property**: *cssClass* <br/>`$('#dropdown1').ejDropDownList({cssClass : "customClass",});` | **Property**: *cssClass* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({cssClass: "customClass"});dropDownListObject.appendTo('#ddlelement');`|
| **showRoundedCorner** | **Property**: *showRoundedCorner* <br/>`$('#dropdown1').ejDropDownList({showRoundedCorner : true,});` | **Property**: *cssClass* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({cssClass: "customClass"});dropDownListObject.appendTo('#ddlelement');`|

## Sorting

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Default** |	**Property**: *enableSorting* <br/>`$('#dropdown1').ejDropDownList({enableSorting : true,});` | **Acheivable through [sortOrder](https://ej2.syncfusion.com/documentation/drop-down-list/api-dropDownList.html?lang=typescript#sortorder) property** |
| **Order of sorting** | **Property**: *sortOrder* <br/>`$('#dropdown1').ejDropDownList({sortOrder : ej.sortOrder.Descending,});` | **Property**: *sortOrder* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({sortOrder: "Ascending"});dropDownListObject.appendTo('#ddlelement');`|

## Popup

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--- | --- | --- |
| **Popup height** | **Property**: *popupHeight* <br/>`$('#dropdown1').ejDropDownList({popupHeight : "500px",});`| **Property**: popupHeight <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({popupHeight: "300px"});dropDownListObject.appendTo('#ddlelement');`|
| **Popup width** |	**Property**: *popupWidth* <br/>`$('#dropdown1').ejDropDownList({popupWidth : "500px",});` | **Property**: *popupWidth* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({popupWidth: "400px"});dropDownListObject.appendTo('#ddlelement');`|
| **Popup show on load** |	**Property**: *showPopupOnLoad* <br/> `$('#dropdown1').ejDropDownList({showPopupOnLoad : true,});`|	**By default, the data load on demand.** |
| **enableAnimation** |	**Property**: *enableAnimation* <br/>`$('#dropdown1').ejDropDownList({enableAnimation : true,});`| **Not applicable** |
| **Popup resizing** | **Property**: *enablePopupResize* <br/>`$('#dropdown1').ejDropDownList({enablePopupResize : true,})`| **Not applicable** |
| **Maximum Popup height** | **Property**: *maxPopupHeight* <br/>`$('#dropdown1').ejDropDownList({maxPopupHeight : "500px",});`| **Not applicable** |
| **Minimum Popup height** | **Property**: *minPopupHeight*<br/>`$('#dropdown1').ejDropDownList({minPopupHeight : "500px",});`<br/>}); | **Not applicable** |
| **Maximum Popup width** | **Property**: *maxPopupWidth* <br/>`$('#dropdown1').ejDropDownList({maxPopupWidth : "500px",});`| **Not applicable** |
| **Minimum Popup width** |	**Property**: *minPopupWidth* <br/>`$('#dropdown1').ejDropDownList({minPopupWidth : "500px",});` | **Not applicable** |
| **Loading data** | **Property**: *loadOnDemand* <br/>`$('#dropdown1').ejDropDownList({loadOnDemand : true,});` | **By default, it is true** |
| **Popup showing manually** | **Method**: *showPopup* <br/>`$('#dropdown').ejDropDownList('showPopup')` | **Method**: *showPopup* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList();dropDownListObject.appendTo('#ddlelement')`<br/>`dropDownListObject.showPopup();`|
| **Popup hiding manually** |**Method**: *hidePopup* <br/>`$('#dropdown').ejDropDownList('hidePopup')` | **Method**: *hidePopup*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList();dropDownListObject.appendTo('#ddlelement')`<br/>`dropDownListObject.hidePopup();`|
| **Before Popup hide event** | **Event**: *beforePopupHide* <br/>`$('#dropdown1').ejDropDownList({beforePopupHide : function (args) {/*Do your changes */}});`| **Not applicable** |
| **Before Popup shown event** | **Event**: *beforePopupShown*<br/>`$('#dropdown1').ejDropDownList({beforePopupShown : function (args) {/*Do your changes */}});`| **Event**: *beforeOpen* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({beforeOpen: "open"});dropDownListObject.appendTo('#ddlelement');`|
| **Popup hide event** | **Event**: *popupHide*<br/>`$('#dropdown1').ejDropDownList({popupHide : function (args) {/*Do your changes */}});`|**Event**: *close* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({close: "close"});dropDownListObject.appendTo('#ddlelement');` |
| **Popup resize event** | **Event**: *popupResize*<br/>`$('#dropdown1').ejDropDownList({popupResize : function (args) {/*Do your changes */}});`|	**Not applicable** |
| **Popup resize start event**| **Event**: *popupResizeStart*<br/>`$('#dropdown1').ejDropDownList({popupResizeStart : function (args) {/*Do your changes */}});`|	**Not applicable** |
| **Popup resize stop event** | **Event**: *popupResizeStop*<br/>`$('#dropdown1').ejDropDownList({popupResizeStop : function (args) {/*Do your changes */}});`| **Not applicable** |
| **Popup shown event** | **Event**: *popupShown*<br/>`$('#dropdown1').ejDropDownList({popupShown : function (args) {/*Do your changes */}});`| **Event**: *open*<br/> `var dropDownListObject = new ej.dropdowns.DropDownList({open: "open"});dropDownListObject.appendTo('#ddlelement');`|

## Placeholder

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Watermark text** | **Property**: *watermarkText* <br/>`$('#dropdown1').ejDropDownList({watermarkText : "Select"});`| **Property**: *placeholder* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({placeholder: "select"});dropDownListObject.appendTo('#ddlelement');`|
| **Floating  of watermark text** | **Not applicable** |	**Property**: *floatLabelType* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({floatLabelType: "Auto"});dropDownListObject.appendTo('#ddlelement');`|

## Grouping

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Default** | **Property**: *fields.groupBy* <br/>`$('#dropdown1').ejDropDownList({fields: {groupBy: "text"},});`|**Property**: *fields.groupBy*<br/>>`var dropDownListObject = new ej.dropdowns.DropDownList({fields: { groupBy: 'ContactName',}});dropDownListObject.appendTo('#ddlelement');`|
| **Group Template**| **Not applicable** | **Property**: *groupTemplate*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({ groupTemplate: "<strong>${City}</strong>"});dropDownListObject.appendTo('#ddlelement');` |

## Accessibility

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Globalization** | **Property**: *locale*<br/>`$('#dropdown1').ejDropDownList({locale: "fr-FE"});`| **Property**: *locale*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({ locale: "fr-FE"});dropDownListObject.appendTo('#ddlelement');` |
| **Rtl support** |	**Property**: *enableRTL*<br/>`$('#dropdown1').ejDropDownList({enableRTL: true,});` | **Property**: *enableRtl*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({ enableRtl: true});dropDownListObject.appendTo('#ddlelement');` |

## Miscellaneous

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Enable/disable** | **Property**: *enabled*<br/>`$('#dropdown1').ejDropDownList({enabled: true,});` | **Property**: *enabled* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({ enabled: true});dropDownListObject.appendTo('#ddlelement');` |
| Read only | **Property**: *readOnly* <br/>`$('#dropdown1').ejDropDownList({readOnly: true,});` | <br/>**Property**: *readOnly*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({ readOnly: true});dropDownListObject.appendTo('#ddlelement');` |
| Persistence of data | **Property**: *enablePersistence*<br/>`$('#dropdown1').ejDropDownList({enablePersistence: true,});` |**Property**: *enablePersistence*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({ enablePersistence: true});dropDownListObject.appendTo('#ddlelement');` |
| **Disable** |	**Method**: *disable*<br/>`$('#dropdown').ejDropDownList('disable')` |**Property**: *enabled*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({ enabled:false});dropDownListObject.appendTo('#ddlelement');`|
| **Enable** | **Method**: *enable*<br/>`$('#dropdown').ejDropDownList('enable')`| **Property**: *enabled*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({ enabled: true});dropDownListObject.appendTo('#ddlelement');`|
| **Height** | **Property**: *height* <br/>`$('#dropdown1').ejDropDownList({height: "500px",});`| **Property**: *height* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({ height: "300px"});dropDownListObject.appendTo('#ddlelement');`|
| **Width** |	**Property**: *width* <br/>`$('#dropdown1').ejDropDownList({width: "500px",});` | **Property**: *width* <br/>`var dropDownListObject = new ej.dropdowns.DropDownList({ width: "300px"});dropDownListObject.appendTo('#ddlelement');`|

## Selection

<!-- markdownlint-disable MD010 -->
| Behavior	| API in Essential JS 1	| API in Essential JS 2 |
|--- | --- | --- |
| Selecting particular index | **Property**: *selectedIndex*<br/>`$('#dropdown1').ejDropDownList({selectedIndex: 3,});` | **Property**: *index*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({ index: 3});dropDownListObject.appendTo('#ddlelement');` |
| **Selecting particular value** | **Property**: *value*<br/>`$('#dropdown1').ejDropDownList({value: "data",});` | **Property**: *value*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({ value: "data"});dropDownListObject.appendTo('#ddlelement');`|
| **Selecting particular text** | **Property**: *text* <br/>`$('#dropdown1').ejDropDownList({text: "data",});`|**Property**: *text*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({ text: "data"});dropDownListObject.appendTo('#ddlelement');` |
| **Target id** | **Property**: *targetId* <br/>`$('#dropdown1').ejDropDownList({targetId: "Id",});` | **Not applicable** |
| **Selecting item using text**	| **Method**: *selectItemByText* <br/>`$('#dropdown').ejDropDownList('selectItemByText','car')` |	**Not applicable** |
| **Unselect item using text** | **Method**: *unselectItemByText*<br/>`$('#dropdown').ejDropDownList('unselectItemByText','car')` | **Not applicable** |
| **Selecting item using value**| **Method**: *selectItemByValue*<br/>`$('#dropdown').ejDropDownList('selectItemByValue','car')` | **Not applicable** |
| **Getting data by using value** |	**Method**: *getItemDataByValue*<br/>`$('#dropdown').ejDropDownList('unselectItemByValue','car')` | **Method**: *getDataByValue*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList();dropDownListObject.appendTo('#ddlelement')`<br/>`dropDownListObject.getDataByValue();`|
| **Get selected value** | **Method**: *getSelectedItem*<br/>`$('#dropdown').ejDropDownList('getSelectedItem')` |**Not applicable** |
| **Get selected text** | **Method**: *getSelectedText*<br/>`$('#dropdown').ejDropDownList('getSelectedText')`| **Property**: *text*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({text="data"});dropDownListObject.appendTo('#ddlelement')` |
| **Select event** | **Event**: *select*<br/>`$('#dropdown1').ejDropDownList({select : function (args) {/*Do your changes */}});`| **Event**: *select*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({select:  "onSelect"});dropDownListObject.appendTo('#ddlelement')`|
| **Addition of Html attributes** | **Property**: *htmlAttributes*<br/>`$('#dropdown1').ejDropDownList({htmlAttributes: { disabled: "disabled"},});`| **Property**: *htmlAttributes*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({htmlAttributes:"attrib"});dropDownListObject.appendTo('#ddlelement')` |

## Common

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Adding new item** | **Method** : *addItem*<br/>`$('#dropdown').ejDropDownList("addItem", {text:"India"});` | **Method**: *addItem*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList();dropDownListObject.appendTo('#ddlelement')`<br/>`dropDownListObject.addItem("data");` |
| **Clearing the text**| **Method** : *clearText*<br/>`$('#dropdown').ejDropDownList('clearText')` | **Property:** *value*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({value:""});dropDownListObject.appendTo('#ddlelement')`|
| **Destroy the component** | **Method** : *destroy*<br/>`$('#dropdown').ejDropDownList('destroy')`| **Method**: *destroy*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList();dropDownListObject.appendTo('#ddlelement')`<br/>`dropDownListObject.destroy();` |
| **Getting the data** | **Method** : *getListData*<br/>`$('#dropdown').ejDropDownList('getListData')` |**Method** : *getItems*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList();dropDownListObject.appendTo('#ddlelement')`<br/>`dropDownListObject.getItems();` |
| **Create event** | **Event**: *create*<br/>`$('#dropdown1').ejDropDownList({create : function (args) {/*Do your changes */}});` | **Event**: *created*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({created:"create"});dropDownListObject.appendTo('#ddlelement')` |
| **Destroy event** | **Event**: *destroy*<br/>`$('#dropdown1').ejDropDownList({destroy : function (args) {/*Do your changes */}});`|**Event**: *destroyed*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({destroyed:"create"});dropDownListObject.appendTo('#ddlelement')` |
| **Cascade  event** | **Event**: *cascade*<br/>`$('#dropdown1').ejDropDownList({cascade : function (args) {/*Do your changes */}});`|<https://ej2.syncfusion.com/javascript/demos/#/material/drop-down-list/cascading.html> |
| **Change event** | **Event**: *change*<br/>`$('#dropdown1').ejDropDownList({change : function (args) {/*Do your changes */}});`| **Event**: *change*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({change:"create"});dropDownListObject.appendTo('#ddlelement')` |
| **Focus out event** |	**Event**: *focusOut*<br/>`$('#dropdown1').ejDropDownList({focusOut : function (args) {/*Do your changes */}});`| **Event**: *blur*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({blur:"create"});dropDownListObject.appendTo('#ddlelement')`|
| **Focus in event**| **Event**: *focusIn*<br/><br/>`$('#dropdown1').ejDropDownList({focusIn : function (args) {/*Do your changes */}});` | **Event**: *focus*<br/>`var dropDownListObject = new ej.dropdowns.DropDownList({focus:"create"});dropDownListObject.appendTo('#ddlelement')` |
