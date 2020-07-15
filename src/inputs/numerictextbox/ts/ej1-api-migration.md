---
title: "Migration from Essential JS 1"
component: "NumericTextBox"
description: "Explains the common steps for migrating from Essential JS 1 application to Essential JS 2 components especially, NumericTextBox component."
---

# Migration from Essential JS 1

This article describes the API migration process of NumericTextBox component from Essential JS 1 to Essential JS 2.

## Common

| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| Triggers on creation | **Event:** *create*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 120,<br />create: function(){}<br/>}); | **Event:** *created*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 120,<br />created: function(){}<br />});<br />numeric.appendTo("#numeric"); |
| Adding custom classes | **Property:** *cssClass*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />cssClass: “custom”<br />}); | **Property:** *cssClass*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 100,<br />cssClass: “custom”<br />});<br />numeric.appendTo("#numeric"); |
| Triggers when editor is destroyed | **Event:** *destroy*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 120,<br />destroy: function(){}<br/>}); | **Event:** *destroyed*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 120,<br />destroyed: function(){}<br />});<br />numeric.appendTo("#numeric"); |
| Destroys textbox | **Method:** *destroy*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100<br />});<br />var numericObj = $(“#numeric”).data(“ejNumericTextBox”);<br />numericObj.destroy(); | **Method:** *destroy*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 100,<br />enabled: false<br />});<br />numeric.appendTo("#numeric");<br />numeric.destroy(); |
| Control state | **Property:** *enabled*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />enabled: false<br />}); | **Property:** *enabled*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 100,<br />enabled: false<br />});<br />numeric.appendTo("#numeric"); |
| Persistence | **Property:** *enablePersistence*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />enablePersistence: true<br />}); | **Property:** *enablePersistence*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 100,<br />enablePersistence: true<br />});<br />numeric.appendTo("#numeric"); |
| Right To Left | **Property:** *enableRTL*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />enableRTL: true<br />}); | **Property:** *enableRtl*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 100,<br />enableRtl: true<br />});<br />numeric.appendTo("#numeric"); |
| Triggers when editor is focused in | **Event:** *focusIn*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 20,<br />focusIn: function(){}}) |**Event:** *focus*<br/><br/>let numeric: NumericTextBox = new NumericTextBox({<br/>value: 100,<br/>focus: function() {}<br/>});<br/>numeric.appendTo("#numeric"); |
| Triggers when editor is focused out | **Event:** *focusOut*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />focusOut: function(){}}) | **Event:** *blur*<br/><br/>let numeric: NumericTextBox = new NumericTextBox({<br/>value: 100,<br/>blur: function() {}<br/>});<br/>numeric.appendTo("#numeric"); |
| Sets Height | **Property:** *height*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />height: "40px"<br />}); | **Can be achieved using,** <br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 100,<br />cssClass: "custom"<br />});<br />numeric.appendTo("#numeric");<br />**Css**<br />.e-numerictextbox.custom{<br />height: 40px;<br />} |
| HTML Attributes | **Property:** *htmlAttributes*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />htmlAttributes: {disabled: "disabled"}<br />}); | **Can be achieved using,** <br/><br/>&lt;input id="numeric" type="text" name="textbox" /> <br/>let numeric: NumericTextBox = new NumericTextBox({<br/>value: 1234",<br/>});<br/>numeric.appendTo("#numeric") |
| Name of editor | **Property:** *name*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />name: “Textbox”<br />}); | **Can be achieved using,** <br/><br/> **HTML**<br/> &lt;input id="numeric" type="text" name="textbox" /> <br/> let numeric: NumericTextBox = new NumericTextBox({<br/>value: 100 ,<br/>});<br/>numeric.appendTo("#numeric"); |
| Read only | **Property:** *readOnly*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 80,<br />readOnly: true<br />}); | **Property:** *readonly*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 80,<br /> readonly: true<br />});<br />numeric.appendTo("#numeric"); |
| Rounded corners | **Property:** *showRoundedCorner*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 80,<br />showRoundedCorner: true<br />}); | **Can be achieved using**<br/>let numeric: NumericTextBox  = new NumericTextBox({<br />value: 100,<br />cssClass: “e-style”<br />});<br />numeric.appendTo("#numeric");<br/>*CSS*<br/>e-control-wrapper.e-numeric.e-input-group.e-style {<br/>border: 2.5px solid;<br/>border-radius: 1rem;<br/>padding-left: 12px;<br/>}<br/>.e-control-wrapper.e-numeric.e-float-input.e-style .e-float-line::before, .e-control-wrapper.e-numeric.e-float-input.e-style  .e-float-line::after{<br/>background: none ;<br/>}<br/>.e-control-wrapper.e-numeric.e-input-group.e-style.e-input-focus{<br/> border: solid grey  !important;<br/>} |
| Spin Button | **Property:** *showSpinButton*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 20,<br />showSpinButton: false<br />}); | **Property:** *showSpinButton*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 20,<br />showSpinButton: false<br />});<br />numeric.appendTo("#numeric"); |
| Width | **Property:** *width*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 20,<br />width: "220px"<br />}); | **Property:** *width*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 20,<br />width: "220px"<br />});<br />numeric.appendTo("#numeric"); |
| Clear Button | Not Applicable | **Property:** *showClearButton*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 100,<br />showClearButton: true<br />});<br />numeric.appendTo("#numeric"); |

