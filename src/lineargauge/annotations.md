# Annotations

<!-- markdownlint-disable MD013 -->

Annotations are used to mark the specific area of interest in the gauge area with texts, shapes or images. You can add any number of annotations to the gauge.

## Annotation

By using the [`content`](../api/linear-gauge/annotation/#content-string) property of [`annotation`](../api/linear-gauge/annotation) object, you can either specify the id of the element or specify the code to create a new element, that needs to be displayed in the gauge area.

<!-- markdownlint-disable MD036 -->

 ```html
<script id='fruits' type="text/x-template">
    <div id='apple'>
        <img src='src/lineargauge/images/apple.png'>
    </div>
</script>

```

```typescript

import { LinearGauge, Annotations } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(Annotations);
let gauge: LinearGauge = new LinearGauge({
    annotations: [{
        content: 'fruits',
        x: 100,
        y: 100
    }]
}, '#element');

```

## Annotation Customization

You can customize the annotation using following properties.

* [`zIndex`](../api/linear-gauge/annotation/#zindex-string) - When annotation overlaps with another element, you can use this property to bring annotation to the front or back.
* [`horizontalAlignment`](../api/linear-gauge/annotation#horizontalalignment-string) - To move annotation horizontally. Possible values are "Center", "Far", "Near", "None"
* [`verticalAlignment`](../api/linear-gauge/annotation#verticalalignment-string) - To move annotation vertically. Possible values are "Center", "Far", "Near", "None"
* [`x`](../api/linear-gauge/annotation/#x-number) and [`y`](../api/linear-gauge/annotation/#y-number) - To move annotation to the specified location.

**Changing the z-order**

You can change the z-order of the annotation element by using the [`zIndex`](../api/linear-gauge/annotation/#zindex-string) property.

{% tab template= "linear-gauge/annotations", sourceFiles="index.ts,index.html", es5Template="es5Annotation" %}

```typescript

import { LinearGauge, Annotations } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(Annotations);
let gauge: LinearGauge = new LinearGauge({
     annotations: [{
       content: '<div id="first"><h1>Gauge</h1></div>',
       verticalAlignment: 'Center',
       horizontalAlignment: 'Center',
       zIndex: '1'
    }]
}, '#element');

```

{% endtab %}

**Positioning the Annotation**

You can place the annotation anywhere in gauge area by specifying pixel values to the [`x`](../api/linear-gauge/annotation/#x-number) and [`y`](../api/linear-gauge/annotation/#y-number) properties.

{% tab template= "linear-gauge/annotations", sourceFiles="index.ts,index.html", es5Template="es5Position" %}

```typescript

import { LinearGauge, Annotations } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(Annotations);
let gauge: LinearGauge = new LinearGauge({
    annotations: [{
        content: '<div id="first"><h1>Gauge</h1></div>',
        x: 100,
        y: 100,
        zIndex: '1'
    }]
}, '#element');

```

{% endtab %}

<!-- markdownlint-disable MD036 -->

**Alignment of Annotation**

You can align the annotation using [`horizontalAlignment`](../api/linear-gauge/annotation#horizontalalignment-string) and [`verticalAlignment`](../api/linear-gauge/annotation#verticalalignment-string) properties.

{% tab template= "linear-gauge/annotations", sourceFiles="index.ts,index.html", es5Template="es5Alignment" %}

```typescript

import { LinearGauge, Annotations } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(Annotations);
let gauge: LinearGauge = new LinearGauge({
    annotations: [{
       content: '<div id="first"><h1>Gauge</h1></div>',
       verticalAlignment: 'Center',
       horizontalAlignment: 'Center',
       zIndex: '1'
    }]
}, '#element');

```

{% endtab %}

## Multiple Annotations

You can add multiple annotations to the gauge as demonstrated below.

{% tab template= "linear-gauge/annotations", sourceFiles="index.ts,index.html", es5Template="es5MultipleAnnotation" %}

```typescript

import { LinearGauge, Annotations } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(Annotations);
let gauge: LinearGauge = new LinearGauge({
      annotations: [
            {
                content: '<div id="first"><h1 style="color:red;">Speed</h1></div>',
                verticalAlignment: 'Near',
                horizontalAlignment: 'Center',
                x: 100,
                y: 150,
                zIndex: '1'
            },
            {
                content: '<div id="first"><h1 style="color:blue;">Meter</h1></div>',
                verticalAlignment: 'Center',
                horizontalAlignment: 'Center',
                x: -100,
                y: -100,
                zIndex: '1'
            }]
}, '#element');

```

{% endtab %}