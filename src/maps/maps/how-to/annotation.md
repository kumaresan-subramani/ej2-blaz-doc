# Annotations

Annotations are used to mark the specific area of interest in a map area with texts, shapes, or images. To update the annotation in maps, please follow the given procedure.
 <!-- markdownlint-disable MD031 -->
Initialize the maps control with annotation option, and specify the ID of HTML element in the content that needs to be displayed in maps area by using the `content` property. You can specify the content position with `x` and `y` values as mentioned in the following code example. To know more about annotations, please refer to the [`API`](../../api/maps/annotation/) documentation.

{% tab template="maps/default-map", sourceFiles="index.ts,index.html", es5Template="annotation" %}

```typescript
import { Africa_Continent } from './Africa_Continent.ts';
import { Maps , Annotations } from '@syncfusion/ej2-maps';
Maps.Inject(Annotations);

// initialize Maps component
let map: Maps = new Maps({
        layers: [
        {
            shapeData: Africa_Continent,
            shapeSettings: {
                fill: 'url(#grad1)'
            }
        }
    ],
    annotations:[
        {
        content:'#maps-annotation', // To insert the text content
        x: '0%', y: '70%'
        },
        {
        content: '#compass-maps',  // To insert the image
        x: '80%', y: '5%'
        }
    ]
}, '#element');

```

{% endtab %}

```html
    <svg height="150" width="400">
        <defs>
            <linearGradient id="grad1" x1="0%" y1="0%" x2="0%" y2="100%">
                <stop offset="0%" style="stop-color:#C5494B;stop-opacity:1"></stop>
                <stop offset="100%" style="stop-color:#4C134F;stop-opacity:1"></stop>
            </linearGradient>
        </defs>
    </svg>
    <div id="maps-annotation" style="display: none;">
          <div id="annotation">
              <div>
                  <p style="margin-left:10px;font-size:13px;font-weight:500">Facts about Africa</p>
              </div>
              <hr style="margin-top:-3px;margin-bottom:10px;border:0.5px solid #DDDDDD">
              <div>
                  <ul style="list-style-type:disc; margin-left:-20px;margin-bottom:2px; font-weight:400">
                      <li>Africa is the second largest and second most populated continent in the world.</li>
                      <li style="padding-top:5px;">Africa has 54 sovereign states and 10 non-sovereign territories.</li>
                      <li style="padding-top:5px;">Algeria is the largest country in Africa, where as Mayotte is the smallest.</li>
                  </ul>
              </div>
          </div>
      </div>
      <div id="compass-maps" style="display: none;">
          <img src="src/app/images/compass.png" height="75px" width="75px">
      </div>
       <style>
            #annotation {
              color: #DDDDDD;
              font-size: 12px;
              font-family: Roboto;
              background: #3E464C;
              margin: 20px;
              padding: 10px;
              border-radius: 2px;
              width: 300px;
              box-shadow: 0px 2px 5px #666;
             }
        </style>
```