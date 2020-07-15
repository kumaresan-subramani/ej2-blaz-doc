---
title: "Globalization"
component: "Calendar"
description: "Learn about how to globalize the calendar component and how to localize the culture related content."
---

# Globalization

Globalization is the combination of  adapting the component to
various languages by means of parsing and formatting the date or
number [`Internationalization`](../common/internationalization/) and also by adding cultural specific customizations and translating the text [`localization`](../common/localization/)

By default, the Calendar date format, week, and month names are specific to American English culture. It uses the [`Essential JavaScript 2 Internationalization`](http://ej2.syncfusion.com/documentation/common/internationalization/)
package to parse and format date object based on the culture using the official [`UNICODE CLDR`](http://cldr.unicode.org/) JSON data. It provides the
[`loadCldr`](http://ej2.syncfusion.com/documentation/common/internationalization#loading-culture-data)
method to load the culture-specific CLDR JSON data.

All the Essential JS 2  component are specific to English culture ('en-US'). If you want to go with the different culture other than `English`, follow the below steps.

* Install the `CLDR-Data` package by using the below command (installs the CLDR JSON data). To know more about CLDR data, refer to the [`CLDR-Data`](http://cldr.unicode.org/index/cldr-spec/json) link.

```cmd
npm install cldr-data --save
```

 Once the package is installed, the culture-specific JSON data will be available in `\node_modules\cldr-data`.

* Now, import the installed CLDR JSON data to the `app.ts` file. To import JSON data, install the JSON plugin loader. In the example, SystemJS JSON plugin loader is used.

```sh
npm install systemjs-plugin-json --save-dev
```

* After it is installed, configure the `system.config.js`  settings as given below to map the `systemjs-plugin-json` loader.

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
        "@syncfusion/ej2-buttons": "syncfusion:ej2-buttons/dist/ej2-buttons.umd.min.js",
        "@syncfusion/ej2-splitbuttons": "syncfusion:ej2-splitbuttons/dist/ej2-splitbuttons.umd.min.js",
        "@syncfusion/ej2-lists": "syncfusion:ej2-lists/dist/ej2-lists.umd.min.js",
        "@syncfusion/ej2-popups": "syncfusion:ej2-popups/dist/ej2-popups.umd.min.js",
        "@syncfusion/ej2-calendars": "syncfusion:ej2-calendars/dist/ej2-calendars.umd.min.js",
        "cldr-data": 'npm:cldr-data',
        //systemjs-plugin-json loader package mapping
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

* Now, use the [`loadCldr`](http://ej2.syncfusion.com/documentation/common/internationalization#cldr-data-dependencies)
method to load the culture-specific CLDR JSON data from the installed location to `app.ts` file.

* Calendar displayed `Sunday` as the first day of week based on default culture ("en-US"). If you want to display the Calendar with loaded culture's first day of week, you need to import `weekdata.json` file from the `cldr-data/suppemental` as given in the code example.

```typescript
//import the loadCldr from ej2-base
import { loadCldr } from '@syncfusion/ej2-base';

declare var require: any;

loadCldr(
    require('cldr-data/supplemental/numberingSystems.json'),
    require('cldr-data/main/de/ca-gregorian.json'),
    require('cldr-data/main/de/numbers.json'),
    require('cldr-data/main/de/timeZoneNames.json'),
    require('cldr-data/supplemental/weekdata.json')); // To load the culture based first day of week
```

> The [`Localization`](../api/base/l10n) library allows you to localize default text content of the Calendar. The Calendar component has static text for  **today** feature that can be changed to other cultures (Arabic, Deutsch, French, etc.) by defining the
[`locale`](../api/calendar#locale) value and translation object.

Locale keywords |Text
-----|-----
today | Name of the button to choose Today date.

* Before changing the culture other than `English`, ensure that locale text for the concerned culture is loaded through `load` method of
[L10n](../api/base/l10n#load) class.

```typescript

//Load the L10n from ej2-base
import { L10n } from '@syncfusion/ej2-base';

//load the locale object to set the localized placeholder value
L10n.load({
    'de': {
        'calendar': { today: 'heute'}
    }
});
```

* Set the culture by using the [`locale`](../api/calendar#locale)
property. The code example initializes the Calendar component in the `German` culture.

```typescript
import { Calendar } from '@syncfusion/ej2-calendars';
//import the loadCldr from ej2-base
import { loadCldr, L10n } from '@syncfusion/ej2-base';

declare var require: any;

loadCldr(
    require('cldr-data/supplemental/numberingSystems.json'),
    require('cldr-data/main/de/ca-gregorian.json'),
    require('cldr-data/main/de/numbers.json'));
    require('cldr-data/main/de/timeZoneNames.json'));

L10n.load({
    'de': {
        'calendar': { today: 'heute' }
    }
});

let calendarObject: Calendar = new Calendar({
    //sets the locale.
    locale: 'de'
});
calendarObject.appendTo('#element');
```

The following example displays the Calendar in `German` culture.

{% tab template="calendar/internationalization", isDefaultActive = "true", sourceFiles="index.html,styles.css",es5Template="calendar-internationalization-template" %}

```typescript
import { Calendar } from '@syncfusion/ej2-calendars';
//import the loadCldr from ej2-base
import { loadCldr, L10n } from '@syncfusion/ej2-base';
//load the CLDR JSON data files.
import * as numberingSystems from './numberingSystems.json';
import * as gregorian from './ca-gregorian.json';
import * as numbers from './numbers.json';
import * as timeZoneNames from './timeZoneNames.json';

loadCldr(numberingSystems, gregorian, numbers, timeZoneNames);

L10n.load({
    'de': {
        'calendar': {
            today: 'heute'
        }
    }

});

//creates a calendar with German culture.
let calendarObject: Calendar = new Calendar({ locale: 'de' });
calendarObject.appendTo('#element');
```

{% endtab %}

## Right-to-left

The Calendar supports right-to-left functionality for languages like Arabic,  Hebrew, etc. to display text in the right-to-left direction. Use
[`enableRtl`](../api/calendar#enablertl) property to set the RTL direction.

The following code example initializes the Calendar component in `Arabic` culture.

```typescript
import { Calendar } from '@syncfusion/ej2-calendars';
//import the loadCldr from ej2-base
import { loadCldr, L10n } from '@syncfusion/ej2-base';

declare var require: any;

loadCldr(
    require('cldr-data/supplemental/numberingSystems.json'),
    require('cldr-data/main/ar/ca-gregorian.json'),
    require('cldr-data/main/ar/numbers.json'));
    require('cldr-data/main/ar/timeZoneNames.json'));

L10n.load({
    'ar': {
        'calendar': {
            today: 'اليوم'
        }
    }

});

let calendarObject: Calendar = new Calendar({
    //sets the locale.
    locale: 'ar'
});
calendarObject.appendTo('#element');
```

The following example displays the Calendar in `Arabic`
culture in the right-to-left direction.

{% tab template="calendar/rtl", sourceFiles="index.html,styles.css",es5Template="calendar-rtl-template" %}

```typescript
//imports the loadCldr from ej2-base
import { loadCldr, L10n } from '@syncfusion/ej2-base';
import { Calendar } from '@syncfusion/ej2-calendars';
//loads the CLDR data files.
import * as numberingSystems from './numberingSystems.json';
import * as gregorian from './ca-gregorian.json';
import * as numbers from './numbers.json';
import * as timeZoneNames from './timeZoneNames.json';

loadCldr(numberingSystems, gregorian, numbers, timeZoneNames);

L10n.load({
    'ar': {
        'calendar': { today: 'اليوم'}
    }
});

//creates the calendar with Arabic culture.
let calendarObject: Calendar = new Calendar({
    //sets the locale
    locale: 'ar',
    //sets the enableRtl
    enableRtl: true
});
calendarObject.appendTo('#element');
```

{% endtab %}