## Globalization

| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| Localization culture | **Property:** *locale*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 80,<br />locale: “de-DE”<br />}); | **Property:** *locale*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 80,<br />locale: “de-DE”<br />});<br />numeric.appendTo("#numeric"); |

## Group

| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| Group digits in editor | **Property:** *groupSize*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />groupSize: "2"<br />}); | Not Applicable |
| Group Separator | **Property:** *groupSeparator*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />groupSeparator: "-"<br />}); | Not Applicable |

## Numeric configuration

| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | ---- |
| Triggers on value change | **Event:** *change*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 120,<br />change: function(){}}) | **Event:** *change*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 120,<br />change: function(){}<br />});<br />numeric.appendTo("#numeric"); |
| Sets digits allowed after decimal point | **Property:** *decimalPlaces*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />decimalPlaces: 2<br />}); | **Property:** *decimals*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 100,<br />format: “n2”,<br />decimals: 2<br />});<br />numeric.appendTo("#numeric"); |
| Decrement value | Not Applicable | **Method:** *decrement*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 100<br />});<br />numeric.appendTo("#numeric");<br />numeric.decrement(); |
| Disable the textbox | **Method:** *disable*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 200<br />});<br />var numericObj = $(“#numeric”).data(“ejNumericTextBox”);<br />numericObj.disable(); | **Can be achieved using**<br/>**API:** *enabled*<br/>let numeric: NumericTextBox = new NumericTextBox({<br />value: 100<br />});<br />numeric.appendTo("#numeric");<br/>var numObj = document.getElementById("numeric").ej2_instances[0];<br/>numObj.enabled = false; |
| Enable the textbox | **Method:** *enable*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 200<br />});<br />var numericObj = $(“#numeric”).data(“ejNumericTextBox”);<br />numericObj.enable(); | **Can be achieved using,**<br/> **API:** *enabled* <br/>let numeric: NumericTextBox = new NumericTextBox({<br />value: 100<br />});<br />numeric.appendTo("#numeric");<br/>var numObj = document.getElementById("numeric").ej2_instances[0];<br/>numObj.enabled = true; |
| Gets value of editor | **Method:** *getValue*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100<br />});<br />var numericObj = $(“#numeric”).data(“ejNumericTextBox”);<br />numericObj.getValue(); | **Method:** *getText*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 100<br />});<br />numeric.appendTo("#numeric");<br />numeric.getText(); |
| Increment value | Not Applicable | **Method:** *increment*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 80<br />});<br />numeric.appendTo("#numeric");<br />numeric.increment(); |
| Step value | **Property:** *incrementStep*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />incrementStep: 2<br />}); | **Property:** *step*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 100,<br />step: 2<br />});<br />numeric.appendTo("#numeric"); |
| Sets Maximum value | **Property:** *maxValue*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />maxValue: 200<br />}); | **Property:** *max*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 100,<br />max: 200<br />});<br />numeric.appendTo("#numeric"); |
| Sets Minimum value | **Property:** *minValue*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />minValue: 20<br />}); | **Property:** *min*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 100,<br />min: 20<br />});<br />numeric.appendTo("#numeric"); |
| Negative pattern for formatting values | **Property:** *negativePattern*<br /><br />$("#numeric").ejNumericTextBox({<br />value: -20,<br />negativePattern: "( n)"<br />}); | Not Applicable |
| Positive pattern for formatting values | **Property:** *positivePattern*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 20,<br />positivePattern: "n kg"<br />}); | Not Applicable |
| Specifies value | **Property:** *value*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100<br />}); | **Property:** *value*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 100<br />});<br />numeric.appendTo("#numeric"); |
| Displays hint on editor | **Property:** *watermarkText*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 80<br />watermarkText: "Enter value:"<br />}); | **Property:** *placeholder*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 100<br />placeholder: "Enter value:"<br />});<br />numeric.appendTo("#numeric"); |
| Placeholder float type | Not Applicable | **Property:** *floatLabelType*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 200<br />placeholder: "Enter value:"<br />floatLabelType: "Auto"<br />});<br />numeric.appendTo("#numeric"); |

