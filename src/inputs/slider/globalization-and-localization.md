---
title: "Syncfusion JavaScript Range Slider Globalization"
component: "Slider"
description: "Learn about JavaScript range slider control localization, allows the end user to localize values of the slider in various cultures."
---

# Globalization

## Localization

The [`Localization`](../api/base/l10n) library allows you to localize default text content of the Slider. The slider control has static text on some features (like increase and decrease button) that can be changed to other cultures (Arabic, Deutsch, French, etc.) by defining the
[`locale`](../api/slider#locale) value and translation object.

The following list of properties and its values are used in the slider.

Locale keywords |Text
-----|-----
Increase | Increase
Decrease | Decrease

### Loading translations

To load translation object in an application, use [`load`](../api/base/l10n#load) function of the [`L10n`](../api/base/l10n) class.

The following example demonstrates the Slider in `Deutsch` culture.

{% tab template="slider/localization", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css", es5Template="localization-template" %}

```typescript


import { Slider } from '@syncfusion/ej2-inputs';
import { L10n } from '@syncfusion/ej2-base';


L10n.load({
    'de-DE': {
        'slider': {
            incrementTitle: 'Erhöhen, ansteigen', decrementTitle: 'verringern'
        }
    }
});
    // Initialize range Slider control
    let rangeObj: Slider = new Slider({
        value: [30, 70],
        type: 'Range',
        locale: 'de-DE',
        showButtons: true
    });
    rangeObj.appendTo('#slider');

```

{% endtab %}

## See Also

* [Internationalization](../common/internationalization/)
* [Localization](../common/localization/)