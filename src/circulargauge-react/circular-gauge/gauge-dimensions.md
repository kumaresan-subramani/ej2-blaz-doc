
# Circular Gauge Dimensions

## Size for Container

Circular gauge can render to its container size. You can set the size via inline or CSS as demonstrated below.

```html
    <div id='container'>
        <div id='circular-container' style="width:650px; height:350px;"></div>
    </div>
```

{% tab template="circulargauge/gauge-dimensions", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge'>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}
<!-- markdownlint-disable MD036 -->

## Size for Circular Gauge

<!-- markdownlint-disable MD036 -->

You can also set size for the gauge directly through [`width`](../api/circular-gauge/#width-string)
and [`height`](../api/circular-gauge/#height-string) properties.

**In Pixel**

You can set the size of the gauge in pixel as demonstrated below.

{% tab template="circulargauge/gauge-dimensions", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge' width='650' height='350'>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}

**In Percentage**

By setting value in percentage, gauge gets its dimension with respect to its container. For example, when
the height is ‘50%’, gauge renders to half of the container height.

{% tab template="circulargauge/gauge-dimensions", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge' width='80%' height='50%'>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}

>Note: When you do not specify the size, it takes `450px` as the height and window size as its width.