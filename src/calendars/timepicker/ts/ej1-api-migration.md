---
title: "Migration from Essential JS 1"
component: "TimePicker"
description: "Explains the common steps for migrating from Essential JS 1 application to Essential JS 2 components especially, time picker component."
---

# Migration from Essential JS 1

This article describes the API migration process of TimePicker component from Essential JS 1 to Essential JS 2.

## Time Selection

<!-- markdownlint-disable MD033 -->
<table>
<thead>
<tr>
<th>Behavior</th>
<th>API in Essential JS 1</th>
<th>API in Essential JS 2</th>
</tr>
<tr>
<td>
Setting the value
</td>
<td>
<b>Property:</b> <i>value</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    value: new Date("5/5/2014 12:00 PM")
});
```

</td>
<td>
<b>Property:</b> <i>value</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    value: new Date("05/11/2017 2:00 PM")
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
</thead>
</table>

## Time Format

<!-- markdownlint-disable MD033 -->
<table>
<thead>
<tr>
<th>Behavior</th>
<th>API in Essential JS 1</th>
<th>API in Essential JS 2</th>
</tr>
<tr>
<td>
Display time format
</td>
<td>
<b>Property:</b> <i>timeFormat</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    timeFormat: 'hh:mm:ss tt'
});
```

</td>
<td>
<b>Property:</b> <i>format</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    format:'hh:mm:ss'
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
</thead>
</table>

## Time Range

<!-- markdownlint-disable MD033 -->
<table>
<thead>
<tr>
<th>Behavior</th>
<th>API in Essential JS 1</th>
<th>API in Essential JS 2</th>
</tr>
<tr>
<td>
Minimum time
</td>
<td>
<b>Property:</b> <i>minTime</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    minTime: '10:00 AM'
});
```

</td>
<td>
<b>Property:</b> <i>min</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    min: new Date('5/5/2019 3:00 AM')
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Maximum time
</td>
<td>
<b>Property:</b> <i>maxTime</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    maxTime: '10:00 AM'
});
```

</td>
<td>
<b>Property:</b> <i>Max</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    max: new Date('5/5/2019 8:00 AM')
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Set current time
</td>
<td>
<b>Method:</b> <i>setCurrentTime()</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
});
console.log(timeObj.setCurrentTime());
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let timepickerObject: TimePicker = new TimePicker({
    value: new Date()
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
</thead>
</table>

## Disabled Time Ranges

<!-- markdownlint-disable MD033 -->
<table>
<thead>
<tr>
<th>Behavior</th>
<th>API in Essential JS 1</th>
<th>API in Essential JS 2</th>
</tr>
<tr>
<td>
Disable time ranges
</td>
<td>
<b>Property:</b> <i>disableTimeRanges</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    disableTimeRanges :[{ startTime: '3:00 AM', endTime: '6:00 AM' }, { startTime: '1:00 PM', endTime: '3:00 PM' }, { startTime: '8:00 PM', endTime: '10:00 PM' }]
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let timepickerObject: TimePicker = new TimePicker({
    itemRender: itemRanderHandler
});
timepickerObject.appendTo('#element');

function itemRenderHandler(args: ItemEventArgs): void {
    if (args.value.getHours() === 4) {
        args.isDisabled = true;
    }
}
```

</td>
</tr>
</thead>
</table>

## Customization

<!-- markdownlint-disable MD033 -->
<table>
<thead>
<tr>
<th>Behavior</th>
<th>API in Essential JS 1</th>
<th>API in Essential JS 2</th>
</tr>
<tr>
<td>
CSS Class
</td>
<td>
<b>Property:</b> <i>CssClass</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    cssClass :'gradient-lime'
});
```

</td>
<td>
<b>Property:</b> <i>CssClass</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    cssClass: 'e-custom-style'
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Popup list customization
</td>
<td>
<b>Not Applicable</b>
</td>
<td>
<b>Event:</b> <i>itemRender</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    itemRender: itemRanderHandler
});
timepickerObject.appendTo('#element');

function itemRenderHandler(args: ItemEventArgs): void { /* code block*/}
```

</td>
</tr>
<tr>
<td>
Show/Hide the popup button
</td>
<td>
<b>Property:</b> <i>showPopupButton</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    showPopupButton : false
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let timepickerObject: TimePicker = new TimePicker({
    focus: onFocus
});
timepickerObject.appendTo('#element');

function onFocus(args: FocusEventArgs): void {
    timepickerObject.show();
}
```

```css
.e-control-wrapper .e-input-group-icon.e-time-icon {
    display: none;
}
```

</td>
</tr>
<tr>
<td>
Enable/Disable the rounded corner
</td>
<td>
<b>Property:</b> <i>showRoundedCorner</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    showRoundedCorner : true
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let timepickerObject: TimePicker = new TimePicker({
    cssClass: 'e-custom-style'
});
timepickerObject.appendTo('#element');
```

```css
.e-control-wrapper.e-custom-style.e-time-wrapper.e-input-group {
    border-radius: 4px;
}
```

</td>
</tr>
<tr>
<td>
Enable/Disable the animation
</td>
<td>
<b>Property:</b> <i>enableAnimation</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    enableAnimation : true
});
```

