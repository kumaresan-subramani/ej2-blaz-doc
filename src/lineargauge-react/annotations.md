# Annotations

<!-- markdownlint-disable MD013 -->

Annotations are used to mark the specific area of interest in the gauge area with texts, shapes or images. You can add any number of annotations to the gauge.

## Annotation

By using the [`content`](../api/linear-gauge/annotation/#content-string) property of [`annotation`](../api/linear-gauge/annotation/) object, you can either specify the id of the element or specify the code to create a new element, that needs to be displayed in the gauge area.

<!-- markdownlint-disable MD036 -->

 ```html

<script id='fruits' type="text/x-template">
    <div id='apple'>
        <img src='src/lineargauge/images/apple.png'>
    </div>
</script>

```

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { LinearGaugeComponent, AnnotationsDirective, AnnotationDirective, Annotations, Inject } from '@syncfusion/ej2-react-lineargauge';

ReactDOM.render(
    <LinearGaugeComponent id='gauge'>
    <Inject services={[Annotations]}/>
        <AnnotationsDirective>
            <AnnotationDirective content='fruits' x={100} y={100}>
            </AnnotationDirective>
        </AnnotationsDirective>
    </LinearGaugeComponent>,document.getElementById('gauge'));

```

## Annotation Customization

You can customize the annotation using following properties.

* [`zIndex`](../api/linear-gauge/annotation/#zindex-string) - When annotation overlaps with another element, you can use this property to bring annotation to the front or back.
* [`horizontalAlignment`](../api/linear-gauge/annotation#horizontalalignment-string) - To move annotation horizontally. Possible values are "Center", "Far", "Near", "None"
* [`verticalAlignment`](../api/linear-gauge/annotation#verticalalignment-string) - To move annotation vertically. Possible values are "Center", "Far", "Near", "None"
* [`x`](../api/linear-gauge/annotation/#x-number) and [`y`](../api/linear-gauge/annotation/#y-number) - To move annotation to the specified location.

**Changing the z-order**

You can change the z-order of the annotation element by using the [`zIndex`](../api/linear-gauge/annotation/#zindex-string) property.

{% tab template="linear-gauge/annotations", compileJsx=true sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { LinearGaugeComponent, AnnotationsDirective, AnnotationDirective, Annotations,Inject } from '@syncfusion/ej2-react-lineargauge';

ReactDOM.render(
    <LinearGaugeComponent id='gauge'>
    <Inject services={[Annotations]}/>
        <AnnotationsDirective>
            <AnnotationDirective content='<div id="first"><h1>Gauge</h1></div>' verticalAlignment='Center' horizontalAlignment='Center' zIndex='-1'>
            </AnnotationDirective>
        </AnnotationsDirective>
    </LinearGaugeComponent>,document.getElementById('gauge'));

```

{% endtab %}

**Positioning the Annotation**

You can place the annotation anywhere in gauge area by specifying pixel values to the [`x`](../api/linear-gauge/annotation/#x-number) and [`y`](../api/linear-gauge/annotation/#y-number) properties.

{% tab template="linear-gauge/annotations", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { LinearGaugeComponent, AnnotationsDirective, AnnotationDirective, Annotations, Inject } from '@syncfusion/ej2-react-lineargauge';

ReactDOM.render(
    <LinearGaugeComponent id='gauge'>
    <Inject services={[Annotations]}/>
        <AnnotationsDirective>
            <AnnotationDirective content='<div id="first"><h1>Gauge</h1></div>' x={100} y={100}>
            </AnnotationDirective>
        </AnnotationsDirective>
    </LinearGaugeComponent>,document.getElementById('gauge'));

```

{% endtab %}

<!-- markdownlint-disable MD036 -->

**Alignment of Annotation**

You can align the annotation using [`horizontalAlignment`](../api/linear-gauge/annotation/#horizontalalignment-string) and [`verticalAlignment`](../api/linear-gauge/annotation/#verticalalignment-string) properties.

{% tab template="linear-gauge/annotations", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { LinearGaugeComponent, AnnotationsDirective, AnnotationDirective, Annotations, Inject } from '@syncfusion/ej2-react-lineargauge';

ReactDOM.render(
    <LinearGaugeComponent id='gauge'>
    <Inject services={[Annotations]}/>
        <AnnotationsDirective>
            <AnnotationDirective content='<div id="first"><h1>Gauge</h1></div>' verticalAlignment='Center' horizontalAlignment='Center'>
            </AnnotationDirective>
        </AnnotationsDirective>
    </LinearGaugeComponent>,document.getElementById('gauge'));

```

{% endtab %}

## Multiple Annotations

You can add multiple annotations to the gauge as demonstrated below.

{% tab template="linear-gauge/annotations", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { LinearGaugeComponent, AnnotationsDirective, AnnotationDirective, Annotations, Inject } from '@syncfusion/ej2-react-lineargauge';

ReactDOM.render(
    <LinearGaugeComponent id='gauge'>
    <Inject services={[Annotations]}/>
        <AnnotationsDirective>
            <AnnotationDirective content='<div id="first"><h1 style="color:red;">Speed</h1></div>' verticalAlignment='Near' horizontalAlignment='Center' x={100} y={150}>
            </AnnotationDirective>
            <AnnotationDirective content='<div id="first"><h1 style="color:blue;">Meter</h1></div>' verticalAlignment='Center' horizontalAlignment='Center' x={-100} y={-100}>
            </AnnotationDirective>
        </AnnotationsDirective>
    </LinearGaugeComponent>,document.getElementById('gauge'));

```

{% endtab %}
