---
id: faq
title: 'Frequently Asked Questions'
---

### Do binaries get automatically deleted?

No, this package will **not** delete any binaries, so after an system / package upgrade the binaries may have to be cleaned manually.

### Why is there no documentation about class-options / interfaces in the documentation?

It is currently recommended to directly look at the TSDoc for these properties to get their type & documentation.

### Do testing database paths get cleaned up?

If the Database-path is a temporary directory (generated with `mkdtemp`), then it will automatically get cleaned-up when calling `.stop()`, this can be disabled with `.stop(false)`.  
If the Database-path is manually set with `dbPath`, then it needs to be manually cleaned-up with `.cleanup(true)`.

:::tip
Since `8.4.0` objects can also be used instead of just booleans for parameter in [`stop`](../api/classes/mongo-memory-server.md#stop) and [`cleanup`](../api/classes/mongo-memory-server.md#cleanup) (the same applies to `MongoMemoryReplSet`).  

For Example `.stop({ doCleanup: false })` can be used instead of `.stop(false)`.
:::

### Does this package support Explicit Resource Management?

Yes, `[Symbol.asyncDispose]` is implemented for all manager classes, behavior can be configured via `dispose` options:

- [`MongoMemoryServerOpts.dispose`](../api/interfaces/mongo-memory-server-opts.md#dispose)
- [`ReplSetOpts.dispose`](../api/interfaces/replset-opts.md#dispose)

:::note
Note that when using `await using server =` that `[Symbol.asyncDispose]` is called at the end of the scope even if the value is reassigned to something out of the current scope.
:::
