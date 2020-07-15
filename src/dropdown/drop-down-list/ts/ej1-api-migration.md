# Migration from Essential JS 1

This article describes the API migration process of  DropDownList component from Essential JS 1 to Essential JS 2.

## DataBinding

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Default** | **Property**: *dataSource* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{dataSource: List});` | **Property**: *dataSource* <br/>`let dropDownListObject = new DropDownList({dataSource: sportsData,});dropDownListObject.appendTo('#ddlelement');`|
| **Fields for mapping** | **Property**: *fields* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{fields: {text: "text",value: "country",},});`| **Property**: *fields* <br/>`let dropDownListObject = new DropDownList({fields: { text: 'Game', value: 'Id' },});dropDownListObject.appendTo('#ddlelement');`|
| **Query** | **Property**: *query* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{query: ej.Query().requiresCount();});`| **Property**: *query*<br/>`let dropDownListObject = new DropDownList({query: new Query().from('Customers').select(['ContactName', 'CustomerID']).take(6),});dropDownListObject.appendTo('#ddlelement');`|
| **Begin event** | **Event** :*actionBegin* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{actionBegin : function (args) {/*Do your changes */}});` | **Event** : *actionBegin* <br/>`let dropDownListObject = new DropDownList({actionBegin: "actionBegin"});dropDownListObject.appendTo('#ddlelement');`|
| **Complete event** | **Event**: *actionComplete* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{actionComplete : function (args) {/*Do your changes */}});` | **Event**: *actionComplete* <br/>`let dropDownListObject = new DropDownList({actionComplete: "actionComplete"});dropDownListObject.appendTo('#ddlelement');`|
| **Failure event** | **Event**: *actionFailure* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{actionFailure : function (args) {/*Do your changes */}});`| **Event**: *actionFailure* <br/>`let dropDownListObject = new DropDownList({actionFailure: "actionFailure"});dropDownListObject.appendTo('#ddlelement');`|
| **Success event**| **Event**: *actionSuccess* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{actionSuccess : function (args) {/*Do your changes */}});`| **Not Applicable** |
| **Data binding event** | **Event**: *dataBound* <br/> `var sample = new ej.DropDownList($('#dropdown1'),{dataBound : function (args) {/*Do your changes */}});`| **Event**: *dataBind* <br/>`let dropDownListObject = new DropDownList({dataBind: "dataBind"});dropDownListObject.appendTo('#ddlelement');`|

## Filtering

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Default** |	**Property**: *enableFilterSearch* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{enableFilterSearch : true,});`| **Property**: *allowFiltering* <br/>`let dropDownListObject = new DropDownList({allowFiltering: true});dropDownListObject.appendTo('#ddlelement');` |
| **Server filtering** | **Property**: *enableServerFiltering* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{enableServerFiltering : true,});`| **Property**: *allowFiltering* <br/>`let dropDownListObject = new DropDownList({allowFiltering: true});dropDownListObject.appendTo('#ddlelement');` |
| **Filter type** | **Property**: *filterType* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{fiterType : ej.FilterType.Contains,});` |<https://ej2.syncfusion.com/javascript/demos/#/material/drop-down-list/filtering.html> |
| **No Records Template** |	**Not Applicable** | **Property**: *noRecordsTemplate* <br/> `let dropDownListObject = new DropDownList({noRecordsTemplate: "<span class='norecord'> NO DATA AVAILABLE</span>"});dropDownListObject.appendTo('#ddlelement');` |
| **Filter Bar watermark text** | **Not Applicable** | **Property**: *filterBarPlaceholder* <br/>`let dropDownListObject = new DropDownList({filterBarPlaceholder: "search"});dropDownListObject.appendTo('#ddlelement');` |
| **Ignore casing and diacritics** | **Not Applicable** |**Property**: *ignoreAccent*<br/>`let dropDownListObject = new DropDownList({ignoreAccent: true});dropDownListObject.appendTo('#ddlelement');` |
| **Incremental search**| **Property**: *enableIncrementalSearch*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{enableIncrementalSearch : true,});` | **By default it is true** |
| **Case sensitivity** | **Property**: *caseSensitiveSearch*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{caseSensitiveSearch : true,});` | <https://ej2.syncfusion.com/javascript/demos/#/material/drop-down-list/filtering.html> |
| **Search event** | **Event**: *search* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{search : function (args) {/*Do your changes */}});` | **Event**: *filtering* <br/>`let dropDownListObject = new DropDownList({filtering: "search"});dropDownListObject.appendTo('#ddlelement');` |

## Template

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Default** | **Property**: *template* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{template: '<div class="flag ${flag}"> </div>' + '<div class="txt"> ${text} </div>', width: "200px"});` |**Property**: *itemTemplate*<br/>`let dropDownListObject = new DropDownList({itemTemplate: "<span><span class='name'>${FirstName}</span><span class ='city'>${City}</span></span>"});dropDownListObject.appendTo('#ddlelement');`|
| **Group Template** | **Not Applicable** | **Property**: *groupTemplate* <br/>`let dropDownListObject = new DropDownList({ groupTemplate: "<strong>${City}</strong>"});dropDownListObject.appendTo('#ddlelement');`|
| **ValueTemplate** | **Not Applicable** | **Property**: *valueTemplate* <br/>`let dropDownListObject = new DropDownList({valueTemplate: "<span>${FirstName} - ${City}</span>"});dropDownListObject.appendTo('#ddlelement');`|
| **Header Template** | **Property**: *headerTemplate* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{ headerTemplate: "<div class='header'><span class='flag-head'>Flag</span> <span class='con-head'>Countries</span> </div>"});`| **Property**: *headerTemplate* <br/>`let dropDownListObject = new DropDownList({headerTemplate: "<span class='head'><span class='name'>Name</span><span class='city'>City</span></span>",});dropDownListObject.appendTo('#ddlelement');`|
| **FooterTemplate** | **Not applicable** |	**Property**: *footerTemplate* <br/>`let dropDownListObject = new DropDownList({footerTemplate: "<span class='foot'> Total list items: " + sportsData.length + "</span>"});dropDownListObject.appendTo('#ddlelement');`|
| **No records Template** | **Not applicable** | **Property**: *noRecordsTemplate* <br/>`let dropDownListObject = new DropDownList({noRecordsTemplate: "<span class='norecord'> NO DATA AVAILABLE</span>"});dropDownListObject.appendTo('#ddlelement');`|
| **Action failure Template** | **Not applicable** | **Property**: *actionFailureTemplate* <br/>`let dropDownListObject = new DropDownList({actionFailureTemplate: "<span class='action-failure'> Data fetch get fails</span>"});dropDownListObject.appendTo('#ddlelement');`|

## Virtual Scrolling

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Default** |	**Property**: *allowVirtualScrolling* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{allowVirtualScrolling : true,});` | **Not applicable** |

