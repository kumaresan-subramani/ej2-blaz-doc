
# Linear Gauge Dimensions

<!-- markdownlint-disable MD013 -->

## Size for Container

Linear gauge can render to its container size. You can set the size via inline or CSS as demonstrated below.

```html
 <div id="charts" style="width:650px; height:350px"></div>
```

{% tab template="linear-gauge/dimensions", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { LinearGaugeComponent } from '@syncfusion/ej2-react-lineargauge';

ReactDOM.render(
    <LinearGaugeComponent id='gauge'>
    </LinearGaugeComponent>,document.getElementById('gauge'));

```

{% endtab %}

<!-- markdownlint-disable MD036 -->

## Size for Linear Gauge

You can also set size for linear gauge directly through [`width`](../api/linear-gauge/linearGaugeModel/#width-string) and [`height`](../api/linear-gauge/linearGaugeModel/#height-string) properties.

**In Pixel**

You can set the size of lineargauge in pixel as demonstrated below.

{% tab template="linear-gauge/dimensions", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { LinearGaugeComponent } from '@syncfusion/ej2-react-lineargauge';

ReactDOM.render(
    <LinearGaugeComponent id='gauge' width='650px' height='350px'>
    </LinearGaugeComponent>,document.getElementById('gauge'));

```

{% endtab %}

**In Percentage**

By setting value in percentage, linear gauge gets its dimension with respect to its container. For example, when the height is ‘50%’, linear gauge renders to half of the container height.

```html
    <div id='container'>
        <div id='element' style="width:1000px; height:600px;"></div>
    </div>
```

{% tab template="linear-gauge/dimensions", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { LinearGaugeComponent } from '@syncfusion/ej2-react-lineargauge';

ReactDOM.render(
    <LinearGaugeComponent id='gauge' width='100%' height='50%'>
    </LinearGaugeComponent>,document.getElementById('gauge'));

```

{% endtab %}

>Note: When you do not specify the size, it takes `450px` as the height and window size as its width.