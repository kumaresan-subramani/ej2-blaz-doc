# Migration from Essential JS 1

This article describes the API migration process of DateRangePicker component from Essential JS 1 to Essential JS 2.

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

```ts
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
    value: "11/1/2013 - 12/3/2019",
});
```

</td>
<td>
<b>property:</b> value

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    value: [new Date("10/07/2017"), new Date("2/2/2019")]
});
daterangeObject.appendTo('#element');
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
Display  the date format
</td>
<td>
<b>property:</b> dateFormat

```ts
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
    dateFormat: "dd/MM/yyyy"
});
```

</td>
<td>
<b>property:</b> format

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    format: 'dd\'\/\'MMM\'\/\'yy hh:mm a',
    startDate: new Date("11/9/2017"),
    endDate: new Date("11/21/2017")
});
daterangeObject.appendTo('#element');
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
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
    minDate: new Date("1/1/2017")
});
```

</td>
<td>
<b>property:</b> min

```ts

let daterangeObject: DateRangePicker = new DateRangePicker({
    min: new Date("1/1/2017")
});
daterangeObject.appendTo('#element');
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
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
    maxDate: new Date("1/1/2017")
});
```

</td>
<td>
<b>property:</b> max

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    max: new Date("1/1/2017")
});
daterangeObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Start date
</td>
<td>
<b>property:</b> startDate

```ts
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
    startDate: new Date("1/1/2017")
});
```

</td>
<td>
<b>property:</b> startDate

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    startDate: new Date("11/9/2017")
});
daterangeObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
End date
</td>
<td>
<b>property:</b> endDate

```ts
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
    endDate: new Date("1/1/2017")
});
```

</td>
<td>
<b>property:</b> endDate

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    endDate: new Date("11/21/2017")
});
daterangeObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Preset ranges
</td>
<td>
<b>property:</b> ranges

```ts
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
    ranges: [  
    { label: "Today", range: [new Date(), new Date()] },
    { label: "Last 1 Week", range: [new Date(new Date().setDate(new Date().getDate() - 7)), new Date()] },
    { label: "Last 1 Month", range: [new Date(new Date().setMonth(new Date().getMonth() - 1)), new Date()] },
    { label: "Last 2 Month", range: [new Date(new Date().setMonth(new Date().getMonth() - 2)), new Date()] }]
});
```

</td>
<td>
<b>property:</b> presets

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    presets: [
    { label: 'Today', start: new Date(), end: new Date() },
    { label: 'This Month', start: new Date(new Date().setDate(1)), end: new Date() },
    { label: 'Last Month', start: new Date(new Date(new Date().setMonth(new Date().getMonth() - 1)).setDate(1)), end: new Date() },
    { label: 'Last Year', start: new Date(new Date().getFullYear() - 1, 0, 1), end: new Date() }]
});
daterangeObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Add ranges
</td>
<td>
<b>Method:</b> addRanges()

```ts
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
});
daterangeObj.addRanges("new Range", [new Date("11/12/2019"),new Date("11/12/2021")] );
```

</td>
<td>
<b>Not Applicable</b>
</td>
</tr>
<tr>
<td>
Clear ranges
</td>
<td>
<b>Method:</b> clearRanges()

```ts
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
});
daterangeObj.clearRanges();
```

</td>
<td>
<b>Not Applicable</b>
</td>
</tr>
<tr>
<td>
Get selected range
</td>
<td>
<b>Method:</b> getSelectedRange()

```ts
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
    startDate: new Date("11/9/2017"),
    endDate: new Date("11/21/2017")
});
console.log(daterangeObj.clearRanges());
```

</td>
<td>
<b>Method:</b> getSelectedRange()

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    startDate: new Date("11/9/2017"),
    endDate: new Date("11/21/2017")
});
daterangeObject.appendTo('#element');
console.log(daterangeObject.getSelectedRange());
```

