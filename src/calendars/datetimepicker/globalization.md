---
title: "Globalization"
component: "DateTimePicker"
description: "Learn about how to globalize the date time picker component and how to localize the culture related content."
---

# Globalization

Globalization is the combination of internalization and localization. You can adapt the component to
various languages by parsing and formatting the date or
number [`Internationalization`](../common/internationalization/), and also add culture specific customization and translation to the text [`localization`](../common/localization/).

By default, the date format, week, month, time format and meridian names are specific to the `American English` culture. It utilizes the
[`Essential JavaScript 2 Internationalization`](../common/internationalization/)
package to parse and format the date object based on the culture by using the official [`UNICODE CLDR`](http://cldr.unicode.org/)
JSON data.  It provides the `loadCldr` method to load culture specific CLDR JSON data. To use a different culture other
than `English`, follow the steps below:

* Install the `CLDR-Data` package by using the following command (installs all the CLDR JSON data). To
know more about CLDR-Data refer to the [`CLDR-Data`](http://cldr.unicode.org/index/cldr-spec/json) link.

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
        "@syncfusion/ej2-data": "syncfusion:ej2-data/dist/ej2-data.umd.min.js",
        "@syncfusion/ej2-inputs": "syncfusion:ej2-inputs/dist/ej2-inputs.umd.min.js",
        "@syncfusion/ej2-splitbuttons": "syncfusion:ej2-splitbuttons/dist/ej2-splitbuttons.umd.min.js",
        "@syncfusion/ej2-popups": "syncfusion:ej2-popups/dist/ej2-popups.umd.min.js",
        "@syncfusion/ej2-lists": "syncfusion:ej2-lists/dist/ej2-lists.umd.min.js",
        "@syncfusion/ej2-data": "syncfusion:ej2-data/dist/ej2-data.umd.min.js",
        "@syncfusion/ej2-buttons": "syncfusion:ej2-buttons/dist/ej2-buttons.umd.min.js",
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

* Use the [`loadCldr`](../common/internationalization#installing-cldr-data) method to load the culture specific CLDR JSON data from the installed location to `app.ts` file.

* DateTimePicker displayed `Sunday` as the first day of week based on default culture ("en-US"). If you want to display the DateTimePicker with loaded culture's first day of week, you need to import `weekdata.json` file from the `cldr-data/suppemental` as given in the code example.

```typescript

import { loadCldr } from '@syncfusion/ej2-base';

declare var require: any;

loadCldr(
    require('cldr-data/main/de/numbers.json'),
    require('cldr-data/main/de/ca-gregorian.json'),
    require('cldr-data/main/de/numbers.json'),
    require('cldr-data/supplemental/numberingSystems.json'),
    require('cldr-data/main/de/timeZoneNames.json'),
    require('cldr-data/supplemental/weekdata.json') // To load the culture based first day of week
);
```

> The `Localization` library allows you to localize default text content of the DateTimePicker. The DateTimePicker component has static text for  **today** feature that can be changed to other cultures (Arabic, Deutsch, French, etc.) by defining the
[`locale`](../api/datetimepicker#locale) value and translation object.

Locale keywords |Text
-----|-----
today | Name of the button to choose Today date.
placeholder | Hint to describe expected value in input element.

* Before changing to a culture other than `English`, ensure that locale text for the concerned culture is loaded through `load` method of
[L10n](../api/base/l10n#load) class.

```typescript

//Load the L10n, loadCldr from ej2-base
import { loadCldr, L10n } from '@syncfusion/ej2-base';

//load the locale object to set the localized placeholder value
L10n.load({
    'de': {
        'datetimepicker': {
            placeholder: 'Wählen Sie ein Datum und eine Uhrzeit aus',
            today:'heute'
        }
    }
});
```

* Set the culture by using the
[`locale`](../api/datetimepicker#locale)
property. In the following code example, the DateTimePicker is initialized
in `German` culture with
corresponding localized text.

The following example demonstrates the DateTimePicker in `German` culture.

{% tab template="datetimepicker/globalization", isDefaultActive = "true",sourceFiles="app.ts,index.html",es5Template="datetimepicker-globalization-template" %}

```typescript
import { DateTimePicker } from '@syncfusion/ej2-calendars';
//Load the L10n, loadCldr from ej2-base
import { loadCldr, L10n } from '@syncfusion/ej2-base';
//load the CLDR data files.
import * as numberingSystems from './numberingSystems.json';
import * as gregorian from './ca-gregorian.json';
import * as numbers from './numbers.json';
import * as detimeZoneNames from './timeZoneNames.json';
import { enableRipple } from '@syncfusion/ej2-base';

loadCldr(numberingSystems, gregorian, numbers, detimeZoneNames);
L10n.load({
    'de': {
        'datetimepicker': {
            placeholder:'Wählen Sie ein Datum und eine Uhrzeit aus',
            today:'heute'
        }
    }
});

// creates the simple DateTimePicker component with de culture
let datetimeObject: DateTimePicker = new DateTimePicker({
    // sets the locale property.
    locale: 'de',
    value: new Date("12/11/2017 1:00 AM"),
});
datetimeObject.appendTo('#element');
```

{% endtab %}

## Right-To-Left

The DateTimePicker supports RTL (right-to-left) functionality for languages like Arabic and Hebrew to displays
the text in the right-to-left direction. Use
[`enableRtl`](../api/datetimepicker#enablertl)
property to set the RTL direction.
The following code example initialize the DateTimePicker component in `Arabic` culture and
also explains how to set the localized text to
the placeholder using
`load` method of
[L10n](../api/base/l10n#load) class.

{% tab template="datetimepicker/rtl", isDefaultActive = "true",sourceFiles="app.ts,index.html",es5Template="datetimepicker-rtl-template" %}

```typescript

import { DateTimePicker } from '@syncfusion/ej2-calendars';
//Load the L10n, loadCldr from ej2-base
import { loadCldr, L10n } from '@syncfusion/ej2-base';
//load the CLDR data files.
import * as numberingSystems from './numberingSystems.json';
import * as gregorian from './ca-gregorian.json';
import * as numbers from './numbers.json';
import * as detimeZoneNames from './timeZoneNames.json';
import { enableRipple } from '@syncfusion/ej2-base';

loadCldr(numberingSystems, gregorian, numbers, detimeZoneNames);

L10n.load({
    'ar': {
        'datetimepicker': {
            placeholder: 'حدد التاريخ والوقت',
            today: 'اليوم'
        }
    }
});

// creates the simple DateTimePicker component
let datetimeobject: DateTimePicker = new DateTimePicker({
    //sets the locale
    locale: 'ar',
    //sets the enableRtl
    enableRtl: true,
});
datetimeobject.appendTo('#element');
```

{% endtab %}
