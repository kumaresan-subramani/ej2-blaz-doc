---
title: "Globalization"
component: "DateRangePicker"
description: "Learn about how to globalize the date range picker component and how to localize the culture related content."
---

# Globalization

Globalization is the combination of internalization and localization. You can adapt the component to
various languages by parsing and formatting the date or
number (Internationalization), and also add culture specific customization and translation to the text
(Localization).

By default, DateRangePicker date format, week, and month names are specific to the English culture. It utilizes the
[`Essential JavaScript 2 Internationalization`](http://ej2.syncfusion.com/documentation/base/internationalization/)
package to parse and format the date object based on the culture by using the official [`UNICODE CLDR`](http://cldr.unicode.org/)
JSON data. It allows to load culture specific CLDR JSON data by using
`loadCldr`
method.

To use a different culture other than `English`, follow the below steps:

* Install the `CLDR-Data` package by using the below command (Installs the CLDR JSON data). To
know more about CLDR-Data refer to the
[`CLDR-Data`](http://cldr.unicode.org/index/cldr-spec/json) link.

```cmd
npm install cldr-data --save
```

 Once the package is installed, you can find the culture
specific JSON data under the location `\node_modules\cldr-data`.

* Import the installed CLDR JSON data into the `app.ts` file.
To import JSON data, install the JSON plugin loader. Here, The SystemJS JSON plugin loader is used.

```sh
npm install systemjs-plugin-json --save-dev
```

* After installation, configure the `system.config.js` configuration settings as given below to map the
`systemjs-plugin-json` loader.

```typescript
System.config({
    paths: {
        'npm:': './node_modules/',
        'syncfusion:': 'npm:@syncfusion/'

    },
    map: {
        app: 'app',

        //Syncfusion packages mapping
        "@syncfusion/ej2-base": "syncfusion:ej2-base/dist/ej2-base.umd.min.js",
        "@syncfusion/ej2-inputs": "syncfusion:ej2-inputs/dist/ej2-inputs.umd.min.js",
        "@syncfusion/ej2-popups": "syncfusion:ej2-popups/dist/ej2-popups.umd.min.js",
        "@syncfusion/ej2-lists": "syncfusion:ej2-lists/dist/ej2-lists.umd.min.js",
        "@syncfusion/ej2-data": "syncfusion:ej2-data/dist/ej2-data.umd.min.js",
        "@syncfusion/ej2-buttons": "syncfusion:ej2-buttons/dist/ej2-buttons.umd.min.js",
        "@syncfusion/ej2-splitbuttons": "syncfusion:ej2-splitbuttons/dist/ej2-splitbuttons.umd.min.js",
        "@syncfusion/ej2-calendars": "syncfusion:ej2-calendars/dist/ej2-calendars.umd.min.js",
        "cldr-data": 'npm:cldr-data',
        "plugin-json": "npm:systemjs-plugin-json/json.js"
    },
    meta: {
        '*.json': { loader: 'plugin-json' }
    },
    packages: {
        'app': { main: 'app', defaultExtension: 'js' },
        'cldr-data': { main: 'index.js', defaultExtension: 'js' }
    }
});

System.import('app');

```

* Use the `loadCldr` method to load the culture specific CLDR JSON data from the installed location to `app.ts` file.

* DateRangePicker displayed `Sunday` as the first day of week based on default culture ("en-US"). If you want to display the DateRangePicker with loaded culture's first day of week, you need to import `weekdata.json` file from the `cldr-data/suppemental` as given in the code example.

```typescript
declare var require: any;

loadCldr(
    require('cldr-data/main/de/numbers.json'),
    require('cldr-data/main/de/ca-gregorian.json'),
    require('cldr-data/main/de/numbers.json'),
    require('cldr-data/main/de/timeZoneNames.json'),
    require('cldr-data/supplemental/weekdata.json') // To load the culture based first day of week
);
```

> The `Localization` library allows you to localize default text content of the DateRangePicker. The DateRangePicker component has static text for  **today** feature that can be changed to other cultures (Arabic, Deutsch, French, etc.) by defining the
[`locale`](../api/daterangepicker#locale) value and translation object.

Locale keywords |Text
-----|-----
placeholder | Hint to describe expected value in input element.
startLabel | Label to represent the start date.
endLabel | Label to represent the end date.
applyText | Text present in the apply button.
cancelText | Text present in the cancel button.
selectedDays | Text to represent selected days.
days | Text represents days.
customRange | Text present in the custom range button in presets container.

* Before changing to a culture other than `English`, ensure that locale text for the concerned culture is loaded through `load` method of
[L10n](../api/base/l10n#load) class.

```typescript

//Load the L10n, loadCldr from ej2-base
import { loadCldr, L10n } from '@syncfusion/ej2-base';

//load the locale object to set the localized placeholder value
L10n.load({
    'de': {
        'daterangepicker': { placeholder: 'Wählen Sie ein Datum aus' }
    }
});
```

* Set the culture by using the
[`locale`](../api/daterangepicker#locale)
property. In the following code example, the DateRangePicker is initialized
in `German` culture with
corresponding localized text.

The following example demonstrates the DateRangePicker in `German` culture.

{% tab template="daterangepicker/globalization", isDefaultActive = "true",sourceFiles="app.ts,index.html",es5Template="daterangepicker-globalization-template" %}

```typescript
import { DateRangePicker } from '@syncfusion/ej2-calendars';
//Load the L10n, loadCldr from ej2-base
import { loadCldr, L10n } from '@syncfusion/ej2-base';
//load the CLDR data files.
import * as numberingSystems from './numberingSystems.json';
import * as gregorian from './ca-gregorian.json';
import * as numbers from './numbers.json';
import * as detimeZoneNames from './timeZoneNames.json';

loadCldr(numberingSystems, gregorian, numbers, detimeZoneNames);
L10n.load({
    'de': {
        'daterangepicker': {
         placeholder:'Wählen Sie einen Bereich aus',
         startLabel: 'Wählen Sie Startdatum',
         endLabel: 'Wählen Sie Enddatum',
         applyText: 'Sich bewerben',
         cancelText: 'Stornieren',
         selectedDays: 'Ausgewählte Tage',
         days: 'Tage',
         customRange: 'benutzerdefinierten Bereich'
        }
    }
});

// creates the simple DateRangePicker component with de culture
let daterangeObject: DateRangePicker = new DateRangePicker({
    // sets the locale property.
    locale: 'de',
    value: new Date(),
});
daterangeObject.appendTo('#element');
```

{% endtab %}

## Right-To-Left

The DateRangePicker supports RTL (right-to-left) functionality for languages like Arabic and Hebrew to displays
the text in the right-to-left direction. Use
[`enableRtl`](../api/daterangepicker#enablertl)
property to set the RTL direction.
The following code example initialize the DateRangePicker component in `Hebrew` culture and
also explains how to set the localized text to
the placeholder using
`load` method of
[L10n](../api/base/l10n#load) class.

{% tab template="daterangepicker/rtl" , sourceFiles="app.ts,index.html",es5Template="daterangepicker-rtl-template" %}

```typescript

import { loadCldr, L10n } from '@syncfusion/ej2-base';
import { DateRangePicker } from '@syncfusion/ej2-calendars';
import * as numberingSystems from './numberingSystems.json';
import * as gregorian from './ca-gregorian.json';
import * as numbers from './numbers.json';
import * as hetimeZoneNames from './timeZoneNames.json';

loadCldr(numberingSystems, gregorian, numbers, hetimeZoneNames);

L10n.load({
    'he': {
        'daterangepicker': {
            placeholder: 'בחר טווח'
            startLabel: 'תווית התחלה',
            endLabel: 'ח',
            applyText: 'להחיל טקסט',
            cancelText: 'בטל טקסט',
            selectedDays: 'ימים נבחרים',
            days: 'أימים',
            customRange: 'טווח מותאם אישית'
        }
    }
});

// creates the simple DateRangePicker component
let daterangeobject: DateRangePicker = new DateRangePicker({
    //sets the locale
    locale: 'he',
    //sets the enableRtl
    enableRtl: true,
});
daterangeobject.appendTo('#element');
```

{% endtab %}

## Customize the date format

Representation of start and end date strings can be customized to required format by using [`format`](../api/daterangepicker#format) property. By default, the format is based on the culture.
To know more about the date format standards, refer to the Internationalization Date Format section.
In the following sample, the date strings are formatted to `yyyy-MM-dd` and in between the string "to" is set as a [`separator`](../api/daterangepicker#separator).

{% tab template="daterangepicker/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html",es5Template="daterangepicker-format-template" %}

```typescript

import { DateRangePicker } from '@syncfusion/ej2-calendars';
// creates a daterangepicker with format property
let daterangeObject: DateRangePicker = new DateRangePicker({
    format:"yyyy-MM-dd",
    separator: "to",
    placeholder:"Select Range"

});
daterangeObject.appendTo('#element');

```

{% endtab %}