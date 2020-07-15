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
| Triggers on creation | **Event:** *create*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 120,<br />create: function(){}<br/>}); | **Event:** *created*<br /><br />var numeric  = new ej.inputs.NumericTextBox({<br />value: 120,<br />created: function(){}<br />});<br />numeric.appendTo("#numeric"); |
| Adding custom classes | **property:** *cssClass*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />cssClass: “custom”<br />}); | **Property:** *cssClass*<br /><br />var numeric  = new ej.inputs.NumericTextBox({<br />value: 100,<br />cssClass: “custom”<br />});<br />numeric.appendTo("#numeric"); |
| Triggers when editor is destroyed | **Event:** *destroy*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 120,<br />destroy: function(){}<br/>}); | **Event:** *destroyed*<br /><br />var numeric  = new ej.inputs.NumericTextBox({<br />value: 120,<br />destroyed: function(){}<br />});<br />numeric.appendTo("#numeric"); |
| Destroys textbox | **Method:** *destroy*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100<br />});<br />var numericObj = $(“#numeric”).data(“ejNumericTextBox”);<br />numericObj.destroy(); | **Method:** *destroy*<br /><br />var numeric  = new ej.inputs.NumericTextBox({<br />value: 100,<br />enabled: false<br />});<br />numeric.appendTo("#numeric");<br />numeric.destroy(); |
| Control state | **property:** *enabled*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />enabled: false<br />}); | **Property:** *enabled*<br /><br />var numeric  = new ej.inputs.NumericTextBox({<br />value: 100,<br />enabled: false<br />});<br />numeric.appendTo("#numeric"); |
| Persistence | **property:** *enablePersistence*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />enablePersistence: true<br />}); | **Property:** *enablePersistence*<br /><br />var numeric  = new ej.inputs.NumericTextBox({<br />value: 100,<br />enablePersistence: true<br />});<br />numeric.appendTo("#numeric"); |
| Right To Left | **property:** *enableRTL*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />enableRTL: true<br />}); | **Property:** *enableRtl*<br /><br />var numeric  = new ej.inputs.NumericTextBox({<br />value: 100,<br />enableRtl: true<br />});<br />numeric.appendTo("#numeric"); |
| Triggers when editor is focused in | **Event:** *focusIn*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 20,<br />focusIn: function(){}<br/>}); | **Event:** *focus*<br/><br/>var numeric = new ej.inputs.NumericTextBox({<br/>value: 100,<br/>focus: function() {}<br/>});<br/>numeric.appendTo("#numeric"); |
| Triggers when editor is focused out | **Event:** *focusOut*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />focusOut: function(){}<br/>}); | **Event:** *blur*<br/><br/>var numeric = new ej.inputs.NumericTextBox({<br/>value: 100,<br/>blur: function() {}<br/>});<br/>numeric.appendTo("#numeric"); |
| Sets Height | **property:** *height*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />height: "40px"<br />}); | **Can be achieved using,** <br /><br />var numeric  = new ej.inputs.NumericTextBox({<br />value: 100,<br />cssClass: "custom"<br />});<br />numeric.appendTo("#numeric");<br />**Css**<br />.e-numerictextbox.custom{<br />height: 40px;<br />} |
| HTML Attributes | **property:** *htmlAttributes*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />htmlAttributes: {disabled: "disabled"}<br />}); | **Can be achieved using,** <br/><br/>&lt;input id="numeric" type="text" name="textbox" /> <br/>var numeric  = new ej.inputs.NumericTextBox({<br />value: 100<br />});<br />numeric.appendTo("#numeric") |
| Name of editor | **property:** *name*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />name: “Textbox”<br />}); | **Can be achieved using,** <br/><br/> **HTML**<br/> &lt;input id="numeric" type="text" name="textbox" /> <br/> var numeric  = new ej.inputs.NumericTextBox({<br />value: 100,<br />});<br />numeric.appendTo("#numeric"); |
| Read only | **property:** *readOnly*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 80,<br />readOnly: true<br />}); | **Property:** *readonly*<br /><br />var numeric  = new ej.inputs.NumericTextBox({<br />value: 80,<br />readonly: true<br />});<br />numeric.appendTo("#numeric"); |
| Rounded corners | **property:** *showRoundedCorner*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 80,<br />showRoundedCorner: true<br />}); | **Can be achieved using**<br/>var numeric  = new ej.inputs.NumericTextBox({<br />value: 100,<br />cssClass: "e-style"<br />});<br />numeric.appendTo("#numeric");<br/>**CSS**<br/>.e-control-wrapper.e-numeric.e-input-group.e-style {<br/>border: 2.5px solid;<br/>border-radius: 1rem;<br/>padding-left: 12px;<br/>}<br/>.e-control-wrapper.e-numeric.e-float-input.e-style .e-float-line::before, .e-control-wrapper.e-numeric.e-float-input.e-style  .e-float-line::after{<br/>background: none ;<br/>}<br/>.e-control-wrapper.e-numeric.e-input-group.e-style.e-input-focus{<br/> border: solid grey  !important;<br/>} |
| Spin Button | **property:** *showSpinButton*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 20,<br />showSpinButton: false<br />}); | **Property:** *showSpinButton*<br /><br />var numeric  = new ej.inputs.NumericTextBox({<br />value: 20,<br />showSpinButton: false<br />});<br />numeric.appendTo("#numeric"); |
| Width | **property:** *width*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 20,<br />width: "220px"<br />}); | **Property:** *width*<br /><br />var numeric  = new ej.inputs.NumericTextBox({<br />value: 20,<br />width: "220px"<br />});<br />numeric.appendTo("#numeric"); |
| Clear Button | Not Applicable | **Property:** *showClearButton*<br /><br />var numeric  = new ej.inputs.NumericTextBox({<br />value: 100,<br />showClearButton: true<br />});<br />numeric.appendTo("#numeric"); |

