# Bubble

Bubbles in the maps control represent the underlying data values of the map. Bubbles are scattered throughout the map shapes that contains bound values.

Bubbles are included when the data binding and the `bubbleSettings` are set to the shape layers.

To add bubbles to the map, bind the data source to the layer `bubbleSeetings` and set the `valuePath` to population. The following example illustrates enabling the bubbles  for the world map with **datasource**.

{% aspTab template="maps/bubble/bubble", sourceFiles="bubble.cs" %}

{% endaspTab %}

## Bubble Sizing

Using the `minRadius` and `maxRadius` properties in `bubbleSettings`, you can render the bubbles in different sizes based on the `valuePath` and `dataSource` values

{% aspTab template="maps/bubble/bubblesize", sourceFiles="bubblesize.cs" %}

{% endaspTab %}

## Enable legends for bubbles

To enable the legends for bubbles, set the `legendSettings.visible` to true and `legendSettings.type` to 'Bubbles'. Refer to the following code sample to enable the legend for each bubbles with different colors.

{% aspTab template="maps/bubble/bubble-legend", sourceFiles="bubble-legend.cs" %}

{% endaspTab %}

Refer to the [`API`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsBubble.html) for bubble feature.
