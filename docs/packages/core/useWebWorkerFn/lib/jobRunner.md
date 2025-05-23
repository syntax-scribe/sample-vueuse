[⬅️ Back to Table of Contents](../../../../index.md)

# 📄 `jobRunner.ts`

## 📚 Table of Contents

- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 0
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useWebWorkerFn/lib/jobRunner.ts`**

## 📦 Imports

> No imports found in this file.


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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---