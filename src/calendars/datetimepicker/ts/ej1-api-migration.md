# Migration from Essential JS 1

This article describes the API migration process of DateTimePicker component from Essential JS 1 to Essential JS 2.

## DateTime Selection

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior</b>
</td>
<td>
<b>API in Essential JS 1</b>
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Setting the value
</td>
<td>
<b>property:</b> <i>value</i>

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    value: new Date("5/5/2014 12:00 PM")
});
```

</td>
<td>
<b>property:</b> <i>value</i>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    value: new Date("05/11/2017 12:00 PM")
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
</table>

## DateTime Format

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior</b>
</td>
<td>
<b>API in Essential JS 1</b>
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Display the datetime format
</td>
<td>
<b>property:</b> <i>dateTimeFormat</i>

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    value: new Date("5/5/2014 12:00 PM"),
    dateTimeFormat: "dd/MM/yyyy hh:mm tt"
});
```

</td>
<td>
<b>property:</b> <i>format</i>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    value: new Date("05/11/2017 12:00 PM"),
    format: 'dd/MM/yyyy hh:mm a'
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Day header format
</td>
<td>
<b>property:</b> <i>dayHeaderFormat</i>

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    dayHeaderFormat: "short"
});
```

</td>
<td>
<b>Not Applicable</b>
</td>
</tr>
</table>

## Calendar Views

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior</b>
</td>
<td>
<b>API in Essential JS 1</b>
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Start view
</td>
<td>
<b>property:</b> <i>startLevel</i>

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    startLevel: ej.DateTimePicker.Level.Year
});
```

</td>
<td>
<b>property:</b> <i>start</i>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    start:'Decade'
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Depth view
</td>
<td>
<b>property:</b> <i>depthLevel</i>

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    depthLevel: ej.DateTimePicker.Level.Year
});
```

</td>
<td>
<b>property:</b> <i>depth</i>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    depth:'Year'
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
</table>

## Date Range

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior</b>
</td>
<td>
<b>API in Essential JS 1</b>
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Minimum datetime
</td>
<td>
<b>property:</b> <i>minDateTime</i>

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    minDateTime: new Date("5/1/2013 10:00 AM")
});
```

</td>
<td>
<b>property:</b> <i>min</i>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    min: new Date("5/1/2013 10:00 AM"
)});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Maximum datetime
</td>
<td>
<b>property:</b> <i>maxDateTime</i>

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    maxDateTime: new Date("5/1/2013 10:00 AM")
});
```

</td>
<td>
<b>property:</b> <i>max</i>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    max : new Date("5/30/2015 10:00 PM")
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
</table>

## Disabled Dates

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior</b>
</td>
<td>
<b>API in Essential JS 1</b>
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Disabled dates
</td>
<td>
<b>property:</b> <i>disabledDateTimeRanges</i>

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    disableDateTimeRanges: [{ startDateTime: new Date("11/30/2018 11:59 PM"),       endDateTime:new Date("12/1/2018 11:59 PM")    }]
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    renderDayCell: disableDate
});
datetimepickerObject.appendTo('#element');
function disableDate(args: RenderDayCellEventArgs): void {
    if (args.date.getDay() === 0 || args.date.getDay() === 6) {
        args.isDisabled = true;
    }
}
```

</td>
</tr>
</table>

## Customization

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior</b>
</td>
<td>
<b>API in Essential JS 1</b>
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
CSS Class
</td>
<td>
<b>property:</b> cssClass

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    cssClass: "gradient-lime"
});
```

</td>
<td>
<b>property:</b> cssClass

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    cssClass: 'e-custom-style'
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Show/Hide the today button
</td>
<td>
<b>Can be achieved by</b>

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    cssClass: "e-custom-class"
});
```

```css
.e-datetime-popup.e-popup.e-custom-class .e-button-container{
    display: none !important;
}
```

