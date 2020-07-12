# Appearance

## Circular gauge title

You can add a title to the Circular Gauge using the [`Title`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.CircularGauge.SfCircularGauge~Title.html) property. The title can be customized using the [`CircularGaugeTitleStyle`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.CircularGauge.CircularGaugeTitleStyle_members.html) tag.

```csharp
@using Syncfusion.Blazor.CircularGauge

<SfCircularGauge Title="Speedometer">
    <CircularGaugeTitleStyle Color="blue" FontWeight="bold" Size="25"></CircularGaugeTitleStyle>
</SfCircularGauge>
```

![Circular Gauge with title](./images/title.png)

## Circular gauge position

The Circular Gauge can be positioned anywhere in the container using the [`CenterX`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.CircularGauge.SfCircularGauge~CenterX.html) and [`CenterY`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.CircularGauge.SfCircularGauge~CenterY.html) properties which accept values either in percentage or in pixels.

The default value of the [`CenterX`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.CircularGauge.SfCircularGauge~CenterX.html) and [`CenterY`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.CircularGauge.SfCircularGauge~CenterY.html) property are 50%, so the Circular Gauge will get rendered to the center of the container.

### In pixel

You can set the mid point of the Circular Gauge in pixel as demonstrated as follows.

```csharp
@using Syncfusion.Blazor.CircularGauge

<SfCircularGauge CenterX="20px" CenterY="20px">
    <CircularGaugeAxes>
        <CircularGaugeAxis StartAngle="90" EndAngle="180"></CircularGaugeAxis>
    </CircularGaugeAxes>
</SfCircularGauge>
```

![Circular Gauge in custom position](./images/in-position.png)

### In percentage

By setting the value in percentage, Circular Gauge gets its mid point with respect to its plot area. For example, when setting the value of [`CenterX`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.CircularGauge.SfCircularGauge~CenterX.html) to '1%' and the value of [`CenterY`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.CircularGauge.SfCircularGauge~CenterY.html) to ‘50%’, the gauge will be positioned at the top-left corner of the plot area.

```csharp
@using Syncfusion.Blazor.CircularGauge

<SfCircularGauge CenterX="1%" CenterY="50%">
    <CircularGaugeAxes>
        <CircularGaugeAxis StartAngle="0" EndAngle="180"></CircularGaugeAxis>
    </CircularGaugeAxes>
</SfCircularGauge>
```

![Circular Gauge in custom position](./images/percentages.png)

## Background customization

Using the [`Background`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.CircularGauge.SfCircularGauge~Background.html) and [`CircularGaugeBorder`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.CircularGauge.CircularGaugeBorder_members.html) properties, you can change the background color and border of the Circular Gauge.

```csharp
@using Syncfusion.Blazor.CircularGauge

<SfCircularGauge Background="skyblue">
    <CircularGaugeBorder Color="#FF0000"
                         Width="2">
    </CircularGaugeBorder>
    <CircularGaugeAxes>
        <CircularGaugeAxis>
            <CircularGaugeRanges>
                <CircularGaugeRange Start="1"
                                    End="50"
                                    Radius="110%">
                </CircularGaugeRange>
                <CircularGaugeRange Start="80"
                                    End="100"
                                    Radius="110%">
                </CircularGaugeRange>
            </CircularGaugeRanges>
            <CircularGaugePointers>
                <CircularGaugePointer Value="50"
                                      Radius="60%">
                </CircularGaugePointer>
            </CircularGaugePointers>
        </CircularGaugeAxis>
    </CircularGaugeAxes>
</SfCircularGauge>
```

![Circular Gauge with background and border](./images/background-border.png)

## Radius calculation based on angles

You can render semi or quarter Circular Gauge by modifying the start and end angles. By enabling the radius based on angle option, the radius of circular gauge will be calculated based on the start and end angles to avoid excess white space.

```csharp
@using Syncfusion.Blazor.CircularGauge

<SfCircularGauge>
    <CircularGaugeAxes>
        <CircularGaugeAxis Radius="60%" StartAngle="270" EndAngle="90">
            <CircularGaugeAxisLineStyle Width="5">
            </CircularGaugeAxisLineStyle>
        </CircularGaugeAxis>
    </CircularGaugeAxes>
</SfCircularGauge>
```

![Circular Gauge with custom radius and angle](./images/radius-angle.png)