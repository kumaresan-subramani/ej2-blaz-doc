# Migration from Essential JS 1

This article describes the API migration process of ComboBox component from Essential JS 1 to Essential JS 2.

## DataBinding

<!-- markdownlint-disable MD010 -->
| Behavior	| API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Default** |	**Property**: *datasource*<br/>`$('#dropdown1').ejComboBox({dataSource: List});`|**Property**: *DataSource*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({dataSource: sportsData,});comboBoxObject.appendTo('#cmbelement');`|
| **Fields for mapping** | **Property**: *fields*<br/>`$('#dropdown1').ejComboBox({fields: { text: "text", value: "empid" }});`|**Property**: *fields*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({fields: { text: "text", value: "empid" },});comboBoxObject.appendTo('#cmbelement');` |
|**Query** | **Property**: *query*<br/>`$('#dropdown1').ejComboBox({query: ej.Query().requiresCount()})` | **Property**: *query*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({query: new Query().from('Customers').select(['ContactName', 'CustomerID']).take(6),});comboBoxObject.appendTo('#cmbelement');` |
| **Begin event** | **Event**:*actionBegin*<br/>`$('#dropdown1').ejComboBox({actionBegin: "begin"});` | **Event**: *actionBegin*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({actionBegin: "begin",});comboBoxObject.appendTo('#cmbelement');` |
| **Complete event** | **Event**:*actionComplete*<br/>`$('#dropdown1').ejComboBox({actionComplete: "begin"});` | **Event**: *actionComplete*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({actionComplete: "begin",});comboBoxObject.appendTo('#cmbelement');`|
| **Failure event** |**Event**:*actionFailure*<br/>`$('#dropdown1').ejComboBox({actionFailure: "begin"});` | **Event**: *actionFailure*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({actionFailure: "begin",});comboBoxObject.appendTo('#cmbelement');` |

## Filtering

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Default**| **Property**: *allowFiltering*<br/>`$('#dropdown1').ejComboBox({allowFiltering: true});`| **Property**: *allowFiltering*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({allowFiltering: true,});comboBoxObject.appendTo('#cmbelement');`|
| **No records template** | **Property**: *noRecordsTemplate*<br/>`$('#dropdown1').ejComboBox({allowFiltering: "<span class='norecord'> NO DATA AVAILABLE</span>"});` |**Property**: *noRecordsTemplate*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({allowFiltering: true,});comboBoxObject.appendTo('#cmbelement');` |
| **Ignore casing and diacritics**| **Not Applicable** | **Property**: *ignoreAccent*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({ignoreAccent: true,});comboBoxObject.appendTo('#cmbelement');` |
| **Custom value addition** | **Property**: *allowCustom*<br/>`$('#dropdown1').ejComboBox({allowCustom: true});` | <https://ej2.syncfusion.com/demos/#/material/combo-box/custom-value.html> |
| **Search event** | **Event**: *filtering*<br/>`$('#dropdown1').ejComboBox({filtering: "filtering"});` | **Event**: *filtering*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({filtering: "filtering",});comboBoxObject.appendTo('#cmbelement');` |

## Template

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Default** | **Property**: *itemTemplate*<br/>`$('#dropdown1').ejComboBox({itemTemplate: "<span class='item' ><span class='name'>${FirstName}</span><span class='city'>${City}</span></span>"});` | **Property**: *itemTemplate*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({itemTemplate: "<span class='item' ><span class='name'>${FirstName}</span><span class='city'>${City}</span></span>",});comboBoxObject.appendTo('#cmbelement');`|
| **Group Template** | **Property**: *groupTemplate*<br/>`$('#dropdown1').ejComboBox({groupTemplate: "<strong>${City}</strong>"});` | **Property**: *groupTemplate*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({groupTemplate: "<strong>${City}</strong>",});comboBoxObject.appendTo('#cmbelement');`|
| **ValueTemplate** | **Not Applicable** |**Property**: *valueTemplate*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({valueTemplate: "<span>${FirstName} - ${City}</span>",});comboBoxObject.appendTo('#cmbelement');` |
| **Header Template** | **Property**: *headerTemplate*<br/>`$('#dropdown1').ejComboBox({headerTemplate: "<span class='head'><span class='name'>Name</span><span class='city'>City</span></span>"});` |	**Property**: *headerTemplate*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({headerTemplate: "<span class='head'><span class='name'>Name</span><span class='city'>City</span></span>",});comboBoxObject.appendTo('#cmbelement');` |
| **FooterTemplate**| **Property**: *footerTemplate*<br/>`$('#dropdown1').ejComboBox({footerTemplate: "<span class='foot'> Total list items: " + sportsData.length + "</span>"});`| **Property**: *footerTemplate*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({footerTemplate: "<span class='foot'> Total list items: " + sportsData.length + "</span>",});comboBoxObject.appendTo('#cmbelement');` |
| **No records Template** |	**Property**: *noRecordsTemplate*<br/>`$('#dropdown1').ejComboBox({noRecordsTemplate: "<span class='norecord'> NO DATA AVAILABLE</span>"});`| **Property**: *noRecordsTemplate*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({noRecordsTemplate: "<span class='norecord'> NO DATA AVAILABLE</span>",});comboBoxObject.appendTo('#cmbelement');` |
| **Auto fill** | **Property**: *autoFill*<br/>`$('#dropdown1').ejComboBox({autoFill: true});`|**Property**: *autoFill*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({autoFill: true,});comboBoxObject.appendTo('#cmbelement');`|
| **Action failure Template** |	**Property**: *actionFailureTemplate*<br/>`$('#dropdown1').ejComboBox({actionFailureTemplate: "<span class='action-failure'> Data fetch get fails</span>"});`|**Property**: *actionFailureTemplate*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({actionFailureTemplate: "<span class='action-failure'> Data fetch get fails</span>",});comboBoxObject.appendTo('#cmbelement');`|

