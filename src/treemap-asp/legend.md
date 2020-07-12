# Legend

Legend is used to provide valuable information for interpreting what the tree map is displaying and can be represented in various colors, shapes or other identifiers based on data.

## Position and alignment

Legend position is used to place legend in various positions. Based on the legend position, the legend item will be aligned. For example, if the position is top or bottom, the legend items are placed by rows. If the position is left or right, the legend items are placed by columns.

The following options are available to customize the legend position:

* Top
* Bottom
* Left
* Right
* Float

The following code example shows the legend position.

{% aspTab template="treemap/legend/position", sourceFiles="position.cs" %}

{% endaspTab %}

Legend Alignment is used to align the legend items in specific location. The following options are available to customize the legend alignment:

* Near
* Center
* Far

The following code example shows legend alignment.

{% aspTab template="treemap/legend/align", sourceFiles="align.cs" %}

{% endaspTab %}

## Legend mode

The tree map control supports two different types of legend rendering modes such as `Default` and `Interactive`.

<!-- markdownlint-disable MD036 -->

**Default mode**

In default mode, legends have symbols with legend labels that are used to identify the items in tree map control.

The following code example shows the default mode of legends.

{% aspTab template="treemap/legend/default", sourceFiles="default.cs" %}

{% endaspTab %}

<!-- markdownlint-disable MD036 -->

**Interactive mode**

The legends can be made interactive with an arrow mark that indicates exact range color in legend when the mouse hovers over the corresponding shape. You can enable this option by setting the mode property in legendSettings value to “Interactive”. The default value of the mode property is “Default” to enable normal legend.

The following code example shows the interactive mode of legends.

{% aspTab template="treemap/legend/interactive", sourceFiles="interactive.cs" %}

{% endaspTab %}

## Legend size

You can customize the legend size by modifying the [`height`] and [`width`] properties in the legendSettings. It accepts values in both percentage and pixel. If the value is specified in percentage for height or width, the legend height will be calculated for overall height.

Legend size is shown in the following example.

{% aspTab template="treemap/legend/size", sourceFiles="size.cs" %}

{% endaspTab %}

**Paging support**

The tree map supports the legend paging. Legend paging will be enabled if the legend items cannot placed within provided height and width.

The following code example shows enabling legend paging.

{% aspTab template="treemap/legend/paging", sourceFiles="paging.cs" %}

{% endaspTab %}

## Legend for items excluded from color mapping

Based on the ranges in the data source, get the excluded ranges from color mapping, and then show the legend with excluded range values are bound to the specific legend.

{% aspTab template="treemap/legend/excludelegend", sourceFiles="excludelegend.cs" %}

{% endaspTab %}

## Hide desired legend items

To enable or disable the desired legend for each colormapping,set the `showLegend` property to `true` in `colorMapping`.

{% aspTab template="treemap/legend/hidelegend", sourceFiles="hidelegend.cs" %}

{% endaspTab %}

## Hide legend items based data source value

To enable or disable the legend visibility for each item, bind the field name in the data source to the `showLegendPath` property in `legendSettings`.

{% aspTab template="treemap/legend/hidelegendbasedDS", sourceFiles="hidelegendbasedDS.cs" %}

{% endaspTab %}

## Bind legend item text from data source

To show the legend text based on binding, the field name in the datasource should be set to the `valuePath` property in `legendSettings`.

{% aspTab template="treemap/legend/bindlegendtext", sourceFiles="bindlegendtext.cs" %}

{% endaspTab %}

## Hide duplicate legend items

To enable or disable the duplicate legend items, set the  `removeDuplicateLegend` property to `true` in `legendSettings`.

{% aspTab template="treemap/legend/duplicatelegend", sourceFiles="duplicatelegend.cs" %}

{% endaspTab %}

## Legend Responsiveness

Use a responsive legend that switches positions between the right and bottom based on the available height and width. To enable the responsive legend, set the `position` property to `auto` in the `legendSettings` API, and the legend position is changed based on available height and width.

In the following sample, the  responsive legend is shown.

{% aspTab template="treemap/legend/legend-responsive", sourceFiles="legend-responsive.cs" %}

{% endaspTab %}
