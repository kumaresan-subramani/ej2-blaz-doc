# Bubble

Bubbles in the Maps control represent the underlying data values of the map. Bubbles are scattered throughout the map shapes that contains bound values.

Bubbles are included when data binding and the `bubbleSettings` is set to the shape layers.

To add bubbles to the map, bind data source to the layer `bubbleSettings` and set the `valuePath` as population. Following example illustrates bubble enable for the World map with **datasource**.
To render bubble in maps need to inject `Bubble` module using `Maps.Inject(Bubble)` method.

{% tab template="maps/default-map", es5Template="bubble" %}

{% endtab %}

## Bubble Sizing

Using the `minRadius` and `maxRadius` properties in `bubbleSettings`, you can render the bubbles in different sizes based on the `valuePath` and `dataSource` values.

{% tab template="maps/default-map", es5Template="bubbleSizing" %}

{% endtab %}

## Multiple bubble groups

You can specify multiple types of bubble groups using the `bubbleSettings` property and customize it according to your requirement.

In the following code example, the gender-wise population ratio is demonstrated with two different bubble groups.

{% tab template="maps/default-map", es5Template="bubbleGroup" %}

{% endtab %}

## Enable Legend for Bubble

To enable the legend for the bubble, need to set `legendSettings.visible` as true and `legendSettings.type` as 'Bubbles'.Refer the below code snippet to enable the legend for bubbles with each bubble different colors rendering.

{% tab template="maps/default-map", es5Template="bubble-legend" %}

{% endtab %}

Refer the [`API`](../api/maps/bubbleSettingsModel/) for Bubble feature.