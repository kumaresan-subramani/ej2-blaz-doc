# Circular Gauge Dimensions

## Size for Circular Gauge

You can set size for the Circular Gauge directly using the [`Width`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.CircularGauge.SfCircularGauge~Width.html) and [`Height`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.CircularGauge.SfCircularGauge~Height.html) properties.

### In pixel

You can set the size of the Circular Gauge in pixel as demonstrated below.

```csharp
@using Syncfusion.Blazor.CircularGauge

<SfCircularGauge Width= "200px" Height= "200px"></SfCircularGauge>
```

![Circular Gauge size in pixel](./images/percentage.png)

### In percentage

By setting value in percentage, gauge gets its dimension with respect to its container. For example, when
the height is ‘50%’, gauge is rendered to half of the container height.

```csharp
@using Syncfusion.Blazor.CircularGauge

<div style="height:450px; width:450px">
    <SfCircularGauge Width="50%" Height="50%"></SfCircularGauge>
</div>
```

![Circular Gauge size in percentage](./images/percentage.png)

>Note: When you do not specify the size, it takes `450`  pixels as the height and takes window size as its width.