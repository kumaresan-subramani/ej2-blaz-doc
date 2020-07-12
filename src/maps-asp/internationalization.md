# Internationalization

Maps supports internationalization for the following elements:

* Datalabel
* Tooltip

For more information about number and date formatter you can refer to
[`internationalization`](http://ej2.syncfusion.com/documentation/base/intl.html).

<!-- markdownlint-disable MD036 -->
**Globalization**

Globalization is the process of designing and developing a component that works in different
cultures/locales. Internationalization library is used to globalize number, date and time values on
Maps component using the [`format`] property in the maps model.

**Numeric format**

In the following code example, tooltip is globalized to Deutsch culture.

```html
<ejs-maps id="maps" width="100%" load="window.onMapLoad" format="n" useGroupingSeparator="true">
    <e-maps-layers>
        <e-maps-layer dataSource="ViewBag.marker" shapeData="ViewBag.mapdata">
        </e-maps-layer>
    </e-maps-layers>
</ejs-maps>

```
