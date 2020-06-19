# Navigation Lines

Navigation lines are used to denote the path between the two locations. We can use this feature as flight or train or sea routes.

Following example shows rendering the path between two locations using latitudes and longitudes.

Yon can customize the navigation line color, dashArray, width and angle by modifying their default values in
`MapsNavigationLine`.

Refer the below code snippet to navigate line between two cities in World map.

```csharp
<SfMaps>
    <MapsLayers>
        <MapsLayer ShapeData='new {dataOptions ="https://cdn.syncfusion.com/maps/map-data/world-map.json"}'>
            <MapsNavigationLineSettings>
                <MapsNavigationLine Visible="true"
                                    Color="black"
                                    Angle="90"
                                    Width="2"
                                    DashArray="4"
                                    Latitude="new double[]{ 40.7128, 36.7783 }"
                                    Longitude="new double[]{ -74.0060, -119.4179 }">
                </MapsNavigationLine>
            </MapsNavigationLineSettings>
        </MapsLayer>
    </MapsLayers>
</SfMaps>
```

![Maps with navigation lines](./images/NavigationLine/Navigationline.png)

## Enabling arrows

You can enable arrows in the navigation lines using the [`ShowArrow`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsArrow~ShowArrow.html) property in [`MapsArrow`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsArrow_members.html) tag. You can also customize the following properties in arrow:

* Color - Specifies the color of arrow.
* Offset - Specifies the arrow's offset position.
* Position - Specifies the arrow position to the [`Start`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsArrow~Position.html) or [`End`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.Maps.MapsArrow~Position.html) of line.
* Size - Specifies the arrow size in pixels.

```csharp
@using Syncfusion.Blazor.Maps

<SfMaps>
    <MapsLayers>
        <MapsLayer ShapeData='new {dataOptions ="https://cdn.syncfusion.com/maps/map-data/world-map.json"}'>
            <MapsNavigationLines>
                <MapsNavigationLine Visible="true"
                                    Color="blue"
                                    Angle="90"
                                    Width="2"
                                    DashArray="4"
                                    Latitude="new double[]{ 40.7128, 36.7783 }"
                                    Longitude="new double[]{ -74.0060, -119.4179 }">
                    @*  To set arrow for navigation line  *@
                    <MapsArrow ShowArrow="true" Color="blue"></MapsArrow>
                </MapsNavigationLine>
            </MapsNavigationLines>
        </MapsLayer>
    </MapsLayers>
</SfMaps>
```