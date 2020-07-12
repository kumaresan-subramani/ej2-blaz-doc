# Annotations

Annotations are used to mark a specific area of interest in the gauge with texts, shapes or images.

## Content

You can place any custom element on the axis area by assigning the id of the element to
[`content`](../api/circular-gauge/annotation/#content-string) property of
[`annotation`](../api/circular-gauge/annotation/) object.

*Note: To use annotation feature, we need to inject `Annotations` module into the `services`.*

{% tab template="circulargauge/gauge-annotations", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, AxesDirective, AxisDirective, PointersDirective, PointerDirective, Inject, Annotations, AnnotationsDirective, AnnotationDirective } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge'>
    <Inject services={[ Annotations ]}/>
    <AxesDirective>
      <AxisDirective>
        <PointersDirective>
            <PointerDirective value = {50}></PointerDirective>
        </PointersDirective>
        <AnnotationsDirective>
            <AnnotationDirective content='<div><div><span>Pointer Value : 50</span></div></div>'/>
        </AnnotationsDirective>
      </AxisDirective>
    </AxesDirective>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}

## Position

Annotation can be placed around the axis by using [`radius`](../api/circular-gauge/annotation/#radius-string)
and [`angle`](../api/circular-gauge/annotation/#angle-number) property.
For example, if the angle is 90 degree and the radius is 110%, then the annotation, will be placed at the right side of the axis.

Radius of the annotation takes value either in pixel or percentage.
By setting value in percentage, annotation gets its position with respect to its axis radius.

{% tab template="circulargauge/gauge-annotations", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, AxesDirective, AxisDirective, PointersDirective, PointerDirective, Inject, Annotations, AnnotationsDirective, AnnotationDirective } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge'>
    <Inject services={[ Annotations ]}/>
    <AxesDirective>
      <AxisDirective>
        <PointersDirective>
            <PointerDirective value = {50}></PointerDirective>
        </PointersDirective>
        <AnnotationsDirective>
            <AnnotationDirective content='<div><div><span>Pointer Value : 50</span></div></div>' angle= {90} radius = '150%'/>
        </AnnotationsDirective>
      </AxisDirective>
    </AxesDirective>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}

## Sub Gauge

As the annotation allows you to place any custom element,
we can initialize a gauge to the element and can be used to place that in another gauge.

{% tab template="circulargauge/gauge-annotations", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, AxesDirective, AxisDirective, PointersDirective, PointerDirective, Inject, Annotations, AnnotationsDirective, AnnotationDirective, RangesDirective, RangeDirective, ILoadedEventArgs } from '@syncfusion/ej2-react-circulargauge';
import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let loadRender: EmitType<ILoadedEventArgs> = (args: ILoadedEventArgs): void => {
    let gauge: CircularGauge = new CircularGauge({
        axes: [{
            minimum: 0, maximum: 12, startAngle: 0,
            endAngle: 360, majorTicks:{ interval: 3 },
            lineStyle: { width: 0 },
            ranges: [
                { start: 0, end: 3, startWidth: 5, endWidth: 5, color: 'rgba(29,29,29,0.7)'},
                { start: 3, end: 12, startWidth: 5, endWidth: 5, color: 'rgba(168,145,102,0.1)'}
            ],
            labelStyle: { hiddenLabel: 'First', offset: -5 },
            pointers: [{
                pointerWidth: 2, radius: '40%',
                color: 'rgb(29,29,29)', border: { width: 1, color: 'rgb(29,29,29)' },
                cap: {
                    color: 'rgb(29,29,29)', radius: 2,
                    border: { width: 0.2, color: 'red' }
                },
                needleTail: { length: '0%' },
                animation: { enable: false }
            }]
        }]
    }, '#subGauge');
};
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge' loaded= {loadRender}>
    <Inject services={[ Annotations ]}/>
    <AxesDirective>
      <AxisDirective  minimum= {0} maximum= {12} startAngle= {0} endAngle= {360} lineStyle= {{ width: 0 }} labelStyle = {{
            hiddenLabel: 'First'
        }}>
        <RangesDirective>
            <RangeDirective start={0} end={3} color='rgba(29,29,29,0.7)'></RangeDirective>
            <RangeDirective start={3} end={12} color='rgba(168,145,102,0.1)'></RangeDirective>
        </RangesDirective>
        <AnnotationsDirective>
            <AnnotationDirective content='<div id="subGauge" style="width:90px;height:90px;"></div>' angle= {270} radius = '40%'/>
            <AnnotationDirective content='<div id="time"><span>6:30 PM</span></div>' angle= {90} radius = '40%'/>
        </AnnotationsDirective>
        <PointersDirective>
            <PointerDirective pointerWidth= {5} radius= '40%' value= {6.5} color= 'rgb(29,29,29)' border = {{ width: 1, color: 'rgb(29,29,29)' }} cap = {{
                color: 'rgb(29,29,29)',
                radius: 0,
                border: {
                    width: 0.2,
                    color: 'red'
                }
            }} needleTail = {{
                length: '0%'
            }} animation = {{
                enable: false
            }}></PointerDirective>
            <PointerDirective radius= '60%' value = {6} pointerWidth= {5} color= 'rgb(29,29,29)'  border = {{
                width: 1,
                color: 'rgb(29,29,29)'
            }} cap = {{
                color: 'rgb(29,29,29)',
                radius: 0,
                border: {
                    width: 0.2,
                    color: 'red'
                }
            }} needleTail = {{
                length: '0%'
            }} animation = {{
                enable: false
            }}></PointerDirective>
            <PointerDirective radius= '70%' pointerWidth= {4} value= {9.8}
            color= 'rgba(168,145,102,1)' cap = {{
                color: 'rgba(168,145,102,1)',
                radius: 4,
                border: {
                    width: 0.2,
                    color: 'rgba(168,145,102,1)'
                }
            }} needleTail = {{
                color: 'rgba(168,145,102,1)',
                length: '20%'
            }} animation = {{
                enable: false,
                duration: 500
            }}></PointerDirective>
        </PointersDirective>
      </AxisDirective>
    </AxesDirective>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}

## See also

* [Tooltip for Annotation](https://ej2.syncfusion.com/documentation/circular-gauge/gauge-user-interaction/tooltip-for-ranges-and-annotations/)
