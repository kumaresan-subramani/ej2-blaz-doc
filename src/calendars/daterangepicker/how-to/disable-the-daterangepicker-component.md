---
title: "How To"
component: "DateRangePicker"
description: "Miscellaneous aspects of customizing the date range picker"
---

# Disable the component

DateRangePicker can be inactivated on a page, by setting [`enabled`](../../api/daterangepicker#enabled) value as false that will disable the component completely from all the user interactions including in form post. The following example demonstrates the disabled component.

{% tab template="daterangepicker/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html" ,es5Template="daterangepicker-disabled-template"%}

```typescript

import { DateRangePicker } from '@syncfusion/ej2-calendars';
// creates daterangepicker with enabled property
let daterangeObject: DateRangePicker = new DateRangePicker({
    // sets the enabled as false
    enabled:false, placeholder:"Select Range"
});
daterangeObject.appendTo('#element');

```

{% endtab %}