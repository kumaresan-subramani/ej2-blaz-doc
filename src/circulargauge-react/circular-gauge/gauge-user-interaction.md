
# User Interaction

## Tooltip for pointers

Circular gauge will displays the pointer details through [tooltip](../api/circular-gauge/tooltipSettings/),
when the mouse is moved over the pointer.

<!-- markdownlint-disable MD036 -->

## Tooltip for ranges

Circular gauge displays the information about the ranges through tooltip when hovering the mouse over the ranges. You can enable this feature by setting the type property of tooltip to ‘Range’ in the array collection.

**Tooltip customization for ranges**

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

**Tooltip customization for annotation**

To customize the annotation tooltip, use the `annotationSettings` property in tooltip. The following options are available to customize the annotation tooltip:

* fill - Specifies the annotation tooltip fill color.

* textStyle - Specifies the annotation tooltip text style.

* format - Specifies the annotation content format.

* template - Specifies the tooltip content with custom template.

* enableAnimation - Animates as it moves from one point to another.

* border - Specifies the tooltip border.

The following code example shows the tooltip for the pointers, ranges and annotation.

{% tab template="circulargauge/gauge-user-interaction", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, RangesDirective, AnnotationsDirective, AnnotationDirective, RangeDirective, AxesDirective, AxisDirective, PointersDirective, PointerDirective, Inject, GaugeTooltip } from '@syncfusion/ej2-react-circulargauge';

class App extends React.Component<{}, {}>{
    render() {
        return  <CircularGaugeComponent id='circulargauge' tooltip={{
                               type:['Pointer', 'Range', 'Annotation'],
                               enable: true,
                                enableAnimation: false,
                                annotationSettings: { template:'<div>CircularGauge</div>' },
                                rangeSettings: { fill:'red' }
                              }}
                    >
                  <Inject services={[ GaugeTooltip ]}/>
                  <AxesDirective>
                                <AxisDirective startAngle={240} endAngle={120} radius='90%' minimum={0} maximum={120}
                                    majorTicks={{
                                        color: 'white', offset: -5, height: 12
                                    }}
                                    lineStyle={{ width: 0 }}
                                    minorTicks={{
                                        width: 0
                                    }} labelStyle={{
                                        useRangeColor: true, font: { color: '#424242', size: '13px', fontFamily: 'Roboto' }
                                    }}>
                                    <AnnotationsDirective>
                                          <AnnotationDirective content='Circular Gauge' angle= {180} zIndex= {1} radius = '40%'/>
                                   </AnnotationsDirective>
                                    <PointersDirective>
                                        <PointerDirective value={70} radius='60%'
                                            cap={{
                                                radius: 10, border: { color: '#33BCBD', width: 5 }
                                            }}
                                            animation={{
                                                enable: true, duration: 1500
                                            }} color='#33BCBD' />
                                    </PointersDirective>
                                    <RangesDirective>
                                        <RangeDirective start={0} end={50} radius='102%' color='#3A5DC8' startWidth={10} endWidth={10} />
                                        <RangeDirective start={50} end={120} radius='102%' color='#33BCBD' startWidth={10} endWidth={10} />
                                    </RangesDirective>
                                </AxisDirective>
                            </AxesDirective>
                </CircularGaugeComponent>
    }
}
ReactDOM.render(<App />, document.getElementById('circulargauge'));
```

{% endtab %}

<!-- markdownlint-disable MD036 -->

**Template**

Any HTML elements can be displayed in the tooltip by using the
[`template`](../api/circular-gauge/tooltipSettings/#template-string) property of the tooltip.

{% tab template="circulargauge/gauge-user-interaction", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, AxesDirective, AxisDirective, PointersDirective, PointerDirective, Inject, GaugeTooltip } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge' tooltip= {{
        enable: true,
        template: '<div id="templateWrap"><div style="float: right; padding-left:10px; line-height:30px;"><span>Pointer &nbsp;&nbsp;:&nbsp; ${Math.round(pointers[0].value)}</span></div></div>'
    }}>
    <Inject services={[ GaugeTooltip ]}/>
    <AxesDirective>
      <AxisDirective>
        <PointersDirective>
            <PointerDirective value = {70}></PointerDirective>
        </PointersDirective>
      </AxisDirective>
    </AxesDirective>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}

## Pointer Drag

Pointers can be dragged over the axis value.
This can be achieved by clicking and dragging the pointer.
To enable or disable the pointer drag, you can use [`enablePointerDrag`](../api/circular-gauge/#enablepointerdrag-boolean) property.

{% tab template="circulargauge/gauge-user-interaction", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, AxesDirective, AxisDirective, PointersDirective, PointerDirective, Inject, GaugeTooltip } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge' enablePointerDrag = {true} tooltip= {{
        enable: true,
        template: '<div id="templateWrap"><div style="float: right; padding-left:10px; line-height:30px;"><span>Pointer &nbsp;&nbsp;:&nbsp; ${Math.round(pointers[0].value)}</span></div></div>'
    }}>
    <Inject services={[ GaugeTooltip ]}/>
    <AxesDirective>
      <AxisDirective>
        <PointersDirective>
            <PointerDirective value = {70}></PointerDirective>
        </PointersDirective>
      </AxisDirective>
    </AxesDirective>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}