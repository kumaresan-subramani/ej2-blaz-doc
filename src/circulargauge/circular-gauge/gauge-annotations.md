# Annotations

Annotations are used to mark a specific area of interest in the gauge with texts, shapes or images.

## Content

You can place any custom element on the axis area by assigning the id of the element to
[`content`](../api/circular-gauge/annotation#content-string) property of [`annotation`](../api/circular-gauge/annotation) object.

>Note: To use annotation feature, we need to inject `Annotations` module using `CircularGauge.Inject(Annotations)` method.

{% tab template= "circular-gauge/gauge-annotations", sourceFiles="index.ts,index.html", es5Template="es5Position" %}

```typescript

import { CircularGauge, Annotations } from '@syncfusion/ej2-circulargauge';
CircularGauge.Inject(Annotations);
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        annotations: [{
            content: 'annotation-template', zIndex:'1'
        }],
        pointers:[{
            value: 50
        }]
    }]
}, '#element');

```

{% endtab %}

## Position

Annotation can be placed around the axis by using [`radius`](../api/circular-gauge/annotation#radius-string)
and [`angle`](../api/circular-gauge/annotation#angle-number) property.
For example, if the angle is 90 degree and the radius is 110%, then the annotation, will be placed at the right side of the axis.

Radius of the annotation takes value either in pixel or percentage. By setting value in percentage, annotation gets its position with respect to its axis radius.

{% tab template= "circular-gauge/gauge-annotations", sourceFiles="index.ts,index.html", es5Template="es5Template" %}

```typescript

import { CircularGauge, Annotations } from '@syncfusion/ej2-circulargauge';
CircularGauge.Inject(Annotations);
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        annotations: [{
            content: '#annotation-template',
            angle: 90,
            radius: '150%'
        }],
        pointers:[{
            value: 50
        }]
    }]
}, '#element');

```

{% endtab %}

## Sub Gauge

As the annotation allows you to place any custom element, we can initialize a gauge to the element and can
be used to place that in another gauge.

{% tab template= "circular-gauge/gauge-annotations", sourceFiles="index.ts,index.html", es5Template="es5SubGauge" %}

```typescript

import { CircularGauge, Annotations } from '@syncfusion/ej2-circulargauge';
CircularGauge.Inject(Annotations);
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        minimum: 0,
        maximum: 12,
        startAngle: 0,
        endAngle: 360,
        lineStyle: { width: 0 },
        ranges: [
            {
                start: 0, end: 3,
                color: 'rgba(29,29,29,0.7)'
            }, {
                start: 3, end: 12,
                color: 'rgba(168,145,102,0.1)'
            }
        ],
        annotations: [{
            angle: 270,
            radius: '40%',
            content: '<div id="subGauge" style="width:90px;height:90px;"></div>'
        },{
            angle: 90,
            radius: '40%',
            content: '<div id="time"><span>6:30 PM</span></div>'
        }],
        labelStyle: {
            hiddenLabel: 'First'
        },
        pointers: [{
            pointerWidth: 5,
            radius: '40%',
            value: 6.5,
            color: 'rgb(29,29,29)',
            border: { width: 1, color: 'rgb(29,29,29)' },
            cap: {
                color: 'rgb(29,29,29)',
                radius: 0,
                border: {
                    width: 0.2,
                    color: 'red'
                }
            },
            needleTail: {
                length: '0%'
            }, animation: {
                enable: false
            }
        }, {
            radius: '60%',
            pointerWidth: 5,
            color: 'rgb(29,29,29)',
            border: {
                width: 1,
                color: 'rgb(29,29,29)'
            },
            value: 6,
            cap: {
                color: 'rgb(29,29,29)',
                radius: 0,
                border: {
                    width: 0.2,
                    color: 'red'
                }
            },
            needleTail: {
                length: '0%'
            }, animation: {
                enable: false
            }
        }, {
            radius: '70%',
            pointerWidth: 4,
            value: 9.8,
            color: 'rgba(168,145,102,1)',
            cap: {
                color: 'rgba(168,145,102,1)',
                radius: 4,
                border: {
                    width: 0.2,
                    color: 'rgba(168,145,102,1)'
                }
            },
            needleTail: {
                color: 'rgba(168,145,102,1)',
                length: '20%'
            }, animation: {
                enable: false,
                duration: 500
            }
        }]
    }]
}, '#element');

let gauge: CircularGauge = new CircularGauge({
    axes: [{
        minimum: 0,
        maximum: 12,
        startAngle: 0,
        endAngle: 360,
        majorTicks:{
            interval: 3
        },
        lineStyle: { width: 0 },
        ranges: [
            {
                start: 0, end: 3,
                startWidth: 5, endWidth: 5,
                color: 'rgba(29,29,29,0.7)'
            }, {
                start: 3, end: 12,
                startWidth: 5, endWidth: 5,
                color: 'rgba(168,145,102,0.1)'
            }
        ],
        labelStyle: {
            hiddenLabel: 'First',
            offset: -5
        },
        pointers: [{
            pointerWidth: 2,
            radius: '40%',
            color: 'rgb(29,29,29)',
            border: { width: 1, color: 'rgb(29,29,29)' },
            cap: {
                color: 'rgb(29,29,29)',
                radius: 2,
                border: {
                    width: 0.2,
                    color: 'red'
                }
            },
            needleTail: {
                length: '0%'
            }, animation: {
                enable: false
            }
        }]
    }]
}, '#subGauge');

```

{% endtab %}

## See also

* [Tooltip for Annotation](https://ej2.syncfusion.com/documentation/circular-gauge/gauge-user-interaction/tooltip-for-ranges-and-annotations/)