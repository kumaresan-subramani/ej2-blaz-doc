# Navigation lines

Navigation lines are used to denote the path between the two locations. You can use this feature to draw the navigation lines for flight, train or sea routes.

## Customization

You can customize the following properties in the navigation lines by modifying their default values in `navigationlineSettings`

* Color - Specifies the color of navigation line.
* Dash array - Specifies the type of dash array line.
* Width - Specifies the line width.
* Angle - Specifies the navigation line angle.
* Highlight settings - Customizes the opacity, border, and fill color when the cursor hovers over it.
* Selection settings - Customizes the opacity, border, and fill color when the line is selected.

The following example shows rendering the path between two locations using latitudes and longitudes.

You can customize the navigation line color, dashArray, width and angle by modifying their default values in
`navigationLineSettings`.

Refer to the following code sample to navigate the line between two cities in World map. Provide two locations latitude and longitude values to `navigationLineSettings`.

{% aspTab template="maps/navigation-line", sourceFiles="navigation-line.cs" %}

{% endaspTab %}

## Enabling the arrows

You can enable the arrows in the navigation line using [`arrowSettings.showArrow`](../api/maps/arrow) API, also you can customize following properties in arrow

* color - Specifies the color of the arrow
* offset - Specifies the arrow's offset position
* position - Specifies the arrow position to `start` or `end` line
* size - Specifies the arrow size in pixel

{% aspTab template="maps/navigation-line/arrowSettings", sourceFiles="arrow.cs" %}

{% endaspTab %}

Refer to the [`API`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsNavigationLine.html) for Navigation Lines feature.