## Applying CSS

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Default** | **Property**: *cssClass* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{cssClass : "customClass",});` | **Property**: *cssClass* <br/>`let dropDownListObject = new DropDownList({cssClass: "customClass"});dropDownListObject.appendTo('#ddlelement');`|
| **showRoundedCorner** | **Property**: *showRoundedCorner* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{showRoundedCorner : true,});` | **Property**: *cssClass* <br/>`let dropDownListObject = new DropDownList({cssClass: "customClass"});dropDownListObject.appendTo('#ddlelement');`|

## Sorting

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Default** |	**Property**: *enableSorting* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{enableSorting : true,});` | **Acheivable through [sortOrder](https://ej2.syncfusion.com/documentation/drop-down-list/api-dropDownList.html?lang=typescript#sortorder) property** |
| **Order of sorting** | **Property**: *sortOrder* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{sortOrder : ej.sortOrder.Descending,});` | **Property**: *sortOrder* <br/>`let dropDownListObject = new DropDownList({sortOrder: "Ascending"});dropDownListObject.appendTo('#ddlelement');`|

## Popup

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
|--- | --- | --- |
| **Popup height** | **Property**: *popupHeight* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{popupHeight : "500px",});`| **Property**: popupHeight <br/>`let dropDownListObject = new DropDownList({popupHeight: "300px"});dropDownListObject.appendTo('#ddlelement');`|
| **Popup width** |	**Property**: *popupWidth* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{popupWidth : "500px",});` | **Property**: *popupWidth* <br/>`let dropDownListObject = new DropDownList({popupWidth: "400px"});dropDownListObject.appendTo('#ddlelement');`|
| **Popup show on load** |	**Property**: *showPopupOnLoad* <br/> `var sample = new ej.DropDownList($('#dropdown1'),{showPopupOnLoad : true,});`|	**By default, the data load on demand.** |
| **enableAnimation** |	**Property**: *enableAnimation* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{enableAnimation : true,});`| **Not applicable** |
| **Popup resizing** | **Property**: *enablePopupResize* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{enablePopupResize : true,})`| **Not applicable** |
| **Maximum Popup height** | **Property**: *maxPopupHeight* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{maxPopupHeight : "500px",});`| **Not applicable** |
| **Minimum Popup height** | **Property**: *minPopupHeight*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{minPopupHeight : "500px",});`<br/>}); | **Not applicable** |
| **Maximum Popup width** | **Property**: *maxPopupWidth* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{maxPopupWidth : "500px",});`| **Not applicable** |
| **Minimum Popup width** |	**Property**: *minPopupWidth* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{minPopupWidth : "500px",});` | **Not applicable** |
| **Loading data** | **Property**: *loadOnDemand* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{loadOnDemand : true,});` | **By default, it is true** |
| **Popup showing manually** | **Method**: *showPopup* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{'showPopup'})` | **Method**: *showPopup* <br/>`let dropDownListObject = new DropDownList();dropDownListObject.appendTo('#ddlelement')`<br/>`dropDownListObject.showPopup();`|
| **Popup hiding manually** |**Method**: *hidePopup* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{'hidePopup'})` | **Method**: *hidePopup*<br/>`let dropDownListObject = new DropDownList();dropDownListObject.appendTo('#ddlelement')`<br/>`dropDownListObject.hidePopup();`|
| **Before Popup hide event** | **Event**: *beforePopupHide* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{beforePopupHide : function (args) {/*Do your changes */}});`| **Not applicable** |
| **Before Popup shown event** | **Event**: *beforePopupShown*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{beforePopupShown : function (args) {/*Do your changes */}});`| **Event**: *beforeOpen* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{beforeOpen: "open"});dropDownListObject.appendTo('#ddlelement');`|
| **Popup hide event** | **Event**: *popupHide*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{popupHide : function (args) {/*Do your changes */}});`|**Event**: *close* <br/>`let dropDownListObject = new DropDownList({close: "close"});dropDownListObject.appendTo('#ddlelement');` |
| **Popup resize event** | **Event**: *popupResize*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{popupResize : function (args) {/*Do your changes */}});`|	**Not applicable** |
| **Popup resize start event**| **Event**: *popupResizeStart*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{popupResizeStart : function (args) {/*Do your changes */}});`|	**Not applicable** |
| **Popup resize stop event** | **Event**: *popupResizeStop*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{popupResizeStop : function (args) {/*Do your changes */}});`| **Not applicable** |
| **Popup shown event** | **Event**: *popupShown*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{popupShown : function (args) {/*Do your changes */}});`| **Event**: *open*<br/> `let dropDownListObject = new DropDownList({open: "open"});dropDownListObject.appendTo('#ddlelement');`|

## Placeholder

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Watermark text** | **Property**: *watermarkText* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{watermarkText : "Select"});`| **Property**: *placeholder* <br/>`let dropDownListObject = new DropDownList({placeholder: "select"});dropDownListObject.appendTo('#ddlelement');`|
| **Floating  of watermark text** | **Not applicable** |	**Property**: *floatLabelType* <br/>`let dropDownListObject = new DropDownList({floatLabelType: "Auto"});dropDownListObject.appendTo('#ddlelement');`|

