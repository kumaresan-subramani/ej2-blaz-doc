# Customize the limits

Slider appearance can be customized via CSS. By overriding the slider CSS classes, the slider limit bar can be customized. Here, the limit bar is customized with different background color. By default, the slider has class `e-limits` for limits bar. You can override the class with our own color values as given in the following code snippet.

```csharp
.e-control-wrapper.e-slider-container.e-horizontal .e-limits {
    background-color: rgba(69, 100, 233, 0.46);
}
```

And on implementing the above code snippet in the below slider control's Blazor code, the overview would be like the one found below.

```csharp
@using Syncfusion.Blazor.Inputs;
@using Syncfusion.Blazor.Buttons;

<div class="col-lg-8 control-section sb-property-border">
    <div class="content-wrapper">
        <div class='sliderwrap'>
            <label class="userselect">MinRange Slider With Limits</label>
            <SfSlider @bind-Value="@Default" Min="0" Max="100" Type=SliderType.MinRange>
                <SliderTicksData Placement="@Placement.Before" LargeStep="20" SmallStep="5" ShowSmallTicks="true"></SliderTicksData>
                <SliderTooltipData IsVisible="true" Placement="@TooltipPlacement.Before" ShowOn="@TooltipShowOn.Focus"></SliderTooltipData>
                <SliderLimitData Enabled="true"
                                 MinStart="10"
                                 MinEnd="40"
                                 StartHandleFixed="false"></SliderLimitData>
            </SfSlider>
        </div>
        <div class='sliderwrap'>
            <label class="userselect">Range Slider With Limits</label>
            <SfSlider @bind-Value="@Range" Min="0" Max="100" Type=SliderType.Range>
                <SliderTicksData Placement="@Placement.Before" LargeStep="20" SmallStep="5" ShowSmallTicks="true"></SliderTicksData>
                <SliderTooltipData IsVisible="true" Placement="@TooltipPlacement.Before" ShowOn="@TooltipShowOn.Focus"></SliderTooltipData>
                <SliderLimitData Enabled="true"
                                 MinStart="10"
                                 MinEnd="40"
                                 MaxStart="50"
                                 MaxEnd="90"
                               ></SliderLimitData>
            </SfSlider>
        </div>
    </div>
</div>

@code{
    int Default = 25;
    int[] Range = { 25, 75 };
}
<style>
    .content-wrapper {
        width: 52%;
        margin: 0 auto;
        min-width: 185px;
    }
    .sliderwrap {
        margin-top: 45px;
    }
    .e-bigger .content-wrapper {
        width: 80%;
    }
    .e-control-wrapper.e-slider-container.e-horizontal .e-limits {
    background-color: rgba(69, 100, 233, 0.46);
     }
    .sliderwrap label {
        padding-bottom: 50px;
        font-size: 13px;
        font-weight: 500;
        margin-top: 15px;
    }
    .userselect {
        -webkit-user-select: none;
        /* Safari 3.1+ */
        -moz-user-select: none;
        /* Firefox 2+ */
        -ms-user-select: none;
        /* IE 10+ */
        user-select: none;
        /* Standard syntax */
    }
    .property-custom td {
        padding: 5px;
    }
</style>
```

![Blazor- Slider - Limits](./../images/limits.gif)