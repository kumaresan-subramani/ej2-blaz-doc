
# Accessibility

The Circular Gauge provides built-in compliance with the [WAI-ARIA](http://www.w3.org/WAI/PF/aria-practices/) specifications. The
WAI-ARIA accessibility supports are achieved through the attributes such as `aria-label`. It helps to provide information about elements
in a document for assistive technology.

**Aria-label:**   Provides the text label with some default description for the following elements in gauge.

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Element</b></td>
<td><b>Default description</b></td>
</tr>
<tr>
<td>Pointer</td>
<td>Reads the pointer value.</td>
</tr>
<tr>
<td>Annotation</td>
<td>Reads the annotation description.</td>
</tr>
<tr>
<td>Gauge Title</td>
<td>Reads the gauge title.</td>
</tr>
</table>

 You can change this default description, using the description property available in [`CircularGaugePointers`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.CircularGauge.CircularGaugePointers_members.html), [`CircularGaugeAnnotations`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.CircularGauge.CircularGaugeAnnotations_members.html) and [`SfCircularGauge`](https://help.syncfusion.com/cr/aspnetcore-blazor/Syncfusion.Blazor~Syncfusion.Blazor.CircularGauge.SfCircularGauge_members.html) tags.  It helps the screen reader to read for assistive purpose.