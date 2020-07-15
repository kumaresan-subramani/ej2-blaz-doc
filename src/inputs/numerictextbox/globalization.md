---
title: "Globalization"
component: "NumericTextBox"
description: "Globalization support in numeric textbox"
---

# Globalization

## Localization

[`Localization`](../common/localization/) library allows users to localize the default text contents
of the NumericTextBox to different cultures using the [`locale`](../api/numerictextbox#locale) property.
In NumericTextBox, spin buttons title for the tooltip will be localized based on the culture.

| Locale key | en-US (default)  |
|------|------|
| incrementTitle |  Increment value |
| decrementTitle |  Decrement value |

### Loading translations

To load translation object in your application use `load` function of `L10n` class.

The below example demonstrates the NumericTextBox in `German` culture with the spin buttons tooltip.

{% tab template="numeric-textbox/getting-started", sourceFiles="app.ts,index.html,styles.css", es5Template="numeric-localization-template" %}

```typescript

import { NumericTextBox } from '@syncfusion/ej2-inputs';
import { L10n } from '@syncfusion/ej2-base';

// Load `German` culture to override spin buttons tooltip text
L10n.load({
    'de': {
        'numerictextbox': {
            incrementTitle: 'Wert erhöhen', decrementTitle: 'Dekrementwert'
        }
    },

});

let numeric: NumericTextBox = new NumericTextBox({
    // sets `German` culture using the culture value 'de'
    locale: 'de',
    // sets value to the NumericTextBox
    value: 10
});

// renders initialized NumericTextBox
numeric.appendTo('#numeric');

```

{% endtab %}

## Internationalization

Internationalization library provides support for formatting and parsing the number by using the
official [Unicode CLDR](http://cldr.unicode.org/) JSON data and also provides the
`loadCldr` method to load the culture specific CLDR JSON data. The NumericTextBox comes with built-in
internationalization support to adapt based on culture. For more information about internationalization,
refer to this [link](../common/internationalization/).

By default, all the Essential JS 2  component are specific to English culture ('en-US').
If you want to go with the different culture other than `English`, follow the below steps.

* Install the `CLDR-Data` package by using the below command (it installs the CLDR JSON data). For more information about CLDR-Data,
refer to this [link](http://cldr.unicode.org/index/cldr-spec/json).

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
        'syncfusion:': 'npm:@syncfusion/'
    },
    map: {
        app: 'app',

        //Syncfusion packages mapping
        "@syncfusion/ej2-base": "syncfusion:ej2-base/dist/ej2-base.umd.min.js",
        "@syncfusion/ej2-inputs": "syncfusion:ej2-inputs/dist/ej2-inputs.umd.min.js",
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

* Now import the required culture
from the installed location to `app.ts` file as like the below code snippets.

```typescript
declare var require: any;

loadCldr(
        require('cldr-data/main/de/numbers.json'),
        require('cldr-data/main/de/currencies.json'),
        require('cldr-data/supplemental/numberingSystems.json'),
        require('cldr-data/supplemental/currencyData.json')
    );
```

* Set the culture by using the [`locale`](../api/numerictextbox#locale) property.

The below example demonstrates the NumericTextBox in `German` culture with the `EUR` currency format.

{% tab template="numeric-textbox/internationalization" , isDefaultActive = "true" , sourceFiles="app.ts,index.html,styles.css", es5Template="numeric-internationalization-template" %}

```typescript

import { NumericTextBox } from '@syncfusion/ej2-inputs';
import { loadCldr,L10n } from '@syncfusion/ej2-base';
// Here we have referred local json files for preview purpose
import * as numberingSystems from './numberingSystems.json';
import * as currencyData from './currencyData.json';
import * as numbers from './numbers.json';
import * as currencies from './currencies.json';

loadCldr(numberingSystems, currencyData, numbers, currencies);

L10n.load({
    'de': {
      'numerictextbox': { incrementTitle: 'Wert erhöhen', decrementTitle: 'Dekrementwert'}
    }
});

let currency: NumericTextBox = new NumericTextBox({
    // sets `German` culture using the culture value 'de'
    locale: 'de',
    // sets the 'EUR' currency format
    currency: 'EUR',
    format: 'c2',
    value: 100,
 });

currency.appendTo('#numeric');

```

{% endtab %}

## Right to Left(RTL)

RTL provides an option to switch the text direction and layout of the NumericTextBox component from right to left. It improves the user experiences and accessibility for users who use right-to-left languages (Arabic, Farsi, Urdu, etc.). To enable RTL NumericTextBox, set the [`enableRtl`](../api/numerictextbox#enablertl) to true.

{% tab template="numeric-textbox/rtl" , isDefaultActive = "true" , sourceFiles="app.ts,index.html,styles.css", es5Template="numeric-rtl-template" %}

```typescript

import { NumericTextBox } from '@syncfusion/ej2-inputs';
import { loadCldr,L10n } from '@syncfusion/ej2-base';

L10n.load({
    'ar-AE': {
      'numerictextbox': { incrementTitle: 'قيمة الزيادة', decrementTitle: 'قيمة تناقص'}
    }
});

let currency: NumericTextBox = new NumericTextBox({
    // sets `Arabic` culture using the culture value 'ar-AE'
    locale: 'ar-AE',
    value: 100,
    placeholder: 'أدخل القيمة',
    enableRtl: true,
    floatLabelType: 'Auto'
 });

currency.appendTo('#numeric');

```

{% endtab %}
