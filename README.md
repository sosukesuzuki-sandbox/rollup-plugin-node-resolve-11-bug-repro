# rollup-plugin-node-resolve-11-bug-repro

From: https://github.com/prettier/prettier/pull/9804

## Actual

**terminal log:**

```
> rollup -c


src/index.js → bundle.js...
(!) Plugin node-resolve: Package subpath './util' is not defined by "exports" in /Users/sosukesuzuki/development/rollup-plugin-node-resolve-11-bug-repro/pkg/package.json
(!) Unresolved dependencies
https://rollupjs.org/guide/en/#warning-treating-module-as-external-dependency
pkg/util (imported by src/index.js)
created bundle.js in 16ms
```

**bundle.js:**

```js
"use strict";

Object.defineProperty(exports, "__esModule", { value: true });

var util = require("pkg/util");

Object.defineProperty(exports, "hello", {
  enumerable: true,
  get: function () {
    return util.hello;
  },
});
```

## Expected

**bundle.js:**

```js
// bundle.js
"use strict";

Object.defineProperty(exports, "__esModule", { value: true });

function hello() {
  console.log("util.js");
}

exports.hello = hello;
```
