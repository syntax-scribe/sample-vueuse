[⬅️ Back to Table of Contents](../../../../index.md)

# 📄 `createWorkerBlobUrl.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 2
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useWebWorkerFn/lib/createWorkerBlobUrl.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `depsParser` | `./depsParser` |
| `jobRunner` | `./jobRunner` |


---

## Functions

### `createWorkerBlobUrl(fn: Function, deps: string[], localDeps: Function[]): string`

<details><summary>Code</summary>

```ts
function createWorkerBlobUrl(fn: Function, deps: string[], localDeps: Function[]) {
  const blobCode = `${depsParser(deps, localDeps)}; onmessage=(${jobRunner})(${fn})`
  const blob = new Blob([blobCode], { type: 'text/javascript' })
  const url = URL.createObjectURL(blob)
  return url
}
```
</details>

- **JSDoc**:
```ts
/**
 * Converts the "fn" function into the syntax needed to be executed within a web worker
 *
 * @param fn the function to run with web worker
 * @param deps array of strings, imported into the worker through "importScripts"
 * @param localDeps array of function, local dependencies
 *
 * @returns a blob url, containing the code of "fn" as a string
 *
 * @example
 * createWorkerBlobUrl((a,b) => a+b, [])
 * // return "onmessage=return Promise.resolve((a,b) => a + b)
 * .then(postMessage(['SUCCESS', result]))
 * .catch(postMessage(['ERROR', error])"
 */
```

- **Parameters**:
  - `fn: Function`
  - `deps: string[]`
  - `localDeps: Function[]`
- **Return Type**: `string`
- **Calls**:
  - `depsParser (from ./depsParser)`
  - `URL.createObjectURL`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---