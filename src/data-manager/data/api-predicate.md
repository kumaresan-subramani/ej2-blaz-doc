# Predicate

Predicate class is used to generate complex filter criteria.
This will be used by DataManager to perform multiple filtering operation.

## Methods

### and

Adds new predicate on existing predicate with “and” condition.

Returns [*Predicate*](./api-predicate.html)

### or

Adds new predicate on existing predicate with “or” condition.

Returns [*Predicate*](./api-predicate.html)

### toJson

Converts predicates to plain JavaScript.
This method is uses Json stringify when serializing Predicate object.

Returns *Object*

### validate

Validate the record based on the predicates.

| Parameter | Type | Description |
|------|------|-------------|
| record |  `Object` | Defines the datasource record.<br> |

Returns *boolean*

### and

Adds n-number of new predicates on existing predicate with “and” condition.

| Parameter | Type | Description |
|------|------|-------------|
| args |  `Object[]` | Defines the collection of predicates.<br> |

Returns [*Predicate*](./api-predicate.html)

### fromJson

Converts plain JavaScript object to Predicate object.

| Parameter | Type | Description |
|------|------|-------------|
| json |  `Predicate[]` &#124;  [`Predicate`](./api-predicate.html) | Defines single or collection of Predicate.<br> |

Returns *Predicate[]*

### or

Adds n-number of new predicates on existing predicate with “or” condition.

| Parameter | Type | Description |
|------|------|-------------|
| args |  `Object[]` | Defines the collection of predicates.<br> |

Returns [*Predicate*](./api-predicate.html)
