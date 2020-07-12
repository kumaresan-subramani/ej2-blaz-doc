# User Interactions

The options such as zoom, pan, single-click, double-click, highlight, and map selection provide effective interaction on the maps elements.

## Zooming

The zooming feature enables you to zoom in and zoom out the maps to show the in-depth information. It is controlled using the [`ZoomFactor`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsZoomSettings~ZoomFactor.html) property of the [`MapsZoomSettings`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsZoomSettings_members.html) in maps. When the `ZoomFactor` is increased, the map is zoomed in and when the `ZoomFactor` is decreased, the map is zoomed out.

<b>Enable zooming</b>

To enable the zooming feature, set the [`Enable`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsZoomSettings~Enable.html) property to true in [`MapsZoomSettings`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsZoomSettings_members.html).

```csharp
@using Syncfusion.Blazor.Maps

<SfMaps>
    <MapsZoomSettings Enable="true"></MapsZoomSettings>
    <MapsLayers>
        <MapsLayer ShapeData='new {dataOptions ="https://cdn.syncfusion.com/maps/map-data/usa.json"}'>
        </MapsLayer>
    </MapsLayers>
</SfMaps>
```

![Maps with zoom toolbar](./images/UserInteraction/Zoom.png)

<b>Enable panning</b>

We can enable or disable the panning feature, using the `EnablePanning` in [`MapsZoomSettings`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.EJ2.Blazor~Syncfusion.EJ2.Blazor.Maps.MapsZoomSettings_members.html)

### Various types of zooming

Zooming can be performed in the following types:

<b>Zooming toolbar</b>

By default, the toolbar is rendered with `zoom-in`, `zoom-out`, and `reset` options when it is set to 'true' in the [`Enable`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsZoomSettings~Enable.html) property of [`MapsZoomSettings`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsZoomSettings_members.html). You can also customize the toolbar items using the [`Toolbars`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsZoomSettings~Toolbars.html) property in [`MapsZoomSettings`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsZoomSettings_members.html).

The following options are available in toolbar, and you can use the options as needed:

1. Zoom - Provides rectangular zoom support.
2. ZoomIn - Zooms in the maps.
3. ZoomOut - Zooms out the maps.
4. Pan - Switches to panning if rectangular zoom is activated.
5. Reset - Restores the maps to the default view.

```csharp
@using Syncfusion.Blazor.Maps

<SfMaps>
    <MapsZoomSettings Enable="true"
                      ToolBarOrientation="Orientation.Vertical"
                      Toolbars='new string[]{"Zoom", "ZoomIn", "ZoomOut", "Pan", "Reset" }'>
    </MapsZoomSettings>
    <MapsLayers>
        <MapsLayer ShapeData='new {dataOptions ="https://cdn.syncfusion.com/maps/map-data/usa.json"}'>
        </MapsLayer>
    </MapsLayers>
</SfMaps>
```

<b>Pinch zooming</b>

Use the [`PinchZooming`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsZoomSettings~PinchZooming.html) property in [`MapsZoomSettings`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsZoomSettings_members.html) to enable or disable the pinch zooming.

```csharp
@using Syncfusion.Blazor.Maps

<SfMaps>
    <MapsZoomSettings Enable="true" PinchZooming="true"></MapsZoomSettings>
    <MapsLayers>
        <MapsLayer ShapeData='new {dataOptions ="https://cdn.syncfusion.com/maps/map-data/usa.json"}'>
        </MapsLayer>
    </MapsLayers>
</SfMaps>
```

<b>Single-click zooming</b>

Use the [`ZoomOnClick`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsZoomSettings~ZoomOnClick.html) property in [`MapsZoomSettings`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsZoomSettings_members.html) to enable or disable the single-click zooming.

```csharp
@using Syncfusion.Blazor.Maps

<SfMaps>
    <MapsZoomSettings Enable="true" ZoomOnClick="true"></MapsZoomSettings>
    <MapsLayers>
        <MapsLayer ShapeData='new {dataOptions ="https://cdn.syncfusion.com/maps/map-data/usa.json"}'>
        </MapsLayer>
    </MapsLayers>
</SfMaps>
```

<b>Double-click zooming</b>

Use the [`DoubleClickZoom`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsZoomSettings~DoubleClickZoom.html) property in [`MapsZoomSettings`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsZoomSettings_members.html) to enable or disable the double-click zooming.

