
# Ranges

You can categories certain interval on gauge axis using
[`ranges`](../api/circular-gauge/range/#properties) property.

## Start and End

Start and end value of a range in an axis can be customized by using
[`start`](../api/circular-gauge/range/#start-number) and [`end`](../api/circular-gauge/range/#end-number) properties.

{% tab template="circulargauge/gauge-ranges", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, AxesDirective, AxisDirective, RangesDirective, RangeDirective } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge'>
    <AxesDirective>
      <AxisDirective>
        <RangesDirective>
            <RangeDirective start = {40} end = {80}></RangeDirective>
        </RangesDirective>
      </AxisDirective>
    </AxesDirective>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}

## Customization

Color and thickness of the range can be customized by using
[`color`](../api/circular-gauge/range/#color-string),
[`startWidth`](../api/circular-gauge/range/#startwidth-number) and
[`endWidth`](../api/circular-gauge/range/#endwidth-number) property.

{% tab template="circulargauge/gauge-ranges", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, AxesDirective, AxisDirective, RangesDirective, RangeDirective } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge'>
    <AxesDirective>
      <AxisDirective>
        <RangesDirective>
            <RangeDirective start = {40} end = {80} startWidth = {15} endWidth = {15}
            color = '#ff5985'></RangeDirective>
        </RangesDirective>
      </AxisDirective>
    </AxesDirective>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}

<!-- markdownlint-disable MD036 -->

## Radius

You can place the range inside or outside of the axis by using
[`radius`](../api/circular-gauge/range/#radius-string) property.
The radius of the range can takes value either in percentage or in pixels.
By default, ranges take 100% of the axis radius.

**In Pixel**

You can set the radius of the range in pixel as demonstrated below,

{% tab template="circulargauge/gauge-ranges", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, AxesDirective, AxisDirective, RangesDirective, RangeDirective } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge'>
    <AxesDirective>
      <AxisDirective>
        <RangesDirective>
            <RangeDirective start = {40} end = {80} radius = '100'></RangeDirective>
        </RangesDirective>
      </AxisDirective>
    </AxesDirective>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}

<!-- markdownlint-disable MD036 -->

**In Percentage**

By setting value in percentage, range gets its dimension with respect to its axis radius.
For example, when the radius is ‘50%’, range renders to half of the axis radius.

{% tab template="circulargauge/gauge-ranges", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, AxesDirective, AxisDirective, RangesDirective, RangeDirective } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge'>
    <AxesDirective>
      <AxisDirective>
        <RangesDirective>
            <RangeDirective start = {40} end = {80} radius = '50%'></RangeDirective>
        </RangesDirective>
      </AxisDirective>
    </AxesDirective>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}

## Dragging range

The ranges can be dragged on the axis values by clicking and dragging the same. To enable or disable the range drag, use the [`enableRangeDrag`](../api/circular-gauge/circularGaugeModel/#enablerangedrag) property.

{% tab template="circulargauge/gauge-pointers", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, AxesDirective, AxisDirective, PointersDirective, PointerDirective,
RangesDirective, RangeDirective } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge' enableRangeDrag='true' height='250px' width='250px'>
    <AxesDirective>
      <AxisDirective>
        <RangesDirective>
            <RangeDirective start = {0} end = {100} startWidth={8} endWidth={8} radius='108%' color='#30B32D'></RangeDirective>
        </RangesDirective>
        <PointersDirective>
            <PointerDirective value = {50}></PointerDirective>
        </PointersDirective>
      </AxisDirective>
    </AxesDirective>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}

## Multiple Ranges

You can add multiple ranges to an axis with the above customization as demonstrated below.

*Note: You can set the range color to axis ticks and labels by enabling `useRangeColor` property in [`majorTicks`](../api/circular-gauge/tick/),
[`minorTicks`](../api/circular-gauge/tick/) and [`labelStyle`](../api/circular-gauge/label/) object.*

{% tab template="circulargauge/gauge-ranges", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, AxesDirective, AxisDirective, RangesDirective, RangeDirective } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge'>
    <AxesDirective>
      <AxisDirective majorTicks = {{ useRangeColor: true }} minorTicks = {{ useRangeColor: true }} labelStyle = {{ useRangeColor: true }}>
        <RangesDirective>
            <RangeDirective start = {0} end = {25} radius = '108%'></RangeDirective>
            <RangeDirective start = {25} end = {50} radius = '70%'></RangeDirective>
            <RangeDirective start = {50} end = {75} radius = '70%'></RangeDirective>
            <RangeDirective start = {75} end = {100} radius = '108%'></RangeDirective>
        </RangesDirective>
      </AxisDirective>
    </AxesDirective>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}

## Rounded corner radius

You can customize the corner radius using the `roundedCornerRadius` property in `ranges`.

{% tab template="circulargauge/gauge-ranges", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, AxesDirective, AxisDirective, RangesDirective, RangeDirective } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge'>
    <AxesDirective>
      <AxisDirective>
        <RangesDirective>
            <RangeDirective start = {40} end = {80} radius = '50%' roundedCornerRadius = {5}></RangeDirective>
        </RangesDirective>
      </AxisDirective>
    </AxesDirective>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}

