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
<b>property:</b> <i>value</i>

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
    value: new Date("5/5/2014")
});
```

</td>
<td>
<b>property:</b> <i>value</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    value: new Date("05/11/2017")
});
datepickerObject.appendTo('#element');
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
<b>property:</b> <i>dateFormat</i>

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
    dateFormat: "dd/MM/yyyy"
});
```

</td>
<td>
<b>property:</b> <i>format</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    format: 'yyyy-MM-dd'
});
datepickerObject.appendTo('#element');
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
var dateObj = new ej.DatePicker($("#datepicker"), {
   dayHeaderFormat: ej.DatePicker.Header.Long
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
<b>property:</b> startLevel

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
   startLevel: ej.DatePicker.Level.Year
});
```

</td>
<td>
<b>property:</b> <i>start</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    start:'Decade'
});
datepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Depth view
</td>
<td>
<b>property:</b> depthLevel

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
   depthLevel: ej.DatePicker.Level.Year
});
```

</td>
<td>
<b>property:</b> <i>depth</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    depth:'Year'
});
datepickerObject.appendTo('#element');
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

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
  minDate: new Date("5/1/2013")
});
```

</td>
<td>
<b>property:</b> <i>min</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    min: new Date("5/1/2013")
});
datepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Maximum date
</td>
<td>
<b>property:</b> maxDate

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
  maxDate: new Date("5/1/2013")
});
```

</td>
<td>
<b>property:</b> <i>max</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    max: new Date("5/1/2013")
});
datepickerObject.appendTo('#element');
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

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
  blackoutDates: [new Date(2016, 4, 10), new Date(2016, 4, 15), new Date(2016, 4, 20), new Date(2016, 4, 22), new Date(2016, 5, 12), new Date(2016, 5, 24)]
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let datepickerObject: DatePicker = new DatePicker({
    renderDayCell: disableDate
});
datepickerObject.appendTo('#element');

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
var dateObj = new ej.DatePicker($("#datepicker"), {
   cssClass: "gradient-lime"
});
```

</td>
<td>
<b>property:</b> <i>cssClass</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    cssClass: 'e-custom-style'
});
datepickerObject.appendTo('#element');
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
let datepickerObject: DatePicker = new DatePicker({
    renderDayCell: onRenderCell
});
datepickerObject.appendTo('#element');
function onRenderCell(args: RenderDayCellEventArgs): void {
    /* code block */
}
```

</td>
</tr>
<tr>
<td>
Show/Hide the today button
</td>
<td>
<b>property:</b> showFooter

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
  showFooter: false
});
```

</td>
<td>
<b>property:</b> <i>showTodayButton</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    showTodayButton: false
});
datepickerObject.appendTo('#element');
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
var dateObj = new ej.DatePicker($("#datepicker"), {
   showOtherMonths: false
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let datepickerObject: DatePicker = new DatePicker();

datepickerObject.appendTo('#element');
```

```css
.e-datepicker .e-calendar .e-content tr.e-month-hide,
.e-datepicker .e-calendar .e-content td.e-other-month > .e-day {
    visibility: none;
}
.e-datepicker .e-calendar .e-content td.e-month-hide,
.e-datepicker .e-calendar .e-content td.e-other-month {
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

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
   showDisabledRange: false,
    blackoutDates: [new Date(2016, 4, 10), new Date(2016, 4, 15), new Date(2016, 4, 20), new Date(2016, 4, 22), new Date(2016, 5, 12), new Date(2016, 5, 24)]
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

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
   showPopupButton: false
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let datepickerObject: DatePicker = new DatePicker({
    focus: onFocus
});
datepickerObject.appendTo('#element');
function onFocus(args: FocusEventArgs) {
    datepickerObject.show();
}
```

```css
.e-datepicker .e-control-wrapper .e-input-group-icon.e-date-icon{
    display: none;
}
```

