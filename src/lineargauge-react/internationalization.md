# Internationalization

<!-- markdownlint-disable MD013 -->

Linear gauge provide supports for internationalization for below gauge elements.

* Axis label.
* Tooltip

For more information about number and date formatter you can refer
[`internationalization`](http://ej2.syncfusion.com/documentation/base/intl.html).

<!-- markdownlint-disable MD036 -->

**Globalization**

Globalization is the process of designing and developing an component that works in different cultures/locales. Internationalization library is used to globalize number in LinearGauge component
using [`format`](../api/linear-gauge/label/#format-string) property in [`labelStyle`](../api/linear-gauge/label/).

**Numeric Format**

In the below example axis labels are `globalized` to EUR.

{% tab template="linear-gauge/internationalization", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { LinearGaugeComponent, AxesDirective, AxisDirective } from '@syncfusion/ej2-react-lineargauge';

ReactDOM.render(
    <LinearGaugeComponent id='gauge'>
        <AxesDirective>
            <AxisDirective minimum={0} maximum={120} majorTicks={ { interval:10, height:10 } } minorTicks={ { interval:5, height:5 } } labelStyle={ { format: 'c' } } >
            </AxisDirective>
        </AxesDirective>
    </LinearGaugeComponent>,document.getElementById('gauge'));

```

{% endtab %}