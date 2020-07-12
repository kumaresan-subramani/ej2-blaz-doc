# Legend

A legend is a key used on a map that contains swatches of symbols with descriptions. This provides valuable information for interpreting what the map displays; it can be represented in various colors, shapes or other identifiers based on the data. Legends give a breakdown of what each symbol represents throughout the map.

## Visibility

The legends can be made visible by setting the visible property of legendSettings to true.

## Positioning of the legend

The legend can be positioned in the following ways:

* Absolute position.

* Dock position.

### Absolute position

Based on the margin values of x and y-axes, the legends can be positioned using the `location.x` and `location.y` properties available in legendSettings. For positioning the legend based on margins corresponding to a map, set the value of position to ‘Float’.

### Dock position

The legends can be positioned in following locations within the container.
You can set the following options by using the `position` property in legendSettings.

* Top

* Left

* Bottom

* Right

The above four positions can be aligned with the combination of 'Near', 'Center' and 'Far' using the `alignment` property in `legendSettings`. So, the legends can be aligned to 12 positions.

## Legend Mode

Legend had two type of mode. `Default` mode and `Interactive` mode.

### Default mode

The default mode legends have symbols with legend labels that are used to identify the shape, bubble or marker color.

### Interactive mode

The legends can be made interactive with an arrow mark that indicates the exact range color in the legend when the mouse hovers over the corresponding shapes. You can enable this option by setting the value of the `mode` property in legendSettings value to “Interactive” and the default value of the `mode` property to“Default” to enable the normal legend.

## Legend size

The map legend size can be modified by using the `height` and `width` properties in `legendSettings`.

## Legend for shapes

The layer shape type legends can be generated for each color mappings in shape settings.

**Note:** The following code sample demonstrates the equal colorMapping legends for the shapes.

```sh
[
    { value: 5, State: "Alabama", Candidate: "Trump", Trump:62.9,Clinton:34.6 },
    { value: 5, State: "Alaska", Candidate: "Trump", Trump:52.9,Clinton:37.7},
    { value: 5, State: "Arkansas", Candidate: "Trump", Trump:60.6,Clinton:33.7 },
    { value: 5, State: "Arizona", Candidate: "Trump", Trump:49.5,Clinton:45.4 },
    { value: 1, State: "California", Candidate: "Clinton", Trump:32.8,Clinton:61.6},
    { value: 1, State: "Colorado", Candidate: "Clinton", Trump:47.3,Clinton:44.4 },
    { value: 1, State: "Connecticut", Candidate: "Clinton", Trump:41.2,Clinton:54.5},
    { value: 1, State: "Delaware", Candidate: "Clinton", Trump:53.4,Clinton:41.9 },
    { value: 1, State: "District of Columbia",  Candidate: "Clinton", Trump:4.1,Clinton:92.8},
    { value: 5, State: "Florida", Candidate: "Trump", Trump:49.1,Clinton:47.8 },
    { value: 5, State: "Georgia", Candidate: "Trump", Trump:51.3,Clinton:45.6 },
    { value: 1, State: "Hawaii", Candidate: "Clinton", Trump:62.2,Clinton:30 },
    { value: 5, State: "Idaho", Candidate: "Trump", Trump:59.2,Clinton:27.6  },
    { value: 1, State: "Illinois", Candidate: "Clinton", Trump:55.4,Clinton:39.4  },
    { value: 5, State: "Indiana", Candidate: "Trump", Trump:57.2,Clinton:37.9  },
    { value: 5, State: "Iowa", Candidate: "Trump", Trump:51.8,Clinton:42.2  },
    { value: 5, State: "Kansas", Candidate: "Trump", Trump:57.2,Clinton:36.2 },
    { value: 5, State: "Kentucky", Candidate: "Trump", Trump:62.5,Clinton:32.7  },
    { value: 5, State: "Louisiana", Candidate: "Trump", Trump:58.1,Clinton:38.4  },
    { value: 1, State: "Maine", Candidate: "Clinton", Trump:45.2,Clinton:47.9 },
    { value: 1, State: "Maryland", Candidate: "Clinton", Trump:35.3,Clinton:60.5  },
    { value: 1, State: "Massachusetts", Candidate: "Clinton", Trump:33.5,Clinton:60.8 },
    { value: 5, State: "Michigan", Candidate: "Trump", Trump:47.6,Clinton:47.3  },
    { value: 1, State: "Minnesota", Candidate: "Clinton", Trump:45.4,Clinton:46.9 },
    { value: 5, State: "Mississippi", Candidate: "Trump", Trump:58.3,Clinton:39.7  },
    { value: 5, State: "Missouri", Candidate: "Trump", Trump:57.1,Clinton:38.0  },
    { value: 5, State: "Montana", Candidate: "Trump", Trump:56.5,Clinton:36.0 },
    { value: 5, State: "Nebraska", Candidate: "Trump", Trump:60.3,Clinton:34.0  },
    { value: 1, State: "Nevada", Candidate: "Clinton", Trump:45.5,Clinton:47.9  },
    { value: 1, State: "New Hampshire", Candidate: "Clinton", Trump:47.2,Clinton:47.6  },
    { value: 1, State: "New Jersey", Candidate: "Clinton", Trump:41.8,Clinton:55.0},
    { value: 1, State: "New Mexico", Candidate: "Clinton", Trump:40.0,Clinton:48.3  },
    { value: 1, State: "New York", Candidate: "Clinton", Trump:37.5,Clinton:58.8 },
    { value: 5, State: "North Carolina", Candidate: "Trump", Trump:50.5,Clinton:46.7 },
    { value: 5, State: "North Dakota", Candidate: "Trump", Trump:64.1,Clinton:27.8 },
    { value: 5, State: "Ohio", Candidate: "Trump", Trump:52.1,Clinton:43.5 },
    { value: 5, State: "Oklahoma", Candidate: "Trump", Trump:65.3,Clinton:28.9 },
    { value: 1, State: "Oregon", Candidate: "Clinton", Trump:41.1,Clinton:51.7  },
    { value: 5, State: "Pennsylvania", Candidate: "Trump", Trump:48.8,Clinton:47.6 },
    { value: 1, State: "Rhode Island", Candidate: "Clinton", Trump:39.8,Clinton:55.4 },
    { value: 5, State: "South Carolina", Candidate: "Trump", Trump:54.9,Clinton:40.8 },
    { value: 5, State: "South Dakota", Candidate: "Trump", Trump:61.5,Clinton:31.7 },
    { value: 5, State: "Tennessee", Candidate: "Trump", Trump:61.1,Clinton:34.9 },
    { value: 5, State: "Texas", Candidate: "Trump", Trump:52.6,Clinton:43.4  },
    { value: 5, State: "Utah", Candidate: "Trump", Trump:45.9,Clinton:27.8  },
    { value: 1, State: "Vermont", Candidate: "Clinton", Trump:39.7,Clinton:61.1  },
    { value: 1, State: "Virginia", Candidate: "Clinton", Trump:45.0,Clinton:49.9 },
    { value: 1, State: "Washington", Candidate: "Clinton", Trump:4.1,Clinton:92.8  },
    { value: 5, State: "Wisconsin", Candidate: "Trump", Trump:68.7,Clinton:26.5 },
    { value: 5, State: "West Virginia", Candidate: "Trump", Trump:47.9,Clinton:46.9  },
    { value: 5, State: "Wyoming", Candidate: "Trump", Trump:70.1,Clinton:22.5  }
    ]
```

