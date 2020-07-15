
# Migration from Essential JS 1

This article describes the API migration process of ComboBox component from Essential JS 1 to Essential JS 2.

## DataBinding

<!-- markdownlint-disable MD010 -->
| Behavior	| API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Default** |	**Property**: *datasource*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{dataSource: List});`|**Property**: *dataSource*<br/>`let comboBoxObject = new ComboBox({dataSource: sportsData,});comboBoxObject.appendTo('#cmbelement');`|
| **Fields for mapping** | **Property**: *fields*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{fields: { text: "text", value: "empid" }});`|**Property**: *fields*<br/>`let comboBoxObject = new ComboBox({fields: { text: "text", value: "empid" },});comboBoxObject.appendTo('#cmbelement');` |
|**Query** | **Property**: *query*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{query: ej.Query().requiresCount()})` | **Property**: *query*<br/>`let comboBoxObject = new ComboBox({query: new Query().from('Customers').select(['ContactName', 'CustomerID']).take(6),});comboBoxObject.appendTo('#cmbelement');` |
| **Begin event** | **Event**:*actionBegin*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{actionBegin: "begin"});` | **Event**: *actionBegin*<br/>`let comboBoxObject = new ComboBox({actionBegin: "begin",});comboBoxObject.appendTo('#cmbelement');` |
| **Complete event** | **Event**:*actionComplete*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{actionComplete: "begin"});` | **Event**: *actionComplete*<br/>`let comboBoxObject = new ComboBox({actionComplete: "begin",});comboBoxObject.appendTo('#cmbelement');`|
| **Failure event** |**Event**:*actionFailure*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{actionFailure: "begin"});` | **Event**: *actionFailure*<br/>`let comboBoxObject = new ComboBox({actionFailure: "begin",});comboBoxObject.appendTo('#cmbelement');` |

## Filtering

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Default**| **Property**: *allowFiltering*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{allowFiltering: true});`| **Property**: *allowFiltering*<br/>`let comboBoxObject = new ComboBox({allowFiltering: true,});comboBoxObject.appendTo('#cmbelement');`|
| **No records template** | **Property**: *noRecordsTemplate*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{allowFiltering: "<span class='norecord'> NO DATA AVAILABLE</span>"});` |**Property**: *noRecordsTemplate*<br/>`let comboBoxObject = new ComboBox({allowFiltering: true,});comboBoxObject.appendTo('#cmbelement');` |
| **Ignore casing and diacritics**| **Not Applicable** | **Property**: *ignoreAccent*<br/>`let comboBoxObject = new ComboBox({ignoreAccent: true,});comboBoxObject.appendTo('#cmbelement');` |
| **Custom value addition** | **Property**: *allowCustom*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{allowCustom: true});` | <https://ej2.syncfusion.com/javascript/demos/#/material/combo-box/custom-value.html> |
| **Search event** | **Event**: *filtering*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{filtering: "filtering"});` | **Event**: *filtering*<br/>`let comboBoxObject = new ComboBox({filtering: "filtering",});comboBoxObject.appendTo('#cmbelement');` |

