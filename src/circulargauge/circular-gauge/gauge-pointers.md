
# Pointers

Pointers are used to indicate values on the axis. Value of the pointer can be modified using the
[`value`](../api/circular-gauge/pointer#value-number) property.

{% tab template= "circular-gauge/gauge-pointers", sourceFiles="index.ts,index.html", es5Template="es5Pointer" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        pointers: [{
            value: 90
        }]
    }]
}, '#element');

```

{% endtab %}

Gauge supports 3 types of pointers such as `Needle`, `RangeBar` and `Marker`. You can choose any one of the pointer by using [`type`](../api/circular-gauge/pointer#type-string) property.

## Needle Pointers

A needle pointer contains three parts, a needle, a cap / knob and a tail. The length of the needle can be
customized by using [`radius`](../api/circular-gauge/pointer#radius-string) property. The length of the tail can be
customized by using [`length`](../api/circular-gauge/needleTailModel#length-string) property. The radius of the cap
can be customized by using [`radius`](../api/circular-gauge/capModel#radius-number) in cap object. The needle and tail
length takes value either in `percentage` or `pixel`.

{% tab template= "circular-gauge/gauge-pointers", sourceFiles="index.ts,index.html", es5Template="es5NeedlePointer" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        pointers: [{
            value: 90,
            radius: '50%',
            cap: {
                radius: 10
            },
            needleTail: {
                length: '25%'
            }
        }]
    }]
}, '#element');

```

{% endtab %}

<!-- markdownlint-disable MD036 -->

**Customization**

Needle color and width can be customized by using [`color`](../api/circular-gauge/pointer#color-string) and [`pointerWidth`](../api/circular-gauge/pointer#pointerwidth-number) property.
Cap and tails can be customized by using [`cap`](../api/circular-gauge/pointer#cap-capmodel) and
[`needleTail`](../api/circular-gauge/pointer#needletail-needletailmodel) object.

{% tab template= "circular-gauge/gauge-pointers", sourceFiles="index.ts,index.html", es5Template="es5NeedleCustomization" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        pointers: [{
            value: 90,
            radius: '50%',
            cap: {
                radius: 15,
                color: 'white',
                border: {
                    color: '#007DD1',
                    width: 5
                }
            },
            needleTail: {
                length: '22%',
                color: '#007DD1'
            },
            color: '#007DD1',
            pointerWidth: 25
        }]
    }]
}, '#element');

```

{% endtab %}

The appearance of the needle pointer can be customized by using [`needleStartWidth`](../api/circular-gauge/pointer/#needlestartwidth) and [`needleEndWidth`](../api/circular-gauge/pointer/#needleendwidth).

{% tab template= "circular-gauge/gauge-pointers", sourceFiles="index.ts,index.html", es5Template="es5Needle" %}

```typescript

import { CircularGauge, Annotations} from '@syncfusion/ej2-circulargauge';
CircularGauge.Inject(Annotations);
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        startAngle: 270,
        endAngle: 90,
        lineStyle: { width: 3, color: '#1E7145' },
        labelStyle: {
            position: 'Outside',
            font: { size: '0px', color: '#1E7145' }
        }, majorTicks: {
            width: 1,
            height: 0,
            interval: 100
        }, minorTicks: {
            height: 0,
            width: 0,
        },
        radius: '90%',
        minimum: 0,
        maximum: 100,
        pointers: [{
        animation: { enable: true , duration: 1000},
        value: 70,
        radius: '80%',
        color: 'green',
        pointerWidth: 2,
        needleStartWidth: 4,
        needleEndWidth: 4,
        cap: {
            radius: 8,
            color: 'green'
        },
        needleTail: {
            length: '0%'
        }
        }],
        annotations: [
            {
                angle: 180, zIndex: '1',
                radius: '20%',
                content: '<div style="color:#757575; font-family:Roboto; font-size:14px;padding-top: 26px">Customized Needle</div>'
            }
        ]
    }]
}, '#element');

```

{% endtab %}

## RangeBar Pointer

RangeBar pointer is like ranges in an axis, that can be placed on gauge to mark the pointer value.
RangeBar starts from the beginning of the gauge and ends at the pointer value.

{% tab template= "circular-gauge/gauge-pointers", sourceFiles="index.ts,index.html", es5Template="es5RangeBarPointer" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        pointers: [{
            value: 50,
            type: 'RangeBar',
            radius: '60%'
        }]
    }]
}, '#element');

```

{% endtab %}

**Customization**

RangeBar can be customized in terms of color, border and thickness by using
[`color`](../api/circular-gauge/pointer#color-string), [`border`](../api/circular-gauge/pointer#border-bordermodel) and [`pointerWidth`](../api/circular-gauge/pointer#pointerwidth-number) property.

{% tab template= "circular-gauge/gauge-pointers", sourceFiles="index.ts,index.html", es5Template="es5RangeBarCustomization" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        pointers: [{
            value: 50,
            type: 'RangeBar',
            radius: '60%',
            color: '#007DD1',
            border: {
                color: 'grey',
                width: 2
            },
            pointerWidth: 15
        }]
    }]
}, '#element');

