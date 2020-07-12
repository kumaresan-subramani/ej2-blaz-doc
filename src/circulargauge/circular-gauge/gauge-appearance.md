# Appearance

## Gauge Title

Circular gauge can be given a title by using [`title`](../api/circular-gauge#title-string) property, to show the information about the gauge.
Title can be customized by using [`titleStyle`](../api/circular-gauge#titlestyle-fontmodel) property in gauge.

{% tab template= "circular-gauge/gauge-appearance", sourceFiles="index.ts,index.html", es5Template="es5Title" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    title: 'Speedometer',
    titleStyle: {
        color: '#27d5ff'
    }
}, '#element');

```

{% endtab %}

## Gauge Position

<!-- markdownlint-disable MD036 -->

Gauge can be positioned anywhere in the container with the help of
[`centerX`](../api/circular-gauge#centerx-string) and
[`centerY`](../api/circular-gauge#centery-string)
property and it accepts values either in percentage or in pixels.
The default value of the [`centerX`](../api/circular-gauge#centerx-string) and
[`centerY`](../api/circular-gauge#centery-string) property is 50%, which means gauge will get rendered to the centre of the container.

**In Pixel**

You can set the mid point of the gauge in pixel as demonstrated below,

{% tab template= "circular-gauge/gauge-appearance", sourceFiles="index.ts,index.html", es5Template="es5Pixel" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    centerX: '20',
    centerY: '20',
    axes: [{
        lineStyle: {
            width: 2,
            color: '#F8F8F8'
        },
        startAngle: 90,
        endAngle: 180
    }]
}, '#element');

```

{% endtab %}
<!-- markdownlint-disable MD036 -->

**In Percentage**

By setting the value in percentage, gauge gets its mid point with respect to its plot area.
For example, when the [`centerX`](../api/circular-gauge#centerx-string)
value as '0%' and [`centerY`](../api/circular-gauge#centery-string) value is ‘50%’, gauge will get positioned at the top left corner of the plot area.

{% tab template= "circular-gauge/gauge-appearance", sourceFiles="index.ts,index.html", es5Template="es5Percentage" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    centerX: '10%',
    centerY: '50%',
    axes: [{
        lineStyle: {
            width: 2,
            color: '#F8F8F8'
        },
        startAngle: 0,
        endAngle: 180
    }]
}, '#element');

```

{% endtab %}
<!-- markdownlint-disable MD036 -->

## Area Customization

**Customize the gauge background**

Using [`background`](../api/circular-gauge#background-string) and
[`border`](../api/circular-gauge#border-bordermodel) properties, you can change the background color and border of the circular gauge.

{% tab template= "circular-gauge/gauge-appearance", sourceFiles="index.ts,index.html", es5Template="es5Background" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    background: 'skyblue',
    //Customize the chart border and opacity
    border: {color: "#FF0000", width: 2},
     axes: [{
        radius: '90%',
        maximum: 120,
        startAngle: 230,
        endAngle: 130,
        majorTicks: {
            width: 1, color: '#8c8c8c'
        },
        lineStyle: { width: 2 },
        minorTicks: {
            width: 1, color: '#8c8c8c'
        },
        pointers: [{
            value: 60,
            radius: '60%'
        }],
        ranges: [{
            start: 0,
            end: 70,
            radius: '110%',
            strokeWidth: 10
        }, {
            start: 70,
            end: 110,
            radius: '110%',
            strokeWidth: 10
        }, {
            start: 110,
            end: 120,
            radius: '110%',
            strokeWidth: 10
        }]
    }]
}, '#element');

```

{% endtab %}

**Gauge Margin**

You can set margin for gauge from its container through
[`margin`](../api/circular-gauge#margin-marginmodel) property.

{% tab template= "circular-gauge/gauge-appearance", sourceFiles="index.ts,index.html", es5Template="es5Margin" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    background: 'skyblue',
    //Customize the chart border and opacity
    border: {color: "#FF0000", width: 2},
    //Change chart margin to left, right, top and bottom
    margin: { left: 40, right: 40, top: 40, bottom: 40 },
    axes: [{
        radius: '90%',
        maximum: 120,
        startAngle: 230,
        endAngle: 130,
        majorTicks: {
            width: 1, color: '#8c8c8c'
        },
        lineStyle: { width: 2 },
        minorTicks: {
            width: 1, color: '#8c8c8c'
        },
        pointers: [{
            value: 60,
            radius: '60%'
        }],
        ranges: [{
            start: 0,
            end: 70,
            radius: '110%',
            strokeWidth: 10
        }, {
            start: 70,
            end: 110,
            radius: '110%',
            strokeWidth: 10
        }, {
            start: 110,
            end: 120,
            radius: '110%',
            strokeWidth: 10
        }]
    }]
}, '#element');

```

{% endtab %}

## Radius calculation based on angles

Render semi or quarter circular gauges by modifying the start and end angles. By enabling the radius based on angle option, the radius of circular gauge will be calculated based on the start and end angles to avoid excess white space.

{% tab template= "circular-gauge/gauge-appearance", sourceFiles="index.ts,index.html", es5Template="es5CornerRadius" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    moveToCenter: true,
    axes: [{
        lineStyle: {
            width: 2,
            color: '#F8F8F8'
        },
        startAngle: 270,
        endAngle: 90,
        radius: '80%'
    }]
}, '#element');

```

{% endtab %}