```csharp
@using Syncfusion.Blazor.Maps

<SfMaps>
    <MapsZoomSettings Enable="true" DoubleClickZoom="true"></MapsZoomSettings>
    <MapsLayers>
        <MapsLayer ShapeData='new {dataOptions ="https://cdn.syncfusion.com/maps/map-data/usa.json"}'>
        </MapsLayer>
    </MapsLayers>
</SfMaps>
```

<b>Mouse wheel zooming</b>

Use the [`MouseWheelZoom`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsZoomSettings~MouseWheelZoom.html) property in [`MapsZoomSettings`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsZoomSettings_members.html) to enable or disable mouse wheel zooming.

```csharp
@using Syncfusion.Blazor.Maps

<SfMaps>
    <MapsZoomSettings Enable="true" MouseWheelZoom="true"></MapsZoomSettings>
    <MapsLayers>
        <MapsLayer ShapeData='new {dataOptions ="https://cdn.syncfusion.com/maps/map-data/usa.json"}'>
        </MapsLayer>
    </MapsLayers>
</SfMaps>
```

### Zooming with animation

You can use the [`AnimationDuration`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsLayer~AnimationDuration.html) property in [`MapsLayer`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsLayer_members.html) to zoom in or zoom out the maps with animation.

```csharp
@using Syncfusion.Blazor.Maps

<SfMaps>
    <MapsZoomSettings Enable="true">
    </MapsZoomSettings>
    <MapsLayers>
        <MapsLayer ShapeData='new {dataOptions ="https://cdn.syncfusion.com/maps/map-data/usa.json"}'
                   AnimationDuration="500">
        </MapsLayer>
    </MapsLayers>
</SfMaps>
```

## Selection

### Shape selection

Each shape in the maps can be selected and deselected when interacting with the shapes.

In [`MapsLayerSelectionSettings`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.LayerSelectionSettings_members.html), the [`Fill`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.MapsSelectionSettings~Fill.html) property is used to change the selected layer shape color. The [`Color`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.LayerSelectionBorder.html) and [`Width`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.LayerSelectionBorder.html) properties are used to customize the selected shape border.

You can select a shape by tapping the shape. The single selection is enabled using the [`Enable`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.MapsSelectionSettings~Enable.html) property of shape layer. When the [`Enable`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.MapsSelectionSettings~Enable.html) property is set to false, the shapes cannot be selected.

```csharp
@using Syncfusion.Blazor.Maps

<SfMaps>
    <MapsLayers>
        <MapsLayer ShapeData='new {dataOptions ="https://cdn.syncfusion.com/maps/map-data/usa.json"}'>
            <MapsLayerSelectionSettings Enable="true" Fill="green">
                <MapsLayerSelectionBorder Color="White" Width="2"></MapsLayerSelectionBorder>
            </MapsLayerSelectionSettings>
        </MapsLayer>
    </MapsLayers>
</SfMaps>
```

![Maps with shape selection](./images/UserInteraction/Selection.png)

### Legend selection

By tapping a specific legend, the shapes bound to the selected legends are selected and vice-versa.