## Gradient Color

Gradient support allows to add multiple colors in the ranges and pointers of the circular gauge. The following gradient types are supported in the circular gauge.

* Linear Gradient
* Radial Gradient

### Linear Gradient

Using linear gradient, colors will be applied in a linear progression. The start value of the linear gradient can be set using the [`startValue`](../api/circular-gauge/linearGradient/#startvalue) property. The end value of the linear gradient will be set using the [`endValue`](../api/circular-gauge/linearGradient/#endvalue) property. The color stop values such as color, opacity and offset are set using [`colorStop`](../api/circular-gauge/linearGradient/#colorstop) property.

To apply linear gradient to the range, follow the below code sample.

{% tab template="circulargauge/gauge-ranges", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, AxesDirective, AxisDirective, RangesDirective, RangeDirective, Annotations, Inject, Gradient, PointerDirective, PointersDirective, AnnotationsDirective, AnnotationDirective } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent  id='circulargauge' title='Short Put Distance' titleStyle={{ size: '18px'}} centerY="57%'">
    <Inject services={[Annotations, Gradient]} />
     <AxesDirective>
        <AxisDirective startAngle={200} endAngle={130} radius='90%' minimum={0} maximum={14}
          lineStyle={{
            width: 0, color: '#1d1d1d'
          }}
          majorTicks={{ width: 0 }}
          minorTicks={{ width: 0 }} labelStyle={{ font: { size: '0px' }}}>
         <PointersDirective>
            <PointerDirective type="Marker" value={12} markerShape="Image" imageUrl="src/circular-gauge/images/football.png" radius='108%' markerWidth={28} markerHeight={28} animation={{ duration: 1500 }} />
            <PointerDirective type="Marker" value={11} markerShape="Image" imageUrl="src/circular-gauge/images/basketball.png" radius='78%' markerWidth={28} markerHeight={28} animation={{ duration: 1200 }} />
            <PointerDirective type="Marker" value={10} markerShape="Image" imageUrl="src/circular-gauge/images/golfball.png" radius='48%' markerWidth={28} markerHeight={28} animation={{ duration: 900 }} />
            <PointerDirective type="Marker" value={12} markerShape="Image" imageUrl="src/circular-gauge/images/athletics.png" radius='0%' markerWidth={90} markerHeight={90} animation={{ duration: 0 }} />
            <PointerDirective type="Marker" value={0.1} markerShape="Image" imageUrl="src/circular-gauge/images/girl1.png" radius='108%' markerWidth={28} markerHeight={28} animation={{ duration: 1500 }} />
            <PointerDirective type="Marker" value={0.1} markerShape="Image" imageUrl="src/circular-gauge/images/man1.png" radius='78%' markerWidth={28} markerHeight={28} animation={{ duration: 1500 }} />
            <PointerDirective type="Marker" value={0.1} markerShape="Image" imageUrl="src/circular-gauge/images/man2.png" radius='48%' markerWidth={28} markerHeight={28} animation={{ duration: 1500 }} />
            </PointersDirective>
          <RangesDirective>
            <RangeDirective start={0} end={12} radius='115%' color='#01aebe' startWidth={25} endWidth={25}
            linearGradient={{
              startValue: '0%', endValue: '100%',
              colorStop: [
              { color: '#9E40DC', offset: '0%', opacity: 0.9 },
              { color: '#E63B86', offset: '70%', opacity: 0.9 }]
            }}/>
            <RangeDirective start={0} end={11} radius='85%' color='#3bceac' startWidth={25} endWidth={25}
            linearGradient={{
              startValue: '0%', endValue: '100%',
              colorStop: [
              { color: '#9E40DC', offset: '0%', opacity: 0.9 },
              { color: '#E63B86', offset: '70%', opacity: 0.9 }]
            }}/>
            <RangeDirective start={0} end={10} radius='55%' color='#ee4266' startWidth={25} endWidth={25}
            linearGradient={{
              startValue: '0%', endValue: '100%',
              colorStop: [
              { color: '#9E40DC', offset: '0%', opacity: 0.9 },
              { color: '#E63B86', offset: '70%', opacity: 0.9 }]
            }}/>
          </RangesDirective>
          <AnnotationsDirective>
            <AnnotationDirective content='12 M' radius='108%' angle={98} zIndex='1' />
            <AnnotationDirective content='11 M' radius='80%' angle={81} zIndex='1' />
            <AnnotationDirective content='10 M' radius='50%' angle={69} zIndex='1' />
            <AnnotationDirective content='Doe' radius='108%' angle={190} zIndex='1' />
            <AnnotationDirective content='Almaida' radius='80%' angle={185} zIndex='1' />
            <AnnotationDirective content='John' radius='50%' angle={180} zIndex='1' />
          </AnnotationsDirective>
        </AxisDirective>
      </AxesDirective>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}

### Radial Gradient

