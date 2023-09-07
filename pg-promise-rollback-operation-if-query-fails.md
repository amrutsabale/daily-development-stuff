Using pg-promise transaction we can easily rollback executed db opertaion if any query fails.

When implementing a transaction in an external SQL file you need to provide all the proper handling for COMMIT and ROLLBACK. When you do not do that, 
the transaction status may become unpredictable inside your server-side code, and result in the type of errors that you are getting.

This can be a bit tricky, and easier said than done. This is why the best solution is not to do it at all.

Module pg-promise that you are already using provides reliable handling for transactions, via method tx, which is what you should be using.

From the tx method documentation:

````
Executes a callback function as a transaction (...)

A transaction wraps a regular task into additional queries:

it executes BEGIN just before invoking the callback function

it executes COMMIT, if the callback didn't throw any error or return a rejected promise, it executes ROLLBACK, if the callback did throw an error or return a rejected promise

it executes corresponding SAVEPOINT commands when the method is called recursively.
````

example
```
await db.tx(async t => {
    await t.none('DELETE...');
    await t.any('UPDATE...');
});
```
Ref: https://stackoverflow.com/questions/38558254/postgresql-catching-transaction-error-and-rollback
