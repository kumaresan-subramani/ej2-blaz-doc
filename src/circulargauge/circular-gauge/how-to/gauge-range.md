# Range

## Add a range to the circular gauge dynamically

You can add a range to the circular gauge dynamically by pushing the new ranges to the circular gauge axes in button click.

To add ranges dynamically to the circular gauge, follow the given steps:

**Step 1**:

Initialize the circular gauge with one range.

{% tab template= "circular-gauge/how-to", sourceFiles="index.ts,index.html", es5Template="es5StaticRange" %}

```typescript

import { CircularGauge, Range } from '@syncfusion/ej2-circulargauge';

// initialize the circular gauge
let circulargauge: CircularGauge = new CircularGauge({
  axes: [
    {
      minimum: 0, maximum: 120,
      // initialize the ranges
      ranges: [
        {
          start: 0, end: 20
        }
      ]
    }
  ]
});
// render initialized circular gauge
circulargauge.appendTo('#element');
```

{% endtab %}

**Step 2**:

You can add ranges to the circular gauge dynamically using the button click event. In button click, add
the new ranges to the circular gauge axes. To refresh the circular gauge, invoke the `refresh` method.

{% tab template= "circular-gauge/how-to", sourceFiles="index.ts,index.html", es5Template="es5Range" %}

```typescript

import { CircularGauge, Range } from '@syncfusion/ej2-circulargauge';
let circulargauge: CircularGauge = new CircularGauge({
  axes: [
    {
      minimum: 0, maximum: 120,
      ranges: [
        {
          start: 0, end: 20
        }
      ]
    }
  ]
});
circulargauge.appendTo('#element');

document.getElementById("addRange").onclick = function () {
  let start: number;
  let end: number;
  start = +(circulargauge.axes[0].ranges[circulargauge.axes[0].ranges.length - 1].start) + 20;
  end = start + 20;
  if (end > circulargauge.axes[0].maximum) {
    circulargauge.axes[0].maximum = end;
  }
  let range = { start: start, end: end };
  circulargauge.axes[0].ranges.push(new Range(<Range>(circulargauge.axes[0].ranges[0]), 'ranges', range));
  circulargauge.refresh();
}
```

{% endtab %}