## Template

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Default** | **Property**: *itemTemplate*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{itemTemplate: "<span class='item' ><span class='name'>${FirstName}</span><span class='city'>${City}</span></span>"});` | **Property**: *itemTemplate*<br/>`let comboBoxObject = new ComboBox({itemTemplate: "<span class='item' ><span class='name'>${FirstName}</span><span class='city'>${City}</span></span>",});comboBoxObject.appendTo('#cmbelement');`|
| **Group Template** | **Property**: *groupTemplate*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{groupTemplate: "<strong>${City}</strong>"});` | **Property**: *groupTemplate*<br/>`let comboBoxObject = new ComboBox({groupTemplate: "<strong>${City}</strong>",});comboBoxObject.appendTo('#cmbelement');`|
| **ValueTemplate** | **Not Applicable** |**Property**: *valueTemplate*<br/>`let comboBoxObject = new ComboBox({valueTemplate: "<span>${FirstName} - ${City}</span>",});comboBoxObject.appendTo('#cmbelement');` |
| **Header Template** | **Property**: *headerTemplate*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{headerTemplate: "<span class='head'><span class='name'>Name</span><span class='city'>City</span></span>"});` |	**Property**: *headerTemplate*<br/>`let comboBoxObject = new ComboBox({headerTemplate: "<span class='head'><span class='name'>Name</span><span class='city'>City</span></span>",});comboBoxObject.appendTo('#cmbelement');` |
| **FooterTemplate**| **Property**: *footerTemplate*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{footerTemplate: "<span class='foot'> Total list items: " + sportsData.length + "</span>"});`| **Property**: *footerTemplate*<br/>`let comboBoxObject = new ComboBox({footerTemplate: "<span class='foot'> Total list items: " + sportsData.length + "</span>",});comboBoxObject.appendTo('#cmbelement');` |
| **No records Template** |	**Property**: *noRecordsTemplate*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{noRecordsTemplate: "<span class='norecord'> NO DATA AVAILABLE</span>"});`| **Property**: *noRecordsTemplate*<br/>`let comboBoxObject = new ComboBox({noRecordsTemplate: "<span class='norecord'> NO DATA AVAILABLE</span>",});comboBoxObject.appendTo('#cmbelement');` |
| **Auto fill** | **Property**: *autoFill*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{autoFill: true});`|**Property**: *autoFill*<br/>`let comboBoxObject = new ComboBox({autoFill: true,});comboBoxObject.appendTo('#cmbelement');`|
| **Action failure Template** |	**Property**: *actionFailureTemplate*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{actionFailureTemplate: "<span class='action-failure'> Data fetch get fails</span>"});`|**Property**: *actionFailureTemplate*<br/>`let comboBoxObject = new ComboBox({actionFailureTemplate: "<span class='action-failure'> Data fetch get fails</span>",});comboBoxObject.appendTo('#cmbelement');`|

## Applying CSS

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | ---|
| **Default** | **Property**: *cssClass* <br/>`var sample = new ej.ComboBox($('#dropdown1'),{cssClass: "className"});`| **Property**: *cssClass*<br/>`let comboBoxObject = new ComboBox({cssClass: "className",});comboBoxObject.appendTo('#cmbelement');` |
| **width** | **Property**: *width* <br/>`var sample = new ej.ComboBox($('#dropdown1'),{width: "500px"});` | **Property**: *Width*<br/>`let comboBoxObject = new ComboBox({width: "500px",});comboBoxObject.appendTo('#cmbelement');` |

## Grouping

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2|
| --- | --- | --- |
| **Default** | **Property**: *fields*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{fields: { groupBy: "text", value: "empid" }});`| **Property**: *fields*<br/>`let comboBoxObject = new ComboBox({fields: { groupBy: "text", value: "empid" },});comboBoxObject.appendTo('#cmbelement');` |

## Accessibility

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2|
| --- | --- | --- |
| **Globalization** | **Property**: *locale*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{locale: true});`| **Property**: *locale*<br/>`let comboBoxObject = new ComboBox({locale: true});comboBoxObject.appendTo('#cmbelement');` |
| **Rtl support**| **Property**: *enableRtl*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{enableRtl: true});`|**Property**: *enableRtl*<br/>`let comboBoxObject = new ComboBox({enableRtl: true,});comboBoxObject.appendTo('#cmbelement');`|

## Placeholder

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2|
| --- | --- | --- |
| **Watermark text** | **Property**: *placeholder*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{placeholder: "Select"});`|<br/>**Property**: *placeholder*<br/>`let comboBoxObject = new ComboBox({placeholder: "Select",});comboBoxObject.appendTo('#cmbelement');` |
| **Floating  of watermark text**| **Not applicable** |**Property**: *floatLabelType*<br/>`let comboBoxObject = new ComboBox({floatLabelType: "Auto",});comboBoxObject.appendTo('#cmbelement');` |

## Miscellaneous

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2|
| --- | --- | --- |
| **Enable/disable** | **Property**: *enabled*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{enabled: true});`|**Property**: *enabled*<br/>`let comboBoxObject = new ComboBox({enabled: true,});comboBoxObject.appendTo('#cmbelement');` |
| **Read only** | **Property**: *readOnly*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{readOnly: true});` |**Property**: *readOnly*<br/>`let comboBoxObject = new ComboBox({readOnly: true,});comboBoxObject.appendTo('#cmbelement');`|
| **Addition of Html attributes** | **Property**: *htmlAttributes*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{htmlAttributes: { disabled: "disabled"}});` | **Property**: *htmlAttributes*<br/>`let comboBoxObject = new ComboBox({htmlAttributes: { disabled: "disabled"},});comboBoxObject.appendTo('#cmbelement');`|

## Sorting

