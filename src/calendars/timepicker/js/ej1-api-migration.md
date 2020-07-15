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

```javascript
$("#timepicker").ejTimePicker({value: new Date("5/5/2014 12:00 PM")});
```

</td>
<td>
<b>Property:</b> <i>value</i>

```javascript
var timepicker = new ej.calendars.TimePicker({
    value: new Date("05/11/2017 2:00 PM")
});
timepicker.appendTo('#element');
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

```javascript
$("#timepicker").ejTimePicker({timeFormat: 'hh:mm:ss tt'});
```

</td>
<td>
<b>Property:</b> <i>format</i>

```javascript
var timepicker = new ej.calendars.TimePicker({
    format:'hh:mm:ss'
});
timepicker.appendTo('#element');
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

```javascript
$("#timepicker").ejTimePicker({
    minTime: '10:00 AM'
});
```

</td>
<td>
<b>Property:</b> <i>min</i>

```javascript
var timepicker = new ej.calendars.TimePicker({
    min: new Date('5/5/2019 3:00 AM')
});
timepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Maximum time
</td>
<td>
<b>Property:</b> <i>maxTime</i>

```javascript
$("#timepicker").ejTimePicker({
    maxTime: '10:00 AM'
});
```

</td>
<td>
<b>Property:</b> <i>Max</i>

```javascript
var timepicker = new ej.calendars.TimePicker({
    max: new Date('5/5/2019 8:00 AM')
});
timepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Set current time
</td>
<td>
<b>Method:</b> <i>setCurrentTime()</i>

```javascript
$("#timepicker").ejTimePicker();
var timeObj = $("#timepicker").data("ejTimePicker");
console.log(timeObj.setCurrentTime());
```

</td>
<td>
<b>Can be achieved by</b>

```javascript
var timepicker = new ej.calendars.TimePicker({
    value: new Date()
});
timepicker.appendTo('#element');
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

```javascript
$("#timepicker").ejTimePicker({
    disableTimeRanges :[{ startTime: '3:00 AM', endTime: '6:00 AM' }, { startTime: '1:00 PM', endTime: '3:00 PM' }, { startTime: '8:00 PM', endTime: '10:00 PM' }]
});
```

</td>
<td>
<b>Can be achieved by</b>

```javascript
var timepicker = new ej.calendars.TimePicker({
    itemRender: itemRanderHandler
});
timepicker.appendTo('#element');