</td>
</tr>
<tr>
<td>
Enable /Disable the rounded corner
</td>
<td>
<b>property:</b> showRoundedCorner

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
   showRoundedCorner: true
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let datepickerObject: DatePicker = new DatePicker({
    cssClass: 'e-custom-style'
});
datepickerObject.appendTo('#element');
```

```css
.e-control-wrapper.e-custom-style.e-date-wrapper.e-input-group{
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
var dateObj = new ej.DatePicker($("#datepicker"), {
    stepMonths: 2
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let datepickerObject: DatePicker = new DatePicker({
    value: new Date("09/04/2019"),
    open:onOpen
});
datepickerObject.appendTo('#element');
function onOpen(args:any){
    datepickerObject.navigateTo('Year', new Date("03/18/2018"));
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
var dateObj = new ej.DatePicker($("#datepicker"), {
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
Button text
</td>
<td>
<b>property:</b> buttonText

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
     buttonText : "Now"
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
L10n.load({ 'en': {'datepicker': {today:'Now' }}});
let datepickerObject: DatePicker = new DatePicker({
    locale: 'en'
});
datepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Display inline
</td>
<td>
<b>property:</b> displayInline

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
    displayInline: true
});
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

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
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
Highlight dates
</td>
<td>
<b>property:</b> highlightSection

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
    highlightSection: "week"
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let datepickerObject: DatePicker = new DatePicker({
    renderDayCell: highlightDate
});
datepickerObject.appendTo('#element');
function highlightDate(args: RenderDayCellEventArgs): void {
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

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
    highlightWeekend : true
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let datepickerObject: DatePicker = new DatePicker({
    renderDayCell: highlightDate
});
datepickerObject.appendTo('#element');
function highlightDate(args: RenderDayCellEventArgs): void {
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

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
    tooltipFormat : "dd/MM/yyyy"
});
```

</td>
<td>
<b>Not Applicable</b>
</td>
</tr>
<tr>
<td>
Special dates
</td>
<td>
<b>property:</b> specialDates

```ts
specialDays = [ { date: new Date(2018, 09, 08), tooltip: "In Australia", iconClass: "flags sprite-Australia" },{ date: new Date(2018, 09, 21), tooltip: "In France", iconClass: "flags sprite-France" }]

var dateObj = new ej.DatePicker($("#datepicker"), {
    specialDates : specialDays
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let datepickerObject: DatePicker = new DatePicker({
    renderDayCell: customDates,
    value: new Date('5/5/2017')
});
datepickerObject.appendTo('#element');
function customDates(args: RenderDayCellEventArgs) {
    if (args.date.getDate() === 10) {
        let span: HTMLElement;
        span = document.createElement('span');
        span.setAttribute('class', 'e-icons highlight');
        args.element.firstElementChild.setAttribute('title', 'Birthday !');
        args.element.setAttribute('title', 'Birthday !');
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

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
    focusIn: function (args) {/*code block*/}
});
```

</td>
<td>
<b>Event:</b> <i>focus</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    focus: onFocus
});
datepickerObject.appendTo('#element');
function onFocus(args: FocusEventArgs): void {
    /*code block*/
}
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
var dateObj = new ej.DatePicker($("#datepicker"), {
    focusOut: function (args) {/*code block*/}
});
```

</td>
<td>
<b>Event:</b> <i>blur</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    blur: onBlur
});
datepickerObject.appendTo('#element');
function onBlur(args: BlurEventArgs): void {
    /*code block*/
}
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
let datepickerObject: DatePicker = new DatePicker({
    placeholder: 'Enter date'
});
datepickerObject.appendTo('#element');
datepickerObject.focusIn();
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
<b>Method:</b> <i>focusOut()</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    placeholder: 'Enter date'
});
datepickerObject.appendTo('#element');
datepickerObject.focusOut();
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
let datepickerObject: DatePicker = new DatePicker({
    close: function (args: PreventableEventArgs) {
        args.preventDefault();
    }
});
datepickerObject.appendTo('#element');
datepickerObject.show();
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
<b>Event:</b> <i>close</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    open: function (args: PreventableEventArgs) {
        args.preventDefault();
    }
});
datepickerObject.appendTo('#element');
datepickerObject.show();
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
var dateObj = new ej.DatePicker($("#datepicker"), {
    enableRTL : true
});
```

</td>
<td>
<b>property:</b> <i>enableRtl</i>

```ts

let datepickerObject: DatePicker = new DatePicker({
    enableRtl : true
})
datepickerObject.appendTo('#element');
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
var dateObj = new ej.DatePicker($("#datepicker"), {
    enablePersistence : true
});
```

</td>
<td>
<b>property:</b> <i>enablePersistence</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    enablePersistence : true
});
datepickerObject.appendTo('#element');
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
var dateObj = new ej.DatePicker($("#datepicker"), {
    validationRules : {required : true}
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let datepickerObject: DatePicker = new DatePicker({
    placeholder: 'Enter date',
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
var dateObj = new ej.DatePicker($("#datepicker"), {
    validationRules : {required : true},
    validationMessage : {required: "Required Date value" }
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let datepickerObject: DatePicker = new DatePicker({
    placeholder: 'Enter date',
    value: new Date()
});
datepickerObject.appendTo('#element');
let options: FormValidatorModel = {
    rules: {
        'datevalue': { required: [true, 'Date value required']  }
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
var dateObj = new ej.DatePicker($("#datepicker"), {
    width: 200
});
```