```

{% endtab %}

## Rounded corner for range bar pointer

The start and end pointers of range bar in the circular gauge are rounded to form arc gauges.

{% tab template= "circular-gauge/gauge-pointers", sourceFiles="index.ts,index.html", es5Template="es5RangeBarCornerRadius" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        lineStyle: {
            color: 'transparent'
        },
        ranges: [
            { start: 0, end: 50, color: '#30B32D', radius:'108%' },
            { start: 50, end: 100, color: '#FFDD00', radius:'108%' }],
        pointers: [{
            value: 50,
            type: 'RangeBar',
            roundedCornerRadius: 6
        }]
    }]
}, '#element');

```

{% endtab %}

## Marker Pointer

Different type of marker shape can be used to mark the pointer value in axis.  You can change the marker shape using [`markerShape`](../api/circular-gauge/pointer#markershape-string) property in pointer. Gauge supports the below marker shape.
* Circle
* Rectangle
* Triangle
* InvertedTriangle
* Diamond

We can use image instead of rendering marker shape to denote the pointer value. It can be achieved by setting [`markerShape`](../api/circular-gauge/pointer#markershape-string) to Image and assigning  image path to [`imageUrl`](../api/circular-gauge/pointer#imageurl-string) in pointer.

{% tab template= "circular-gauge/gauge-pointers", sourceFiles="index.ts,index.html", es5Template="es5MarkerPointer" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        pointers: [{
            value: 90,
            type: 'Marker',
            markerShape: 'InvertedTriangle',
            radius: '100%',
            markerHeight: 15,
            markerWidth: 15
        }]
    }]
}, '#element');

```

{% endtab %}

**Customization**

The marker can be customized in terms of color, border, width and height by using
[`color`](../api/circular-gauge/pointer#color-string),
[`border`](../api/circular-gauge/pointer#border-bordermodel),
[`markerWidth`](../api/circular-gauge/pointer#markerwidth-number) and
[`markerHeight`](../api/circular-gauge/pointer#markerheight-number) property in
[`pointer`](../api/circular-gauge/pointer).

{% tab template= "circular-gauge/gauge-pointers", sourceFiles="index.ts,index.html", es5Template="es5MarkerCustomization" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        pointers: [{
            value: 90,
            type: 'Marker',
            markerShape: 'Triangle',
            radius: '100%',
            color: 'white',
            border: {
                color: '#007DD1',
                width: 2
            },
            markerHeight: 15,
            markerWidth: 15
        }]
    }]
}, '#element');

```

{% endtab %}

## Dragging pointer

The pointers can be dragged over the axis line by clicking and dragging the same. To enable or disable the pointer drag, use the [`enablePointerDrag`](../api/circular-gauge/circularGaugeModel/#enablepointerdrag) property.

{% tab template= "circular-gauge/gauge-pointers", sourceFiles="index.ts,index.html", es5Template="es5DragPointer" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    enablePointerDrag:true,
    height:'250px',
    width:'250px',
    axes: [{
        pointers: [{
            value: 50
        }]
    }]
}, '#element');

```

{% endtab %}

## Multiple Pointers

In addition to the default pointer, you can add n number of pointer to an axis by using `pointers` property.

 {% tab template= "circular-gauge/gauge-pointers", sourceFiles="index.ts,index.html", es5Template="es5MultiplePointers" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        pointers: [{
            value: 90,
            type: 'Marker',
            markerShape: 'InvertedTriangle',
            radius: '100%',
            markerHeight: 15,
            markerWidth: 15
        }, {
            value: 90,
            type: 'RangeBar',
            radius: '60%',
            pointerWidth: 10
        }, {
            value: 90,
            radius: '60%',
            cap: {
                radius: 15,
                border: {
                    width: 5
                }
            },
            needleTail: {
                length: '22%',
            },
            pointerWidth: 25
        }]
    }]
}, '#element');

```

{% endtab %}

## Animation

Pointer will get animate on loading the gauge, this can be handled by using
[`animation`](../api/circular-gauge/pointer#animation-animationmodel) property in pointer.
The [`enable`](../api/circular-gauge/animationModel#enable-boolean) property in animation allows you to enable or disable the animation.
The [`duration`](../api/circular-gauge/animationModel#duration-number) property specify the duration of the animation in milliseconds.

{% tab template= "circular-gauge/gauge-pointers", sourceFiles="index.ts,index.html", es5Template="es5Animation" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        pointers: [{
            value: 90,
            animation: {
                enable: true,
                duration: 1500
            }
        }]
    }]
}, '#element');