</td>
<td>
<b>property:</b> showTodayButton

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    showTodayButton: false
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Show/Hide the other month dates
</td>
<td>
<b>property:</b> showOtherMonths

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    showOtherMonths: false
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker();
datetimepickerObject.appendTo('#element');
```

```css
.e-DateTimePicker .e-calendar .e-content tr.e-month-hide,
.e-DateTimePicker .e-calendar .e-content td.e-other-month > .e-day {
    visibility: none;
}
.e-DateTimePicker .e-calendar .e-content td.e-month-hide,
.e-DateTimePicker .e-calendar .e-content td.e-other-month {
    pointer-events: none;
    touch-action: none;
}
```

</td>
</tr>
<tr>
<td>
Show/Hide the popup button
</td>
<td>
<b>property:</b> showPopupButton

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    showPopupButton: false
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts

let datetimepickerObject: DateTimePicker = new DateTimePicker({
    focus: onFocus
});
datetimepickerObject.appendTo('#element');
function onFocus(args: FocusEventArgs) {
    datetimepickerObject.show();
}
```

```css
.e-control-wrapper .e-input-group-icon.e-date-icon {
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
<b>property:</b> showRoundedCorner

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    showRoundedCorner: true
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    cssClass: 'e-custom-style'
});
datetimepickerObject.appendTo('#element');
```

```css
.e-control-wrapper.e-custom-style.e-date-wrapper.e-input-group {
    border-radius: 4px;
}
```

</td>
</tr>
<tr>
<td>
Skip a month
</td>
<td>
<b>property:</b> stepMonths

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    stepMonths: 2
});
```

</td>
<td>
<b>Method:</b> navigateTo()

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    value: new Date("09/04/2019"),
    open:onOpen
});
datetimepickerObject.appendTo('#element');
function onOpen(args:any){
    datepicker.navigateTo('Year', new Date("03/18/2018"));
}
```

</td>
</tr>
<tr>
<td>
Show/Hide the tooltip
</td>
<td>
<b>property:</b> showTooltip

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    showTooltip: false
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
<b>property:</b> interval

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    interval: 60
});
```

</td>
<td>
<b>property:</b> step

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    step: 60
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Button text
</td>
<td>
<b>property:</b> buttonText

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    buttonText : { today: "Today", timeNow: "Time Now",  done: "Done",  timeTitle: "Time" }
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
L10n.load({ 'en': {  'DateTimePicker': { today:'Now' } }});
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    locale: 'en'
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Enable/Disable the animation
</td>
<td>
<b>property:</b> enableAnimation

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    enableAnimation : false
});
```

</td>
<td>
<b>Not Applicable</b>
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
<b>Method:</b> focusIn()

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    placeholder: 'Enter date'
});
datetimepickerObject.appendTo('#element');
datetimepickerObject.focusIn();
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
<b>Method:</b> focusOut()

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    placeholder: 'Enter date'
});
datetimepickerObject.appendTo('#element');
datetimepickerObject.focusOut();
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
<b>Can be achieved by</b>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    close: function (args: PreventableEventArgs) {
        args.preventDefault();
    }
});
datetimepickerObject.appendTo('#element');
datetimepickerObject.show();
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
<b>Can be achieved by</b>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    open: function (args: PreventableEventArgs) {
        args.preventDefault();
    }
});
datetimepickerObject.appendTo('#element');
datetimepickerObject.show();
```

</td>
</tr>
</table>

## Accessibility

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior</b>
</td>
<td>
<b>API in Essential JS 1</b>
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Enable/Disable the RTL
</td>
<td>
<b>property:</b> enableRTL

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    enableRTL : true
});
```

</td>
<td>
<b>property:</b> enableRtl

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    enableRtl : true
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
</table>

## Persistence

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior</b>
</td>
<td>
<b>API in Essential JS 1</b>
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Enable/Disable the persistence
</td>
<td>
<b>property:</b> enablePersistence

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    enablePersistence : true
});
```

</td>
<td>
<b>property:</b> enablePersistence

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    enablePersistence : true
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
</table>

## Validation

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior</b>
</td>
<td>
<b>API in Essential JS 1</b>
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Validation rules
</td>
<td>
<b>property:</b> validationRules

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    validationRules : {required : true}
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    placeholder: 'Enter datetime',
    value: new Date()
});
datepickerObject.appendTo('#element');
let options: FormValidatorModel = {
    rules: {
        'datevalue': { required: true }
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
<b>property:</b> validationMessage

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    validationRules : {required : true},
    validationMessage : {required: "Required DateTime value" }
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    placeholder: 'Enter dateTime',
    value: new Date()
});
datetimepickerObject.appendTo('#element');
let options: FormValidatorModel = {
    rules: {
        'datevalue': { required: [true, 'DateTime value required']  }
    },
    customPlacement: function (inputElement, errorElement) {
        (<HTMLElement>inputElement).parentElement.parentElement.appendChild(errorElement);
    }
}
let formObject: FormValidator = new FormValidator('#form-element', options);
```

