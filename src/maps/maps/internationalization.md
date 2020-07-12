# Internationalization

Maps provides support for internationalization for the below elements.

* Datalabel
* Tooltip

For more information about number and date formatter you can refer
[`internationalization`](http://ej2.syncfusion.com/documentation/base/intl.html).

<!-- markdownlint-disable MD036 -->
**Globalization**

Globalization is the process of designing and developing an component that works in different
cultures/locales. Internationalization library is used to globalize number, date, time values in
Maps component using [`format`] property in the maps model.

**Numeric Format**

In the below example tooltip is globalized to Deutsch culture.

```typescript
import { Maps } from '@syncfusion/ej2-maps';
import { world_map } from './world-map.ts';
import { setCulture } from '@syncfusion/ej2-base';
setCulture('de');
let maps: Maps = new Maps({
    format: 'c',
    layers: [
         {
            shapeData: world_map,
            dataSource: [{  "Country": "China", "Membership": "Permanent"},
            {"Country": "France","Membership": "Permanent" },
            { "Country": "Russia","Membership": "Permanent"},
            {"Country": "Kazakhstan","Membership": "Non-Permanent"},
            { "Country": "Poland","Membership": "Non-Permanent"},
            {"Country": "Sweden","Membership": "Non-Permanent"}],
            shapePropertyPath: 'name',
            shapeDataPath: 'Country'
            shapeSettings: {
                colorValuePath: 'Membership',
                colorMapping: [
                {
                    value: 'Permanent', color: '#D84444'
                },
                {
                    value: 'Non-Permanent', color: '#316DB5'
                }]
            }
        }
    ]
});
maps.appendTo('#element');
```