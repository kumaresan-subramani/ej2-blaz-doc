# Annotations

Annotations are used to mark a specific area of interest in the Circular Gauge with texts, shapes, or images.

## Customization

You can place any custom element on the axis area using [`ContentTemplate`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.CircularGauge.CircularGaugeAnnotation~ContentTemplate.html) in the [`CircularGaugeAnnotation`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.CircularGauge.CircularGaugeAnnotation_members.html).

```csharp
@using Syncfusion.Blazor.CircularGauge

<SfCircularGauge Height="250px" Width="250px">
    <CircularGaugeAxes>
        <CircularGaugeAxis>
            <CircularGaugePointers>
                <CircularGaugePointer Value="50"></CircularGaugePointer>
            </CircularGaugePointers>
            <CircularGaugeAnnotations>
                <CircularGaugeAnnotation Angle="195" ZIndex="1">
                    <ContentTemplate>
                        <div class="custom-annotation">50</div>
                    </ContentTemplate>
                </CircularGaugeAnnotation>
            </CircularGaugeAnnotations>
        </CircularGaugeAxis>
    </CircularGaugeAxes>
</SfCircularGauge>
<style type="text/css">
    .custom-annotation {
        color: white;
        background-color: blue;
        height: 30px;
        width: 30px;
        border-radius: 15px;
        padding: 4px 0 0 6px;
        font-weight: bold;
    }
</style>
```

![Circular Gauge with annotation](./images/annotations.png)

## Positioning the annotation

Annotations can be placed around an axis using the [`Radius`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.CircularGauge.CircularGaugeAnnotation~Radius.html) and [`Angle`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.CircularGauge.CircularGaugeAnnotation~Angle.html) properties.
For example, if the angle is 90 degrees and the radius is 110%, then the annotation will be placed at the right of the axis.

The radius of an annotation takes values either in pixel or in percentage. By setting value in percentage, annotation gets its position with respect to its axis radius.

```csharp
@using Syncfusion.Blazor.CircularGauge

<SfCircularGauge Height="250px" Width="250px">
    <CircularGaugeAxes>
        <CircularGaugeAxis>
            <CircularGaugePointers>
                <CircularGaugePointer Value="50"></CircularGaugePointer>
            </CircularGaugePointers>
            <CircularGaugeAnnotations>
                <CircularGaugeAnnotation Angle="90"
                                         Radius="110%"
                                         ZIndex="1">
                    <ContentTemplate>
                        <div class="custom-annotation">50</div>
                    </ContentTemplate>
                </CircularGaugeAnnotation>
            </CircularGaugeAnnotations>
        </CircularGaugeAxis>
    </CircularGaugeAxes>
</SfCircularGauge>
<style type="text/css">
    .custom-annotation {
        color: white;
        background-color: blue;
        height: 30px;
        width: 30px;
        border-radius: 15px;
        padding: 4px 0 0 6px;
        font-weight: bold;
    }
</style>
```

![Circular Gauge Sample](./images/customization-percentages.png)

## Multiple annotations

Using [`CircularGaugeAnnotation`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.CircularGauge.CircularGaugeAnnotation_members.html), you can add multiple annotations to the circular gauge and each annotation content can be customized separately.

```csharp
@using Syncfusion.Blazor.CircularGauge

<SfCircularGauge Height="250px" Width="250px">
    <CircularGaugeAxes>
        <CircularGaugeAxis>
            <CircularGaugeRanges>
                <CircularGaugeRange Start="35"
                                    End="70"
                                    Color="blue"
                                    Opacity="0.2">
                </CircularGaugeRange>
            </CircularGaugeRanges>
            <CircularGaugePointers>
                <CircularGaugePointer Value="50"></CircularGaugePointer>
            </CircularGaugePointers>
            <CircularGaugeAnnotations>
                <CircularGaugeAnnotation Angle="325" Radius="150%" ZIndex="1">
                    <ContentTemplate>
                        <div class="custom-annotation">Speed to get higher milage</div>
                    </ContentTemplate>
                </CircularGaugeAnnotation>
                <CircularGaugeAnnotation Angle="195" ZIndex="1">
                    <ContentTemplate>
                        <div class="speed">50</div>
                    </ContentTemplate>
                </CircularGaugeAnnotation>
            </CircularGaugeAnnotations>
        </CircularGaugeAxis>
    </CircularGaugeAxes>
</SfCircularGauge>
<style type="text/css">
    .speed {
        color: white;
        background-color: blue;
        height: 30px;
        width: 30px;
        border-radius: 15px;
        padding: 4px 0 0 6px;
        font-weight: bold;
    }

    .custom-annotation {
        background-color: lightgray;
        width: 100%;
        padding: 1px;
    }
</style>
```

![Circular gauge with multiple annotation](./images/multiple-annotation.png)

## See also

* [Tooltip for Annotation](gauge-user-interaction/#tooltip-for-annotations)