Using radial gradient, colors will be applied in circular progression. The inner circle position of the radial gradient will be set using the [`innerPosition`](../api/circular-gauge/radialGradient/#innerposition) property. The outer circle position of the radial gradient can be set using the [`outerPosition`](../api/circular-gauge/radialGradient/#outerposition) property. The color stop values such as color, opacity and offset are set using [`colorStop`](../api/circular-gauge/radialGradient/#colorstop) property.

To apply radial gradient to the range, follow the below code sample.

{% tab template="circulargauge/gauge-ranges", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, AxesDirective, AxisDirective, RangesDirective, RangeDirective, Annotations, Inject, Gradient, PointerDirective, PointersDirective, AnnotationsDirective, AnnotationDirective } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id="circulargauge" title='Short Put Distance' titleStyle={{ size: '18px' }}
  centerY="57%'">
    <Inject services={[Annotations, Gradient]} />
     <AxesDirective>
        <AxisDirective startAngle={200} endAngle={130} radius='90%' minimum={0} maximum={14}
          lineStyle={{
            width: 0, color: '#1d1d1d'
          }}
          majorTicks={{ width: 0 }}
          minorTicks={{ width: 0 }} labelStyle={{ font: { size: '0px' }}}>
         <PointersDirective>
            <PointerDirective type="Marker" value={12} markerShape="Image" imageUrl="src/circular-gauge/images/football.png" radius='108%' markerWidth={28} markerHeight={28} animation={{ duration: 1500 }} />
            <PointerDirective type="Marker" value={11} markerShape="Image" imageUrl="src/circular-gauge/images/basketball.png" radius='78%' markerWidth={28} markerHeight={28} animation={{ duration: 1200 }} />
            <PointerDirective type="Marker" value={10} markerShape="Image" imageUrl="src/circular-gauge/images/golfball.png" radius='48%' markerWidth={28} markerHeight={28} animation={{ duration: 900 }} />
            <PointerDirective type="Marker" value={12} markerShape="Image" imageUrl="src/circular-gauge/images/athletics.png" radius='0%' markerWidth={90} markerHeight={90} animation={{ duration: 0 }} />
            <PointerDirective type="Marker" value={0.1} markerShape="Image" imageUrl="src/circular-gauge/images/girl1.png" radius='108%' markerWidth={28} markerHeight={28} animation={{ duration: 1500 }} />
            <PointerDirective type="Marker" value={0.1} markerShape="Image" imageUrl="src/circular-gauge/images/man1.png" radius='78%' markerWidth={28} markerHeight={28} animation={{ duration: 1500 }} />
            <PointerDirective type="Marker" value={0.1} markerShape="Image" imageUrl="src/circular-gauge/images/man2.png" radius='48%' markerWidth={28} markerHeight={28} animation={{ duration: 1500 }} />
            </PointersDirective>
          <RangesDirective>
            <RangeDirective start={0} end={12} radius='115%' color='#01aebe' startWidth={25} endWidth={25}
            radialGradient={{
              radius: '50%', innerPosition: { x: '50%', y: '50%' },
              outerPosition: { x: '50%', y: '50%' },
              colorStop: [
              { color: '#9E40DC', offset: '90%', opacity: 0.9 },
              { color: '#E63B86', offset: '160%', opacity: 0.9 }]
            }}/>
            <RangeDirective start={0} end={11} radius='85%' color='#3bceac' startWidth={25} endWidth={25}
            radialGradient={{
              radius: '50%', innerPosition: { x: '50%', y: '50%' },
              outerPosition: { x: '50%', y: '50%' },
              colorStop: [
              { color: '#9E40DC', offset: '90%', opacity: 0.9 },
              { color: '#E63B86', offset: '160%', opacity: 0.9 }]
            }}/>
            <RangeDirective start={0} end={10} radius='55%' color='#ee4266' startWidth={25} endWidth={25}
            radialGradient={{
              radius: '50%', innerPosition: { x: '50%', y: '50%' },
              outerPosition: { x: '50%', y: '50%' },
              colorStop: [
              { color: '#9E40DC', offset: '90%', opacity: 0.9 },
              { color: '#E63B86', offset: '160%', opacity: 0.9 }]
            }}/>
          </RangesDirective>
          <AnnotationsDirective>
            <AnnotationDirective content='12 M' radius='108%' angle={98} zIndex='1' />
            <AnnotationDirective content='11 M' radius='80%' angle={81} zIndex='1' />
            <AnnotationDirective content='10 M' radius='50%' angle={69} zIndex='1' />
            <AnnotationDirective content='Doe' radius='108%' angle={190} zIndex='1' />
            <AnnotationDirective content='Almaida' radius='80%' angle={185} zIndex='1' />
            <AnnotationDirective content='John' radius='50%' angle={180} zIndex='1' />
          </AnnotationsDirective>
        </AxisDirective>
      </AxesDirective>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}

## See also

* [Tooltip for Ranges](https://ej2.syncfusion.com/documentation/circular-gauge/gauge-user-interaction/tooltip-for-ranges-and-annotations/)
