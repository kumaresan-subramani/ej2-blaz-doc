# Deferred

Deferred is used to handle asynchronous operation.

## Properties

### catch `Function`

Defines the callback function triggers when the Deferred object is rejected.

### promise `Promise`

Promise is an object that represents a value that may not be available yet, but will be resolved at some point in the future.

### reject `Function`

Reject a Deferred object and call failCallbacks with the given args.

### resolve `Function`

Resolve a Deferred object and call doneCallbacks with the given args.

### then `Function`

Defines the callback function triggers when the Deferred object is resolved.
