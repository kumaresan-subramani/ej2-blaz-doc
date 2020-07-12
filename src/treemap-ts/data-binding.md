# Data Binding

The tree map control supports data binding using the dataSource property.

## Populate data

The [`dataSource`] property accepts collection values as input. For example, a list of objects can be provided as input. Data can be given as either flat or hierarchical collection to the [`dataSource`] property.

<!-- markdownlint-disable MD036 -->

**Flat collection**

The following code shows how to bind a flat collection as data source to the tree map control.

{% tab template= "treemap/databind", sourceFiles="index.ts,index.html", es5Template="es5FlatCollection" %}

```typescript

import { TreeMap } from '@syncfusion/ej2-treemap';
let treemap: TreeMap = new TreeMap({
     dataSource: [
    {State:"United States", GDP:17946, percentage:11.08, Rank:1},
    {State:"China", GDP:10866, percentage: 28.42, Rank:2},
    {State:"Japan", GDP:4123, percentage:-30.78, Rank:3},
    {State:"Germany", GDP:3355, percentage:-5.19, Rank:4},
    {State:"United Kingdom", GDP:2848, percentage:8.28, Rank:5},
    {State:"France", GDP:2421, percentage:-9.69, Rank:6},
    {State:"India", GDP:2073, percentage:13.65, Rank:7},
    {State:"Italy", GDP:1814, percentage:-12.45, Rank:8},
    {State:"Brazil", GDP:1774, percentage:-27.88, Rank:9},
    {State:"Canada", GDP:1550, percentage:-15.02, Rank:10}
],
        weightValuePath: 'GDP',
        leafItemSettings: {
            labelPath: 'State'
        },
}, '#container');

```

{% endtab %}

**Hierarchical collection**

The following code shows how to bind a hierarchical collection as data source to the tree map control.

<!-- markdownlint-disable MD010 -->

{% tab template= "treemap/databind", sourceFiles="index.ts,index.html", es5Template="es5HierachicalCollection" %}

```typescript

import { TreeMap } from '@syncfusion/ej2-treemap';
let treemap: TreeMap = new TreeMap({
     dataSource: [{
 		"Continent": [{
 			"Name": "Africa",
 			"Population": 1216130000,
 			"States": [{
 					"Name": "Eastern Africa",
 					"Population": 410637987,
 					"Region": [{
 						"Name": "Ethiopia",
 						"Population": 107534882
 					}]
 				},
 				{
 					"Name": "Middle Africa",
 					"Population": 158562976,
 					"Region": [{
 						"Name": "Democratic, Republic of the Congo",
 						"Population": 84004989
 					}]
 				}
 			]
 		}]
 	},

 	{
 		"Continent": [{
 			"Name": "Asia",
 			"Population": 4436224000,
 			"States": [{
 					"Name": "Central Asia",
 					"Population": 69787760,
 					"Region": [{
 						"Name": "Uzbekistan",
 						"Population": 32364996
 					}]
 				},
 				{
 					"Name": "Eastern Asia",
 					"Population": 1641908531,
 					"Region": [{
 						"Name": "China",
 						"Population": 1415045928
 					}]
 				}
 			]
 		}]
 	},

 	{
 		"Continent": [{
 			"Name": "North America",
 			"Population": 579024000,
 			"States": [{
 					"Name": "Central America",
 					"Population": 174988756,
 					"Region": [{
 						"Name": "Mexico",
 						"Population": 130759074
 					}]
 				},
 				{
 					"Name": "Northern America",
 					"Population": 358593810,
 					"Region": [{
 						"Name": "U.S.",
 						"Population": 3267667480
 					}]
 				}
 			]
 		}]
 	},
 	{
 		"Continent": [{
 			"Name": "South America",
 			"Population": 422535000,
 			"States": [{
 				"Name": "Brazil",
 				"Population": 204519000
 			}]
 		}]
 	},
 	{
 		"Continent": [{
 			"Name": "Europe",
 			"Population": 738849000,
 			"States": [{
 					"Name": "Eastern Europe",
 					"Population": 291953328,
 					"Region": [{
 						"Name": "Russia",
 						"Population": 143964709
 					}]
 				},
 				{
 					"Name": "Northern Europe",
 					"Population": 103642971,
 					"Region": [{
 						"Name": "United Kingdom",
 						"Population": 66573504
 					}]
 				}
 			]
 		}]
 	}
 ],
       weightValuePath: 'Population',
        leafItemSettings: {
            labelPath: 'Name',
            fill:'#0077b3',
            border: { color: 'black', width: 0.5 }
        },
         levels: [
        { groupPath: 'Continent',fill:'#004466', border: { color: 'black', width: 0.5 } },
        { groupPath: 'States', fill:'#0099e6', border: { color: 'black', width: 0.5 } },
    ]
}, '#container');

```

{% endtab %}