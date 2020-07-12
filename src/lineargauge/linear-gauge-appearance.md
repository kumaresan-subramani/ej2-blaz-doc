
# Appearance

## Gauge Area Customization

<!-- markdownlint-disable MD036 -->

**Customize the Linear Gauge background**

Using [`background`](../api/linear-gauge/linearGaugeModel/#background-string) and
[`border`](../api/linear-gauge/linearGaugeModel/#border-bordermodel) properties, you can change the background color and border of the linear gauge.

{% tab template= "linear-gauge/lineargauge-appearance", sourceFiles="index.ts,index.html", es5Template="es5Background" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
    background: 'skyblue',
    border: { color: "#FF0000", width: 2 }
}, '#element');

```

{% endtab %}

**Gauge Margin**

You can set margin for the lineargauge through [`margin`](../api/linear-gauge/marginModel) property.

{% tab template= "linear-gauge/lineargauge-appearance", sourceFiles="index.ts,index.html", es5Template="es5Margin" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
    margin: { left: 40, right: 40, top: 40, bottom: 40 }
}, '#element');

```

{% endtab %}

## Gauge Title

You can give the title using [`title`](../api/linear-gauge/linearGaugeModel/#title-string) property to show the information about the linear gauge. Its appearance can be customized by using the [`titleStyle`](../api/linear-gauge/linearGaugeModel/#titlestyle-fontmodel) property.

{% tab template= "linear-gauge/lineargauge-appearance", sourceFiles="index.ts,index.html", es5Template="es5TitleCustomization" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
        //Title for linear gauge
        title: 'linear gauge',
        titleStyle: {
            fontFamily: "Arial",
            fontStyle: 'italic',
            fontWeight: 'regular',
            color: "#E27F2D",
            size: '23px'
        }
}, '#element');

```

{% endtab %}

## Gauge Container

The area used to render the ranges and pointers at the center position of the gauge is called [`container`](../api/linear-gauge/containerModel). It can be customized by using [`type`](../api/linear-gauge/containerModel/#type-string), [`offset`](../api/linear-gauge/containerModel/#offset-number), [`width`](../api/linear-gauge/containerModel/#width-number), [`height`](../api/linear-gauge/containerModel/#height-number) and [`backgroundColor`](../api/linear-gauge/containerModel/#backgroundcolor-string) properties in [`container`](../api/linear-gauge/containerModel). It is of three types namely,

* Normal
* Rounded Rectangle
* Thermometer

**Normal**

The normal type will render the container as rectangle and this is the default container type.

{% tab template= "linear-gauge/lineargauge-appearance", sourceFiles="index.ts,index.html", es5Template="es5NormalContainer" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
    container: {
        height: 300,
        width: 30
    },
    axes: [{
        pointers: [{
            value:50,
            width:15,
            type:'Bar'
        }]
    }]
}, '#element');

```

{% endtab %}

**Rounded Rectangle**

The rounded rectangle type will render the container as rectangle with rounded corners.

{% tab template= "linear-gauge/lineargauge-appearance", sourceFiles="index.ts,index.html", es5Template="es5RoundedContainer" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
      container: {
        height: 300,
        width: 30,
        type: 'RoundedRectangle'
    },
    axes: [{
        pointers: [{
            value:50,
            width:15,
            type:'Bar'
        }]
    }]
}, '#element');

```

{% endtab %}

**Thermometer**

This type is used to render the container similar to the thermometer appearance.

{% tab template= "linear-gauge/lineargauge-appearance", sourceFiles="index.ts,index.html", es5Template="es5ThermometerContainer" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
     container: {
        height: 300,
        width: 30,
        type: 'Thermometer'
    },
    axes: [{
        pointers: [{
            value:50,
            width:15,
            type:'Bar'
        }]
    }]
}, '#element');

```

{% endtab %}