## Globalization

| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| Localization culture | **property:** *locale*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 80,<br />locale: “de-DE”<br />}); | **Property:** *locale*<br /><br />var numeric  = new ej.inputs.NumericTextBox({<br />value: 80,<br />locale: “de-DE”<br />});<br />numeric.appendTo("#numeric"); |

## Group

| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| Group digits in editor | **property:** *groupSize*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />groupSize: "2"<br />}); | Not Applicable |
| Group Separator | **property:** *groupSeparator*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />groupSeparator: "-"<br />}); | Not Applicable |

## Numeric configuration

| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| Triggers on value change | **Event:** *change*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 120,<br />change: function(){}<br/>}); | **Event:** *change*<br /><br />var numeric  = new ej.inputs.NumericTextBox({<br />value: 120,<br />change: function(){}<br />});<br />numeric.appendTo("#numeric"); |
| Sets digits allowed after decimal point | **property:** *decimalPlaces*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />decimalPlaces: 2<br />}); | **Property:** *decimals*<br /><br />var numeric = new ej.inputs.NumericTextBox({<br />value: 100,<br />format: “n2”,<br />decimals: 2<br />});<br />numeric.appendTo("#numeric"); |
| Decrement value | Not Applicable | **Method:** *decrement*<br /><br />var numeric = new ej.inputs.NumericTextBox({<br />value: 100<br />});<br />numeric.appendTo("#numeric");<br />numeric.decrement(); |
| Disable the textbox | **Method:** *disable*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 200<br />});<br />var numericObj = $(“#numeric”).data(“ejNumericTextBox”);<br />numericObj.disable(); | **Can be achieved using,**<br/> **API:** *enabled* <br/>var numeric  = new ej.inputs.NumericTextBox({<br />value: 100,<br />});<br />numeric.appendTo("#numeric");<br/>var numObj = document.getElementById("numeric").ej2_instances[0]<br/>numObj.enabled = false; |
| Enable the textbox | **Method:** *enable*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 200<br />});<br />var numericObj = $(“#numeric”).data(“ejNumericTextBox”);<br />numericObj.enable(); | **Can be achieved using,**<br/> **API:** *enabled* <br/>var numeric  = new ej.inputs.NumericTextBox({<br />value: 100,<br />});<br />numeric.appendTo("#numeric");<br/>var numObj = document.getElementById("numeric").ej2_instances[0]<br/>numObj.enabled = true; |
| Gets value of editor | **Method:** *getValue*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100<br />});<br />var numericObj = $(“#numeric”).data(“ejNumericTextBox”);<br />numericObj.getValue(); | **Method:** *getText*<br /><br />var numeric = new ej.inputs.NumericTextBox({<br />value: 100<br />});<br />numeric.appendTo("#numeric");<br />numeric.getText(); |
| Increment value | Not Applicable | **Method:** *increment*<br /><br />var numeric = new ej.inputs.NumericTextBox({<br />value: 80<br />});<br />numeric.appendTo("#numeric");<br />numeric.increment(); |
| Step value | **property:** *incrementStep*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />incrementStep: 2<br />}); | **Property:** *step*<br /><br />var numeric = new ej.inputs.NumericTextBox({<br />value: 100,<br />step: 2<br />});<br />numeric.appendTo("#numeric"); |
| Sets Maximum value | **property:** *maxValue*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />maxValue: 200<br />}); | **Property:** *max*<br /><br />var numeric = new ej.inputs.NumericTextBox({<br />value: 100,<br />max: 200<br />});<br />numeric.appendTo("#numeric"); |
| Sets Minimum value | **property:** *minValue*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />minValue: 20<br />}); | **Property:** *min*<br /><br />var numeric = new ej.inputs.NumericTextBox({<br />value: 100,<br />min: 20<br />});<br />numeric.appendTo("#numeric"); |
| Negative pattern for formatting values | **property:** *negativePattern*<br /><br />$("#numeric").ejNumericTextBox({<br />value: -20,<br />negativePattern: "( n)"<br />}); | Not Applicable |
| Positive pattern for formatting values | **property:** *positivePattern*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 20,<br />positivePattern: "n kg"<br />}); | Not Applicable |
| Specifies value | **property:** *value*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100<br />}); | **Property:** *value*<br /><br />var numeric = new ej.inputs.NumericTextBox({<br />value: 100<br />});<br />numeric.appendTo("#numeric"); |
| Displays hint on editor | **property:** *watermarkText*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 80<br />watermarkText: "Enter value:"<br />}); | **Property:** *placeholder*<br /><br />var numeric = new ej.inputs.NumericTextBox({<br />value: 100<br />placeholder: "Enter value:"<br />});<br />numeric.appendTo("#numeric"); |
| Placeholder float type | Not Applicable | **Property:** *floatLabelType*<br /><br />var numeric = new ej.inputs.NumericTextBox({<br />value: 200<br />placeholder: "Enter value:"<br />floatLabelType: "Auto"<br />});<br />numeric.appendTo("#numeric"); |

