# Ranges

<!-- markdownlint-disable MD013 -->

You can categorize the axis values using [`start`](../api/linear-gauge/range/#start-number) and [`end`](../api/linear-gauge/range/#end-number) property in the [`ranges`](../api/linear-gauge/range/#properties). You can add any number of range for an axis by using array of range objects.

{% tab template="linear-gauge/ranges", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { LinearGaugeComponent, AxesDirective, AxisDirective, RangesDirective, RangeDirective } from '@syncfusion/ej2-react-lineargauge';

ReactDOM.render(
    <LinearGaugeComponent id='gauge'>
        <AxesDirective>
            <AxisDirective>
                <RangesDirective>
                    <RangeDirective start={50} end={80}>
                    </RangeDirective>
                </RangesDirective>
            </AxisDirective>
        </AxesDirective>
    </LinearGaugeComponent>,document.getElementById('gauge'));

```

{% endtab %}

## Ranges Customization

Ranges can be customized using the following properties.

* [`startWidth`](../api/linear-gauge/range/#startwidth-number) - Specifies start width of the range
* [`endWidth`](../api/linear-gauge/range/#endwidth-number) - Specifies end width of the range
* [`color`](../api/linear-gauge/range/#color-string) - Specifies color of the range
* `position` - Specifies the range bar position. Its possible values are 'inside' and 'outside'
* `Offset` - Specifies offset value from its default position
* `LinearGaugeRangeBorder` - Specifies range bar border color and width.
{% tab template="linear-gauge/ranges", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { LinearGaugeComponent, AxesDirective, AxisDirective, RangesDirective, RangeDirective } from '@syncfusion/ej2-react-lineargauge';

ReactDOM.render(
    <LinearGaugeComponent id='gauge'>
        <AxesDirective>
            <AxisDirective>
                <RangesDirective>
                    <RangeDirective start={50} end={80} statWidth={10} endWidth={20} color='red'>
                    </RangeDirective>
                </RangesDirective>
            </AxisDirective>
        </AxesDirective>
    </LinearGaugeComponent>,document.getElementById('gauge'));

```

{% endtab %}

## Multiple Ranges

You can add the multiple ranges to highlight the same axis.

{% tab template="linear-gauge/ranges", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { LinearGaugeComponent, AxesDirective, AxisDirective, RangesDirective, RangeDirective } from '@syncfusion/ej2-react-lineargauge';

ReactDOM.render(
    <LinearGaugeComponent id='gauge'>
        <AxesDirective>
            <AxisDirective>
                <RangesDirective>
                    <RangeDirective start={0} end={30} statWidth={10} endWidth={10} color='#41f47f'>
                    </RangeDirective>
                    <RangeDirective start={30} end={50} statWidth={10} endWidth={10} color='#f49441'>
                    </RangeDirective>
                    <RangeDirective start={50} end={100} statWidth={10} endWidth={10} color='#cd41f4'>
                    </RangeDirective>
                </RangesDirective>
            </AxisDirective>
        </AxesDirective>
    </LinearGaugeComponent>,document.getElementById('gauge'));

```

{% endtab %}

## Gradient Color

Gradient support allows to add multiple colors in the ranges and pointers of the linear gauge. The following gradient types are supported in the linear gauge.

* Linear Gradient
* Radial Gradient

### Linear Gradient

Using linear gradient, colors will be applied in a linear progression. The start value of the linear gradient can be set using the [`startValue`](../api/linear-gauge/linearGradient/#startvalue) property. The end value of the linear gradient will be set using the [`endValue`](../api/linear-gauge/linearGradient/#endvalue) property. The color stop values such as color, opacity and offset are set using [`colorStop`](../api/linear-gauge/linearGradient/#colorstop) property.

To apply linear gradient to the range, follow the below code sample.

{% tab template="linear-gauge/ranges", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { LinearGaugeComponent, AxesDirective, AxisDirective, PointersDirective, PointerDirective, RangesDirective, Gradient, Inject, RangeDirective } from '@syncfusion/ej2-react-lineargauge';

ReactDOM.render(
    <LinearGaugeComponent id='gauge' container={{width: 30, offset: 30}} orientation="Horizontal">
    <Inject services={[Gradient]}/>
        <AxesDirective>
            <AxisDirective minimum={0} maximum={100} line={{width: 0}} majorTicks={{width: 0, interval:25}}
                minorTicks={{width:  0}} labelStyle={{font: {color: '#424242'}, offset: 70}}>
                <PointersDirective>
                    <PointerDirective value={80} height={25} width={35} placement="Near" offset={-44} markerType="Triangle" color= '#f54ea2'>
                    </PointerDirective>
                </PointersDirective>
                <RangesDirective>
                    <RangeDirective start={0} end={80} startWidth={30} endWidth={30} color="#f54ea2" offset={30}
                        linearGradient = {{
                            startValue: '0%',
                            endValue: '100%',
                            colorStop: [
                            { color: '#fef3f9', offset: '0%', opacity: 1 },
                            { color: '#f54ea2', offset: '100%', opacity: 1 }]
                        }}>
                    </RangeDirective>
                </RangesDirective>
            </AxisDirective>
        </AxesDirective>
    </LinearGaugeComponent>,document.getElementById('gauge'));

```

{% endtab %}

### Radial Gradient

Using radial gradient, colors will be applied in circular progression. The inner circle position of the radial gradient will be set using the [`innerPosition`](../api/linear-gauge/radialGradient/#innerposition) property. The outer circle position of the radial gradient can be set using the [`outerPosition`](../api/linear-gauge/radialGradient/#outerposition) property. The color stop values such as color, opacity and offset are set using [`colorStop`](../api/linear-gauge/radialGradient/#colorstop) property.

To apply radial gradient to the range, follow the below code sample.

{% tab template="linear-gauge/ranges", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { LinearGaugeComponent, AxesDirective, AxisDirective, PointersDirective, PointerDirective, RangesDirective, Gradient, Inject, RangeDirective } from '@syncfusion/ej2-react-lineargauge';

ReactDOM.render(
    <LinearGaugeComponent id='gauge' container={{width: 30, offset: 30}} orientation="Horizontal">
    <Inject services={[Gradient]}/>
        <AxesDirective>
            <AxisDirective minimum={0} maximum={100} line={{width: 0}} majorTicks={{width: 0, interval: 25}}
                minorTicks={{width:  0}} labelStyle={{font: {color: '#424242'}, offset: 70}}>
                <PointersDirective>
                    <PointerDirective value={80} height={25} width={35} placement="Near" offset={-44} markerType="Triangle" color= '#f54ea2'>
                    </PointerDirective>
                </PointersDirective>
                <RangesDirective>
                    <RangeDirective start={0} end={80} startWidth={30} endWidth={30} color="#f54ea2" offset={30}
                        radialGradient = {{
                            radius: '65%',
                            outerPosition: { x: '50%', y: '70%' },
                            innerPosition: { x: '60%', y: '60%' },
                            colorStop: [
                            { color: '#fff5f5', offset: '5%', opacity: 0.9 },
                            { color: '#f54ea2', offset: '100%', opacity: 0.9 }]
                        }}>
                    </RangeDirective>
                </RangesDirective>
            </AxisDirective>
        </AxesDirective>
    </LinearGaugeComponent>,document.getElementById('gauge'));

```

{% endtab %}