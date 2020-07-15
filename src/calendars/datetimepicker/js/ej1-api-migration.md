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
<b>property:</b> value

```javascript
$("#datetimepicker").ejDateTimePicker({value: new Date("5/5/2014 12:00 PM")});
```

</td>
<td>
<b>property:</b> value

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ value: new Date("05/11/2017 12:00 PM")});datetimepicker.appendTo('#element');
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
<b>property:</b> dateTimeFormat

```javascript
$("#datetimepicker").ejDateTimePicker({
    value: new Date("05/11/2017 12:00 PM"),
    dateTimeFormat: "dd/MM/yyyy hh:mm tt"
});
```

</td>
<td>
<b>property:</b> format

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({
    value: new Date("05/11/2017 12:00 PM"),
    format: 'dd/MM/yyyy hh:mm a'
});
datetimepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Day header format
</td>
<td>
<b>property:</b> dayHeaderFormat

```javascript
$("#datetimepicker").ejDateTimePicker({ dayHeaderFormat: "short"});
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
<b>property:</b> startLevel

```javascript
$("#datetimepicker").ejDateTimePicker({ startLevel: ej.DateTimePicker.Level.Year});
```

</td>
<td>
<b>property:</b> start

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ start:'Decade'});datetimepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Depth view
</td>
<td>
<b>property:</b> depthLevel

```javascript
$("#datetimepicker").ejDateTimePicker({ depthLevel: ej.DateTimePicker.Level.Year});
```

</td>
<td>
<b>property:</b> depth

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ depth:'Year'});datetimepicker.appendTo('#element');
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
<b>property:</b> minDateTime

```javascript
$("#datetimepicker").ejDateTimePicker({ minDateTime: new Date("5/1/2013 10:00 AM")});
```

</td>
<td>
<b>property:</b> min

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ min: new Date("5/1/2013 10:00 AM")});datetimepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Maximum datetime
</td>
<td>
<b>property:</b> maxDateTime

```javascript
$("#datetimepicker").ejDateTimePicker({ maxDateTime : new Date("5/30/2015 10:00 PM")});
```

</td>
<td>
<b>property:</b> max

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ max : new Date("5/30/2015 10:00 PM")});datetimepicker.appendTo('#element');
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
<b>property:</b> disabledDateTimeRanges

```javascript
$("#datetimepicker").ejDateTimePicker({
    disableDateTimeRanges: [{   startDateTime: new Date("11/30/2018 11:59 PM"),   endDateTime:new Date("12/1/2018 11:59 PM")}]
});
```

</td>
<td>
<b>Can be achieved by:</b>

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({
    renderDayCell: disableDate
});
datetimepicker.appendTo('#element');

function disableDate(args) {
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

```javascript
$("#datetimepicker").ejDateTimePicker({ cssClass: "gradient-lime"});
```

</td>
<td>
<b>property:</b> cssClass

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ cssClass: 'e-custom-style'});datetimepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Show?Hide the button
</td>
<td>
<b>Can be achieved by:</b>

```javascript
$("#datetimepicker").ejDateTimePicker({ cssClass: "e-custom-class"})
```

```css
.e-datetime-popup.e-popup.e-custom-class .e-button-container { display: none !important;}
```

</td>
<td>
<b>property:</b> showTodayButton

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ showTodayButton: false});datetimepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Show/Hide the other month dates
</td>
<td>
<b>property:</b> showOtherMonths

```javascript
$("#datetimepicker").ejDateTimePicker({ showOtherMonths: false});
```

</td>
<td>
<b> Ca be achieved by:</b>

```javascript
var datetimepicker = new ej.calendars.DateTimePicker();
datetimepicker.appendTo('#element');
```

```css
.e-DateTimePicker .e-calendar .e-content tr.e-month-hide,.e-DateTimePicker .e-calendar .e-content td.e-other-month > .e-day {
    visibility: none;
}
.e-DateTimePicker .e-calendar .e-content td.e-month-hide,.e-DateTimePicker .e-calendar .e-content td.e-other-month {
    pointer-events: none;
    touch-action: none;}
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

```javascript
$("#datetimepicker").ejDateTimePicker({ showPopupButton: false});
```

