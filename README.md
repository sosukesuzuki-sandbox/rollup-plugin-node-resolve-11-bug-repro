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
created bundle.js in 13ms
```

**bundle.js:**

```js
export { hello } from "pkg/util";
```

## Expected

**bundle.js:**

```js
function hello() {
  console.log("util.js");
}

export { hello };
```
