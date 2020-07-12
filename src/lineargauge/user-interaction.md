
# User Interaction

## Tooltip

<!-- markdownlint-disable MD036 -->

Linear gauge will display the details about the pointer value through [tooltip](../api/linear-gauge/tooltipSettings), when the mouse is moved over the pointer. By default, tooltip will not be visible and you can enable the tooltip by setting [`enable`](../api/linear-gauge/tooltipSettings/#enable-boolean) property to true and by injecting `GaugeTooltip` module using `LinearGauge.Inject(GaugeTooltip)`.

{% tab template= "linear-gauge/user-interaction", sourceFiles="index.ts,index.html", es5Template="es5Tooltip" %}

```typescript
import { LinearGauge, GaugeTooltip } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(GaugeTooltip);
let gauge: LinearGauge = new LinearGauge({
   tooltip: {
       enable: true
   },
   axes: [{
            pointers: [{
                value: 80
            }]
        }]
}, '#element');

```

{% endtab %}

<!-- markdownlint-disable MD013 -->

**Format the Tooltip**

<!-- markdownlint-disable MD013 -->

By default, tooltip will show the pointer value only. In addition to that, you can show more information in tooltip. For example, the format `${value}` shows pointer value with currency using the `format` property.

{% tab template= "linear-gauge/user-interaction", sourceFiles="index.ts,index.html", es5Template="es5TooltipFormat" %}

```typescript
import { LinearGauge, GaugeTooltip } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(GaugeTooltip);
let gauge: LinearGauge = new LinearGauge({
     tooltip: {
       enable: true,
       format: '${value}'
   },
   axes: [{
            pointers: [{
                value: 80
            }]
        }]
}, '#element');

```

{% endtab %}

**Tooltip Template**

Any HTML elements can be displayed in the tooltip by using the [`template`](../api/linear-gauge/tooltipSettings/#template-string) property of the tooltip. You can use the {value} as placeholders in the HTML element to display the pointer values of the corresponding axis.

{% tab template= "linear-gauge/user-interaction", sourceFiles="index.ts,index.html", es5Template="es5TooltipTemplate" %}

```typescript
import { LinearGauge, GaugeTooltip } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(GaugeTooltip);
let gauge: LinearGauge = new LinearGauge({
    tooltip: {
            enable: true,
            //tooltip template for Linear gauge
            template: '<div>Pointer: 80 </div>'
        },
        axes: [{
            pointers: [{
                value: 80
            }]
        }]
}, '#element');

```

{% endtab %}

**Customize the Appearance of Tooltip**

* [`fill`](../api/linear-gauge/tooltipSettings/#fill-string) - Specifies fill color for tooltip
* [`border`](../api/linear-gauge/tooltipSettings/#border-bordermodel) - Specifies tooltip border width and color
* [`textStyle`](../api/linear-gauge/tooltipSettings/#textstyle-fontmodel) - Specifies the tooltip text style, such as color, font family, font style and font weight

{% tab template= "linear-gauge/user-interaction", sourceFiles="index.ts,index.html", es5Template="es5TooltipCustomize" %}

```typescript
import { LinearGauge, GaugeTooltip } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(GaugeTooltip);
let gauge: LinearGauge = new LinearGauge({
    tooltip: {
            enable: true,
            fill: '#e5bcbc',
            border: {
                color: '#d80000',
                width: 2
            }
        },
        axes: [{
            pointers: [{
                value: 80
            }]
        }]
}, '#element');

```

{% endtab %}

## Pointer Drag

You can drag and drop either marker or bar pointer over the desired axis value using [`enableDrag`](../api/linear-gauge/pointer/#enabledrag-boolean) property in the [`pointer`](../api/linear-gauge/pointer/#pointer-pointermodel).

{% tab template= "linear-gauge/user-interaction", sourceFiles="index.ts,index.html", es5Template="es5PointerDrag" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
    axes: [{
        pointers: [{
            value: 80,
            enableDrag: true
        }]
    }]
}, '#element');

```

{% endtab %}