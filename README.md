# dynamo-db-local

**A wrapper around Amazon's DynamoDB Local to start and stop it from Node.js.**

[![version](https://img.shields.io/npm/v/dynamo-db-local.svg?style=flat-square)](https://www.npmjs.com/package/dynamo-db-local)

This module wraps Amazon's [DynamoDB Local](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Tools.DynamoDBLocal.html). It exposes one method called `spawn()` which calls [`child_process.spawn()`](https://nodejs.org/api/child_process.html#child_process_child_process_spawn_command_args_options) internally and returns its result.

```js
const dynamoDbLocalProcess = dynamoDbLocal.spawn();
// ...
dynamoDbLocalProcess.kill();
```

The `spawn()` function accecpts an optional options object which can have an optional path. If set,
that path will be used to store the database file. If no path is specified the database will be
kept in memory.

```js
const path = 'somewhere/on/your/disk';
const dynamoDbLocalProcess = dynamoDbLocal.spawn({ path });
// ...
dynamoDbLocalProcess.kill();
```

Another property the options object could have is port. It specifies the port number that the
process will run on. In absence of the port property, 8000 is used as the port number.

```js
const port = 8001;
const dynamoDbLocalProcess = dynamoDbLocal.spawn({ port });
// ...
dynamoDbLocalProcess.kill();
```

Finally the options object could have a sharedDb property. If true, DynamoDB will use a single database file, instead of using separate files for each credential and region. The default of this option is false.

```js
const dynamoDbLocalProcess = dynamoDbLocal.spawn({ sharedDb: true });
// ...
dynamoDbLocalProcess.kill();
```