## Grouping

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Default** | **Property**: *fields.groupBy* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{fields: {groupBy: "text"},});`|**Property**: *fields.groupBy*<br/>`let dropDownListObject = new DropDownList({fields: { groupBy: 'ContactName',}});dropDownListObject.appendTo('#ddlelement');`|
| **Group Template**| **Not applicable** | **Property**: *groupTemplate*<br/>`let dropDownListObject = new DropDownList({ groupTemplate: "<strong>${City}</strong>"});dropDownListObject.appendTo('#ddlelement');` |

## Accessibility

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Globalization** | **Property**: *locale*<br/>`var sample = new ej.DropDownList($('#dropdown1'), {locale: "fr-FE"});`| **Property**: *locale*<br/>`let dropDownListObject = new DropDownList({ locale: "fr-FE"});dropDownListObject.appendTo('#ddlelement');` |
| **Rtl support** |	**Property**: *enableRTL*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{enableRTL: true,});` | **Property**: *enableRtl*<br/>`let dropDownListObject = new DropDownList({ enableRtl: true});dropDownListObject.appendTo('#ddlelement');` |

## Miscellaneous

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Enable/disable** | **Property**: *enabled*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{enabled: true,});` | **Property**: *enabled* <br/>`let dropDownListObject = new DropDownList({ enabled: true});dropDownListObject.appendTo('#ddlelement');` |
| Read only | **Property**: *readOnly* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{readOnly: true,});` | <br/>**Property**: *readOnly*<br/>`let dropDownListObject = new DropDownList({ readOnly: true});dropDownListObject.appendTo('#ddlelement');` |
| Persistence of data | **Property**: *enablePersistence*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{enablePersistence: true,});` |**Property**: *enablePersistence*<br/>`let dropDownListObject = new DropDownList({ enablePersistence: true});dropDownListObject.appendTo('#ddlelement');` |
| **Disable** |	**Method**: *disable*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{'disable'})` |**Property**: *enabled*<br/>`let dropDownListObject = new DropDownList({ enabled:false});dropDownListObject.appendTo('#ddlelement');`|
| **Enable** | **Method**: *enable*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{'enable'})`| **Property**: *enabled*<br/>`let dropDownListObject = new DropDownList({ enabled: true});dropDownListObject.appendTo('#ddlelement');`|
| **Height** | **Property**: *height* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{height: "500px",});`| **Property**: *height* <br/>`let dropDownListObject = new DropDownList({ height: "300px"});dropDownListObject.appendTo('#ddlelement');`|
| **Width** |	**Property**: *width* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{width: "500px",});` | **Property**: *width* <br/>`let dropDownListObject = new DropDownList({ width: "300px"});dropDownListObject.appendTo('#ddlelement');`|

## Selection

<!-- markdownlint-disable MD010 -->
| Behavior	| API in Essential JS 1	| API in Essential JS 2 |
|--- | --- | --- |
| Selecting particular index | **Property**: *selectedIndex*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{selectedIndex: 3,});` | **Property**: *index*<br/>`let dropDownListObject = new DropDownList({ index: 3});dropDownListObject.appendTo('#ddlelement');` |
| **Selecting particular value** | **Property**: *value*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{value: "data",});` | **Property**: *value*<br/>`let dropDownListObject = new DropDownList({ value: "data"});dropDownListObject.appendTo('#ddlelement');`|
| **Selecting particular text** | **Property**: *text* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{text: "data",});`|**Property**: *text*<br/>`let dropDownListObject = new DropDownList({ text: "data"});dropDownListObject.appendTo('#ddlelement');` |
| **Target id** | **Property**: *targetId* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{targetId: "Id",});` | **Not applicable** |
| **Selecting item using text**	| **Method**: *selectItemByText* <br/>`var sample = new ej.DropDownList($('#dropdown1'),{'selectItemByText','car'})` |	**Not applicable** |
| **Unselect item using text** | **Method**: *unselectItemByText*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{'unselectItemByText','car'})` | **Not applicable** |
| **Selecting item using value**| **Method**: *selectItemByValue*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{'selectItemByValue','car'})` | **Not applicable** |
| **Getting data by using value** |	**Method**: *getItemDataByValue*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{'unselectItemByValue','car'})` | **Method**: *getDataByValue*<br/>`let dropDownListObject = new DropDownList();dropDownListObject.appendTo('#ddlelement')`<br/>`dropDownListObject.getDataByValue();`|
| **Get selected value** | **Method**: *getSelectedItem*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{'getSelectedItem'})` |**Not applicable** |
| **Get selected text** | **Method**: *getSelectedText*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{'getSelectedText'})`| **Property**: *text*<br/>`let dropDownListObject = new DropDownList({text="data"});dropDownListObject.appendTo('#ddlelement')` |
| **Select event** | **Event**: *select*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{select : function (args) {/*Do your changes */}});`| **Event**: *select*<br/>`let dropDownListObject = new DropDownList({select:  "onSelect"});dropDownListObject.appendTo('#ddlelement')`|
| **Addition of Html attributes** | **Property**: *htmlAttributes*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{htmlAttributes: { disabled: "disabled"},});`| **Property**: *htmlAttributes*<br/>`let dropDownListObject = new DropDownList({htmlAttributes:{ disabled: "disabled"}});dropDownListObject.appendTo('#ddlelement')` |