</td>
</tr>
<tr>
<td>
Set date range
</td>
<td>
<b>Method:</b> setRange()

```ts
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
});
daterangeObj.setRange([new Date("11/12/2011"), new Date("11/12/2019")]);
```

</td>
<td>
<b>Not Applicable</b>
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
<b>Not Applicable</b>
</td>
<td>
<b>Can be achieved by</b>

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    renderDayCell: disableDate
});
daterangeObject.appendTo('#element');

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
cssClass
</td>
<td>
<b>property:</b> cssClass

```ts
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
    cssClass: "gradient-lime"
});
```

</td>
<td>
<b>property:</b> cssClass

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    cssClass:"customCSS"
});
daterangeObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Enable/Disable the DateRangePicker with TimePicker
</td>
<td>
<b>property:</b> enableTimePicker

```ts
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
    enableTimePicker: true
});
```

</td>
<td>
<b>Not Applicable</b>
</td>
</tr>
<tr>
<td>
Time format
</td>
<td>
<b>property:</b> timeFormat

```ts
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
    timeFormat: "HH:mm"
});
```

</td>
<td>
<b>Not Applicable</b>
</td>
</tr>
<tr>
<td>
Minimum days span
</td>
<td>
<b>Not Applicable</b>
</td>
<td>
<b>property:</b> minDays

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    minDays: 5
});
daterangeObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Maximum days span
</td>
<td>
<b>Not Applicable</b>
</td>
<td>
<b>property:</b> maxDays

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    maxDays: 10
});
daterangeObject.appendTo('#element');
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
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
    buttonText : {  reset: "Reset",cancel: "Cancel",apply: "Apply"}
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
L10n.load({ 'en': {   'daterangepicker': { applyText: 'Apply',  } }});
let daterangeObject: DateRangePicker = new DateRangePicker({
    locale: 'en'
});
daterangeObject.appendTo('#element');
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
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
    showPopupButton: false
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    focus: onFocus
});
daterangeObject.appendTo('#element');
function onFocus(args: FocusEventArgs) {
    daterangeObject.show();
```

```css
.e-daterangepicker .e-control-wrapper .e-input-group-icon.e-range-icon{
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
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
    showRoundedCorner: true
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    cssClass: 'e-custom-style'
});
daterangeObject.appendTo('#element');
```

```css
.e-control-wrapper.e-custom-style.e-date-range-wrapper.e-input-group {
    border-radius: 4px;
}
```

</td>
</tr>
<tr>
<td>
FocusIn event
</td>
<td>
<b>Not Applicable</b>
</td>
<td>
<b>Event:</b> focus

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    focus: onFocus
});
daterangeObject.appendTo('#element');
function onFocus(args: FocusEventArgs) { /* code block*/}
```

</td>
</tr>
<tr>
<td>
FocusOut event
</td>
<td>
<b>Not Applicable</b>
</td>
<td>
<b>Event:</b> blur

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    blur: onBlur
});
daterangeObject.appendTo('#element');
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
<b>Method:</b> focusIn()

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    value: new Date()
});
daterangeObject.appendTo('#element');
daterangeObject.focusIn();
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
let daterangeObject: DateRangePicker = new DateRangePicker({
    value: new Date()
});
daterangeObject.appendTo('#element');
daterangeObject.focusOut();
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
<b>Not Applicable</b>
</td>
<td>
<b>property:</b> enableRtl

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    enableRtl: true
});
daterangeObject.appendTo('#element');
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
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
    enablePersistence: true
});
```

</td>
<td>
<b>property:</b> enablePersistence

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    enablePersistence: true,
    startDate: new Date("11/9/2017"),
    endDate: new Date("11/21/2017")
});
daterangeObject.appendTo('#element');
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
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
   width: 200
});
```