```

{% endtab %}

## Gradient Color

Gradient support allows to add multiple colors in the ranges and pointers of the circular gauge. The following gradient types are supported in the circular gauge.

* Linear Gradient
* Radial Gradient

### Linear Gradient

Using linear gradient, colors will be applied in a linear progression. The start value of the linear gradient can be set using the [`startValue`](../api/circular-gauge/linearGradient/#startvalue) property. The end value of the linear gradient will be set using the [`endValue`](../api/circular-gauge/linearGradient/#endvalue) property. The color stop values such as color, opacity and offset are set using [`colorStop`](../api/circular-gauge/linearGradient/#colorstop) property.

The linear gradient can be applied to all pointer types like marker, range bar and needle. To do so, follow the below code sample.

{% tab template= "circular-gauge/gauge-pointers", sourceFiles="index.ts,index.html" es5Template="es5LinearGradient"%}

```typescript

import { CircularGauge, Gradient } from '@syncfusion/ej2-circulargauge';
CircularGauge.Inject(Gradient);
let pointerLinearGradient: Object = {
    startValue: '0%',
    endValue: '100%',
    colorStop: [
        { color: '#FEF3F9', offset: '0%', opacity: 0.9 },
        { color: '#E63B86', offset: '70%', opacity: 0.9 }]
};
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        startAngle: 270,
        endAngle: 90,
        lineStyle: { width: 3, color: '#E63B86' },
        labelStyle: {
            font: { size: '0px' }
        }, majorTicks: {
            height: 0
        }, minorTicks: {
            height: 0
        },
        radius: '90%',
        minimum: 0,
        maximum: 100,
        pointers: [{
            radius: '80%',
            value: 80,
            animation: { enable: true, duration: 1000 },
            pointerWidth: 10,
            linearGradient: pointerLinearGradient,
            cap: {
                radius: 8,
                color: 'white',
                border: {
                    color: '#E63B86',
                    width: 1
                }
                },
                needleTail: {
                    length: '20%',
                    linearGradient: pointerLinearGradient,
                }
        }, {
            radius: '60%', value: 40,
            animation: { duration: 1000 },
            pointerWidth: 10,
            linearGradient: pointerLinearGradient,
            cap: {
                radius: 8, color: 'white',
                border: { color: '#E63B86', width: 1 }
            },
            needleTail: {
                length: '20%',
                linearGradient: pointerLinearGradient
            }
        }]
    }]
}, '#element');

```

{% endtab %}

### Radial Gradient

Using radial gradient, colors will be applied in circular progression. The inner circle position of the radial gradient will be set using the [`innerPosition`](../api/circular-gauge/radialGradient/#innerposition) property. The outer circle position of the radial gradient can be set using the [`outerPosition`](../api/circular-gauge/radialGradient/#outerposition) property. The color stop values such as color, opacity and offset are set using [`colorStop`](../api/circular-gauge/radialGradient/#colorstop) property.

The radial gradient can be applied to all pointer types like marker, range bar and needle. To do so, follow the below code sample.

{% tab template= "circular-gauge/gauge-pointers", sourceFiles="index.ts,index.html", es5Template="es5RangeGradient" %}

```typescript

import { CircularGauge, Gradient } from '@syncfusion/ej2-circulargauge';
CircularGauge.Inject(Gradient);
let pointerRadialGradient: Object = {
    radius: '50%',
    innerPosition: { x: '50%', y: '50%' },
    outerPosition: { x: '50%', y: '50%' },
    colorStop: [
        { color: '#FEF3F9', offset: '0%', opacity: 0.9 },
        { color: '#E63B86', offset: '60%', opacity: 0.9 }]
};
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        startAngle: 270,
        endAngle: 90,
        lineStyle: { width: 3, color: '#E63B86' },
        labelStyle: {
            font: { size: '0px'}
        }, majorTicks: {
            height: 0
        }, minorTicks: {
            height: 0
        },
        radius: '90%',
        minimum: 0,
        maximum: 100,
        pointers: [{
            radius: '80%',
            value: 80,
            animation: { enable: true, duration: 1000 },
            pointerWidth: 10,
            radialGradient: pointerRadialGradient,
            cap: {
                radius: 8,
                color: 'white',
                border: {
                    color: '#E63B86',
                    width: 1
                }
                },
                needleTail: {
                    length: '20%',
                    radialGradient: pointerRadialGradient,
                }
            }, {
            radius: '60%', value: 40,
            animation: { duration: 1000 },
            pointerWidth: 10,
            radialGradient: pointerRadialGradient,
            cap: {
                radius: 8, color: 'white',
                border: { color: '#E63B86', width: 1 }
            },
            needleTail: {
                length: '20%',
                radialGradient: pointerRadialGradient
            }
        }]
     }]
}, '#element');

```

{% endtab %}