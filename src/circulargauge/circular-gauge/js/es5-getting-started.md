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
> Control Script: `C:\Program Files (x86)\Syncfusion\Essential Studio\JavaScript - EJ2\16.3.0.17\Web (Essential JS 2)\JavaScript\ej2-circulargauge\dist\global\ej2-circulargauge.min.js`

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
        <!-- Essential JS 2 CircularGauge's global script (Control Script) -->
        <script src="resources/circulargauge/ej2-circulargauge.min.js" type="text/javascript"></script>
    </head>
    <body>
    </body>
</html>
```

**Step 5:** Now, add the `CircularGauge` element and initiate the `Syncfusion JavaScript (ES5) Circulargauge` control in the `~/quickstart/index.html` by using following code.

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>Essential JS 2</title>
        <!-- Essential JS 2 Base's global script (Dependency Script) -->
        <script src="resources/base/ej2-base.min.js" type="text/javascript"></script>
        <!-- Essential JS 2 CircularGauge's global script (Control Script) -->
        <script src="resources/circulargauge/ej2-circulargauge.min.js" type="text/javascript"></script>
    </head>
    <body>
        <!-- Add the HTML <circulargauge> element  -->
        <circulargauge id="element">Circular Gauge</circulargauge>
        <script>
            // initialize circulargauge control
            var circulargauge = new ej.circulargauge.CircularGauge();
            // Render initialized circulargauge.
            circulargauge.appendTo('#element');
        </script>
    </body>
</html>
```

**Step 6:** Now, run the `index.html` in web browser, it will render the **Syncfusion JavaScript Circulargauge** control.

### Using CDN link for script reference

**Step 1:** Create an app folder `quickstart` for getting started.

**Step 2:** The Essential JS 2 controls's global scripts is already hosted in the below CDN link formats.

**Syntax:**
> Dependency Script: `https://cdn.syncfusion.com/ej2/{DEPENDENCY_PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Control Script: `https://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`

**Example:**
> Script: [`https://cdn.syncfusion.com/ej2/ej2-circulargauge/dist/global/ej2-circulargauge.min.js`](https://cdn.syncfusion.com/ej2/ej2-circulargauge/dist/global/ej2-circulargauge.min.js)

**Step 3:** Create a HTML page (index.html) in `~/quickstart/index.html` location and add the CDN link references. Now, add the `Circulargauge` element and initiate the `Syncfusion JavaScript (ES5) Circulargauge` control in the index.html by using following code.

{% tab template="circular-gauge/es5-getting-started", es5Template="es5Default" %}

{% endtab %}

**Step 4:** Now, run the `index.html` in web browser, it will render the `Syncfusion JavaScript Circulargauge` control.

## Set Pointer Value

You can change the pointer value in the above sample using [`value`](../api/circular-gauge/pointer#value-number) property in [`pointers`](../api/circular-gauge/pointer).

{% tab template= "circular-gauge/es5-getting-started", es5Template="es5Pointer" %}

{% endtab %}