</td>
</tr>
</table>

## Common

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior</b>
</td>
<td>
<b>API in Essential JS 1</b>
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Width
</td>
<td>
<b>property:</b> width

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    width: 200
});
```

</td>
<td>
<b>property:</b> width

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    width: '200px'
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Readonly
</td>
<td>
<b>property:</b> readOnly

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    readOnly : true
});
```

</td>
<td>
<b>property:</b> readonly

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    readonly:true,
    value:new Date()
});
datetimepickerObject.appendTo('#element');
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
<b>property:</b> showClearButton

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    showClearButton: true
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Height
</td>
<td>
<b>property:</b> height

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    height: 35
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    cssClass: 'e-custom-style'
});
datetimepickerObject.appendTo('#element');
```

```css
.e-control-wrapper.e-custom-style.e-date-wrapper.e-input-group{
    height: 35px;
}
```

</td>
</tr>
<tr>
<td>
Html attributes
</td>
<td>
<b>property:</b> htmlAttributes

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
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
Show/Hide the week number
</td>
<td>
<b>property:</b> weekNumber

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
   weekNumber : true
});
```

</td>
<td>
<b>property:</b> weekNumber

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    weekNumber:true
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Watermark text
</td>
<td>
<b>property:</b> watermarkText

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
   watermarkText: "Enter date"
});
```

</td>
<td>
<b>property:</b> placeholder

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    placeholder: 'Enter date'
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Disable/Enable
</td>
<td>
<b>property:</b> enabled

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
   enabled: false
});
```

</td>
<td>
<b>property:</b> enabled

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    enabled:false
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Enable/Disable the textbox editing
</td>
<td>
<b>property:</b> allowEdit

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
   allowEdit : true
});
```

</td>
<td>
<b>property:</b> allowEdit

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    allowEdit : true
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
zIndex
</td>
<td>
<b>Can be achieved by</b>

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
   cssClass: "e-custom-class"
});
```

```css
.e-datetime-popup.e-popup.e-custom-class {
    z-index: 100 !important;
}
```

</td>
<td>
<b>property:</b> zIndex

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    zIndex: 100
});
datetimepickerObject.appendTo('#element');
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
<b>property:</b> floatLabelType

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    placeholder: 'Enter date',
    floatLabelType: 'Auto'
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Event callback for each cell creation
</td>
<td>
<b>Not Applicable</b>
</td>
<td>
<b>Event:</b> <i>renderDayCell</i>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    renderDayCell: onRenderCell
});
datetimepickerObject.appendTo('#element');
function onRenderCell(args: RenderDayCellEventArgs): void {/* code block*/}
```

</td>
</tr>
<tr>
<td>
FocusIn event
</td>
<td>
<b>Event:</b> focusIn

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
   focusIn: function (args) {/* code block*/}
});
```

</td>
<td>
<b>Event:</b> <i>focus</i>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    focus: onFocus
});
datetimepickerObject.appendTo('#element');
function onFocus(args: FocusEventArgs): void {/* code block*/}
```

</td>
</tr>
<tr>
<td>
FocusOut event
</td>
<td>
<b>Event:</b> focusOut

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
   focusOut: function (args) {/* code block*/}
});
```

</td>
<td>
<b>Event:</b> <i>blur</i>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    blur: onBlur
});
datetimepickerObject.appendTo('#element');
function onBlur(args: BlurEventArgs): void {/* code block*/}
```

</td>
</tr>
<tr>
<td>
Change event
</td>
<td>
<b>Event:</b> change

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
   change: function (args) {/* code block*/}
});
```

</td>
<td>
<b>Event:</b> <i>change</i>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    change: onChange
});
datetimepickerObject.appendTo('#element');
function onChange(args: ChangedEventArgs): void {/* code block*/}
```

</td>
</tr>
<tr>
<td>
Create event
</td>
<td>
<b>Event:</b> create

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
   create: function (args) {/* code block*/}
});
```

