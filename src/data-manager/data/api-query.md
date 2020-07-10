# Query

Query class is used to build query which is used by the DataManager to communicate with datasource.

## Methods

### addParams

Adds additional parameter which will be sent along with the request which will be generated while DataManager execute.

| Parameter | Type | Description |
|------|------|-------------|
| key |  `string` | Defines the key of additional parameter. |
| value |  `Function` &#124;  `string` | Defines the value for the key.<br> |

Returns [*Query*](./api-query.html)

### aggregate

Aggregate the data with given type and field name.

| Parameter | Type | Description |
|------|------|-------------|
| type |  `string` | Defines the aggregate type. |
| field |  `string` | Defines the column field to aggregate.<br> |

Returns [*Query*](./api-query.html)

### clone

Creates deep copy of the Query object.

Returns [*Query*](./api-query.html)

### execute

Executes query with the given DataManager.

| Parameter | Type | Description |
|------|------|-------------|
| dataManager (*optional*) |  [`DataManager`](./api-dataManager.html) | Defines the DataManager. |
| done (*optional*) |  `Function` | Defines the success callback. |
| fail (*optional*) |  `Function` | Defines the failure callback. |
| always (*optional*) |  `Function` | Defines the callback which will be invoked on either success or failure.<br><br><pre><br>let dataManager: DataManager = new DataManager([{ ID: '10' }, { ID: '2' }, { ID: '1' }, { ID: '20' }]);<br>let query: Query = new Query();<br>query.sortBy('ID', (x: string, y: string): number => { return parseInt(x, 10) - parseInt(y, 10) });<br>let promise: Promise< Object > = query.execute(dataManager);<br>promise.then((e: { result: Object }) => { });<br></pre><br> |

Returns *Promise*

### executeLocal

Executes query with the local datasource.

| Parameter | Type | Description |
|------|------|-------------|
| dataManager (*optional*) |  [`DataManager`](./api-dataManager.html) | Defines the DataManager.<br> |

Returns *Object[]*

### expand

Expands the related table.

| Parameter | Type | Description |
|------|------|-------------|
| tables |  `string` &#124;  `Object[]` | <br> |

Returns [*Query*](./api-query.html)

### foreignKey

Sets the foreign key which is used to get data from the related table.

| Parameter | Type | Description |
|------|------|-------------|
| key |  `string` | Defines the foreign key.<br> |

Returns [*Query*](./api-query.html)

### from

Specifies the name of table to retrieve data in query execution.

| Parameter | Type | Description |
|------|------|-------------|
| tableName |  `string` | Defines the table name.<br> |

Returns [*Query*](./api-query.html)

### group

Groups data with the given field name.

Returns [*Query*](./api-query.html)

### hierarchy

Gets the records in hierarchical relationship from two tables. It requires the foreign key to relate two tables.

| Parameter | Type | Description |
|------|------|-------------|
| query |  [`Query`](./api-query.html) | Defines the query to relate two tables. |
| selectorFn |  `Function` | Defines the custom function to select records.<br> |

Returns [*Query*](./api-query.html)

### page

Gets data based on the given page index and size.

| Parameter | Type | Description |
|------|------|-------------|
| pageIndex |  `number` | Defines the current page index. |
| pageSize |  `number` | Defines the no of records per page.<br> |

Returns [*Query*](./api-query.html)

### range

Gets data based on the given start and end index.

| Parameter | Type | Description |
|------|------|-------------|
| start |  `number` | Defines the start index of the datasource. |
| end |  `number` | Defines the end index of the datasource.<br> |

Returns [*Query*](./api-query.html)

### requiresCount

It is used to get total number of records in the DataManager execution result.

Returns [*Query*](./api-query.html)

### search

Search data with given search criteria.

Returns [*Query*](./api-query.html)

### select

Selects specified columns from the data source.

| Parameter | Type | Description |
|------|------|-------------|
| fieldNames |  `string` &#124;  `string[]` | Defines the collection of column fields.<br> |

Returns [*Query*](./api-query.html)

### setKey

Sets the primary key.

| Parameter | Type | Description |
|------|------|-------------|
| field |  `string` | Defines the column field.<br> |

Returns [*Query*](./api-query.html)

### skip

Skips data with given number of records count from the top of the data source.

| Parameter | Type | Description |
|------|------|-------------|
| nos |  `number` | Defines the no of records skip in the datasource.<br> |

Returns [*Query*](./api-query.html)

### sortBy

Sort the data with given sort criteria.
By default, sort direction is ascending.

Returns [*Query*](./api-query.html)

### sortByDesc

Sorts data in descending order.

| Parameter | Type | Description |
|------|------|-------------|
| fieldName |  `string` | Defines the column field.<br> |

Returns [*Query*](./api-query.html)

### take

Gets data from the top of the data source based on given number of records count.

| Parameter | Type | Description |
|------|------|-------------|
| nos |  `number` | Defines the no of records to retrieve from datasource.<br> |

Returns [*Query*](./api-query.html)

### using

Sets default DataManager to execute query.

| Parameter | Type | Description |
|------|------|-------------|
| dataManager |  [`DataManager`](./api-dataManager.html) | Defines the DataManager.<br> |

Returns [*Query*](./api-query.html)

### where

Filter data with given filter criteria.

Returns [*Query*](./api-query.html)