</td>
<td>
<b>Not Applicable</b>
</td>
</tr>
<tr>
<td>
Interval
</td>
<td>
<b>Property:</b> <i>interval</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    interval : 120
});
```

</td>
<td>
<b>Property:</b> <i>step</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    step: 120
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
FocusIn event
</td>
<td>
<b>Event:</b> <i>focusIn</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    focusIn: function (args) {/* code block*/}
});
```

</td>
<td>
<b>Event:</b> <i>focus</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    focus: onFocus
});
timepickerObject.appendTo('#element');
function onFocus(args:any){ /* code block*/}
```

</td>
</tr>
<tr>
<td>
FocusOut event
</td>
<td>
<b>Event:</b> <i>focusOut</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    focusIn: function (args) {/* code block*/}
});
```

</td>
<td>
<b>Event:</b> <i>blur</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    blur: onBlur
});
timepickerObject.appendTo('#element');
function onBlur(args: BlurEventArgs) { /* code block*/}
```

</td>
</tr>
<tr>
<td>
FocusIn method
</td>
<td>
<b>Not Applicable</b>
</td>
<td>
<b>Method:</b> <i>focusIn()</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    value : new Date()
});
timepickerObject.appendTo('#element');
timepickerObject.focusIn();
```

</td>
</tr>
<tr>
<td>
FocusOut method
</td>
<td>
<b>Not Applicable</b>
</td>
<td>
<b>Event:</b> <i>focusOut</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    value : new Date()
});
timepickerObject.appendTo('#element');
timepickerObject.focusOut();
```

</td>
</tr>
<tr>
<td>
Prevent popup close
</td>
<td>
<b>Not Applicable</b>
</td>
<td>
<b>Event:</b> <i>close</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    close: function (args: PreventableEventArgs) {
        args.cancel = true;  
    }
});
timepickerObject.appendTo('#element');
timepickerObject.show();
```

</td>
</tr>
<tr>
<td>
Prevent popup open
</td>
<td>
<b>Not Applicable</b>
</td>
<td>
<b>Event:</b> <i>open</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    open: function (args: PreventableEventArgs) {
        args.cancel = true;  
    }
});
timepickerObject.appendTo('#element');
timepickerObject.show();
```

</td>
</tr>
</thead>
</table>

## Accessibility

<!-- markdownlint-disable MD033 -->
<table>
<thead>
<tr>
<th>Behavior</th>
<th>API in Essential JS 1</th>
<th>API in Essential JS 2</th>
</tr>
<tr>
<td>
Enable/Disable the RTL
</td>
<td>
<b>Property:</b> <i>enableRTL</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    enableRTL: true
});
```

</td>
<td>
<b>Property:</b> <i>enableRtl</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    enableRtl: true
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
</thead>
</table>

## Persistence

<!-- markdownlint-disable MD033 -->
<table>
<thead>
<tr>
<th>Behavior</th>
<th>API in Essential JS 1</th>
<th>API in Essential JS 2</th>
</tr>
<tr>
<td>
Enable/Disable the persistence
</td>
<td>
<b>Property:</b> <i>enablePersistence</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    enablePersistence: true
});
```

</td>
<td>
<b>Property:</b> <i>enablePersistence</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    enablePersistence: true
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
</thead>
</table>

## Validation

<!-- markdownlint-disable MD033 -->
<table>
<thead>
<tr>
<th>Behavior</th>
<th>API in Essential JS 1</th>
<th>API in Essential JS 2</th>
</tr>
<tr>
<td>
Validation rules
</td>
<td>
<b>Property:</b> <i>validationRules</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    validationRules : {required : true},
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let timepickerObject: TimePicker = new TimePicker({
    placeholder: 'Enter Time',
    value: new Date()
});
timepickerObject.appendTo('#element');
let options: FormValidatorModel = {
    rules: {
        'timevalue': { required: true }
    }
}
let formObject: FormValidator = new FormValidator('#form-element', options);
```

</td>
</tr>
<tr>
<td>
Validation message
</td>
<td>
<b>Property:</b> <i>validationMessages</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    validationRules : {required : true},
    validationMessages : {required: "Required time value" }
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let timepickerObject: TimePicker = new TimePicker({
    placeholder: 'Enter Time',
    value: new Date()
});
timepickerObject.appendTo('#element');
let options: FormValidatorModel = {
    rules: {
        'timevalue': { required: [true, 'Time value required']  }
    },
    customPlacement: function (inputElement, errorElement) {
        (<HTMLElement>inputElement).parentElement.parentElement.appendChild(errorElement);
    }
}
let formObject: FormValidator = new FormValidator('#form-element', options);
```

</td>
</tr>
</thead>
</table>

## Common

<!-- markdownlint-disable MD033 -->
<table>
<thead>
<tr>
<th>Behavior</th>
<th>API in Essential JS 1</th>
<th>API in Essential JS 2</th>
</tr>
<tr>
<td>
Width
</td>
<td>
<b>Property:</b> <i>width</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    width: 200
});
```