## Number Formats

| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| Set Currency symbol | **Property:** *currencySymbol*<br /><br />$("#currency").ejCurrencyTextBox({<br />value: 100,<br />currencySymbol: “EUR”<br />}); | **Property:** *currency*<br /><br />let currency: NumericTextBox  = new NumericTextBox({<br />value: 100,<br />format: “c2”,<br />currency: “EUR”<br />});<br />currency.appendTo("#currency"); |
| Number Format | Not Applicable | **Property:** *format*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 200<br />format: "n2"<br />});<br />numeric.appendTo("#numeric"); |

## Validation

| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| Strict Mode | **Property:** *enableStrictMode*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 80,<br />enableStrictMode: true<br />}); | **Property:** *strictMode*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 80,<br />strictMode: true<br />});<br />numeric.appendTo("#numeric"); |
| Validation on typing | **Property:** *validateOnType*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />validateOnType: true<br />}); | **Property:** *validateDecimalOnType*<br /><br />let numeric: NumericTextBox  = new NumericTextBox({<br />value: 100,<br />validateDecimalOnType: true<br />});<br />numeric.appendTo("#numeric"); |
| Validation Message | **Property:** *validationMessage*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />validationRules: {required: true}<br />validationMessage: {required: “Required value”}<br />}); | **Validation in NumericTextBox can be achieved through form validation**<br/>let options: FormValidatorModel = {<br/>rules: {<br/>'numericValue': { required: [true, "Number is required"]},<br/>}<br/> let formObject: FormValidator = new FormValidator('#form-element', options);<br/>formObject.customPlacement= (inputElement, error) => {<br/>document.getElementById('error').appendChild(error);<br/>}<br/>let numeric: NumericTextBox = new NumericTextBox({value: "1234"<br/>});<br/>numeric.appendTo("#numeric");<br/>**HTML** <br/> &lt;form id="form-element" class="form-horizontal"><br/>&lt;input id="numeric" type="text" name="numericValue" class="form-control" /> <br/>&lt;div id="error">&lt;/div><br/>&lt;/form> |
| Validation Rules | **Property:** *validationRules*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />validationRules: {required: true}<br />}); | **Validation in NumericTextBox can be achieved through form validation**<br/>let options: FormValidatorModel = {<br/>rules: {<br/>'numericValue': { required: true},<br/>}<br/> let formObject: FormValidator = new FormValidator('#form-element', options);<br/>let numeric: NumericTextBox = new NumericTextBox({<br/>value: "1234"<br/>});<br/>numeric.appendTo("#numeric");<br/>**HTML** <br/> &lt;form id="form-element"><br/>&lt;input id="numeric" type="text" name="numericValue" class="form-control" /><br/> &lt;/form> |
