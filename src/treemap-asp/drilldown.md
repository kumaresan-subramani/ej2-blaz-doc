# Drill-down

The tree map control supports drill-down to expose the hierarchy achieved by clicking a node. If you click an item in tree map, the tree map will be moved to the next level or sub level and returned back to the previous level by clicking the node header. A single level of the tree map is visible at a time.

## Perform drill-down action

The tree map elements can be drilled down by setting the enableDrillDown property to true. You can view the hierarchy of the tree map by clicking the tree map items and move to the previous level by clicking the drill-down header.

The drill-down concepts are shown in the following code example.

{% aspTab template="treemap/drilldown/drilldown", sourceFiles="drilldown.cs" %}

{% endaspTab %}

## On-demand data loading

In normal drill-down process, all the child items are rendered in DOM, and they are visible at initial time of TreeMap rendering. But, on-demand data loading, it will not render child items at initial time. The child nodes will be rendered at the drill-down process only. By setting the `drillDownView` property to true, you can enable this feature.

In the following sample, on-demand data loading is shown.

{% aspTab template="treemap/drilldown/drilldown-demand", sourceFiles="drilldown-demand.cs" %}

{% endaspTab %}

## Breadcrumb support

Using breadcrumb navigation, you can directly drill up to any level of parent, and it displays the level from root parent to the current level at the top layout of TreeMap.

You can show or hide the breadcrumb using the `enableBreadcrumb` API. You can also customize the breadcrumb connector using the property `breadcrumbConnector` property. By default, `-` is the connector.

{% aspTab template="treemap/drilldown/drilldown-breadcrumb", sourceFiles="drilldown-breadcrumb.cs" %}

{% endaspTab %}