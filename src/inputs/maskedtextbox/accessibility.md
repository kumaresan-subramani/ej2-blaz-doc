---
title: "Accessibility"
component: "MaskedTextBox"
description: "Accessibility support in masked textbox"
---

# Accessibility

The MaskedTextBox is characterized with complete ARIA Accessibility support that helps to access
through the on-screen readers and other assistive technology devices. This component is designed with the
reference of the guidelines document given in [WAI ARAI Accessibility practices](https://www.w3.org/TR/wai-aria-1.1/#textbox).

The MaskedTextBox uses the `textbox` role and following ARIA properties for its element based on its state.

| **Property** | **Functionality** |
| --- | --- |
| aria-live | The `aria-live` attribute indicates the priority of updates to a live region. |
| aria-disabled | The `aria-disabled` property indicates the disabled state of the MaskedTextBox. |
| aria-valuenow | The `aria-valuenow` property specifies the current value of the MaskedTextBox. |
| aria-invalid | The `aria-invalid` property indicates that the user input is incorrect or not within the acceptable ranges. |
| aria-placeholder | The `aria-placeholder` is a short hint to help the users with data entry when the MaskedTextBox has no value. |
| aria-labelledby | The `aria-labelledby` property indicates the floating label element of the MaskedTextBox. |