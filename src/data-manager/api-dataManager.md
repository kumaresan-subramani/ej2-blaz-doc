# DataManager

DataManager is used to manage and manipulate relational data.

## Methods

### executeLocal

Executes the given query with local data source.

| Parameter | Type | Description |
|------|------|-------------|
| query (*optional*) |  [`Query`](./api-query.html) | Defines the query to retrieve data.<br> |

Returns *Object[]*

### executeQuery

Executes the given query with either local or remote data source.
It will be executed as asynchronously and returns Promise object which will be resolved or rejected after action completed.

| Parameter | Type | Description |
|------|------|-------------|
| query |  [`Query`](./api-query.html) &#124;  `Function` | Defines the query to retrieve data. |
| done (*optional*) |  `Function` | Defines the callback function and triggers when the Promise is resolved. |
| fail (*optional*) |  `Function` | Defines the callback function and triggers when the Promise is rejected. |
| always (*optional*) |  `Function` | Defines the callback function and triggers when the Promise is resolved or rejected.<br> |

Returns *Promise*

### insert

Inserts new record in the given table.

Returns *Object* &#124;  *Promise*

### remove

Removes data from the table with the given key.

| Parameter | Type | Description |
|------|------|-------------|
| keyField |  `string` | Defines the column field. |
| value |  `Object` | Defines the value to find the data in the specified column. |
| tableName (*optional*) |  `string` &#124;  [`Query`](./api-query.html) | Defines the table name |
| query (*optional*) |  [`Query`](./api-query.html) | Sets default query for the DataManager.<br> |

Returns *Object* &#124;  *Promise*

### saveChanges

Save bulk changes to the given table name.
User can add a new record, edit an existing record, and delete a record at the same time.
If the datasource from remote, then updated in a single post.

| Parameter | Type | Description |
|------|------|-------------|
| changes |  `Object` | Defines the CrudOptions. |
| key (*optional*) |  `string` | Defines the column field. |
| tableName (*optional*) |  `string` &#124;  [`Query`](./api-query.html) | Defines the table name. |
| query (*optional*) |  [`Query`](./api-query.html) | Sets default query for the DataManager.<br> |

Returns *Promise* &#124;  *Object*

### setDefaultQuery

Overrides DataManager's default query with given query.

| Parameter | Type | Description |
|------|------|-------------|
| query |  [`Query`](./api-query.html) | Defines the new default query.<br> |

Returns [*DataManager*](./api-dataManager.html)

### update

Updates existing record in the given table.

| Parameter | Type | Description |
|------|------|-------------|
| keyField |  `string` | Defines the column field. |
| value |  `Object` | Defines the value to find the data in the specified column. |
| tableName (*optional*) |  `string` &#124;  [`Query`](./api-query.html) | Defines the table name |
| query (*optional*) |  [`Query`](./api-query.html) | Sets default query for the DataManager.<br> |

Returns *Object* &#124;  *Promise*
