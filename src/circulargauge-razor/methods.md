# Methods

## Using methods in Circular Gauge component

You can create object for the circular gauge component using `@ref` and call the [`SetPoinerValue`](https://help.syncfusion.com/cr/cref_files/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.CircularGauge.SfCircularGauge~SetPointerValue.html) method as shown in the following example.

```csharp
@using Syncfusion.Blazor.CircularGauge

<button style="margin-left:34px" @onclick="ChangePoinerValue">Change pointer value</button>
<SfCircularGauge @ref="gauge" Width="250px" Height="250px">
    <CircularGaugeAxes>
        <CircularGaugeAxis>
            <CircularGaugePointers>
                <CircularGaugePointer Value="50"></CircularGaugePointer>
            </CircularGaugePointers>
        </CircularGaugeAxis>
    </CircularGaugeAxes>
</SfCircularGauge>

@code {
    SfCircularGauge gauge;
    void ChangePoinerValue()
    {
        gauge.SetPointerValue(0, 0, 30);
    }
}
```

![Using methods in circular gauge](./images/c-gauge-methods.png)

## Available methods

### SetAnnotationValue

Description: Dynamically set the annotation content to the circular gauge.

Return: void

|   Argument name      |   Description                            |
|----------------------| -----------------------------------------|
|     axis index       |    Specifies the axis index              |
|     annotationIndex  |    Specifies the current annotation index        |
|     content          |    Specifies the current annotation text         |

### SetPointerValue

Description: Dynamically set the pointer value to the circular gauge.

Return: void

|   Argument name      |   Description                            |
|----------------------| -----------------------------------------|
|     axis index       |    Specifies the axis index              |
|     pointerIndex     |    Specifies the current pointer index           |
|     value            |    Specifies the current pointer value           |

### SetRangeValue

Description: Dynamically set the range value to the circular gauge.

Return: void

|   Argument name      |   Description                            |
|----------------------| -----------------------------------------|
|     axis index       |    Specifies the current axis index              |
|     rangeIndex       |    Specifies the current range index             |
|     start            |    Specifies the range start value       |
|     end              |    Specifies the range end value         |