## Number Formats

| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| Set Currency symbol | **property:** *currencySymbol*<br /><br />$("#currency").ejCurrencyTextBox({<br />value: 100,<br />currencySymbol: “EUR”<br />}); | **Property:** *currency*<br /><br />var currency = new ej.inputs.NumericTextBox({<br />value: 100,<br />format: “c2”,<br />currency: “EUR”<br />});<br />currency.appendTo("#currency"); |
| Number Format | Not Applicable | **Property:** *format*<br /><br />var numeric = new ej.inputs.NumericTextBox({<br />value: 200<br />format: "n2"<br />});<br />numeric.appendTo("#numeric"); |

## Validation

| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| Strict Mode | **property:** *enableStrictMode*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 80,<br />enableStrictMode: true<br />}); | **Property:** *strictMode*<br /><br />var numeric = new ej.inputs.NumericTextBox({<br />value: 80,<br />strictMode: true<br />});<br />numeric.appendTo("#numeric"); |
| Validation on typing | **property:** *validateOnType*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />validateOnType: true<br />}); | **Property:** *validateDecimalOnType*<br /><br />var numeric = new ej.inputs.NumericTextBox({<br />value: 100,<br />validateDecimalOnType: true<br />});<br />numeric.appendTo("#numeric"); |
| Validation Message | **property:** *validationMessage*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />validationRules: {required: true}<br />validationMessage: {required: “Required value”}<br />}); | **Validation in NumericTextBox can be achieved through form validation**<br/><br/>var options = {<br/>rules: {<br/> 'numericRange': {required: [true, "Number is required"]},<br/>}<br/>var formObject =  new ej.inputs.FormValidator('#form-element', options);<br/>var customPlace= function(element, error) {<br/> element.parentNode.parentNode.appendChild(error);<br/>};<br/>formObject.customPlacement = customPlace;<br/>var numeric = new ej.inputs.NumericTextBox({<br/>value: 15,<br/>});<br/>numeric.appendTo('#numeric1');<br/><br/>**HTML** <br/> &lt;form id="form-element" class="form-horizontal"><br/>&lt;input id="numeric1" type="text" name="numericRange" class="form-control" /> <br/>&lt;div id="error">&lt;/div><br/>&lt;/form> |
| Validation Rules | **property:** *validationRules*<br /><br />$("#numeric").ejNumericTextBox({<br />value: 100,<br />validationRules: {required: true}<br />}); |**Validation in NumericTextBox can be achieved through form validation**<br/><br/>var options = {<br/>rules: {<br/> 'numericRange': {required: [true]},<br/>}<br/>var formObject =  new ej.inputs.FormValidator('#form-element', options);<br/>var customPlace= function(element, error) {<br/> element.parentNode.parentNode.appendChild(error);<br/>};<br/>formObject.customPlacement = customPlace;<br/>var numeric = new ej.inputs.NumericTextBox({<br/>value: 15,<br/>});<br/>numeric.appendTo('#numeric1');<br/><br/>**HTML** <br/> &lt;form id="form-element" class="form-horizontal"><br/>&lt;input id="numeric1" type="text" name="numericRange" class="form-control" /> <br/>&lt;div id="error">&lt;/div><br/>&lt;/form>  |
