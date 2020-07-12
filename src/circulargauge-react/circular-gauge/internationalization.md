# Internationalization

Circular gauge provide supports for internationalization in `Axis label` and `Tooltip` elements.

For more information about number formatter you can refer
[`internationalization`](http://ej2.syncfusion.com/documentation/base/intl.html).

<!-- markdownlint-disable MD036 -->
**Globalization**

Globalization is the process of designing and developing a component that works in different cultures/locales.
Internationalization library is used to globalize number in CircularGauge component
using [`format`](../api/circular-gauge/label/#format-string) property in [`labelStyle`](../api/circular-gauge/label/).

<!-- markdownlint-disable MD036 -->
**Numeric Format**

In the below example axis labels are `globalized` to EUR.

{% tab template="circulargauge/getting-started", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, AxesDirective, AxisDirective } from '@syncfusion/ej2-react-circulargauge';
import { loadCldr, L10n, setCulture, setCurrencyCode } from '@syncfusion/ej2-base';
setCulture('de');
setCurrencyCode('EUR');
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge'>
    <AxesDirective>
      <AxisDirective labelStyle = {{
            format: 'c'
        }}>
      </AxisDirective>
    </AxesDirective>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}