## Applying CSS

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | ---|
| **Default** | **Property**: *cssClass* <br/>`$('#dropdown1').ejComboBox({cssClass: "className"});`| **Property**: *cssClass*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({cssClass: "className",});comboBoxObject.appendTo('#cmbelement');` |
| **width** | **Property**: *width* <br/>`$('#dropdown1').ejComboBox({width: "500px"});` | **Property**: *Width*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({width: "500px",});comboBoxObject.appendTo('#cmbelement');` |

## Grouping

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2|
| --- | --- | --- |
| **Default** | **Property**: *fields*<br/>`$('#dropdown1').ejComboBox({fields: { groupBy: "text", value: "empid" }});`| **Property**: *fields*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({fields: { groupBy: "text", value: "empid" },});comboBoxObject.appendTo('#cmbelement');` |

## Accessibility

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2|
| --- | --- | --- |
| **Globalization** | **Property**: *locale*<br/>`$('#dropdown1').ejComboBox({locale: true});`| **Property**: *locale*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({locale: true});comboBoxObject.appendTo('#cmbelement');` |
| **Rtl support**| **Property**: *enableRtl*<br/>`$('#dropdown1').ejComboBox({enableRtl: true});`|**Property**: *enableRtl*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({enableRtl: true,});comboBoxObject.appendTo('#cmbelement');`|

## Placeholder

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2|
| --- | --- | --- |
| **Watermark text** | **Property**: *placeholder*<br/>`$('#dropdown1').ejComboBox({placeholder: "Select"});`|<br/>**Property**: *placeholder*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({placeholder: "Select",});comboBoxObject.appendTo('#cmbelement');` |
| **Floating  of watermark text**| **Not applicable** |**Property**: *floatLabelType*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({floatLabelType: "Auto",});comboBoxObject.appendTo('#cmbelement');` |

## Miscellaneous

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2|
| --- | --- | --- |
| **Enable/disable** | **Property**: *enabled*<br/>`$('#dropdown1').ejComboBox({enabled: true});`|**Property**: *enabled*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({enabled: true,});comboBoxObject.appendTo('#cmbelement');` |
| **Read only** | **Property**: *readOnly*<br/>`$('#dropdown1').ejComboBox({readOnly: true});` |**Property**: *readOnly*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({readOnly: true,});comboBoxObject.appendTo('#cmbelement');`|
| **Addition of Html attributes** | **Property**: *htmlAttributes*<br/>`$('#dropdown1').ejComboBox({htmlAttributes: { disabled: "disabled"}});` | **Property**: *htmlAttributes*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({htmlAttributes: { disabled: "disabled"},});comboBoxObject.appendTo('#cmbelement');`|

## Sorting

<!-- markdownlint-disable MD010 -->
|Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Order of sorting** | **Property**: *sortOrder*<br/>`$('#dropdown1').ejComboBox({sortOrder: SortOrder.Ascending});` | **Property**: *sortOrder*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({sortOrder: SortOrder.Ascending,});comboBoxObject.appendTo('#cmbelement');`|

## Selection

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Selecting particular index** | **Property**: *index*<br/>`$('#dropdown1').ejComboBox({index: 1});` | **Property**: *index*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({index: 1,});comboBoxObject.appendTo('#cmbelement');` |
| **Selecting particular value** | **Property**: *value*<br/>`$('#dropdown1').ejComboBox({value: "data"});`| **Property**: *value*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({value: "data",});comboBoxObject.appendTo('#cmbelement');` |
| **Selecting particular text** | **Property**: *text* <br/>`$('#dropdown1').ejComboBox({text: "data"});` | **Property**: *text*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({text: "data",});comboBoxObject.appendTo('#cmbelement');`|
| **Getting data by using value** |	**Method**: *getItemDataByValue*<br/>`$('#dropdown1').ejComboBox({});` <br/> <br/>$('#dropdown1').ejComboBox('getItemDataByValue',"data") | **Method**: *getDataByValue*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({enabled: true,});comboBoxObject.appendTo('#cmbelement');`<br/><br/> comboBoxObject.getDataByValue("data");
| **Select event** | **Event**: *select*<br/>`$('#dropdown1').ejComboBox({select: "onSelect"});`| **Event**: *select*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({select: "onSelect",});comboBoxObject.appendTo('#cmbelement');`|