</td>
<td>
<b>property:</b> <i>width</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    width: '200px'
});
datepickerObject.appendTo('#element');
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
var dateObj = new ej.DatePicker($("#datepicker"), {
    readOnly : true
});
```

</td>
<td>
<b>property:</b> <i>readonly</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    readonly:true,
    value:new Date()
});
datepickerObject.appendTo('#element');
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
<b>property:</b> <i>showClearButton</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    showClearButton: false
});
datepickerObject.appendTo('#element');
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
var dateObj = new ej.DatePicker($("#datepicker"), {
    height: 35
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let datepickerObject: DatePicker = new DatePicker({
    cssClass: 'e-custom-style'
});
datepickerObject.appendTo('#element');
```

```css
.e-control-wrapper.e-custom-style.e-date-wrapper.e-input-group {
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
var dateObj = new ej.DatePicker($("#datepicker"), {
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
Shoe/Hide the Week Number
</td>
<td>
<b>property:</b> <i>weekNumber</i>

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
    weekNumber : true
});
```

</td>
<td>
<b>property:</b> <i>weekNumber</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    weekNumber:true
});
datepickerObject.appendTo('#element');
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
var dateObj = new ej.DatePicker($("#datepicker"), {
    watermarkText: "Enter date"
});
```

</td>
<td>
<b>property:</b> <i>placeholder</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    placeholder: 'Enter date'
    });
datepickerObject.appendTo('#element');
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
var dateObj = new ej.DatePicker($("#datepicker"), {
     enabled: false
});
```

</td>
<td>
<b>property:</b> <i>enabled</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    enabled:false
});
datepickerObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Disable the DatePicker
</td>
<td>
<b>Method:</b> disable()

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
});
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

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
});
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

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
    allowEdit : false
});
```

</td>
<td>
<b>property:</b> <i>allowEdit</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    allowEdit : false
});
datepickerObject.appendTo('#element');
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
<b>property:</b> <i>zIndex</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    zIndex: 100
});
datepickerObject.appendTo('#element');
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
<b>property:</b> <i>floatLabelType</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    placeholder: 'Enter date',
    floatLabelType: 'Auto'
});
datepickerObject.appendTo('#element');
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
var dateObj = new ej.DatePicker($("#datepicker"), {
    locale: "en-US"
});
```

</td>
<td>
<b>property:</b> <i>locale</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    locale: 'en'
});
datepickerObject.appendTo('#element');
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
var dateObj = new ej.DatePicker($("#datepicker"), {
    startDay: 2
});
```

</td>
<td>
<b>property:</b> <i>firstDayOfWeek</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    firstDayOfWeek: 2
});
datepickerObject.appendTo('#element');
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

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
    enableStrictMode : true
});
```

</td>
<td>
<b>property:</b> <i>strictMode</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    strictMode: true,
    value: new Date('5/28/2017'),
    min: new Date('5/5/2017'),
    max: new Date('5/25/2017')
});
datepickerObject.appendTo('#element');
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

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
    close: function (args) {/* code block*/}
});
```

</td>
<td>
<b>Event:</b> <i>close</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    close: function (args: PreventableEventArgs) {/*code block*/}
});
datepickerObject.appendTo('#element');
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
var dateObj = new ej.DatePicker($("#datepicker"), {
});
dateObj.hide();
```

</td>
<td>
<b>Method:</b> <i>hide()</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    value: new Date("05/11/2017")
});
datepickerObject.appendTo('#element');
datepickerObject.hide();
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
var dateObj = new ej.DatePicker($("#datepicker"), {
    open: function (args) {/* code block*/}
});
```

</td>
<td>
<b>Event:</b> <i>open</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    open: function (args: PreventableEventArgs) {
        /*code block*/
    }
});
datepickerObject.appendTo('#element');
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
var dateObj = new ej.DatePicker($("#datepicker"), {
});
dateObj.show();
```

</td>
<td>
<b>Method:</b> <i>show()</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    value: new Date("05/11/2017")
});
datepickerObject.appendTo('#element');
datepickerObject.show();
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

```ts
let datepickerObject: DatePicker = new DatePicker({
    value: new Date("09/04/2019"),
    open:onOpen
});
datepickerObject.appendTo('#element');
function onOpen(args:any){
    datepickerObject.navigateTo('Year', new Date("03/18/2018"));
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

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
    navigate: function (args) {/*code block*/}
});
```

<td>
<b>Event:</b> <i>navigated</i>

```ts
let datepickerObject: DatePicker = new DatePicker({
    navigated: onNavigate
});
datepickerObject.appendTo('#element');
function onNavigate(args: NavigatedEventArgs) {/*code block*/}
```

</td>
</tr>
<tr>
<td>
Drill down
</td>
<td>
<b>property:</b> allowDrillDown

```ts
var dateObj = new ej.DatePicker($("#datepicker"), {
    allowDrillDown : true
});
```

</td>
<td>
<b>Not Applicable</b>
</td>
</tr>
</table>