</td>
<td>
<b>Property:</b> <i>width</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    width: '200px'
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Readonly
</td>
<td>
<b>Property:</b> <i>readOnly</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    readOnly: true
});
```

</td>
<td>
<b>Property:</b> <i>Readonly</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    readonly: true,
    value: new Date()
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Show/Hide the clear button
</td>
<td>
<b>Not Applicable</b>
</td>
<td>
<b>Property:</b> <i>showClearButton</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    showClearButton: true,
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Height
</td>
<td>
<b>Property:</b> <i>Height</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    height: "50px"
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let timepickerObject: TimePicker = new TimePicker({
    cssClass: 'e-custom-style',
});
timepickerObject.appendTo('#element');
```

```css
.e-control-wrapper.e-custom-style.e-time-wrapper.e-input-group {
    height: 35px;
}
```

</td>
</tr>
<tr>
<td>
Html Attributes
</td>
<td>
<b>Property:</b> <i>HtmlAttributes</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    htmlAttributes : {required:"required"}
});
```

</td>
<td>
<b>Not Applicable</b>
</td>
</tr>
<tr>
<td>
Watermark text
</td>
<td>
<b>Property:</b> <i>watermarkText</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    watermarkText : "Enter Time"
});
```

</td>
<td>
<b>Property:</b> <i>placeholder</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    placeholder: 'Select a Time'
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Enable the TimePicker
</td>
<td>
<b>Property:</b> <i>enabled</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    enabled : true
});
```

</td>
<td>
<b>Property:</b> <i>enabled</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    enabled: true
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Disable the TimePicker
</td>
<td>
<b>Method:</b> <i>disable()</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
});
timeObj.disable();
```

</td>
<td>
<b>Property:</b> <i>enabled</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    enabled: false
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Enable/Disable the textBox editing
</td>
<td>
<b>Not Applicable</b>
</td>
<td>
<b>Property:</b> <i>allowEdit</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    allowEdit: false
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
zIndex
</td>
<td>
<b>Not Applicable</b>
</td>
<td>
<b>Property:</b> <i>zIndex</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    zIndex: 2000
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Specify the placeholder text behavior
</td>
<td>
<b>Not Applicable</b>
</td>
<td>
<b>Property:</b> <i>floatLabelType</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    floatLabelType: 'Always',
    placeholder: 'Select a time'
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
</thead>
</table>

## Globalization

<!-- markdownlint-disable MD033 -->
<table>
<thead>
<tr>
<th>Behavior</th>
<th>API in Essential JS 1</th>
<th>API in Essential JS 2</th>
</tr>
<tr>
<td>
Locale
</td>
<td>
<b>Property:</b> <i>locale</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    locale:"en-US"
});
```

</td>
<td>
<b>Property:</b> <i>locale</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    locale: 'en',
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
</thead>
</table>

## Strict Mode

<!-- markdownlint-disable MD033 -->
<table>
<thead>
<tr>
<th>Behavior</th>
<th>API in Essential JS 1</th>
<th>API in Essential JS 2</th>
</tr>
<tr>
<td>
Strict mode
</td>
<td>
<b>Property:</b> <i>enableStrictMode</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    enableStrictMode: true
});
```

</td>
<td>
<b>Property:</b> <i>strictMode</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    strictMode: true,
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
</thead>
</table>

## Open and Close

<!-- markdownlint-disable MD033 -->
<table>
<thead>
<tr>
<th>Behavior</th>
<th>API in Essential JS 1</th>
<th>API in Essential JS 2</th>
</tr>
<tr>
<td>
Close
</td>
<td>
<b>Event:</b> <i>close</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    close: function(args){ /* code block*/}
});
```

</td>
<td>
<b>Event:</b> <i>close</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    close: function (args: PreventableEventArgs) { /* code block*/}
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Open
</td>
<td>
<b>Event:</b> <i>open</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
    open: function(args){ /* code block*/}
});
```

</td>
<td>
<b>Event:</b> <i>open</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
    open: function (args: PreventableEventArgs) { /* code block*/}
});
timepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Hide
</td>
<td>
<b>Method:</b> <i>hide()</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
});
timeObj.show();
timeObj.hide();
```

</td>
<td>
<b>Method:</b> <i>hide()</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
});
timepickerObject.appendTo('#element');
timepickerObject.show();
timepickerObject.hide();
```

</td>
</tr>
<tr>
<td>
Show
</td>
<td>
<b>Method:</b> <i>show()</i>

```ts
var timeObj = new ej.TimePicker($("#timepicker"), {
});
timeObj.show();
timeObj.hide();
```

</td>
<td>
<b>Method:</b> <i>show()</i>

```ts
let timepickerObject: TimePicker = new TimePicker({
});
timepickerObject.appendTo('#element');
timepickerObject.show();
```

</td>
</tr>
</thead>
</table>