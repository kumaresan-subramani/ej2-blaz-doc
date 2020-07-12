# Internationalization

Linear gauge provide supports for internationalization for below gauge elements.

* Axis label.
* Tooltip

For more information about number and date formatter you can refer
[`internationalization`](http://ej2.syncfusion.com/documentation/base/intl.html).

<!-- markdownlint-disable MD036 -->

**Globalization**

Globalization is the process of designing and developing an component that works in different cultures/locales. Internationalization library is used to globalize number in LinearGauge component
using [`format`](../api/linear-gauge/label/#format-string) property in [`labelStyle`](../api/linear-gauge/label).

**Numeric Format**

In the below example axis labels are `globalized` to EUR.

{% tab template= "linear-gauge/getting-started", sourceFiles="index.ts,index.html", es5Template="es5NumericFormat" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
import { loadCldr, setCulture, Ajax, setCurrencyCode } from '@syncfusion/ej2-base';
setCulture("de");
setCurrencyCode('EUR');
let gauge: LinearGauge = new LinearGauge({
    locale: "de",
      format:'c',
      axes: [{
        labelStyle: {
            format: 'c',
            font: {
              color: 'red'
            }
        }
    }]
}, '#element');

```

{% endtab %}