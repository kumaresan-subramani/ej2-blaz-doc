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

```javascript
$("#daterangepicker").ejDateRangePicker({value: "5/5/2014 - 6/6/2018"});
```

</td>
<td>
<b>property:</b> value

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({
    value : [new Date("5/5/2019"), new Date("6/6/2019")]
});
daterangepicker.appendTo('#element');
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
$("#daterangepicker").ejDateRangePicker({dateFormat: "dd/MM/yyyy"});
```

</td>
<td>
<b>property:</b> format

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({
    format: 'dd\'\/\'MMM\'\/\'yy hh:mm a',
    startDate: new Date("11/9/2017"),
    endDate: new Date("11/21/2017")
});
daterangepicker.appendTo('#element');
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
$("#daterangepicker").ejDateRangePicker({minDate: new Date("1/1/2017")});
```

</td>
<td>
<b>property:</b> min

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({min: new Date("1/1/2017")});daterangepicker.appendTo('#element');
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
$("#daterangepicker").ejDateRangePicker({maxDate: new Date("1/1/2017")});
```

</td>
<td>
<b>property:</b> max

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({max: new Date("1/1/2017")});daterangepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Start date
</td>
<td>
<b>property:</b> startDate

```javascript
$("#daterangepicker").ejDateRangePicker({startDate : new Date("5/30/2015")});
```

</td>
<td>
<b>property:</b> startDate

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({startDate: new Date("11/9/2017")});daterangepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
End date
</td>
<td>
<b>property:</b> endDate

```javascript
$("#daterangepicker").ejDateRangePicker({endDate: new Date("5/1/2013")});
```

</td>
<td>
<b>property:</b> endDate

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({endDate: new Date("11/21/2017")});daterangepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Preset ranges
</td>
<td>
<b>property:</b> ranges

```javascript
$("#daterangepicker").ejDateRangePicker({
    ranges: [
            { label: "Today", range: [new Date(), new Date()] },
            { label: "Last 1 Week", range: [new Date(new Date().setDate(new Date().getDate() - 7)), new Date()] },
            { label: "Last 1 Month", range: [new Date(new Date().setMonth(new Date().getMonth() - 1)), new Date()] },
            { label: "Last 2 Month", range: [new Date(new Date().setMonth(new Date().getMonth() - 2)), new Date()] },
        ],
});
```

</td>
<td>
<b>property:</b> presets

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({
    presets: [ { label: 'Today', start: new Date(), end: new Date() }, { label: 'This Month',
    start: new Date(new Date().setDate(1)), end: new Date() }, { label: 'Last Month', start: new
    Date(new Date(new Date().setMonth(new Date().getMonth() - 1)).setDate(1)), end: new Date() },
    { label: 'Last Year', start: new Date(new Date().getFullYear() - 1, 0, 1), end: new Date() },]
});
daterangepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Add ranges
</td>
<td>
<b>Method:</b> addRanges()

```javascript
$("#daterangepicker").ejDateRangePicker();
var dateObj = $("#daterangepicker").data("ejDateRangePicker");
dateObj.addRanges("new Range", [new Date("11/12/2019"),new Date("11/12/2021")] );
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

```javascript
$("#daterangepicker").ejDateRangePicker();
var dateObj = $("#daterangepicker").data("ejDateRangePicker");
dateObj.clearRanges();
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

```javascript
$("#daterangepicker").ejDateRangePicker();
var dateObj = $("#daterangepicker").data("ejDateRangePicker");
dateObj.getSelectedRange();
```

</td>
<td>
<b>Method:</b> getSelectedRange()

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({
    startDate: new Date("11/9/2017"),
    endDate: new Date("11/21/2017")
});
daterangepicker.appendTo('#element');
daterangepicker.getSelectedRange();
```

</td>
</tr>
<tr>
<td>
Set date range
</td>
<td>
<b>Method:</b> setRange()

```javascript
$("#daterangepicker").ejDateRangePicker();
var dateObj = $("#daterangepicker").data("ejDateRangePicker");
dateObj.setRange([new Date("11/12/2011"), new Date("11/12/2019")]);
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
<b>Can be achieved by:</b>

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({renderDayCell: onRenderCell});daterangepicker.appendTo('#element');
function onRenderCell(args){
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
$("#daterangepicker").ejDateRangePicker({cssClass: "gradient-lime"});
```

</td>
<td>
<b>property:</b> cssClass

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({cssClass:"customCSS"});daterangepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Enable/Disable DateRangePicker with TimePicker
</td>
<td>
<b>property:</b> enableTimePicker

```javascript
$("#daterangepicker").ejDateRangePicker({enableTimePicker: true});
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

```javascript
$("#daterangepicker").ejDateRangePicker({timeFormat: "HH:mm"});
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

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({minDays: 5});
daterangepicker.appendTo('#element');
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

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({maxDays: 10});
daterangepicker.appendTo('#element');
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
$("#daterangepicker").ejDateRangePicker({ buttonText : {reset: "Reset", cancel: "Cancel", apply: "Apply"}});
```

</td>
<td>
<b>Can be achieved by:</b>

```javascript
L10n.load({  'en': {'daterangepicker': { applyText: 'Apply'}  }});
var daterangepicker = new ej.calendars.DateRangePicker({ locale: 'en'});
daterangepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Show/hide the popup button
</td>
<td>
<b>property:</b> showPopupButton

```javascript
$("#daterangepicker").ejDateRangePicker({showPopupButton: false});
```