The following code example demonstrates how to add interactive legend along with the configuration of [`MapsLayerSelectionSettings`](s://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsLayerSelectionSettings_members.html) and `MapsLegendSettings` to render interactive shape selection.

```csharp
@using Syncfusion.Blazor.Maps

<SfMaps>
    <MapsLegendSettings Visible="true" Mode="LegendMode.Interactive"></MapsLegendSettings>
    <MapsLayers>
        <MapsLayer ShapeData='new {dataOptions ="https://cdn.syncfusion.com/maps/map-data/world-map.json"}'
                   DataSource="CouncilMemberdetails"
                   ShapeDataPath="Country"
                   ShapePropertyPath='@("name")'>
            <MapsShapeSettings Fill="#E5E5E5" ColorValuePath="Membership">
                <MapsShapeColorMappings>
                    <MapsShapeColorMapping Value="Permanent" Color='@("#D84444")' />
                    <MapsShapeColorMapping Value="Non-Permanent" Color='@("#316DB5")' />
                </MapsShapeColorMappings>
            </MapsShapeSettings>
            <MapsLayerSelectionSettings Enable="true" Fill="#a7f047">
                <MapsLayerSelectionBorder Color="White" Width="2"></MapsLayerSelectionBorder>
            </MapsLayerSelectionSettings>
        </MapsLayer>
    </MapsLayers>
</SfMaps>

@code{
    public class UNCouncil
    {
        public string Country;
        public string Membership;
    };
    private List<UNCouncil> CouncilMemberdetails = new List<UNCouncil>{
         new UNCouncil { Country= "China", Membership= "Permanent"},
         new UNCouncil { Country= "France",Membership= "Permanent" },
         new UNCouncil { Country= "Russia",Membership= "Permanent"},
         new UNCouncil { Country= "Kazakhstan",Membership= "Non-Permanent"},
         new UNCouncil { Country= "Poland",Membership= "Non-Permanent"},
         new UNCouncil { Country= "Sweden",Membership= "Non-Permanent"}
    };
}
```

![Maps with shape selection using legend](./images/UserInteraction/highlight-with-legend.png)

## Public method for the shape selection

Each shape in the map can be selected by calling the `shapeSelection` method. Input parameters for this method are layerIndex, propertyName, country name and selected value as in boolean state(true / false).

```csharp
@using Syncfusion.Blazor.Maps
        <div>
            <SfMaps @ref="mapsref">
                <MapsLayers>
                    <MapsLayer ShapeData='new {dataOptions= "https://cdn.syncfusion.com/maps/map-data/world-map.json"}'>
                        <MapsLayerSelectionSettings Enable="true" Fill="green">
                            <MapsLayerSelectionBorder Color="white" Width="2"></MapsLayerSelectionBorder>
                        </MapsLayerSelectionSettings>
                    </MapsLayer>
                </MapsLayers>
            </SfMaps>
        </div>
        <button id="select" @onclick="Select">select</button>
        <button id="unselect" @onclick="Unselect">unselect</button>
@code{
    SfMaps mapsref;
    public void select() {
        mapsref.ShapeSelection(0, "continent", "Asia", true);
    }
    public void Unselect() {
        mapsref.ShapeSelection(0, "continent", "Asia", false);
    }
}
```

![Markers with cluster](./images/Marker/public-method.png)

## Initial shape selection

Initially, the shape can be selected by using the property `initialShapeSelection` and the values are mapped to the `shapePath` and `shapeValue`.

**Note:** initialShapeSelection is an Array property.

```csharp
<SfMaps>
    <MapsLayers>
        <MapsLayer ShapeData='new {dataOptions= "https://cdn.syncfusion.com/maps/map-data/world-map.json"}'>
            <MapsLayerSelectionSettings Enable="true" Fill="green">
                <MapsLayerSelectionBorder Color="white" Width="2"></MapsLayerSelectionBorder>
            </MapsLayerSelectionSettings>
            <MapsInitialShapeSelectionSettings>
                <MapsInitialShapeSelection ShapePath="continent" ShapeValue="Africa"></MapsInitialShapeSelection>
                <MapsInitialShapeSelection ShapePath="name" ShapeValue="India"></MapsInitialShapeSelection>
            </MapsInitialShapeSelectionSettings>
        </MapsLayer>
    </MapsLayers>
</SfMaps>
```

![initial with selection](./images/Marker/initial-selection.png)

## Highlight

### Shape highlight

Each shape in the maps can be highlighted by hovering the mouse over the shapes.

The [`Fill`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.MapsHighlightSettings~Fill.html) property is used to change the highlighted layer shape color. The [`Color`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.MapsBorderSettings~Color.html) and [`Width`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.MapsBorderSettings~Width.html) properties are used to customize the highlighted shape border.

You can highlight a shape by hovering the mouse over the shape. The highlight is enabled using the [`Enable`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.MapsHighlightSettings~Enable.html) property of [`MapsLayerHighlightSettings`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.LayerHighlightSettings_members.html). When the [`Enable`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.MapsHighlightSettings~Enable.html) property is set to false, the shapes cannot be highlighted.

```csharp
@using Syncfusion.Blazor.Maps

<SfMaps>
    <MapsLayers>
        <MapsLayer ShapeData='new {dataOptions ="https://cdn.syncfusion.com/maps/map-data/usa.json"}'>
            <MapsLayerHighlightSettings Enable="true" Fill="green">
                <MapsLayerHighlightBorder Color="white" Width="2"></MapsLayerHighlightBorder>
            </MapsLayerHighlightSettings>
        </MapsLayer>
    </MapsLayers>
</SfMaps>
```

![Maps with highlighting shape](./images/UserInteraction/Highlight.png)

### Legend highlight

By hovering over a specific legend, the shapes bound to the selected legend are highlighted and vice-versa.

The following code example demonstrates how to add interactive legend along with the configuration of [`MapsLayerHighlightSettings`](tps://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.LayerHighlightSettings_members.html) and `MapsLegendSettings` to render interactive shape highlight with legend items.

```csharp
@using Syncfusion.Blazor.Maps

<SfMaps>
    <MapsLegendSettings Visible="true" Mode="LegendMode.Interactive"></MapsLegendSettings>
    <MapsLayers>
        <MapsLayer ShapeData='new {dataOptions ="https://cdn.syncfusion.com/maps/map-data/world-map.json"}'
                   DataSource="CouncilMemberDetails"
                   ShapeDataPath="Country"
                   ShapePropertyPath='@("name")'>
            <MapsShapeSettings Fill="#E5E5E5" ColorValuePath="Membership">
                <MapsShapeColorMappings>
                    <MapsShapeColorMapping Value="Permanent" Color='@("#D84444")' />
                    <MapsShapeColorMapping Value="Non-Permanent" Color='@("#316DB5")' />
                </MapsShapeColorMappings>
            </MapsShapeSettings>
            <MapsLayerHighlightSettings Enable="true" Fill="#a7f047">
                <MapsLayerHighlightBorder Color="White" Width="2"></MapsLayerHighlightBorder>
            </MapsLayerHighlightSettings>
        </MapsLayer>
    </MapsLayers>
</SfMaps>

@code{
    public class UNCouncil
    {
        public string Country;
        public string Membership;
    };
    private List<UNCouncil> CouncilMemberDetails = new List<UNCouncil>{
         new UNCouncil { Country= "China", Membership= "Permanent"},
         new UNCouncil { Country= "France",Membership= "Permanent" },
         new UNCouncil { Country= "Russia",Membership= "Permanent"},
         new UNCouncil { Country= "Kazakhstan",Membership= "Non-Permanent"},
         new UNCouncil { Country= "Poland",Membership= "Non-Permanent"},
         new UNCouncil { Country= "Sweden",Membership= "Non-Permanent"}
    };
}
```

![Maps with highlighting shape using legend](./images/UserInteraction/highlight-with-legend.png)

## Tooltip

Tooltip is used to get more information about layer, bubble, and marker on mouse over or by performing touch-end event.

### Tooltip format

Tooltip can be enabled for layer by setting [`Visible`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.MapsTooltipSettings~Visible.html) to **true** in [`MapsLayerTooltipSettings`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsLayerTooltipSettings_members.html). The value of tooltip [`ValuePath`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.MapsTooltipSettings~ValuePath.html) needs to be set to display data source whose field is set as tooltip text.

The following steps explain how to enable tooltip for layer to show shape data name field.

**Step 1:** Import the world map geo json data and assign to [`ShapeData`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsLayer~ShapeData.html).

**Step 2:** Enable tooltip for layer by setting [`Visible`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.MapsTooltipSettings~Visible.html) to true in [`MapsLayerTooltipSettings`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsLayerTooltipSettings_members.html) and binding [`ValuePath`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.MapsTooltipSettings~ValuePath.html) value to 'name'.

The following code snippet demonstrates how to enable tooltip for layer to show shape data name field.

```csharp
@using Syncfusion.Blazor.Maps

<SfMaps>
    <MapsLayers>
        <MapsLayer ShapeData='new {dataOptions= "https://cdn.syncfusion.com/maps/map-data/world-map.json"}'
                   ShapePropertyPath='@("name")'
                   DataSource='PerformanceReport'
                   ShapeDataPath="Name">
            <MapsLayerTooltipSettings Visible="true"
                                  ValuePath="CountryName"
                                  Format="<b>${CountryName}</b><br>Finalist: <b>${Winner}</b><br>Win: <b>${Finalist}">
            </MapsLayerTooltipSettings>
            <MapsShapeSettings Fill="#E5E5E5" ColorValuePath="Finalist">
                <MapsShapeColorMappings>
                    <MapsShapeColorMapping Value="1" Color='@("#acaed8")'></MapsShapeColorMapping>
                    <MapsShapeColorMapping Value="2" Color='@("#80c1ff")'></MapsShapeColorMapping>
                    <MapsShapeColorMapping Value="3" Color='@("#1a90ff")'></MapsShapeColorMapping>
                    <MapsShapeColorMapping Value="4" Color='@("#005cb3")'></MapsShapeColorMapping>
                    <MapsShapeColorMapping Value="7" Color='@("#0b0d35")'></MapsShapeColorMapping>
                </MapsShapeColorMappings>
            </MapsShapeSettings>
        </MapsLayer>
    </MapsLayers>
</SfMaps>

@code {
    public List<Country> PerformanceReport = new List<Country> {
            new Country { CountryName="India", Name="India", Finalist="3", Winner="2" },
            new Country { CountryName="United Kingdom", Name="United Kingdom", Finalist="4", Winner="1" },
            new Country { CountryName="Australia", Name="Australia", Finalist="7", Winner="5" },
            new Country { CountryName="Sri Lanka", Name="Sri Lanka", Finalist="3", Winner="1"},
            new Country { CountryName="Pakistan", Name="Pakistan", Finalist="2", Winner="1"  },
            new Country { CountryName="New Zealand", Name="New Zealand", Finalist="1", Winner="0"},
            new Country { CountryName="West Indies", Name="Dominican Rep", Finalist="3", Winner="2"},
            new Country { CountryName="West Indies", Name="Cuba", Finalist="3", Winner="2"},
            new Country { CountryName="West Indies", Name="Jamaica", Finalist="3", Winner="2"},
            new Country { CountryName="West Indies", Name="Haiti", Finalist="3", Winner="2"},
            new Country { CountryName="West Indies",Name="Gayana", Finalist="3", Winner="2"},
            new Country { CountryName="West Indies", Name="Suriname", Finalist="3", Winner="2"},
            new Country { CountryName="West Indies", Name="Trinidad and Tobago", Finalist="3", Winner="2"}
        };
    public class Country
    {
        public string Name;
        public string Winner;
        public string Finalist;
        public string CountryName;
    }
}
```

![Maps with tooltip](./images/UserInteraction/tooltip.png)

### Tooltip for other elements

You can also provide tooltips for other elements such as markers and bubbles using [`MapsMarkerTooltipSettings`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsMarkerTooltipSettings_members.html) and [`MapsBubbleTooltipSettings`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsBubbleTooltipSettings_members.html).

```csharp
@using Syncfusion.Blazor.Maps

<SfMaps>
    <MapsLayers>
        <MapsLayer ShapeData='new {dataOptions= "https://cdn.syncfusion.com/maps/map-data/world-map.json"}'>
            <MapsMarkerSettings>
                <MapsMarker Visible="true"
                            DataSource="OfficeLocations"
                            Fill="white"
                            Width="20"
                            Shape="MarkerType.Circle">
                    <MapsMarkerBorder Color="#285255" Width="2"></MapsMarkerBorder>
                    <MapsMarkerTooltipSettings Visible="true" ValuePath="Name"></MapsMarkerTooltipSettings>
                </MapsMarker>
            </MapsMarkerSettings>
        </MapsLayer>
    </MapsLayers>
</SfMaps>

@code {
    public class OfficeLocation
    {
        public double Latitude;
        public double Longitude;
        public string Name;
    }
    private List<OfficeLocation> OfficeLocations = new List<OfficeLocation> {
        new OfficeLocation{ Latitude= 37.6276571, Longitude= -122.4276688, Name= "San Bruno" },
        new OfficeLocation{ Latitude= 33.5302186, Longitude= -117.7418381, Name= "Laguna Niguel" },
        new OfficeLocation{ Latitude= 40.7424509, Longitude= -74.0081468, Name= "New York" },
        new OfficeLocation{ Latitude= -23.5268201, Longitude= -46.6489927, Name= "Bom Retiro" },
        new OfficeLocation{ Latitude= 43.6533855, Longitude= -79.3729994, Name= "Toronto" },
        new OfficeLocation{ Latitude= 48.8773406, Longitude= 2.3299627, Name= "Paris" },
        new OfficeLocation{ Latitude= 52.4643089, Longitude= 13.4107368, Name= "Berlin" },
        new OfficeLocation{ Latitude= 19.1555762, Longitude= 72.8849595, Name= "Mumbai" },
        new OfficeLocation{ Latitude= 35.6628744, Longitude= 139.7345469, Name= "Minato" },
        new OfficeLocation{ Latitude= 51.5326602, Longitude= -0.1262422, Name= "London" }
    };

}
```

![Maps with marker tooltip](./images/UserInteraction/maps-with-marker-tooltip.png)

## See also

* [Change center position on zooming](how-to/change-center-position-on-zooming)
