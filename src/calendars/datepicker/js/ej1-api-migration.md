# Migration from Essential JS 1

This article describes the API migration process of DatePicker component from Essential JS 1 to Essential JS 2.

## Date Selection

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
$("#datepicker").ejDatePicker({  value: new Date("5/5/2014") });
```

</td>
<td>
<b>property:</b> value

```javascript
var datepicker = new ej.calendars.DatePicker({ value: new Date("05/11/2017")});
datepicker.appendTo('#datepicker');
```

</td>
</tr>
</table>

## Date Format

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
Display the date format
</td>
<td>
<b>property:</b> dateFormat

```javascript
$("#datepicker").ejDatePicker({ dateFormat: "dd/MM/yyyy"});
```

</td>
<td>
<b>property:</b> format

```javascript
var datepicker = new ej.calendars.DatePicker({
    value: new Date("05/11/2017");
    format: 'yyyy-MM-dd'});
datepicker.appendTo('#element');
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
$("#datepicker").ejDatePicker({ dayHeaderFormat: ej.DatePicker.Header.Short});
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
Start
</td>
<td>
<b>property:</b> startLevel

```javascript
$("#datepicker").ejDatePicker({ startLevel: ej.DatePicker.Level.Year});
```

</td>
<td>
<b>property:</b> start

```javascript
var datepicker = new ej.calendars.DatePicker({
    start:'Decade'});
datepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Depth
</td>
<td>
<b>property:</b> depthLevel

```javascript
$("#datepicker").ejDatePicker({depthLevel: ej.DatePicker.Level.Year});
```

</td>
<td>
<b>property:</b> depth

```javascript
var datepicker = new ej.calendars.DatePicker({
    depth:'Year'
});
datepicker.appendTo('#element');
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
Minimum date
</td>
<td>
<b>property:</b> minDate

```javascript
$("#datepicker").ejDatePicker({
    minDate: new Date("5/1/2013")
});
```

</td>
<td>
<b>property:</b> min

```javascript
var datepicker = new ej.calendars.DatePicker({
    min: new Date("5/1/2013")
});
datepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Maximum date
</td>
<td>
<b>property:</b> maxDate

```javascript
$("#datepicker").ejDatePicker({ maxDate : new Date("5/30/2015")});
```

</td>
<td>
<b>property:</b> max

```javascript
var datepicker = new ej.calendars.DatePicker({
    max : new Date("5/30/2015")
});
datepicker.appendTo('#element');
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
Block-out dates
</td>
<td>
<b>property:</b> blackoutDates

```javascript
$("#datepicker").ejDatePicker({
    blackoutDates: [ new Date(2016, 4, 10), new Date(2016, 4, 15), new Date(2016, 4, 20), new Date(2016, 4, 22), new Date(2016, 5, 12), new Date(2016, 5, 24)]
});
```

</td>
<td>
<b>Can be achieved by</b>

```javascript
var datepicker = new ej.calendars.DatePicker({
    renderDayCell: disableDate
});
datepicker.appendTo('#element');
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
$("#datepicker").ejDatePicker({ cssClass: "gradient-lime"});
```

</td>
<td>
<b>property:</b> cssClass

```javascript
var datepicker = new ej.calendars.DatePicker({ cssClass: 'e-custom-style'});datepicker.appendTo('#element');
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
var datepicker = new ej.calendars.DatePicker({
    renderDayCell: onRenderCell
});
datepicker.appendTo('#element');

function onRenderCell(args) {/*code block*/}
```

</td>
</tr>
<tr>
<td>
Show/Hide the today button
</td>
<td>
<b>property:</b> showFooter

```javascript
$("#datepicker").ejDatePicker({ showFooter: false});
```

</td>
<td>
<b>property:</b> showTodayButton