</td>
<td>
<b>Can be achieved by:</b>

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({focus: onFocus});
daterangepicker.appendTo('#element');
function onFocus(args) {
    daterangepicker.show();
}
```

```css
.e-control-wrapper .e-input-group-icon.e-range-icon {display: none;}
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
$("#daterangepicker").ejDateRangePicker({showRoundedCorner: true});
```

</td>
<td>
<b>Can be achieved by:</b>

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({cssClass: 'e-custom-style'});daterangepicker.appendTo('#element');
```

```css
.e-control-wrapper.e-custom-style.e-date-range-wrapper.e-input-group { border-radius: 4px;}
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

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({ focus: onFocus });
daterangepicker.appendTo('#element');
function onFocus(args) {/* code block */}
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

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({blur: onBlur});
daterangepicker.appendTo('#element');
function onBlur(args) {/* code block */}
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
var daterangepicker = new ej.calendars.DateRangePicker({ value: new Date()});daterangepicker.appendTo('#element');
daterangepicker.focusIn();
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
var daterangepicker = new ej.calendars.DateRangePicker({value: new Date()});daterangepicker.appendTo('#element');
daterangepicker.focusOut();
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

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({enableRtl: true});daterangepicker.appendTo('#element');
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
Enable/Disable the Persistence
</td>
<td>
<b>property:</b> enablePersistence

```javascript
$("#daterangepicker").ejDateRangePicker({enablePersistence: true});
```

</td>
<td>
<b>property:</b> enablePersistence

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({
    enablePersistence: true,
    startDate: new Date("11/9/2017"),
    endDate: new Date("11/21/2017")
});
daterangepicker.appendTo('#element');
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
$("#daterangepicker").ejDateRangePicker({width: 200});
```

</td>
<td>
<b>property:</b> width

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({width: 200});
daterangepicker.appendTo('#element');
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

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({readonly:true});
daterangepicker.appendTo('#element');
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
var daterangepicker = new ej.calendars.DateRangePicker({showClearButton: false});daterangepicker.appendTo('#element');
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
$("#daterangepicker").ejDateRangePicker({height: 35});
```

</td>
<td>
<b>Can be achieved by:</b>

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({cssClass:"e-custom-style"});daterangepicker.appendTo('#element');
```

```css
.e-control-wrapper.e-custom-style.e-date-range-wrapper.e-input-group {height: 35px;}
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

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({weekNumber: true});daterangepicker.appendTo('#element');
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
$("#daterangepicker").ejDateRangePicker({watermarkText: "Enter dateRange"});
```

</td>
<td>
<b>property:</b> placeholder

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({placeholder: 'Enter dateRange'});daterangepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Enable/Disable
</td>
<td>
<b>property:</b> enabled

```javascript
$("#daterangepicker").ejDateRangePicker({enabled: false});
```

</td>
<td>
<b>property:</b> enabled

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({enabled: false});
daterangepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Disable the DateRangePicker
</td>
<td>
<b>Method:</b> disable()

```javascript
$("#daterangepicker").ejDateRangePicker();
var dateObj = $("#daterangepicker").data("ejDateRangePicker");
dateObj.disable();
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

```javascript
$("#daterangepicker").ejDateRangePicker();
var dateObj = $("#daterangepicker").data("ejDateRangePicker");
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
$("#daterangepicker").ejDateRangePicker({allowEdit: false});
```

</td>
<td>
<b>property:</b> allowEdit

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({allowEdit: false});daterangepicker.appendTo('#element');
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
var daterangepicker = new ej.calendars.DateRangePicker({
    placeholder: 'Enter date',
    floatLabelType: 'Auto'
});
daterangepicker.appendTo('#element');
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
var daterangepicker = new ej.calendars.DateRangePicker({zIndex: 100});
daterangepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Specify the date range separator
</td>
<td>
<b>property:</b> separator

```javascript
$("#daterangepicker").ejDateRangePicker({separator : "$"});
```

</td>
<td>
<b>property:</b> separator

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({separator : "$"});daterangepicker.appendTo('#element');
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
$("#daterangepicker").ejDateRangePicker({locale: "en-US"});
```

</td>
<td>
<b>property:</b> locale

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({locale: 'en'});
daterangepicker.appendTo('#element');
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

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({firstDayOfWeek: 2});daterangepicker.appendTo('#element');
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

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({strictMode: true});daterangepicker.appendTo('#element');
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
$("#daterangepicker").ejDateRangePicker({ close: function (args) {/* code block */}});
```

</td>
<td>
<b>Event:</b> close

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({
    close: function (args) {/* code block */}
});
daterangepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Hide
</td>
<td>
<b>Method:</b> popupHide()

```javascript
$("#daterangepicker").ejDateRangePicker();
var dateObj = $("#daterangepicker").data("ejDateRangePicker");
dateObj.popupHide();
```

</td>
<td>
<b>Method:</b> hide()

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({value: new Date()});daterangepicker.appendTo('#element');
daterangepicker.hide();
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
$("#daterangepicker").ejDateRangePicker({open: function (args) {/* code block */}});
```

</td>
<td>
<b>Event:</b> open

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({
    open: function (args) {/* code block */}
});
daterangepicker.appendTo('#element');
```

</td>
</tr>
<tr>
<td>
Show
</td>
<td>
<b>Method:</b> popupShow()

```javascript
$("#daterangepicker").ejDateRangePicker();
var dateObj = $("#daterangepicker").data("ejDateRangePicker");
dateObj.popupShow();
```

</td>
<td>
<b>Method:</b> show()

```javascript
var daterangepicker = new ej.calendars.DateRangePicker({value: new Date()});daterangepicker.appendTo('#element');
daterangepicker.show();
```

</td>
</tr>
</table>