</td>
<td>
<b>Can be achieved by:</b>

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ focus: onFocus});
datetimepicker.appendTo('#element');
function onFocus(args) {
    datetimepicker.show();
}
```

```css
.e-control-wrapper .e-input-group-icon.e-date-icon { display: none; }
```

</td>
</tr>
<tr>
<td>
Enable/Disable the rounded corner
</td>
<td>
<b>property:</b> showRoundedCorner

```javascript
$("#datetimepicker").ejDateTimePicker({ showRoundedCorner: true});
```

</td>
<td>
<b>Can be achieved by:</b>

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ cssClass: 'e-custom-style'});datetimepicker.appendTo('#element');
```

```css
.e-control-wrapper.e-custom-style.e-date-wrapper.e-input-group { border-radius: 4px;}
```

</td>
</tr>
<tr>
<td>
Skip a month
</td>
<td>
<b>property:</b> stepMonths

```javascript
$("#datetimepicker").ejDateTimePicker({stepMonths: 2});
```

</td>
<td>
<b>Can be achieved by:</b>

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({
    value: new Date("09/04/2018"),
    open:onOpen
});
datetimepicker.appendTo('#element');

function onOpen(args) {
    datetimepicker.navigateTo('Year', new Date("03/18/2018"));
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

```javascript
$("#datetimepicker").ejDateTimePicker({ showTooltip: false});
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

```javascript
$("#datetimepicker").ejDateTimePicker({ interval: 60});
```

</td>
<td>
<b>property:</b> step

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ step: 60});
datetimepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Button text
</td>
<td>
<b>property:</b> buttonText

```javascript
$("#datetimepicker").ejDateTimePicker({ buttonText : {  today: "Today",  timeNow: "Time Now",  done: "Done", timeTitle: "Time" }});
```

</td>
<td>
<b>Can be achieved by:</b>

```javascript
L10n.load({  'en': { 'DateTimePicker': {today:'Now' }  }});

var datetimepicker = new ej.calendars.DateTimePicker({ locale: 'en'});
datetimepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Enable/Disable the animation
</td>
<td>
<b>property:</b> enableAnimation

```javascript
$("#datetimepicker").ejDateTimePicker({ enableAnimation : false});
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

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ placeholder: 'Enter date'});datetimepicker.appendTo('#element');
datetimepicker.focusIn();
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

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ placeholder: 'Enter date'});datetimepicker.appendTo('#element');
datetimepicker.focusOut();
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
<b>Event:</b> close

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({
    close: function (args) {
        args.preventDefault();
    }
});
datetimepicker.appendTo('#element');
datetimepicker.show();
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
<b>Event:</b> open

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({
    open: function (args) {
        args.preventDefault();
    }
});
datetimepicker.appendTo('#element');
datetimepicker.show();
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
Enable RTL
</td>
<td>
<b>property:</b> enableRTL

```javascript
$("#datetimepicker").ejDateTimePicker({ enableRTL : true});
```

</td>
<td>
<b>property:</b> enableRtl

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ enableRtl : true});
datetimepicker.appendTo('#element');
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
Enable Persistence
</td>
<td>
<b>property:</b> enablePersistence

```javascript
$("#datetimepicker").ejDateTimePicker({ enablePersistence : true});
```

</td>
<td>
<b>property:</b> enablePersistence

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ enablePersistence : true});datetimepicker.appendTo('#element');
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

```javascript
$("#datetimepicker").ejDateTimePicker({ validationRules:{  required : true }});
```

</td>
<td>
<b>Can be achieved by:</b>

```javascript

var datetimepicker = new ej.calendars.DateTimePicker({ placeholder: 'Enter date'});datetimepicker.appendTo('#element');

var options = {  rules: {   'datetime': { required: true }} }
var formObject: FormValidator = new FormValidator('#form-element', options);
```

</td>
</tr>
<tr>
<td>
Validation message
</td>
<td>
<b>property:</b> validationMessage

```javascript
$("#datetimepicker").ejDateTimePicker({ validationRules:{required:true},
validationMessage:{ required: "Required Date value" }
});
```

</td>
<td>
<b>Can be achieved by:</b>

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({
    placeholder: 'Enter date'
});
datetimepicker.appendTo('#element');

var options = {
    rules: {
        'datetime': {    required: [true, 'DateTime value required'] }
    },
    customPlacement: function (inputElement, errorElement) {
        inputElement.parentElement.parentElement.appendChild(errorElement);
    }
};
    var formObject = new ej.inputs.FormValidator('#form-element', options);
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

```javascript
$("#datetimepicker").ejDateTimePicker({width: 200});
```

</td>
<td>
<b>property:</b> width

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ width: '200px'});
datetimepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Readonly
</td>
<td>
<b>property:</b> readOnly

```javascript
$("#datetimepicker").ejDateTimePicker({ readOnly : true});
```

</td>
<td>
<b>property:</b> readonly

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ readonly:true, value:new Date() });datetimepicker.appendTo('#element');
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

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ showClearButton: true});datetimepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Height
</td>
<td>
<b>property:</b> height

```javascript
$("#datetimepicker").ejDateTimePicker({ height: 35});
```

</td>
<td>
<b>Can be achieved by:</b>

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ cssClass: 'e-custom-style'});datetimepicker.appendTo('#element');
```

```css
.e-control-wrapper.e-custom-style.e-date-wrapper.e-input-group{ height: 35px;}
```

</td>
</tr>
<tr>
<td>
Html Attributes
</td>
<td>
<b>property:</b> htmlAttributes

```javascript
$("#datetimepicker").ejDateTimePicker({ htmlAttributes : {required:"required"}});
```

</td>
<td>
<b>Not Applicable</b>
</td>
</tr>
<tr>
<td>
Enable/Disable the Week Number
</td>
<td>
<b>property:</b> weekNumber

```javascript
$("#datetimepicker").ejDateTimePicker({ weekNumber : true});
```

</td>
<td>
<b>property:</b> weekNumber

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ weekNumber:true});
datetimepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Watermark text
</td>
<td>
<b>property:</b> watermarkText

