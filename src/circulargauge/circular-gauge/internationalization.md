# Internationalization

Circular gauge provide supports for internationalization for below gauge elements.

* Axis label.
* Tooltip.

For more information about number formatter you can refer
[`internationalization`](http://ej2.syncfusion.com/documentation/base/intl.html).

<!-- markdownlint-disable MD036 -->
**Globalization**

Globalization is the process of designing and developing a component that works in different cultures/locales.
Internationalization library is used to globalize number in CircularGauge component
using [`format`](../api/circular-gauge/label#format-string) property in [`labelStyle`](../api/circular-gauge/label).

<!-- markdownlint-disable MD036 -->
**Numeric Format**

In the below example axis labels are `globalized` to EUR.

{% tab template= "circular-gauge/gauge-axes", sourceFiles="index.ts,index.html", es5Template="es5NumericFormat" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
import { loadCldr, L10n, setCulture, setCurrencyCode } from '@syncfusion/ej2-base';
setCulture('de');
setCurrencyCode('EUR');
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        labelStyle: {
            position: 'Inside',
            //Label format as currency
            format: 'c'
        }
    }]
}, '#element');

```

{% endtab %}