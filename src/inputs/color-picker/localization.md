---
title: "ColorPicker Localization"
component: "ColorPicker"
description: "TypeScript ColorPicker component supports localization which allows the end user to localize default text content of the colorpicker in various cultures."
---

# Localization and RTL

## Localization

The [`Localization`](../api/base/l10n) library allows you to localize default text content of the
ColorPicker. The ColorPicker component has static text for `control buttons (apply / cancel)` and `mode switcher` that can be changed to other cultures (Arabic, Deutsch, French, etc.) by defining the
[`locale`](../api/color-picker#locale) value and translation object.

The following list of properties and its values are used in the ColorPicker.

Locale key words |Text
-----|-----
Apply |Apply
Cancel |Cancel
ModeSwitcher |Switch Mode

### Loading translations

To load translation object in an application use [`load`](../api/base/l10n#load) function of [`L10n`](../api/base/l10n) class.

The below example demonstrates the ColorPicker in `Deutsch` culture.

{% tab template="colorpicker/how-to", isDefaultActive = "true", sourceFiles="app.ts,index.html,styles.css", es5Template="locale-template" %}

```typescript
import { ColorPicker } from '@syncfusion/ej2-inputs';
import { enableRipple, L10n } from '@syncfusion/ej2-base';

enableRipple(true);

L10n.load({
    'de-DE': {
        'colorpicker': {
            "Apply": "Anwenden",
            "Cancel": "Abbrechen",
            "ModeSwitcher": "Modus wechseln"
        }
    }
});

let colorPicker: ColorPicker = new ColorPicker({ locale: 'de-DE' }, '#element');
```

{% endtab %}

## Right to Left - RTL

ColorPicker component has `RTL` support. It helps to render the ColorPicker from right-to-left direction.
It improves the user experiences and accessibility for users who use right-to-left languages(Arabic, Farsi, Urdu, etc). This can be achieved by setting the [`enableRtl`](../api/color-picker#enablertl) property to `true`.

The following example illustrates how to enable right-to-left support in ColorPicker component.

{% tab template="colorpicker/rtl", sourceFiles="app.ts,index.html,styles.css", es5Template="rtl-template" %}

```typescript
import { ColorPicker } from '@syncfusion/ej2-inputs';
import { enableRipple, L10n } from '@syncfusion/ej2-base';

enableRipple(true);

L10n.load({
    'ar-AE': {
        'colorpicker': {
            'Apply': 'تطبيق',
            'Cancel': 'إلغاء',
            'ModeSwitcher': 'مفتاح كهربائي الوضع'
        }
    }
});

let colorPicker: ColorPicker = new ColorPicker({ enableRtl: true, locale: 'ar-AE' }, '#element');
```

{% endtab %}

## See Also

* [More information about localization](./../common/localization)