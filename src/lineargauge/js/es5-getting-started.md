# Getting Started  with JavaScript(ES5)

The Essential JS 2 for JavaScript (global script) is an ES5 formatted pure JavaScript framework which can be directly used in latest web browsers.

## Control Initialization

The Essential JS 2 JavaScript controls can be initialized by using either of the following ways.

* Using local script references in a HTML page.
* Using CDN link for script reference.

### Using local script references in a HTML page

**Step 1:** Create an app folder `quickstart` for getting started.

**Step 2:** You can get the global scripts from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

**Syntax:**
> Dependency Script: `**(installed location)**\Syncfusion\Essential Studio\JavaScript - EJ2\{RELEASE_VERSION}\Web (Essential JS 2)\JavaScript\{DEPENDENCY_PACKAGE_NAME}\dist\global\{DEPENDENCY_PACKAGE_NAME}.min.js`
>
> Control Script: `**(installed location)**\Syncfusion\Essential Studio\JavaScript - EJ2\{RELEASE_VERSION}\Web (Essential JS 2)\JavaScript\{PACKAGE_NAME}\dist\global\{PACKAGE_NAME}.min.js`

**Example:**
> Dependency Script: `C:\Program Files (x86)\Syncfusion\Essential Studio\JavaScript - EJ2\16.3.0.17\Web (Essential JS 2)\JavaScript\ej2-base\dist\global\ej2-base.min.js`
>
> Control Script: `C:\Program Files (x86)\Syncfusion\Essential Studio\JavaScript - EJ2\16.3.0.17\Web (Essential JS 2)\JavaScript\ej2-lineargauge\dist\global\ej2-lineargauge.min.js`

The below located script file contains all Syncfusion JavaScript (ES5) UI control resources in a single file.

> Scripts: `**(installed location)**\Syncfusion\Essential Studio\JavaScript - EJ2\{RELEASE_VERSION}\Web (Essential JS 2)\JavaScript\ej2\dist\ej2.min.js`

The [`Custom Resource Generator (CRG)`](https://crg.syncfusion.com/) is an online web tool, which can be used to generate the custom script for a set of specific controls. This web tool is useful to combine the required control scripts in a single file.

**Step 3:** Create a folder `~/quickstart/resources` and copy/paste the global scripts from the above installed location to `~/quickstart/resources/package` corresponding package location.

**Step 4:** Create a HTML page (index.html) in `~/quickstart/index.html` and add the Essentials JS 2 script references.

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>Essential JS 2</title>

        <!-- Essential JS 2 Base's global script (Dependency Script) -->
        <script src="resources/base/ej2-base.min.js" type="text/javascript"></script>
        <!-- Essential JS 2 lineargauge's global script (Control Script) -->
        <script src="resources/lineargauge/ej2-lineargauge.min.js" type="text/javascript"></script>
    </head>
    <body>
    </body>
</html>
```

**Step 5:** Now, add the `LinearGauge` element and initiate the `Syncfusion JavaScript (ES5) LinearGauge` control in the `~/quickstart/index.html` by using following code.

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>Essential JS 2</title>

        <!-- Essential JS 2 Base's global script (Dependency Script) -->
        <script src="resources/base/ej2-base.min.js" type="text/javascript"></script>
        <!-- Essential JS 2 lineargauge's global script (Control Script) -->
        <script src="resources/lineargauge/ej2-lineargauge.min.js" type="text/javascript"></script>
    </head>
    <body>
        <!-- Add the HTML <lineargauge> element  -->
        <lineargauge id="element">Linear Gauge</lineargauge>
        <script>
            // initialize lineargauge control
            var lineargauge = new ej.lineargauge.LinearGauge();
            // Render initialized lineargauge.
            lineargauge.appendTo('#element');
        </script>
    </body>
</html>
```

**Step 6:** Now, run the `index.html` in web browser, it will render the **Syncfusion JavaScript Lineargauge** control.

### Using CDN link for script reference

**Step 1:** Create an app folder `quickstart` for getting started.

**Step 2:** The Essential JS 2 controls's global scripts is already hosted in the below CDN link formats.

**Syntax:**
> Dependency Script: `https://cdn.syncfusion.com/ej2/{DEPENDENCY_PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Control Script: `https://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`

**Example:**
> Script: [`https://cdn.syncfusion.com/ej2/ej2-lineargauge/dist/global/ej2-lineargauge.min.js`](https://cdn.syncfusion.com/ej2/ej2-lineargauge/dist/global/ej2-lineargauge.min.js)

**Step 3:** Create a HTML page (index.html) in `~/quickstart/index.html` location and add the CDN link references. Now, add the `LinearGauge` element and initiate the `Syncfusion JavaScript (ES5) LinearGauge` control in the index.html by using following code.

The below example shows a basic linear gauge component.

{% tab template="linear-gauge/es5-getting-started", es5Template="default" %}

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>

            <!-- Essential JS 2 Base's global script (Dependency Script) -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>

            <!-- Essential JS 2 lineargauge's global script (Control Script) -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-lineargauge/dist/global/ej2-lineargauge.min.js" type="text/javascript"></script>

       </head>
       <body>
           <!-- Add the HTML <lineargauge> element  -->
            <lineargauge id="element">Linear Gauge</lineargauge>
            <script>
                ej.base.enableRipple(true);
                // initialize lineargauge control
                var lineargauge = new ej.lineargauge.LinearGauge();
                // Render initialized lineargauge.
                lineargauge.appendTo('#element');
            </script>
       </body>
  </html>
```

{% endtab %}

**Step 4:** Now, run the `index.html` in web browser, it will render the `Syncfusion JavaScript Lineargauge` control.

## Add Gauge Title

You can add a title using [`title`](../api/linear-gauge/linearGaugeModel/#title-string) property to the linear gauge to provide quick information to the user.

{% tab template="linear-gauge/es5-getting-started", es5Template="title" %}

{% endtab %}

## Axis Range

You can set the range to the axis using [`minimum`](../api/linear-gauge/axis/#minimum-number) and [`maximum`](../api/linear-gauge/axis/#maximum-number) properties.

{% tab template="linear-gauge/es5-getting-started", es5Template="axis" %}

{% endtab %}

To denote the axis values with temperature units, we can add °C as suffix to each label. This can be achieved by setting the {value}°C to the format property of labelStyle in the axis. Here, {value} acts as a placeholder for each axis label.

You can change the pointer value from the default value of the gauge by settings the [`value`](../api/linear-gauge/pointer/#value-number)  property in pointers option in axis.

{% tab template="linear-gauge/es5-getting-started", es5Template="temperature" %}

{% endtab %}

## Set Pointer Value

You can change the pointer value in the below sample using [`value`](../api/linear-gauge/pointer/#value-number) property in [`pointers`](../api/linear-gauge/pointer).

{% tab template="linear-gauge/es5-getting-started", es5Template="pointer" %}

{% endtab %}