Provide the `shapePropertyPath` value as 'name and `shapeDataPath` value as 'State'. To enable the equal colormapping refer the `shapeSettings.colorMapping` code sample. Finally set `legendSettings.visible` as true.

{% aspTab template="maps/legend", sourceFiles="legend.cs" %}

{% endaspTab %}

## Legend shape

To get the legend shape value for `legendSettings` use the `shape` property. You can customize the shape by using the `shapeWidth` and `shapeHeight` properties.

## Legend for items excluded from color mapping

Based on the ranges in data source, get the excluded ranges from color mapping, and then show the legend with excluded range values are bound to the specific legend.

The following code example shows legends for the items excluded from color mapping.

{% aspTab template="maps/legendproperties/excludelegend", sourceFiles="excludelegend.cs" %}

{% endaspTab %}

## Hide desired legend items

To enable or disable the desired legend for each colormapping, set the `showLegend` property to `true` in `colorMapping`.

{% aspTab template="maps/legendproperties/hidelegend", sourceFiles="hidelegend.cs" %}

{% endaspTab %}

## Hide legend items based data source value

To enable or disable the legend visibility for each item, bind the field name in the data source to the `showLegendPath` property in `legendSettings`.

The following code example shows how to hide the legend items based data source value.

{% aspTab template="maps/legendproperties/hidelegendbasedDS", sourceFiles="hidelegendbasedDS.cs" %}

{% endaspTab %}

## Bind legend item text from data source

To show the legend text based on binding, the field name in the datasource should be set to the `valuePath` property in `legendSettings`.

{% aspTab template="maps/legendproperties/bindlegendtext", sourceFiles="bindlegendtext.cs" %}

{% endaspTab %}

## Hide duplicate legend items

To enable or disable the duplicate legend items, set the property `removeDuplicateLegend` property to `true` in `legendSettings`.

{% aspTab template="maps/legendproperties/duplicatelegend", sourceFiles="duplicatelegend.cs" %}

{% endaspTab %}

## Toggle option in legend

The toggle option has been provided for legend. So, if you toggle a legend, the given color will be changed to the corresponding maps shape item. You can enable the toggle options using the `toggleLegendSettings` property.

The following options are available to customize the shape of the map:

* `applyShapeSettings` – Applies the fill property value in shapeSettings to a shape of the maps if it is true and a legend item is clicked.
* `fill`- Specifies the color to the shape of the maps.
* `opacity` – Specifies the transparency of the legend.
* `border` – Specifies the border color and width.

The following code example demonstrates how to add the toggle option to legend.

{% aspTab template="maps/legendproperties/togglelegend", sourceFiles="togglelegend.cs" %}

{% endaspTab %}

Refer to the [`API`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsLegendSettings.html) for legend feature.