## Popup

<!-- markdownlint-disable MD010 -->
| Behavior| API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Popup height** | **Property**: *popupHeight*<br/>`$('#dropdown1').ejComboBox({popupHeight: "300px"});`|**Property**:*popupheight*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({popupHeight: "300px",});comboBoxObject.appendTo('#cmbelement');`|
| **Popup width** | **Property**: *popupWidth*<br/>`$('#dropdown1').ejComboBox({popupWidth: "300px"})`|**Property**:*popupWidth*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({popupWidth: "300px",});comboBoxObject.appendTo('#cmbelement');` |
| **Popup showing manually** | **Method**: *showPopup*<br/>`$('#dropdown1').ejComboBox({})` <br/> <br/>`$('#dropdown1').ejComboBox("showPopup");`|	**Method**: *showPopup*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({});comboBoxObject.appendTo('#cmbelement');`<br/><br/>cmbObj.showPopup(); |
| **Popup hiding manually** | **Method**: *hidePopup*<br/>`$('#dropdown1').ejComboBox({})` <br/> <br/>$('#dropdown1').ejComboBox("hidePopup"; | **Method**: *hidePopup*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({popupHeight: "300px",});comboBoxObject.appendTo('#cmbelement');`<br/> <br/> comboBoxObject.hidePopup(); |
| **Popup hide event** | **Event**: *close*<br/>`$('#dropdown1').ejComboBox({close: "onClose"})` | **Event**: *close*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({close: "onclose",});comboBoxObject.appendTo('#cmbelement');`|
| **Popup shown event** | **Event**: *open*<br/>`$('#dropdown1').ejComboBox({open: "onOpen"})`| **Event**: *open*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({open: "onOpen",});comboBoxObject.appendTo('#cmbelement');`|

## Common

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 |API in Essential JS 2 |
| --- | --- | --- |
| **Adding new item** | **Method** : *addItem*<br/>`$('#dropdown1').ejComboBox({})` <br/> <br/>$('#dropdown1').ejComboBox("addItem",{ text :"India"});| **Method**: *addItem*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({});comboBoxObject.appendTo('#cmbelement');`<br/><br/> comboBoxObject.addItem({Id: 'id', Game: 'Golf'},2);|
| **Focus out event** | **Not applicable** | **Event**: *Blur*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({blur: "onclose",});comboBoxObject.appendTo('#cmbelement');` |
| **Focus in event** | **Event**: *Focus*<br/>`$('#dropdown1').ejComboBox({focus:"focus"})` | **Event**: *focusIn*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({focusIn: "focus",});comboBoxObject.appendTo('#cmbelement');` |
| **Focus out** | **Method**: *focusOut*<br/>`$('#dropdown1').ejComboBox({})` <br/> <br/>$('#dropdown1').ejComboBox("focusOut");| **Method**: *focusOut*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({open: "onOpen",});comboBoxObject.appendTo('#cmbelement');`<br/><br/> comboBoxObject.focusOut(); |
| **Focus in** | **Method**: *focusIn*<br/>`$('#dropdown1').ejComboBox({})` <br/> <br/>$('#dropdown1').ejComboBox("focusIn"); | **Method**: *focusIn*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({});comboBoxObject.appendTo('#cmbelement');`<br/><br/> comboBoxObject.focusIn(); |
| **Getting the data** | **Method** : *getItems*<br/>`$('#dropdown1').ejComboBox({})` <br/> <br/>$('#dropdown1').ejComboBox("getItems"); | **Method**: *getItems*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({});comboBoxObject.appendTo('#cmbelement');`<br/><br/> comboBoxObject.getItems();|
| **Create event** | **Event**: *create*<br/>`$('#dropdown1').ejComboBox({create:"onCreate"})` |	**Event**: *created*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({created: "oncreate",});comboBoxObject.appendTo('#cmbelement');` |
| **Change event** | **Event**: *change*<br/>`$('#dropdown1').ejComboBox({focus:"focus"})` | **Event**: *change*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({change: "onchange",});comboBoxObject.appendTo('#cmbelement');` |
| **Custom value event** | **Event**: *customValueSpecifier*<br/>`$('#dropdown1').ejComboBox({customValueSpecifier:"customValueSpecifier"})` | **Event**: *customValueSpecifier*<br/>`var comboBoxObject = new ej.dropdowns.ComboBox({customValueSpecifier: "customValueSpecifier",});comboBoxObject.appendTo('#cmbelement');` |
