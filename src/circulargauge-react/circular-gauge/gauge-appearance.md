# Appearance

## Gauge Title

Circular gauge can be given a title by using
[`title`](../api/circular-gauge/#title-string) property, to show the information about the gauge.
Title can be customized by using [`titleStyle`](../api/circular-gauge/#titlestyle-fontmodel)
property in gauge.

{% tab template="circulargauge/gauge-appearance", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge' title= 'Speedometer'
    titleStyle= {{
        color: '#27d5ff'
    }}>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}

## Gauge Position

<!-- markdownlint-disable MD036 -->

Gauge can be positioned anywhere in the container with the help of
[`centerX`](../api/circular-gauge/#centerx-string) and
[`centerY`](../api/circular-gauge/#centery-string)
property and it accepts values either in percentage or in pixels.
The default value of the [`centerX`](../api/circular-gauge/#centerx-string) and
[`centerY`](../api/circular-gauge/#centery-string) property is 50%, which means gauge will get rendered to the centre of the container.

**In Pixel**

You can set the mid point of the gauge in pixel as demonstrated below,

{% tab template="circulargauge/gauge-appearance", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, AxesDirective, AxisDirective } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge' centerX= '20' centerY= '20'>
    <AxesDirective>
        <AxisDirective lineStyle= {{
            width: 2,
            color: '#F8F8F8'
        }} startAngle= {90} endAngle= {180}>
        </AxisDirective>
    </AxesDirective>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}
<!-- markdownlint-disable MD036 -->

**In Percentage**

By setting the value in percentage, gauge gets its mid point with respect to its plot area.
For example, when the [`centerX`](../api/circular-gauge/#centerx-string)
value as '0%' and [`centerY`](../api/circular-gauge/#centery-string) value is ‘50%’,
gauge will get positioned at the top left corner of the plot area.

{% tab template="circulargauge/gauge-appearance", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, AxesDirective, AxisDirective } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge' centerX= '10%' centerY= '50%'>
    <AxesDirective>
        <AxisDirective lineStyle= {{
            width: 2,
            color: '#F8F8F8'
        }} startAngle= {0} endAngle= {180}>
        </AxisDirective>
    </AxesDirective>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}
<!-- markdownlint-disable MD036 -->

## Area Customization

**Customize the gauge background**

Using [`background`](../api/circular-gauge/#background-string) and
[`border`](../api/circular-gauge/#border-bordermodel) properties, you can change the background color and border of the circular gauge.

{% tab template="circulargauge/gauge-appearance", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, AxesDirective, AxisDirective, PointersDirective, PointerDirective, RangesDirective, RangeDirective } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge' background= 'skyblue' border= {{
      color: "#FF0000", width: 2
    }}>
    <AxesDirective>
        <AxisDirective radius= '90%' maximum= {120} startAngle= {230} endAngle= {130} majorTicks= {{
            width: 1, color: '#8c8c8c'
        }} lineStyle= {{ width: 2 }} minorTicks= {{
            width: 1, color: '#8c8c8c'
        }}>
            <PointersDirective>
                <PointerDirective value= {60} radius= '60%'>
                </PointerDirective>
            </PointersDirective>
            <RangesDirective>
                <RangeDirective start= {0} end= {70} radius= '110%' strokeWidth= {10}></RangeDirective>
                <RangeDirective start= {70} end= {110} radius= '110%' strokeWidth= {10}></RangeDirective>
                <RangeDirective start= {110} end= {120} radius= '110%' strokeWidth= {10}></RangeDirective>
            </RangesDirective>
        </AxisDirective>
    </AxesDirective>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}

**Gauge Margin**

You can set margin for gauge from its container through
[`margin`](../api/circular-gauge/#margin-marginmodel) property.

{% tab template="circulargauge/gauge-appearance", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, AxesDirective, AxisDirective, PointersDirective, PointerDirective, RangesDirective, RangeDirective } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge' background= 'skyblue' border= {{
      color: "#FF0000", width: 2
    }} margin= {{
         left: 40, right: 40, top: 40, bottom: 40
    }}>
    <AxesDirective>
        <AxisDirective radius= '90%' maximum= {120} startAngle= {230} endAngle= {130} majorTicks= {{
            width: 1, color: '#8c8c8c'
        }} lineStyle= {{ width: 2 }} minorTicks= {{
            width: 1, color: '#8c8c8c'
        }}>
            <PointersDirective>
                <PointerDirective value= {60} radius= '60%'>
                </PointerDirective>
            </PointersDirective>
            <RangesDirective>
                <RangeDirective start= {0} end= {70} radius= '110%' strokeWidth= {10}></RangeDirective>
                <RangeDirective start= {70} end= {110} radius= '110%' strokeWidth= {10}></RangeDirective>
                <RangeDirective start= {110} end= {120} radius= '110%' strokeWidth= {10}></RangeDirective>
            </RangesDirective>
        </AxisDirective>
    </AxesDirective>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}

## Radius calculation based on angles

Render semi or quarter circular gauges by modifying the start and end angles. By enabling the radius based on angle option, the radius of circular gauge will be calculated based on the start and end angles to avoid excess white space.

{% tab template="circulargauge/gauge-appearance", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, AxesDirective, AxisDirective } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge'>
    <AxesDirective>
        <AxisDirective lineStyle= {{
            width: 2,
            color: '#F8F8F8'
        }} startAngle= {270} endAngle= {90}>
        </AxisDirective>
    </AxesDirective>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}