<!-- markdownlint-disable MD010 -->
|Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Order of sorting** | **Property**: *sortOrder*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{sortOrder: SortOrder.Ascending});` | **Property**: *sortOrder*<br/>`let comboBoxObject = new ComboBox({sortOrder: SortOrder.Ascending,});comboBoxObject.appendTo('#cmbelement');`|

## Selection

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Selecting particular index** | **Property**: *index*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{index: 1});` | **Property**: *index*<br/>`let comboBoxObject = new ComboBox({index: 1,});comboBoxObject.appendTo('#cmbelement');` |
| **Selecting particular value** | **Property**: *value*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{value: "data"});`| **Property**: *value*<br/>`let comboBoxObject = new ComboBox({value: "data",});comboBoxObject.appendTo('#cmbelement');` |
| **Selecting particular text** | **Property**: *text* <br/>`var sample = new ej.ComboBox($('#dropdown1'),{text: "data"});` | **Property**: *text*<br/>`let comboBoxObject = new ComboBox({text: "data",});comboBoxObject.appendTo('#cmbelement');`|
| **Getting data by using value** |	**Method**: *getItemDataByValue*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{});` <br/> <br/>$('#dropdown1').ejComboBox('getItemDataByValue',"data") | **Method**: *getDataByValue*<br/>`let comboBoxObject = new ComboBox({enabled: true,});comboBoxObject.appendTo('#cmbelement');`<br/><br/> comboBoxObject.getDataByValue("data");
| **Select event** | **Event**: *select*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{select: "onSelect"});`| **Event**: *select*<br/>`let comboBoxObject = new ComboBox({select: "onSelect",});comboBoxObject.appendTo('#cmbelement');`|

## Popup

<!-- markdownlint-disable MD010 -->
| Behavior| API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| **Popup height** | **Property**: *popupHeight*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{popupHeight: "300px"});`|**Property**:*popupheight*<br/>`let comboBoxObject = new ComboBox({popupHeight: "300px",});comboBoxObject.appendTo('#cmbelement');`|
| **Popup width** | **Property**: *popupWidth*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{popupWidth: "300px"})`|**Property**:*popupWidth*<br/>`let comboBoxObject = new ComboBox({popupWidth: "300px",});comboBoxObject.appendTo('#cmbelement');` |
| **Popup showing manually** | **Method**: *showPopup*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{})` <br/> <br/>`sample.showPopup();`|	**Method**: *showPopup*<br/>`let comboBoxObject = new ComboBox({});comboBoxObject.appendTo('#cmbelement');`<br/><br/>cmbObj.showPopup(); |
| **Popup hiding manually** | **Method**: *hidePopup*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{})` <br/> <br/>sample.hidePopup(); | **Method**: *hidePopup*<br/>`let comboBoxObject = new ComboBox({popupHeight: "300px",});comboBoxObject.appendTo('#cmbelement');`<br/> <br/> comboBoxObject.hidePopup(); |
| **Popup hide event** | **Event**: *close*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{close: "onClose"})` | **Event**: *close*<br/>`let comboBoxObject = new ComboBox({close: "onclose",});comboBoxObject.appendTo('#cmbelement');`|
| **Popup shown event** | **Event**: *open*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{open: "onOpen"})`| **Event**: *open*<br/>`let comboBoxObject = new ComboBox({open: "onOpen",});comboBoxObject.appendTo('#cmbelement');`|

## Common

<!-- markdownlint-disable MD010 -->
| Behavior | API in Essential JS 1 |API in Essential JS 2 |
| --- | --- | --- |
| **Adding new item** | **Method** : *addItem*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{})` <br/> <br/>sample.addItem({ text :"India"});| **Method**: *addItem*<br/>`let comboBoxObject = new ComboBox({});comboBoxObject.appendTo('#cmbelement');`<br/><br/> comboBoxObject.addItem({Id: 'id', Game: 'Golf'},2);|
| **Focus out event** | **Not applicable** | **Event**: *Blur*<br/>`let comboBoxObject = new ComboBox({blur: "onclose",});comboBoxObject.appendTo('#cmbelement');` |
| **Focus in event** | **Event**: *focus*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{focus:"focus"})` | **Event**: *focusIn*<br/>`let comboBoxObject = new ComboBox({focusIn: "focus",});comboBoxObject.appendTo('#cmbelement');` |
| **Focus out** | **Method**: *focusOut*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{})` <br/> <br/>sample.focusOut();| **Method**: *focusOut*<br/>`let comboBoxObject = new ComboBox({open: "onOpen",});comboBoxObject.appendTo('#cmbelement');`<br/><br/> comboBoxObject.focusOut(); |
| **Focus in** | **Method**: *focusIn*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{})` <br/> <br/>sample.focusIn(); | **Method**: *focusIn*<br/>`let comboBoxObject = new ComboBox({});comboBoxObject.appendTo('#cmbelement');`<br/><br/> comboBoxObject.focusIn(); |
| **Getting the data** | **Method** : *getItems*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{})` <br/> <br/>sample.getItems(); | **Method**: *getItems*<br/>`let comboBoxObject = new ComboBox({});comboBoxObject.appendTo('#cmbelement');`<br/><br/> comboBoxObject.getItems();|
| **Create event** | **Event**: *create*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{create:"onCreate"})` |	**Event**: *created*<br/>`let comboBoxObject = new ComboBox({created: "oncreate",});comboBoxObject.appendTo('#cmbelement');` |
| **Change event** | **Event**: *change*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{focus:"focus"})` | **Event**: *change*<br/>`let comboBoxObject = new ComboBox({change: "onchange",});comboBoxObject.appendTo('#cmbelement');` |
| **Custom value event** | **Event**: *customValueSpecifier*<br/>`var sample = new ej.ComboBox($('#dropdown1'),{customValueSpecifier:"customValueSpecifier"})` | **Event**: *customValueSpecifier*<br/>`let comboBoxObject = new ComboBox({customValueSpecifier: "customValueSpecifier",});comboBoxObject.appendTo('#cmbelement');` |
