---
title: "Globalization"
component: "DatePicker"
description: "Learn about how to globalize the date picker component and how to localize the culture related content."
---

# Globalization

Globalization is the combination of  adapting the component to
various languages by means of parsing and formatting the date or
number [`Internationalization`](../common/internationalization/) and also by adding cultural specific customizations and translating the text [`localization`](../common/localization/)

By default, DatePicker date format, week and month names are specific to English culture. It utilizes the
[`Essential JavaScript 2 Internationalization`](../common/internationalization/)
package to parse and format the date object based on the culture by using the official [`UNICODE CLDR`](http://cldr.unicode.org/)
JSON data and it allows to load the culture specific CLDR JSON data by using
`loadCldr`
method

The DatePicker component supports only the Gregorian type of calendar.
All the Essential JS 2 component are specific to English culture ('en-US').
If you want to go with the different culture other than English, follow the below steps.

* Install the `CLDR-Data` package by using the below command (it installs the CLDR JSON data). To
know more about CLDR-Data refer the
[`CLDR-Data`](http://cldr.unicode.org/index/cldr-spec/json) link.

```cmd
npm install cldr-data --save
```

Once the package installed, you can find the culture
specific JSON data under the location `\node_modules\cldr-data`.

* Now import the installed CLDR JSON data into the `app.ts` file.
To import JSON data we need to install the JSON plugin loader. Here we have used the SystemJS JSON plugin loader.

```sh
npm install systemjs-plugin-json --save-dev
```

* Once installed, configure the `system.config.js` configuration settings as like below to map the
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
        "@syncfusion/ej2-data": "syncfusion:ej2-data/dist/ej2-data.umd.min.js",
        "@syncfusion/ej2-inputs": "syncfusion:ej2-inputs/dist/ej2-inputs.umd.min.js",
        "@syncfusion/ej2-popups": "syncfusion:ej2-popups/dist/ej2-popups.umd.min.js",
        "@syncfusion/ej2-buttons": "syncfusion:ej2-buttons/dist/ej2-buttons.umd.min.js",
        "@syncfusion/ej2-splitbuttons": "syncfusion:ej2-splitbuttons/dist/ej2-splitbuttons.umd.min.js",
        "@syncfusion/ej2-lists": "syncfusion:ej2-lists/dist/ej2-lists.umd.min.js",
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

* Now use the `loadCldr` method to load the culture specific CLDR JSON data from the installed location to `app.ts` file.

* DatePicker displayed `Sunday` as the first day of week based on default culture ("en-US"). If you want to display the DatePicker with loaded culture's first day of week, you need to import `weekdata.json` file from the `cldr-data/suppemental` as given in the code example.

```typescript
//Load the loadCldr from ej2-base
import { loadCldr } from '@syncfusion/ej2-base';

declare var require: any;

loadCldr(
    require('cldr-data/main/de/ca-gregorian.json'),
    require('cldr-data/main/de/numbers.json'),
    require('cldr-data/main/de/timeZoneNames.json'),
    require('cldr-data/supplemental/weekdata.json') // To load the culture based first day of week
    );
```

> The `Localization` library allows you to localize default text content of the DatePicker. The DatePicker component has static text for  **today** feature that can be changed to other cultures (Arabic, Deutsch, French, etc.) by defining the
[`locale`](../api/datepicker#locale) value and translation object.

Locale keywords |Text
-----|-----
today | Name of the button to choose Today date.
placeholder | Hint to describe expected value in input element.

* Before changing the culture other than `English`, ensure that locale text for the concerned culture is loaded through `load` method of
[L10n](../api/base/l10n#load) class.

```typescript

//Load the L10n from ej2-base
import { L10n } from '@syncfusion/ej2-base';

//load the locale object to set the localized placeholder value
L10n.load({
    'de': {
        'datepicker': { placeholder: 'Wählen Sie ein Datum aus',
         today:'heute'  }
    }
});
```

* Set the culture by using the
[`locale`](../api/datepicker#locale)
property. The below code example, initialize
the DatePicker component in `German` culture with
corresponding localized text.

```typescript
//Load the L10n from ej2-base
import { L10n } from '@syncfusion/ej2-base';
import { DatePicker } from '@syncfusion/ej2-calendars';

//load the locale object to set the localized placeholder value
L10n.load({
    'de': {
        'datepicker': { placeholder: 'Wählen Sie ein Datum aus',
         today:'heute' }
    }
});

let datepickerObject: DatePicker = new DatePicker({
    //sets the locale.
    locale: 'de'
});

datepickerObject.appendTo('#element');
```

The following example demonstrates the DatePicker in `German` culture.

{% tab template="datepicker/internationalization", isDefaultActive = "true",sourceFiles="app.ts,index.html",es5Template="datepicker-internationalization-template" %}

```typescript
import { DatePicker } from '@syncfusion/ej2-calendars';
//Load the L10n, loadCldr from ej2-base
import { loadCldr, L10n } from '@syncfusion/ej2-base';
//load the CLDR data files.
import * as numberingSystems from './numberingSystems.json';
import * as gregorian from './ca-gregorian.json';
import * as numbers from './numbers.json';
import * as timeZoneNames from './timeZoneNames.json';

loadCldr(numberingSystems, gregorian, numbers, timeZoneNames);
L10n.load({
    'de': {
        'datepicker': {
            placeholder: 'Wählen Sie ein Datum aus',
            today:'heute'
        }
    }
});

// creates the simple DatePicker component
let datepickerObject: DatePicker = new DatePicker({
    // sets the locale property.
    locale: 'de',
    value: new Date()
});
datepickerObject.appendTo('#element');
```

{% endtab %}

## Right-To-Left

The DatePicker supports right-to-left functionality for languages like Arabic, Hebrew to displays
the text in the right-to-left direction. Use
[`enableRtl`](../api/datepicker#enablertl)
property to set the RTL direction.

```typescript

import { DatePicker } from '@syncfusion/ej2-calendars';
//Load the L10n from ej2-base
import { L10n, loadCldr } from '@syncfusion/ej2-base';

declare var require: any;

loadCldr(
    require('cldr-data/supplemental/numberingSystems.json'),
    require('cldr-data/main/he/ca-gregorian.json'),
    require('cldr-data/main/he/numbers.json')
    require('cldr-data/main/he/timeZoneNames.json')
);

//load the locale object to set the localized placeholder value
L10n.load({
    'he': {
            'datepicker': { placeholder: 'הזן תאריך',
            today:'היום' }
          }
    });

// creates the datepicker with Hebrew culture.
let datepickerobject: DatePicker = new DatePicker({
    //sets the locale
    locale: 'he',
    value: new Date(),
    //sets the enableRtl
    enableRtl: true
});
datepickerobject.appendTo('#element');

```

The below code example demonstrates the DatePicker component in `Hebrew` culture and
also explains how to set the localized text to
the placeholder using
`load` method of
[L10n](../api/base/l10n#load) class.

{% tab template="datepicker/rtl" , sourceFiles="app.ts,index.html" ,
es5Template="datepicker-rtl-template"%}

```typescript

import { loadCldr, L10n } from '@syncfusion/ej2-base';
import { DatePicker } from '@syncfusion/ej2-calendars';
import * as numberingSystems from './numberingSystems.json';
import * as gregorian from './ca-gregorian.json';
import * as numbers from './numbers.json';
import * as timeZoneNames from './timeZoneNames.json';

loadCldr(numberingSystems, gregorian, numbers, timeZoneNames);

L10n.load({
    'he': {
        'datepicker': {
            placeholder: 'הזן תאריך',
            today:'היום'
        }
    }
});

// creates the simple DatePicker component
let datepickerObject: DatePicker = new DatePicker({
    //sets the locale
    locale: 'he',
    //sets the enableRtl
    enableRtl: true,
    //sets the value
    value: new Date()
});
datepickerObject.appendTo('#element');
```

{% endtab %}