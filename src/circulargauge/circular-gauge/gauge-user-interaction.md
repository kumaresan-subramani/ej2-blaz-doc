
# User Interaction

## Tooltip for pointers

Circular gauge will displays the pointer details through [tooltip](../api/circular-gauge/tooltipSettings),
when the mouse is moved over the pointer.

<!-- markdownlint-disable MD036 -->

**Enable Tooltip**

By default, tooltip is not visible. Enable the tooltip by setting
[`enable`](../api/circular-gauge/tooltipSettings#enable-boolean) property to true and injecting `GaugeTooltip` module using `CircularGauge.Inject(GaugeTooltip)` method.

{% tab template= "circular-gauge/gauge-user-interaction", sourceFiles="index.ts,index.html", es5Template="es5Tooltip" %}

```typescript
import { CircularGauge, GaugeTooltip } from '@syncfusion/ej2-circulargauge';
CircularGauge.Inject(GaugeTooltip);
let gauge: CircularGauge = new CircularGauge({
    // Title for circular gauge
    tooltip: {
        enable: true
    },
    axes:[{
        pointers:[{
            value: 70
        }],
    }]
}, '#element');

```

{% endtab %}

**Template**

Any HTML elements can be displayed in the tooltip by using the
[`template`](../api/circular-gauge/tooltipSettings#template-string) property of the tooltip.

{% tab template= "circular-gauge/gauge-user-interaction", sourceFiles="index.ts,index.html", es5Template="es5TooltipTemplate" %}

```typescript
import { CircularGauge, GaugeTooltip } from '@syncfusion/ej2-circulargauge';
CircularGauge.Inject(GaugeTooltip);
let gauge: CircularGauge = new CircularGauge({
    // Title for circular gauge
    tooltip: {
        enable: true,
        template: '${value}'
    },
    axes:[{
        pointers:[{
            value: 70
        }]
    }]
}, '#element');

```

{% endtab %}

<!-- markdownlint-disable MD036 -->

## Tooltip for ranges

Circular gauge displays the information about the ranges through tooltip when hovering the mouse over the ranges. You can enable this feature by setting the type property of tooltip to ‘Range’ in the array collection.

**Range tooltip customization**

To customize the range tooltip, use the `rangeSettings` property in tooltip. The following options are available to customize the range tooltip:

* fill - Specifies the range tooltip fill color.

* textStyle - Specifies the range tooltip text style.

* format - Specifies the range content format.

* template - Specifies the custom template for tooltip.

* enableAnimation - Animates as it moves from one point to another.

* border - Specifies the tooltip border.

* showMouseAtPosition - Displays the position of the tooltip on the cursor position.

## Tooltip for annotation

Circular gauge displays the information about the annotations through tooltip when hovering the mouse over the annotation. You can enable this feature by setting the type property of tooltip to ‘Annotation’ in the array collection.

**Annotation tooltip customization**

To customize the annotation tooltip, use the `annotationSettings` property in tooltip. The following options are available to customize the annotation tooltip:

* fill - Specifies the annotation tooltip fill color.

* textStyle - Specifies the annotation tooltip text style.

* format - Specifies the annotation content format.

* template - Specifies the tooltip content with custom template.

* enableAnimation - Animates as it moves from one point to another.

* border - Specifies the tooltip border.

The following code example shows the tooltip for the ranges and annotation.

{% tab template= "circular-gauge/gauge-user-interaction", sourceFiles="index.ts,index.html", es5Template="es5TooltipRangeAnnotation" %}

```typescript
import { CircularGauge, GaugeTooltip, Annotations } from '@syncfusion/ej2-circulargauge';
CircularGauge.Inject(GaugeTooltip, Annotations);
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        radius: '90%',
        minimum: 0,
        maximum: 120,
        startAngle: 240,
        endAngle: 120,
        annotations: [{
           content: 'CircularGauge', zIndex:'1', angle: 180
        }],
        lineStyle: { width: 0 },
        majorTicks: { color: 'white', offset: -5, height: 12 },
        minorTicks: { width: 0 },
        labelStyle: { useRangeColor: true, font: { color: '#424242', size: '13px', fontFamily: 'Roboto' } },

        pointers: [{
            value: 70,
            radius: '60%',
            color: '#33BCBD',
            cap: { radius: 10, border: { color: '#33BCBD', width: 5 } },
            animation: { enable: false }
        }],
        ranges: [{
            start: 0,
            end: 50,
            startWidth: 10, endWidth: 10,
            radius: '102%',
            color: '#3A5DC8',
        }, {
            start: 50,
            end: 120,
            radius: '102%',
            startWidth: 10, endWidth: 10,
            color: '#33BCBD',
        }]
    }],
    tooltip: {
        type:['Pointer', 'Range', 'Annotation'],
        enable: true,
        enableAnimation: false,
        annotationSettings: { template:'<div>CircularGauge</div>' },
        rangeSettings: { fill:'red' }
    },

}, '#element');

```

{% endtab %}

## Pointer Drag

Pointers can be dragged over the axis value. This can be achieved by clicking and dragging the pointer. To enable or disable the pointer drag, you can use
[`enablePointerDrag`](../api/circular-gauge#enablepointerdrag-boolean) property.

{% tab template= "circular-gauge/gauge-user-interaction", sourceFiles="index.ts,index.html", es5Template="es5PointerDrag" %}

```typescript
import { CircularGauge, GaugeTooltip } from '@syncfusion/ej2-circulargauge';
CircularGauge.Inject(GaugeTooltip);
let gauge: CircularGauge = new CircularGauge({
    enablePointerDrag: true,
    tooltip: {
        enable: true
    },
    axes:[{
        pointers:[{
            value: 70
        }]
    }]
}, '#element');

```

{% endtab %}