## Common

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Adding new item** | **Method** : *addItem*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{"addItem", {text:"India"}});` | **Method**: *addItem*<br/>`let dropDownListObject = new DropDownList();dropDownListObject.appendTo('#ddlelement')`<br/>`dropDownListObject.addItem("data");` |
| **Clearing the text**| **Method** : *clearText*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{'clearText'})` | **Property**: *value*<br/>`let dropDownListObject = new DropDownList({value:""});dropDownListObject.appendTo('#ddlelement')`|
| **Destroy the component** | **Method** : *destroy*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{'destroy'})`| **Method**: *destroy*<br/>`let dropDownListObject = new DropDownList();dropDownListObject.appendTo('#ddlelement')`<br/>`dropDownListObject.destroy();` |
| **Getting the data** | **Method** : *getListData*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{'getListData'})` |**Method** : *getItems*<br/>`let dropDownListObject = new DropDownList();dropDownListObject.appendTo('#ddlelement')`<br/>`dropDownListObject.getItems();` |
| **Create event** | **Event**: *create*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{create : function (args) {/*Do your changes */}});` | **Event**: *created*<br/>`let dropDownListObject = new DropDownList({created:"create"});dropDownListObject.appendTo('#ddlelement')` |
| **Destroy event** | **Event**: *destroy*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{destroy : function (args) {/*Do your changes */}});`|**Event**: *destroyed*<br/>`let dropDownListObject = new DropDownList({destroyed:"create"});dropDownListObject.appendTo('#ddlelement')` |
| **Cascade  event** | **Event**: *cascade*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{cascade : function (args) {/*Do your changes */}});`|<https://ej2.syncfusion.com/javascript/demos/#/material/drop-down-list/cascading.html> |
| **Change event** | **Event**: *change*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{change : function (args) {/*Do your changes */}});`| **Event**: *change*<br/>`let dropDownListObject = new DropDownList({change:"create"});dropDownListObject.appendTo('#ddlelement')` |
| **Focus out event** |	**Event**: *focusOut*<br/>`var sample = new ej.DropDownList($('#dropdown1'),{focusOut : function (args) {/*Do your changes */}});`| **Event**: *blur*<br/>`let dropDownListObject = new DropDownList({blur:"create"});dropDownListObject.appendTo('#ddlelement')`|
| **Focus in event**| **Event**: *focusIn*<br/><br/>`var sample = new ej.DropDownList($('#dropdown1'),{focusIn : function (args) {/*Do your changes */}});` | **Event**: *focus*<br/>`let dropDownListObject = new DropDownList({focus:"create"});dropDownListObject.appendTo('#ddlelement')` |