</td>
<td>
<b>Event:</b> <i>created</i>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    created: onCreate
});
datetimepickerObject.appendTo('#element');
function onCreate(args): void {/* code block*/}
```

</td>
</tr>
<tr>
<td>
Destroy event
</td>
<td>
<b>Event:</b> destroy

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
   destroy: function (args) {/* code block*/}
});
```

</td>
<td>
<b>Event:</b> <i>destroyed</i>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    destroyed: onDestroy
});
datetimepickerObject.appendTo('#element');
function onDestroy(args): void {/* code block*/}
```

</td>
</tr>
</table>

## Globalization

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior</b>
</td>
<td>
<b>API in Essential JS 1</b>
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Locale
</td>
<td>
<b>property:</b> locale

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
   locale: "en-US"
});
```

</td>
<td>
<b>property:</b> <i>locale</i>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    locale: 'en'
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
First day of week
</td>
<td>
<b>property:</b> startDay

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
   startDay: 2
});
```

</td>
<td>
<b>property:</b> firstDayOfWeek

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    firstDayOfWeek: 2
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
</table>

## Strict Mode

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior</b>
</td>
<td>
<b>API in Essential JS 1</b>
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Strict mode
</td>
<td>
<b>property:</b> <i>enableStrictMode</i>

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    enableStrictMode : true
});
```

</td>
<td>
<b>property:</b> <i>strictMode</i>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    strictMode: true,
    value: new Date('5/28/2017'),
    min: new Date('5/5/2017'),
    max: new Date('5/25/2017')
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
</table>

## Open and Close

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior</b>
</td>
<td>
<b>API in Essential JS 1</b>
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Close
</td>
<td>
<b>Event:</b> <i>close</i>

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    close: function (args) {/* code block*/}}
});
```

</td>
<td>
<b>Event:</b> <i>close</i>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    close: function (args: PreventableEventArgs) {/* code block*/}
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Hide
</td>
<td>
<b>Method:</b> hide()

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
});
datetimeObj.hide();
```

</td>
<td>
<b>Method:</b> </i>hide()</i>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    value: new Date("05/11/2017")
});
datetimepickerObject.appendTo('#element');
datetimepickerObject.hide();
```

</td>
</tr>
<tr>
<td>
Open
</td>
<td>
<b>Event:</b> open

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    open: function (args) {/* code block*/}}
});
```

</td>
<td>
<b>Event:</b> <i>open</i>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    open: function (args: PreventableEventArgs) {/* code block*/}
});
datetimepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Show
</td>
<td>
<b>Method:</b> show()

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
});
datetimeObj.show();
```

</td>
<td>
<b>Method:</b> <i>show()</i>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    value: new Date("05/11/2017")
});
datetimepickerObject.appendTo('#element');
datetimepickerObject.show();
```

</td>
</tr>
</table>

## View Navigation

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior</b>
</td>
<td>
<b>API in Essential JS 1</b>
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Navigate to specific month
</td>
<td>
<b>Not Applicable</b>
</td>
<td>
<b>Method:</b> <i>navigateTo()</i>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    value: new Date("09/04/2019"),
    open:onOpen
});
datetimepickerObject.appendTo('#element');
function onOpen(args:any){
    datepicker.navigateTo('Year', new Date("03/18/2018"));
}
```

</td>
</tr>
<tr>
<td>
Navigation callback
</td>
<td>
<b>Not Applicable</b>
</td>
<td>
<b>Event:</b> <i>navigated</i>

```ts
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    navigated: onNavigate
});
datetimepickerObject.appendTo('#element');
function onNavigate(args: NavigatedEventArgs) {/* code block*/}
```

</td>
</tr>
<tr>
<td>
Drill down
</td>
<td>
<b>property:</b> <i>timeDrillDown</i>

```ts
var datetimeObj = new ej.DateTimePicker($("#datetimepicker"), {
    timeDrillDown: { enabled: true, showMeridian: true, autoClose: true, interval: 10 }
});
```

</td>
<td>
<b>Not Applicable</b>
</td>
</tr>
</table>
