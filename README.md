# feathers-lowdb-yaml

**Deprecated in favor of** https://github.com/lwhiteley/feathers-lowdb

[![Node.js CI](https://github.com/FossPrime/feathers-lowdb-yaml/actions/workflows/Node18.yaml/badge.svg)](https://github.com/FossPrime/feathers-lowdb-yaml/actions/workflows/Node18.yaml)
[![Download Status](https://img.shields.io/npm/dm/@feathersjs/memory.svg?style=flat-square)](https://www.npmjs.com/package/@feathersjs/memory)
[![Discord](https://badgen.net/badge/icon/discord?icon=discord&label)](https://discord.gg/qa8kez8QBx)

A [Feathers](https://feathersjs.com) service adapter for YAML data storage that works on all platforms.
Using LowDB v3. Good for cashing, development, debugging and offline-support.

<p align="center">
  <a href="https://replit.com/new/github/FossPrime/feathers-yaml"><img src="https://replit.com/badge/github/feathersjs/playground" alt="Run on Repl.it"></a> 
</p>

# Roadmap

- [x] Basic LowDB support
- [x] YAML support
- [x] Rename service and adapter
- [x] Publish to NPM
- [ ] JSON support
- [ ] MongoDB compatibility mode (ObjectID's)
- [ ] Alternative production configuration (Swap in a binary DB in prod/staging)


```bash
$ npm i feathers-yaml
```

## API

### `yaml([options])`

Returns a new database instance initialized with the given options.

```js
import { yaml as database } from 'feathers-yaml'

export const createModel = (app: Application) => {
  return database({
    filename: 'users.yaml',
    id: '_id', // todo: https://github.com/feathersjs/feathers/issues/2839
    startId: 1,
    paginate: {
      default: 2,
      max: 4
    }
  })
}
```

**Options:**

- `filename` (_optional, default `/tmp/low-123-321.yaml`) - The full path to the file
- `id` (_optional_, default: `'id'`) - The name of the id field property.
- `startId` (_optional_, default: `0`) - An id number to start with that will be incremented for every new record (unless it is already set).
- `store` (_optional_) - An object with id to item assignments to pre-initialize the data store
- `events` (_optional_) - A list of [custom service events](https://docs.feathersjs.com/api/events.html#custom-events) sent by this service
- `paginate` (_optional_) - A [pagination object](https://docs.feathersjs.com/api/databases/common.html#pagination) containing a `default` and `max` page size
- `whitelist` (_DEPRECATED_) - renamed to `allow`
- `allow` (_optional_) - A list of additional query parameters to allow
- `multi` (_optional_) - Allow `create` with arrays and `update` and `remove` with `id` `null` to change multiple items. Can be `true` for all methods or an array of allowed methods (e.g. `[ 'remove', 'create' ]`)

## Example

_Todo_

## License

Copyright (c) 2023 [Feathers contributors](https://github.com/feathersjs/feathers/graphs/contributors)

Licensed under the [MIT license](LICENSE).
