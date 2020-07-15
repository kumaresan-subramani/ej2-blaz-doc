---
title: "Migration from CSS textbox to JavaScript textbox control "
component: "Textbox"
description: "Explains the common steps for migrating from css textbox to javascript textbox along with its key features such as a floating label, adding icons (input group), and ripple effect."
---

# JavaScript textbox control

> From v16.3.21 version, the textbox is provided as JavaScript control to achieve the floating label textbox with minimal code. You can find the available textbox properties, methods, and events in the [API reference](https://ej2.syncfusion.com/documentation/api/textbox/).

The following table describes the migration from CSS textbox to JavaScript textbox control.

## Normal textbox

<!-- markdownlint-disable MD038 -->
| **Rendering mode** | **CSS textbox** | **JavaScript textbox control** |
| -----------------------| -----------------------------------| ------------------------------------------- |
| Default rendering |  `<div class='e-input-group'>`<br/>`<input class='e-input' type='text' placeholder='Enter Value'/>`<br/>`</div>` |  `<input id='default'/>`<br/><br/>   //To initiate the default textbox control <br/>`let inputObj: TextBox = new TextBox({`<br/>`placeholder: 'Enter Value',`<br/>`floatLabelType: 'Never'`<br/>`});`<br/>`inputObj.appendTo('#default');` |
| Textbox with clear button |  `<div class='e-input-group'>`<br/>`<input class='e-input' placeholder='Enter Value' required='true'>`<br/>`<span class='e-clear-icon'></span>`<br/>`</div>`<br/><br/>Note: You have to write action for clear button. |  `<input id='clear-input'/>`<br/><br/> `let inputObj: TextBox = new TextBox({`<br/>`placeholder: 'Enter Value',`<br/>`showClearButton: 'true',`<br/>`floatLabelType: 'Never'`<br/>`});`<br/>`inputObj.appendTo('#clear-input');` |
| Validation states |  `<div class='e-input-group e-error'>`<br/>`<input class='e-input' type='text' placeholder='Enter Value' />`<br/>`</div>`<br/><br/> Note: Textbox control consists of three types of validation rules such as success, warning, and error. |  `<input id='validation'/>`<br/><br/> `let inputObj: TextBox = new TextBox({`<br/>`placeholder: 'Enter Value',`<br/>`cssClass: 'e-error',`<br/>`floatLabelType: 'Never'`<br/>`});`<br/>`inputObj.appendTo`<br/>`('#validation');` |

## Floating label textbox

<!-- markdownlint-disable MD038 -->
| **Rendering mode** | **CSS textbox** | **JavaScript textbox control** |
| -----------------------| -----------------------------------| ------------------------------------------- |
| Default rendering |  `<div class='e-float-input'>`<br/>`<input type='text' required />`<br/>`<span class='e-float-line'></span>`<br/>`<label class='e-float-text'>Enter Value</label>`<br/>`</div>` |  `<input id='default'/>`<br/><br/> //To initiate the default textbox control with floating option <br/>`let inputObj: TextBox = new TextBox({`<br/>`placeholder: 'Enter Value',`<br/>`floatLabelType: 'Auto'`<br/>`});`<br/>`inputObj.appendTo('#default');` |
| Textbox with clear button |  `<div class='e-float-input e-input-group'>`<br/>`<input type='text' required  value= 'Clear Input' />`<br/>`<span class='e-float-line'></span>`<br/>`<label class='e-float-text'>Enter Value</label>`<br/>`<span class='e-clear-icon'></span>`<br/>`</div>`<br/><br/>Note: You have to write action for clear button. |  `<input id='clear-input'/>`<br/><br/>   //To initiate the textbox control with clear button and floating option<br/>`let inputObj: TextBox = new TextBox({`<br/>`placeholder: 'Enter Value',`<br/>`showClearButton: 'true',`<br/>`floatLabelType: 'Auto'`<br/>`});`<br/>`inputObj.appendTo('#clear-input');` |
| Validation states |  `<div class='e-float-input e-error'>`<br/>`<input type='text' required  />`<br/>`<span class='e-float-line'></span>`<br/>`<label class='e-float-text'>Enter Value</label>`<br/>`</div>`<br/><br/> Note: Textbox control consists of three types of validation rules such as success, warning, and error. |  `<input id='validation'/>`<br/><br/>   //To initiate the textbox control with validation and floating option<br/>`let inputObj: TextBox = new TextBox({`<br/>`placeholder: 'Enter Value',`<br/>`cssClass: 'e-error',`<br/>`floatLabelType: 'Auto'`<br/>`});`<br/>`inputObj.appendTo`<br/>`('#validation');` |