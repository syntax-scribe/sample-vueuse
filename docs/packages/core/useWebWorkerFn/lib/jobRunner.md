[⬅️ Back to Table of Contents](../../../../index.md)

# 📄 `jobRunner.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📊 Variables & Constants | 1 |
| ⚡ Async/Await Patterns | 1 |

## 📚 Table of Contents

- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useWebWorkerFn/lib/jobRunner.ts`**

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `userFuncArgs` | `any` | const | `e.data[0]` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| promise-chain | `jobRunner` | *none* | Promise.resolve(userFunc.apply(undefined, userFuncArgs))
      .then((result) => {
        postMessage(['SUCCESS', result])
      }).catch, Promise.resolve(userFunc.apply(undefined, userFuncArgs)).then, Promise.resolve |


---

## Functions

### `jobRunner(userFunc: Function): (e: MessageEvent<any>) => Promise<void>`

<details><summary>Code</summary>

```ts
function jobRunner(userFunc: Function) {
  return (e: MessageEvent) => {
    const userFuncArgs = e.data[0]

    // eslint-disable-next-line prefer-spread
    return Promise.resolve(userFunc.apply(undefined, userFuncArgs))
      .then((result) => {
        postMessage(['SUCCESS', result])
      })
      .catch((error) => {
        postMessage(['ERROR', error])
      })
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * This function accepts as a parameter a function "userFunc"
 * And as a result returns an anonymous function.
 * This anonymous function, accepts as arguments,
 * the parameters to pass to the function "useArgs" and returns a Promise
 * This function can be used as a wrapper, only inside a Worker
 * because it depends by "postMessage".
 *
 * @param userFunc {Function} fn the function to run with web worker
 *
 * @returns returns a function that accepts the parameters
 * to be passed to the "userFunc" function
 */
```

- **Parameters**:
  - `userFunc: Function`
- **Return Type**: `(e: MessageEvent<any>) => Promise<void>`
- **Calls**:
  - `Promise.resolve(userFunc.apply(undefined, userFuncArgs))
      .then((result) => {
        postMessage(['SUCCESS', result])
      })
      .catch`
  - `postMessage`
- **Internal Comments**:
```
// eslint-disable-next-line prefer-spread
```


---