function itemRenderHandler(args){
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

```javascript
$("#timepicker").ejTimePicker({
    cssClass :'gradient-lime'
});
```

</td>
<td>
<b>Property:</b> <i>CssClass</i>

```javascript
var timepicker = new ej.calendars.TimePicker({
    cssClass: 'e-custom-style'
});
timepicker.appendTo('#element');
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

```javascript
var timepicker = new ej.calendars.TimePicker({
    itemRender: itemRanderHandler
});
timepicker.appendTo('#element');

function itemRenderHandler(args) { /* code block*/}
```

</td>
</tr>
<tr>
<td>
Show/Hide the popup button
</td>
<td>
<b>Property:</b> <i>showPopupButton</i>

```javascript
$("#timepicker").ejTimePicker({
    showPopupButton : false
});
```

</td>
<td>
<b>Can be achieved by</b>

```javascript
var timepicker = new ej.calendars.TimePicker({
    focus: onFocus
});
timepicker.appendTo('#element');

function onFocus(args){
    timepicker.show();
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

```javascript
$("#timepicker").ejTimePicker({
    showRoundedCorner : true
});
```

</td>
<td>
<b>Can be achieved by</b>

```javascript
var timepicker = new ej.calendars.TimePicker({
    cssClass: 'e-custom-style'
});
timepicker.appendTo('#element');
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

```javascript
$("#timepicker").ejTimePicker({
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

```javascript
$("#timepicker").ejTimePicker({
    interval : 120
});
```

</td>
<td>
<b>Property:</b> <i>step</i>

```javascript
var timepicker = new ej.calendars.TimePicker({
    step: 120
});
timepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
FocusIn event
</td>
<td>
<b>Event:</b> <i>focusIn</i>

```javascript
$("#timepicker").ejTimePicker({
    focusIn: function (args) {/* code block*/}
});
```

</td>
<td>
<b>Event:</b> <i>focus</i>

```javascript
var timepicker = new ej.calendars.TimePicker({
    focus: onFocus
});
timepicker.appendTo('#element');
function onFocus(args){ /* code block*/}
```

</td>
</tr>
<tr>
<td>
FocusOut event
</td>
<td>
<b>Event:</b> <i>focusOut</i>

```javascript
$("#timepicker").ejTimePicker({
    focusIn: function (args) {/* code block*/}
});
```

</td>
<td>
<b>Event:</b> <i>blur</i>

```javascript
var timepicker = new ej.calendars.TimePicker({
    blur: onBlur
});
timepicker.appendTo('#element');
function onBlur(args) { /* code block*/}
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

```javascript
var timepicker = new ej.calendars.TimePicker({
    value : new Date()
});
timepicker.appendTo('#element');
timepicker.focusIn();
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

```javascript
var timepicker = new ej.calendars.TimePicker({
    value : new Date()
});
timepicker.appendTo('#element');
timepicker.focusOut();
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

```javascript
var timepicker = new ej.calendars.TimePicker({
    close: function (args: PreventableEventArgs) {
        args.cancel = true;  
    }
});
timepicker.appendTo('#element');
timepicker.show();
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

```javascript
var timepicker = new ej.calendars.TimePicker({
    open: function (args) {
        args.cancel = true;  
    }
});
timepicker.appendTo('#element');
timepicker.show();
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

```javascript
$("#timepicker").ejTimePicker({
    enableRTL: true
});
```

</td>
<td>
<b>Property:</b> <i>enableRtl</i>

```javascript
var timepicker = new ej.calendars.TimePicker({
    enableRtl: true
});
timepicker.appendTo('#element');
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

```javascript
$("#timepicker").ejTimePicker({
    enablePersistence: true
});
```

</td>
<td>
<b>Property:</b> <i>enablePersistence</i>

```javascript
var timepicker = new ej.calendars.TimePicker({
    enablePersistence: true
});
timepicker.appendTo('#element');
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

```javascript
$("#timepicker").ejTimePicker({
    validationRules : {required : true},
});
```

</td>
<td>
<b>Can be achieved by</b>

```javascript
var timepicker = new ej.calendars.TimePicker({ placeholder: 'Enter time'});
timepicker.appendTo('#element');

var options = {  rules: {   'timevalue': { required: true }} }
var formObject: FormValidator = new FormValidator('#form-element', options);
```

</td>
</tr>
<tr>
<td>
Validation messages
</td>
<td>
<b>Property:</b> <i>validationMessages</i>

```javascript
$("#timepicker").ejTimePicker({
    validationRules : {required : true},
    validationMessages : {required: "Required time value" }
});
```

</td>
<td>
<b>Can be achieved by</b>

```javascript
var timepicker = new ej.calendars.TimePicker({
    placeholder: 'Enter date'
});
timepicker.appendTo('#element');

var options = {
    rules: {
        'timevalue': {    required: [true, 'Time value required'] }
    },
    customPlacement: function (inputElement, errorElement) {
        inputElement.parentElement.parentElement.appendChild(errorElement);
    }
};
    var formObject = new ej.inputs.FormValidator('#form-element', options);
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

```javascript
$("#timepicker").ejTimePicker({
    width: 200
});
```

</td>
<td>
<b>Property:</b> <i>width</i>

```javascript
var timepicker = new ej.calendars.TimePicker({
    width: '200px'
});
timepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Readonly
</td>
<td>
<b>Property:</b> <i>readOnly</i>

```javascript
$("#timepicker").ejTimePicker({
    readOnly: true
});
```

</td>
<td>
<b>Property:</b> <i>Readonly</i>

```javascript
var timepicker = new ej.calendars.TimePicker({
    readonly: true,
    value: new Date()
});
timepicker.appendTo('#element');
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

```javascript
var timepicker = new ej.calendars.TimePicker({
    showClearButton: true,
});
timepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Height
</td>
<td>
<b>Property:</b> <i>Height</i>

```javascript
$("#timepicker").ejTimePicker({
    height: "50px"
});
```

</td>
<td>
<b>Can be achieved by</b>

```javascript
var timepicker = new ej.calendars.TimePicker({
    cssClass: 'e-custom-style',
});
timepicker.appendTo('#element');
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

```javascript
$("#timepicker").ejTimePicker({
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

```javascript
$("#timepicker").ejTimePicker({
    watermarkText : "Enter Time"
});
```

</td>
<td>
<b>Property:</b> <i>placeholder</i>

```javascript
var timepicker = new ej.calendars.TimePicker({
    placeholder: 'Select a Time'
});
timepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Enable the TimePicker
</td>
<td>
<b>Property:</b> <i>enabled</i>

```javascript
$("#timepicker").ejTimePicker({
    enabled : true
});
```

</td>
<td>
<b>Property:</b> <i>enabled</i>

```javascript
var timepicker = new ej.calendars.TimePicker({
    enabled: true
});
timepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Disable the TimePicker
</td>
<td>
<b>Method:</b> <i>disable()</i>

```javascript
$("#timepicker").ejTimePicker();
var timeObj = $("#timepicker").data("ejTimePicker");
timeObj.disable();
```

</td>
<td>
<b>Property:</b> <i>enabled</i>

```javascript
var timepicker = new ej.calendars.TimePicker({
    enabled: false
});
timepicker.appendTo('#element');
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

```javascript
var timepicker = new ej.calendars.TimePicker({
    allowEdit: false
});
timepicker.appendTo('#element');
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

```javascript
var timepicker = new ej.calendars.TimePicker({
    zIndex: 2000
});
timepicker.appendTo('#element');
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

```javascript
var timepicker = new ej.calendars.TimePicker({
    floatLabelType: 'Always',
    placeholder: 'Select a time'
});
timepicker.appendTo('#element');
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

```javascript
$("#timepicker").ejTimePicker({
    locale:"en-US"
});
```

</td>
<td>
<b>Property:</b> <i>locale</i>

```javascript
var timepicker = new ej.calendars.TimePicker({
    locale: 'en',
});
timepicker.appendTo('#element');
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

```javascript
$("#timepicker").ejTimePicker({
    enableStrictMode: true
});
```

</td>
<td>
<b>Property:</b> <i>strictMode</i>

```javascript
var timepicker = new ej.calendars.TimePicker({
    strictMode: true,
});
timepicker.appendTo('#element');
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

```javascript
$("#timepicker").ejTimePicker({
    close: function(args){ /* code block*/}
});
```

</td>
<td>
<b>Event:</b> <i>close</i>

```javascript
var timepicker = new ej.calendars.TimePicker({
    close: function (args) { /* code block*/}
});
timepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Open
</td>
<td>
<b>Event:</b> <i>open</i>

```javascript
$("#timepicker").ejTimePicker({
    open: function(args){ /* code block*/}
});
```

</td>
<td>
<b>Event:</b> <i>open</i>

```javascript
var timepicker = new ej.calendars.TimePicker({
    open: function (args) { /* code block*/}
});
timepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Hide
</td>
<td>
<b>Method:</b> <i>hide()</i>

```javascript
$("#timepicker").ejTimePicker();
var timeObj = $("#timepicker").data("ejTimePicker");
timeObj.show();
timeObj.hide();
```

</td>
<td>
<b>Method:</b> <i>hide()</i>

```javascript
var timepicker = new ej.calendars.TimePicker({
});
timepicker.appendTo('#element');
timepicker.show();
timepicker.hide();
```

</td>
</tr>
<tr>
<td>
Show
</td>
<td>
<b>Method:</b> <i>show()</i>

```javascript
$("#timepicker").ejTimePicker();
var timeObj = $("#timepicker").data("ejTimePicker");
timeObj.show();
timeObj.hide();
```

</td>
<td>
<b>Method:</b> <i>show()</i>

```javascript
var timepicker = new ej.calendars.TimePicker({
});
timepicker.appendTo('#element');
timepicker.show();
```

</td>
</tr>
</thead>
</table>