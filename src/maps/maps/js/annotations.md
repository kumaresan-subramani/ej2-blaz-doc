# Annotations

<!-- markdownlint-disable MD013 -->

Annotations are used to mark the specific area of interest in the map area with texts, shapes, or images. You can add any number of annotations to the maps.

## Annotation

By using the [`content`](../api/maps/annotation/#content-string) property of [`annotation`](../api/maps/annotation) object, you can either specify the id of an element or specify the code to create a new element that needs to be displayed in the gauge area.

<!-- markdownlint-disable MD036 -->

 ```html
<script id='annotation' type="text/x-template">
    <div id='template'>
        <img src='src/maps/images/flight.png'>
    </div>
</script>

```

```typescript

var maps = new ej.maps.Maps({
        annotations: [
            {
                content: '#annotation',
                x: '0%', y: '50%'
            }
        ],
        layers: [
            {
                shapeData: world_map,
            }
        ]
    });
    maps.appendTo('#element');

```

## Annotation Customization

**Changing the z-order**

You can change the z-order of an annotation element using the [`zIndex`](./api/maps/annotation/#zindex-string) property.

{% tab template= "maps/default-map", es5Template="annotationZOrder" %}

{% endtab %}

<!-- markdownlint-disable MD036 -->

**Positioning of Annotation**

You can place an annotation anywhere in gauge area by specifying pixel values to the [`x`](./api/maps/annotation/#x-number) and [`y`](./api/maps/annotation/#y-number) properties.

{% tab template= "maps/default-map", es5Template="annotationPosition" %}

{% endtab %}

<!-- markdownlint-disable MD036 -->

**Alignment of Annotation**

You can align annotations using the [`horizontalAlignment`](./api/maps/annotation/#horizontalalignment-string) and [`verticalAlignment`](./api/maps/annotation/#verticalalignment-string) properties.

{% tab template= "maps/default-map", es5Template="annotationAlignment" %}

{% endtab %}