```javascript
$("#datetimepicker").ejDateTimePicker({ watermarkText: "Enter dateTime"});
```

</td>
<td>
<b>property:</b> placeholder

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ placeholder: 'Enter dateTime'});datetimepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Disable/Enable
</td>
<td>
<b>property:</b> enabled

```javascript
$("#datetimepicker").ejDateTimePicker({ enabled: false});
```

</td>
<td>
<b>property:</b> enabled

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ enabled:false});
datetimepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Enable/Disable the textbox editing
</td>
<td>
<b>property:</b> allowEdit

```javascript
$("#datetimepicker").ejDateTimePicker({ allowEdit : true});
```

</td>
<td>
<b>property:</b> allowEdit

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ allowEdit : true});
datetimepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
zIndex
</td>
<td>
<b>Can be achieved by:</b>

```javascript
$("#datetimepicker").ejDateTimePicker({  cssClass: "e-custom-class"})
```

```css
.e-datetime-popup.e-popup.e-custom-class { z-index: 100 !important;}
```

</td>
<td>
<b>property:</b> zIndex

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ zIndex: 100});
datetimepicker.appendTo('#element');
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

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({
    placeholder: 'Enter date',
    floatLabelType: 'Auto'
});
datetimepicker.appendTo('#element');
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
<b>Event:</b> renderDayCell

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ renderDayCell: onRenderCell});datetimepicker.appendTo('#element');
function onRenderCell(args){/*code block*/}
```

</td>
</tr>
<tr>
<td>
FocusIn event
</td>
<td>
<b>Event:</b> focusIn

```javascript
$("#datetimepicker").ejDateTimePicker({focusIn: function (args) {/*code block*/}});
```

</td>
<td>
<b>Event:</b> focus

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ focus: onFocus});
datetimepicker.appendTo('#element');
function onFocus(args){/*code block*/}
```

</td>
</tr>
<tr>
<td>
FocusOut event
</td>
<td>
<b>Event:</b> focusOut

```javascript
$("#datetimepicker").ejDateTimePicker({ focusOut: function (args) {/*code block*/}});
```