</td>
<td>
<b>property:</b> width

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    width: 200
});
daterangeObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Readonly
</td>
<td>
<b>Not Applicable</b>
</td>
<td>
<b>property:</b> readonly

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    readonly:true
});
daterangeObject.appendTo('#element');
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
let daterangeObject: DateRangePicker = new DateRangePicker({
    showClearButton: false
});
daterangeObject.appendTo('#element');
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
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
  height: 35
});
```

</td>
<td>
<b>Can be achieved by</b>

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    cssClass:"e-custom-style"
});
daterangeObject.appendTo('#element');
```

```css
.e-daterangepicker .e-control-wrapper.e-custom-style.e-date-range-wrapper.e-input-group{
    height: 35px;
}
```

</td>
</tr>
<tr>
<td>
Enable/Disable the week number
</td>
<td>
<b>Not Applicable</b>
</td>
<td>
<b>property:</b> weekNumber

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    weekNumber: true
});
daterangeObject.appendTo('#element');
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
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
  watermarkText: "Enter date"
});
```

</td>
<td>
<b>property:</b> placeholder

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    placeholder: 'Enter date'
});
daterangeObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Enable/Disable
</td>
<td>
<b>property:</b> enabled

```ts
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
  enabled: false
});
```

</td>
<td>
<b>property:</b> enabled

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    enabled: false
});
daterangeObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Disable the DateRangePicker
</td>
<td>
<b>Method:</b> disable()

```ts
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
});
daterangeObj.disable();
```

</td>
<td>
<b>Not Applicable</b>
</td>
</tr>
<tr>
<td>
Enable the DateRangePicker
</td>
<td>
<b>Method:</b> enable()

```ts
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
});
daterangeObj.enable();
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
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
     allowEdit: false
});
```

</td>
<td>
<b>property:</b> allowEdit

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    allowEdit: false
});
daterangeObject.appendTo('#element');
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
let daterangeObject: DateRangePicker = new DateRangePicker({
    placeholder: 'Enter date',
    floatLabelType: 'Auto'
});
daterangeObject.appendTo('#element');
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

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    zIndex: 100
});
daterangeObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Specify the date range separator
</td>
<td>
<b>property:</b> separator

```ts
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
    separator : "$"
});
```

</td>
<td>
<b>property:</b> separator

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    separator : "$"
});
daterangeObject.appendTo('#element');
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
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
    locale: "en-US"
});
```

</td>
<td>
<b>property:</b> locale

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    locale: 'en'
});
daterangeObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
First day of week
</td>
<td>
<b>Not Applicable</b>
</td>
<td>
<b>property:</b> firstDayOfWeek

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    firstDayOfWeek: 2
});
daterangeObject.appendTo('#element');
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
<b>Not Applicable</b>
</td>
<td>
<b>property:</b> strictMode

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    strictMode: true
});
daterangeObject.appendTo('#element');
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
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
    close: function (args) { /* code block*/}
});
```

</td>
<td>
<b>Event:</b> close

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    close: function (args: PreventableEventArgs) { /* code block*/}
});
daterangeObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Hide
</td>
<td>
<b>Method:</b> popupHide()

```ts
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
});
daterangeObj.popupHide();
```

</td>
<td>
<b>Method:</b> hide()

```ts
let daterangeObject: DateRangePicker = new DateRangePicker();
daterangeObject.appendTo('#element');
daterangeObject.show();
daterangeObject.hide();
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
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {
    open: function (args) { /* code block*/}
});
```

</td>
<td>
<b>Event:</b> open

```ts
let daterangeObject: DateRangePicker = new DateRangePicker({
    open: function (args: PreventableEventArgs) { /* code block*/}
});
daterangeObject.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Show
</td>
<td>
<b>Method:</b> popupShow()

```ts
var daterangeObj = new ej.DateRangeTimePicker($("#daterangepicker"), {});
daterangeObj.popupShow();
```

</td>
<td>
<b>Method:</b> show()

```ts
let daterangeObject: DateRangePicker = new DateRangePicker();
daterangeObject.appendTo('#element');
daterangeObject.show();
```

</td>
</tr>
</table>