```javascript
var datepicker = new ej.calendars.DatePicker({ showTodayButton: false});
datepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Show?Hide the other month dates
</td>
<td>
<b>property:</b> showOtherMonths

```javascript
$("#datepicker").ejDatePicker({ showOtherMonths: false});
```

</td>
<td>
<b></b>

```javascript
var datepicker = new ej.calendars.DatePicker();
datepicker.appendTo('#element');
```

```css
.e-datepicker .e-calendar .e-content tr.e-month-hide,.e-datepicker .e-calendar .e-content td.e-other-month > .e-day {
    visibility: none;
}
.e-datepicker .e-calendar .e-content td.e-month-hide,.e-datepicker .e-calendar .e-content td.e-other-month {
    pointer-events: none;
    touch-action: none;
}
```

</td>
</tr>
<tr>
<td>
Show/Hide the disabled range
</td>
<td>
<b>property:</b> showDisabledRange

```javascript
$("#datepicker").ejDatePicker({
    blackoutDates: [ new Date(2016, 4, 10), new Date(2016, 4, 15), new Date(2016, 4, 20), new Date(2016, 4, 22), new Date(2016, 5, 12), new Date(2016, 5, 24)]
    showDisabledRange: false
});
```

</td>
<td>
<b>Not Applicable</b>
</td>
</tr>
<tr>
<td>
Show/Hide the popup button
</td>
<td>
<b>property:</b> showPopupButton

```javascript
$("#datepicker").ejDatePicker({ showPopupButton: false});
```

</td>
<td>
<b>Can be achieved by</b>

```javascript
var datepicker = new ej.calendars.DatePicker({
    focus: onFocus
});
datepicker.appendTo('#element');
function onFocus(args) {
    datepicker.show();
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
Enable/Disable rounded corner
</td>
<td>
<b>property:</b> showRoundedCorner

```javascript
$("#datepicker").ejDatePicker({ showRoundedCorner: true});
```

</td>
<td>
<b>Can be achieved by</b>

```javascript
var datepicker = new ej.calendars.DatePicker({
    cssClass: 'e-custom-style'
});
datepicker.appendTo('#element');
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

```javascript
$("#datepicker").ejDatePicker({ stepMonths: 2});
```

</td>
<td>
<b>Can be achieved by</b>

```javascript
var datepicker = new ej.calendars.DatePicker({
    value: new Date("09/04/2018"),
    open:onOpen
});
datepicker.appendTo('#element');

function onOpen(args) {
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

```javascript
$("#datepicker").ejDatePicker({ showTooltip: false});
```

</td>
<td>
<b>Not Applicable</b>
</td>
</tr>
<tr>
<td>
Today button text
</td>
<td>
<b>property:</b> buttonText

```javascript
$("#datepicker").ejDatePicker({ buttonText : "Now"});
```

</td>
<td>
<b>Can be achieved by</b>

```javascript
L10n.load({  'en': { 'datepicker': {today:'Now' }  }});
var datepicker = new ej.calendars.DatePicker({
    locale: 'en'
});
datepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Display inline
</td>
<td>
<b>property:</b> displayInline

```javascript
$("#datepicker").ejDatePicker({ displayInline: true});
```

</td>
<td>
<b>Not Applicable</b>
</td>
</tr>
<tr>
<td>
Enable/Disable the animation
</td>
<td>
<b>property:</b> enableAnimation

```javascript
$("#datepicker").ejDatePicker({ enableAnimation : false});
```

</td>
<td>
<b>Not Applicable</b>
</td>
</tr>
<tr>
<td>
Highlight dates
</td>
<td>
<b>property:</b> highlightSection

```javascript
$("#datepicker").ejDatePicker({ highlightSection: "week"});
```

</td>
<td>
<b>Can be achieved by</b>

```javascript
var datepicker = new ej.calendars.DatePicker({
    renderDayCell: highlightDate
});
datepicker.appendTo('#element');
function highlightDate(args) {
    if (args.date.getDate() === 10) {
      args.element.classList.add('e-highlightweekend');
    }
}
```

```css
.e-highlightweekend {
    background-color: #cfe9f3;
}
```

</td>
</tr>
<tr>
<td>
Highlight weekend
</td>
<td>
<b>property:</b> highlightWeekend

```javascript
$("#datepicker").ejDatePicker({ highlightWeekend : true});
```

</td>
<td>

<b>Can be achieved by</b>

```javascript
var datepicker = new ej.calendars.DatePicker({
    renderDayCell: highlightDate
});
datepicker.appendTo('#element');
function highlightDate(args) {
    if (args.date.getDay() === 0 || args.date.getDay() === 6) {
      args.element.classList.add('e-highlightweekend');
    }
}
```

```css
.e-highlightweekend {
    background-color: #cfe9f3;
}
```

</td>
</tr>
<tr>
<td>
Tooltip format
</td>
<td>
<b>property:</b> tooltipFormat

```javascript
$("#datepicker").ejDatePicker({ tooltipFormat : "dd/MM/yyyy"});
```

</td>
<td>
<b>Not Applicable</b>
</td>
</tr>
<tr>
<td>
Special Dates
</td>
<td>
<b>property:</b> specialDates

```javascript
specialDays = [ { date: new Date(2018, 09, 08), tooltip: "In Australia", iconClass: "flags sprite-Australia" }, { date: new Date(2018, 09, 21), tooltip: "In France", iconClass: "flags sprite-France" }]

$("#datepicker").ejDatePicker({ specialDates: specialDays});
```

</td>
<td>
<b>Can be achieved by</b>

```javascript
var datepicker = new ej.calendars.DatePicker({
    renderDayCell: customDates,
    value: new Date('5/5/2017')
});
datepicker.appendTo('#element');
function customDates(args) {
    if (args.date.getDate() === 10) {
        var span = document.createElement('span');
        span.setAttribute('class', 'e-icons highlight');   args.element.firstElementChild.setAttribute('title', 'Birthday !');   args.element.setAttribute('title', 'Birthday !');
        args.element.setAttribute('data-val', 'Birthday !');
        args.element.appendChild(span);
    }
}
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
$("#datepicker").ejDatePicker({
    focusIn: function (args) {/*code block*/}
});
```

</td>
<td>
<b>Event:</b> focus

```javascript
var datepicker = new ej.calendars.DatePicker({
    focus: onFocus
});
datepicker.appendTo('#element');
function onFocus(args){ /*code block*/}
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
$("#datepicker").ejDatePicker({ focusOut: function (args) { /*code block*/}});
```

</td>
<td>
<b>Event:</b> blur

```javascript
var datepicker = new ej.calendars.DatePicker({
    blur: onBlur
});
datepicker.appendTo('#element');
function onBlur(args){ /*code block*/}
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
<b>Method:</b> focusIn()

```javascript
var datepicker = new ej.calendars.DatePicker({
    placeholder: 'Enter date'
});
datepicker.appendTo('#element');
datepicker.focusIn();
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
var datepicker = new ej.calendars.DatePicker({
    placeholder: 'Enter date'
});
datepicker.appendTo('#element');
datepicker.focusOut();
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
var datepicker = new ej.calendars.DatePicker({
    close: function (args) {
        args.preventDefault();
    }
});
datepicker.appendTo('#element');
datepicker.show();
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
var datepicker = new ej.calendars.DatePicker({
    open: function (args) {
        args.preventDefault();
    }
});
datepicker.appendTo('#element');
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

```javascript
$("#datepicker").ejDatePicker({
    enableRTL : true
});
```

</td>
<td>
<b>property:</b> enableRtl

```javascript
var datepicker = new ej.calendars.DatePicker({
    enableRtl : true
});
datepicker.appendTo('#element');
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
$("#datepicker").ejDatePicker({enablePersistence : true});
```

</td>
<td>
<b>property:</b> enablePersistence

```javascript
var datepicker = new ej.calendars.DatePicker({
    enablePersistence : true
});
datepicker.appendTo('#element');
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
$("#datepicker").ejDatePicker({ validationRules:{ required:true }});
```

</td>
<td>
<b>Can be achieved by</b>

```javascript
var datepicker = new ej.calendars.DatePicker({
    placeholder: 'Enter date'
});
datepicker.appendTo('#element');
var options = {  rules: {   'datevalue': {    required: true }} }
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
$("#datepicker").ejDatePicker({
    validationRules:{ required:true },
    validationMessage:{ required: "Required Date value"}
});
```

</td>
<td>
<b>Can be achieved by</b>

```javascript
var datepicker = new ej.calendars.DatePicker({
    placeholder: 'Enter date'
});

var options = {
    rules: {
        'datevalue': {    required: [true, 'Date value required'] }
    },
    customPlacement: function (inputElement, errorElement) {
        inputElement.parentElement.parentElement.appendChild(errorElement);
    }
};
    var formObject = new ej.inputs.FormValidator('#form-element', options);
    datepicker.appendTo('#element');
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
$("#datepicker").ejDatePicker({ width: 200});
```

</td>
<td>
<b>property:</b> width

```javascript
var datepicker = new ej.calendars.DatePicker({ width: '200px'});
datepicker.appendTo('#element');
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
$("#datepicker").ejDatePicker({ readOnly : true});
```

</td>
<td>
<b>property:</b> readonly

```javascript
var datepicker = new ej.calendars.DatePicker({
    readonly:true,
    value:new Date()
});
datepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Show/Hide the Clear Button
</td>
<td>
<b>Not Applicable</b>
</td>
<td>
<b>property:</b> showClearButton

```javascript
var datepicker = new ej.calendars.DatePicker({ showClearButton: true});
datepicker.appendTo('#element');
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
$("#datepicker").ejDatePicker({ height: 35});
```

</td>
<td>
<b>Can be achieved by</b>

```javascript
var datepicker = new ej.calendars.DatePicker({cssClass: 'e-custom-style'});
datepicker.appendTo('#element');
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
$("#datepicker").ejDatePicker({ htmlAttributes : {required:"required"}});
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
$("#datepicker").ejDatePicker({ weekNumber : true});
```

</td>
<td>
<b>property:</b> weekNumber

```javascript
var datepicker = new ej.calendars.DatePicker({ weekNumber:true});
datepicker.appendTo('#element');
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
$("#datepicker").ejDatePicker({ watermarkText: "Enter date"});
```

</td>
<td>
<b>property:</b> placeholder

```javascript
var datepicker = new ej.calendars.DatePicker({ placeholder: 'Enter date'});
datepicker.appendTo('#element');
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
$("#datepicker").ejDatePicker({ enabled: false});
```

</td>
<td>
<b>property:</b> enabled

```javascript
var datepicker = new ej.calendars.DatePicker({enabled:false});
datepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Disable the DatePicker
</td>
<td>
<b>Method:</b> disable()

```javascript
$("#datepicker").ejDatePicker();
var dateObj = $("#datepicker").data("ejDatePicker");
dateObj.disable();
```

</td>
<td>
<b>Not Applicable</b>
</td>
</tr>
<tr>
<td>
Enable the DatePicker
</td>
<td>
<b>Method:</b> enable()

```javascript
$("#datepicker").ejDatePicker();
var dateObj = $("#datepicker").data("ejDatePicker");
dateObj.enable();
```

</td>
<td>
<b>Not Applicable</b>
</td>
</tr>
<tr>
<td>
Enable/Disable the textbox editing
</td>
<td>
<b>property:</b> allowEdit

```javascript
$("#datepicker").ejDatePicker({ allowEdit : true});
```

</td>
<td>
<b>property:</b> allowEdit

```javascript
var datepicker = new ej.calendars.DatePicker({ allowEdit : true});
datepicker.appendTo('#element');
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
<b>property:</b> zIndex

```javascript
var datepicker = new ej.calendars.DatePicker({ zIndex: 100});
datepicker.appendTo('#element');
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
var datepicker = new ej.calendars.DatePicker({
    placeholder: 'Enter date',
    floatLabelType: 'Auto'
});
datepicker.appendTo('#element');
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
$("#datepicker").ejDatePicker({locale: "en-US"});
```

</td>
<td>
<b>property:</b> locale

```javascript
var datepicker = new ej.calendars.DatePicker({ locale: 'en'});
datepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
First day of week
</td>
<td>
<b>property:</b> startDay

```javascript
$("#datepicker").ejDatePicker({ startDay: 2});
```

</td>
<td>
<b>property:</b> firstDayOfWeek

```javascript
var datepicker = new ej.calendars.DatePicker({ firstDayOfWeek: 2});
datepicker.appendTo('#element');
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
$("#datepicker").ejDatePicker({ enableStrictMode : true});
```

</td>
<td>
<b>property:</b> strictMode

```javascript
var datepicker = new ej.calendars.DatePicker({
    strictMode: true,
    value: new Date('5/28/2017'),
    min: new Date('5/5/2017'),
    max: new Date('5/25/2017')
});
datepicker.appendTo('#element');
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
$("#datepicker").ejDatePicker({ close: function (args) { /*code block*/}});
```

</td>
<td>
<b>Event:</b> close

```javascript
var datepicker = new ej.calendars.DatePicker({
    close: function (args) { /*code block*/}
});
datepicker.appendTo('#element');
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
$("#datepicker").ejDatePicker();
var dateObj = $("#datepicker").data("ejDatePicker");
dateObj.hide();
```

</td>
<td>
<b>Method:</b> hide()

```javascript
var datepicker = new ej.calendars.DatePicker({ value: new Date("05/11/2017")});datepicker.appendTo('#element');
datepicker.hide();
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
$("#datepicker").ejDatePicker({open: function (args) { /*code block*/}});
```

</td>
<td>
<b>Event:</b> open

```javascript
var datepicker = new ej.calendars.DatePicker({ open: function (args) { /*code block*/}});
datepicker.appendTo('#element');
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
$("#datepicker").ejDatePicker();
var dateObj = $("#datepicker").data("ejDatePicker");
dateObj.show();
```

</td>
<td>
<b>Method:</b> show()

```javascript
var datepicker = new ej.calendars.DatePicker({ value: new Date("05/11/2017")});datepicker.appendTo('#element');
datepicker.show();
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
var datepicker = new ej.calendars.DatePicker({
    value: new Date("09/04/2018"),
    open:onOpen
});
datepicker.appendTo('#element');

function onOpen(args) {
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
<b>Event:</b> navigate

```javascript
$("#datepicker").ejDatePicker({ navigate: function (args) { /*code block*/}});
```

</td>
<td>
<b>Event:</b> navigated

```javascript
var datepicker = new ej.calendars.DatePicker({navigated: onNavigate});
datepicker.appendTo('#element');
function onNavigate(args) { /*code block*/}
```

</td>
</tr>
<tr>
<td>
Enable/Disable the drill down
</td>
<td>
<b>property:</b> allowDrillDown

```javascript
$("#datepicker").ejDatePicker({ allowDrillDown : true});
```

</td>
<td>
<b>Not Applicable</b>
</td>
</tr>
</table>