
# Circular Gauge Dimensions

## Size for Container

Circular gauge can render to its container size. You can set the size via inline or CSS as demonstrated below.

```html
    <div id='container'>
        <div id='element' style="width:650px; height:350px;"></div>
    </div>
```

{% tab template= "circular-gauge/gauge-dimensions", sourceFiles="index.ts,index.html", es5Template="es5Size" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({}, '#element');

```

{% endtab %}
<!-- markdownlint-disable MD036 -->

## Size for Circular Gauge

<!-- markdownlint-disable MD036 -->

You can also set size for the gauge directly through [`width`](../api/circular-gauge#width-string) and [`height`](../api/circular-gauge#height-string) properties.

**In Pixel**

You can set the size of the gauge in pixel as demonstrated below.

{% tab template= "circular-gauge/gauge-dimensions", sourceFiles="index.ts,index.html", es5Template="es5SizeInPixel" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    // Width and height for gauge in pixel
    width: '650', height: '350'
}, '#element');

```

{% endtab %}

**In Percentage**

By setting value in percentage, gauge gets its dimension with respect to its container. For example, when
the height is ‘50%’, gauge renders to half of the container height.

{% tab template= "circular-gauge/gauge-dimensions", sourceFiles="index.ts,index.html", es5Template="es5SizeInPercentage" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    // Width and height for gauge in percentage
    width: '80%', height: '50%'
}, '#element');

```

{% endtab %}

>Note: When you do not specify the size, it takes `450px` as the height and window size as its width.