</td>
<td>
<b>Event:</b> blur

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ blur: onBlur});
datetimepicker.appendTo('#element');
function onBlur(args){/*code block*/}
```

</td>
</tr>
<tr>
<td>
Change event
</td>
<td>
<b>Event:</b> change

```javascript
$("#datetimepicker").ejDateTimePicker({change: function (args) {/*code block*/}});
```

</td>
<td>
<b>Event:</b> change

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({change: onChange});
datetimepicker.appendTo('#element');
onChange(args){/*code block*/}
```

</td>
</tr>
<tr>
<td>
Created event
</td>
<td>
<b>Event:</b> create

```javascript
$("#datetimepicker").ejDateTimePicker({create: function (args) {/*code block*/}});
```

</td>
<td>
<b>Event:</b> created

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ created: onCreate});datetimepicker.appendTo('#element');
function onCreate(args) {/*code block*/}
```

</td>
</tr>
<tr>
<td>
Destroy event
</td>
<td>
<b>Event:</b> destroy

```javascript
$("#datetimepicker").ejDateTimePicker({ destroy: function (args) {/*code block*/}});
```

</td>
<td>
<b>Event:</b> destroyed

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ destroyed: onDestroy});datetimepicker.appendTo('#element');
function onDestroy(args){/*code block*/}
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

```javascript
$("#datetimepicker").ejDateTimePicker({ locale: "en-US"});
```

</td>
<td>
<b>property:</b> locale

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ locale: 'en'});
datetimepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Specify the first day of week
</td>
<td>
<b>property:</b> startDay

```javascript
$("#datetimepicker").ejDateTimePicker({ startDay: 2});
```

</td>
<td>
<b>property:</b> firstDayOfWeek

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ firstDayOfWeek: 2});datetimepicker.appendTo('#element');
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
<b>property:</b> enableStrictMode

```javascript
$("#datetimepicker").ejDateTimePicker({ enableStrictMode : true});
```

</td>
<td>
<b>property:</b> strictMode

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({
    strictMode: true,
    value: new Date('5/28/2017'),
    min: new Date('5/5/2017'),
    max: new Date('5/25/2017')
});
datetimepicker.appendTo('#element');
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
<b>Event:</b> close

```javascript
$("#datetimepicker").ejDateTimePicker({close: function (args) {/*code block*/}});
```

</td>
<td>
<b>Event:</b> close

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({
    close: function (args) {/*code block*/}
});
datetimepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Hide
</td>
<td>
<b>Method:</b> hide()

```javascript
$("#datetimepicker").ejDateTimePicker();
var dateObj = $("#datetimepicker").data("ejDateTimePicker");
dateObj.hide();
```

</td>
<td>
<b>Method:</b> hide()

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ value: new Date("05/11/2017")});datetimepicker.appendTo('#element');
datetimepicker.hide();
```

</td>
</tr>
<tr>
<td>
Open
</td>
<td>
<b>Event:</b> open

```javascript
$("#datetimepicker").ejDateTimePicker({open: function (args) {/*code block*/}});
```

</td>
<td>
<b>Event:</b> open

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({
    open: function (args) {/*code block*/}
});
datetimepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Show
</td>
<td>
<b>Method:</b> show()

```javascript
$("#datetimepicker").ejDateTimePicker();
var dateObj = $("#datetimepicker").data("ejDateTimePicker");
dateObj.show();
```

</td>
<td>
<b>Method:</b> show()

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ value: new Date("05/11/2017")});datetimepicker.appendTo('#element');
datetimepicker.show();
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
<b>Method:</b> navigateTo()

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({
    value: new Date("09/04/2018"),
    open:onOpen
});
datetimepicker.appendTo('#element');

function onOpen(args) {
    datetimepicker.navigateTo('Year', new Date("03/18/2018"));
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
<b>Event:</b> navigated

```javascript
var datetimepicker = new ej.calendars.DateTimePicker({ navigated: onNavigate});datetimepicker.appendTo('#element');
function onNavigate(args) {/*code block*/}
```

</td>
</tr>
<tr>
<td>
Enable/Disable the drill down
</td>
<td>
<b>property:</b> timeDrillDown

```javascript
$("#datetimepicker").ejDateTimePicker({ timeDrillDown: { enabled: true, showMeridian: true,   autoClose: true,  interval: 10 }
});
```

</td>
<td>
<b>Not Applicable</b>
</td>
</tr>
</table>
