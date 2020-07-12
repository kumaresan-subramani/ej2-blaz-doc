# Navigation Lines

The navigation lines are used to denote path between two locations. We can use this feature to draw the flight or train or sea routes.

## Customization

You can customize the following properties in the navigation lines by modifying their default values in `navigationlineSettings`

* Color - Specifies the color of navigation line.
* Dash array - Specifies the type of dash array line.
* Width - Specifies the line width.
* Angle - Specifies the navigation line angle.
* Highlight settings - Customizes the opacity, border, and fill color when the cursor hovers over it.
* Selection settings - Customizes the opacity, border, and fill color when the line is selected.

Following example shows rendering the path between two locations using latitudes and longitudes.

Yon can customize the navigation line color, dashArray, width and angle by modifying their default values in
`navigationLineSettings`.

Refer the below code snippet to navigate line between two cities in World map.
Import usmap geo json data from world_map.ts file.
Import the `NavigationLine` Module and Inject into the Maps using `Maps.Inject(NavigationLine)`.
Provide two locations latitude and longitude values to `navigationLineSettings`.

{% tab template= "maps/default-map", es5Template="navigation" %}

{% endtab %}

## Enabling the arrows

You can enable the arrows in the navigation line using [`arrowSettings.showArrow`](../api/maps/arrow) API, also you can customize following properties in arrow

* color - Specifies the color of the arrow
* offset - Specifies the arrow's offset position
* position - Specifies the arrow position to `start` or `end` line
* size - Specifies the arrow size in pixel

{% tab template= "maps/default-map", es5Template="arrowSettings" %}

{% endtab %}

Refer the [`API`](../api/maps/navigationLineSettingsModel/) for Navigation Lines feature.