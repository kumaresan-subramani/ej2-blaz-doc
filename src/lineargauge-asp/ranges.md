# Ranges

You can categorize the axis values using [`start`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.LinearGauge.LinearGaugeRange~Start.html) and [`end`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.LinearGauge.LinearGaugeRange~End.html) property in the [`ranges`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.LinearGauge.LinearGaugeRange.html). You can add any number of range for an axis by using array of range objects.

{% aspTab template="lineargauge/ranges/ranges", sourceFiles="ranges.cs" %}

{% endaspTab %}

## Ranges Customization

Ranges can be customized using the following properties.

* [`startWidth`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.LinearGauge.LinearGaugeRange~StartWidth.html) - Specifies start width of the range
* [`endWidth`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.LinearGauge.LinearGaugeRange~EndWidth.html) - Specifies end width of the range
* [`color`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.LinearGauge.LinearGaugeRange~Color.html) - Specifies color of the range
* `position` - Specifies the range bar position. Its possible values are 'inside' and 'outside'
* `Offset` - Specifies offset value from its default position
* `LinearGaugeRangeBorder` - Specifies range bar border color and width.

{% aspTab template="lineargauge/ranges/range-customization", sourceFiles="range-customization.cs" %}

{% endaspTab %}

## Multiple Ranges

You can add multiple ranges to an axis as demonstrated below.

{% aspTab template="lineargauge/ranges/multiple-ranges", sourceFiles="multiple-ranges.cs" %}

{% endaspTab %}

## Gradient Color

Gradient support allows to add multiple colors in the ranges and pointers of the circular gauge. The following gradient types are supported in the circular gauge.

* Linear Gradient
* Radial Gradient

### Linear Gradient

Using linear gradient, colors will be applied in a linear progression. The start value of the linear gradient can be set using the [`startValue`](../api/linear-gauge/linearGradient/#startvalue) property. The end value of the linear gradient will be set using the [`endValue`](../api/linear-gauge/linearGradient/#endvalue) property. The color stop values such as color, opacity and offset are set using [`colorStop`](../api/linear-gauge/linearGradient/#colorstop) property.

To apply linear gradient to the range, follow the below code sample.

{% aspTab template="lineargauge/ranges/lineargradient", sourceFiles="lineargradient.cs" %}

{% endaspTab %}

## Radial Gradient

Using radial gradient, colors will be applied in circular progression. The inner circle position of the radial gradient will be set using the [`innerPosition`](../api/linear-gauge/radialGradient/#innerposition) property. The outer circle position of the radial gradient can be set using the [`outerPosition`](../api/linear-gauge/radialGradient/#outerposition) property. The color stop values such as color, opacity and offset are set using [`colorStop`](../api/linear-gauge/radialGradient/#colorstop) property.

To apply radial gradient to the range, follow the below code sample.

{% aspTab template="lineargauge/ranges/radialgradient", sourceFiles="radialgradient.cs" %}

{% endaspTab %}