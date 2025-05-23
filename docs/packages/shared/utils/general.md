[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `general.ts`

## 📚 Table of Contents

- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 12
- **Classes**: 0
- **Imports**: 0
- **Interfaces**: 1
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/shared/utils/general.ts`**

## 📦 Imports

> No imports found in this file.


---

## Functions

### `promiseTimeout(ms: number, throwOnTimeout: boolean, reason: string): Promise<void>`

<details><summary>Code</summary>

```ts
export function promiseTimeout(
  ms: number,
  throwOnTimeout = false,
  reason = 'Timeout',
): Promise<void> {
  return new Promise((resolve, reject) => {
    if (throwOnTimeout)
      setTimeout(() => reject(reason), ms)
    else
      setTimeout(resolve, ms)
  })
}
```
</details>

- **Parameters**:
  - `ms: number`
  - `throwOnTimeout: boolean`
  - `reason: string`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `setTimeout`
  - `reject`
### `identity(arg: T): T`

<details><summary>Code</summary>

```ts
export function identity<T>(arg: T): T {
  return arg
}
```
</details>

- **Parameters**:
  - `arg: T`
- **Return Type**: `T`
### `createSingletonPromise(fn: () => Promise<T>): SingletonPromiseReturn<T>`

<details><summary>Code</summary>

```ts
export function createSingletonPromise<T>(fn: () => Promise<T>): SingletonPromiseReturn<T> {
  let _promise: Promise<T> | undefined

  function wrapper() {
    if (!_promise)
      _promise = fn()
    return _promise
  }
  wrapper.reset = async () => {
    const _prev = _promise
    _promise = undefined
    if (_prev)
      await _prev
  }

  return wrapper
}
```
</details>

- **JSDoc**:
```ts
/**
 * Create singleton promise function
 *
 * @example
 * ```
 * const promise = createSingletonPromise(async () => { ... })
 *
 * await promise()
 * await promise() // all of them will be bind to a single promise instance
 * await promise() // and be resolved together
 * ```
 */
```

- **Parameters**:
  - `fn: () => Promise<T>`
- **Return Type**: `SingletonPromiseReturn<T>`
- **Calls**:
  - `fn`
### `wrapper(): Promise<T>`

<details><summary>Code</summary>

```ts
function wrapper() {
    if (!_promise)
      _promise = fn()
    return _promise
  }
```
</details>

- **Return Type**: `Promise<T>`
- **Calls**:
  - `fn`
### `invoke(fn: () => T): T`

<details><summary>Code</summary>

```ts
export function invoke<T>(fn: () => T): T {
  return fn()
}
```
</details>

- **Parameters**:
  - `fn: () => T`
- **Return Type**: `T`
- **Calls**:
  - `fn`
### `containsProp(obj: object, props: string[]): boolean`

<details><summary>Code</summary>

```ts
export function containsProp(obj: object, ...props: string[]) {
  return props.some(k => k in obj)
}
```
</details>

- **Parameters**:
  - `obj: object`
  - `props: string[]`
- **Return Type**: `boolean`
- **Calls**:
  - `props.some`
### `increaseWithUnit(target: number, delta: number): number`

<details><summary>Code</summary>

```ts
export function increaseWithUnit(target: number, delta: number): number
```
</details>

- **JSDoc**:
```ts
/**
 * Increase string a value with unit
 *
 * @example '2px' + 1 = '3px'
 * @example '15em' + (-2) = '13em'
 */
```

- **Parameters**:
  - `target: number`
  - `delta: number`
- **Return Type**: `number`
### `pxValue(px: string): number`

<details><summary>Code</summary>

```ts
export function pxValue(px: string) {
  return px.endsWith('rem') ? Number.parseFloat(px) * 16 : Number.parseFloat(px)
}
```
</details>

- **JSDoc**:
```ts
/**
 * Get a px value for SSR use, do not rely on this method outside of SSR as REM unit is assumed at 16px, which might not be the case on the client
 */
```

- **Parameters**:
  - `px: string`
- **Return Type**: `number`
- **Calls**:
  - `px.endsWith`
  - `Number.parseFloat`
### `objectPick(obj: O, keys: T[], omitUndefined: boolean): Pick<O, T>`

<details><summary>Code</summary>

```ts
export function objectPick<O extends object, T extends keyof O>(obj: O, keys: T[], omitUndefined = false) {
  return keys.reduce((n, k) => {
    if (k in obj) {
      if (!omitUndefined || obj[k] !== undefined)
        n[k] = obj[k]
    }
    return n
  }, {} as Pick<O, T>)
}
```
</details>

- **JSDoc**:
```ts
/**
 * Create a new subset object by giving keys
 */
```

- **Parameters**:
  - `obj: O`
  - `keys: T[]`
  - `omitUndefined: boolean`
- **Return Type**: `Pick<O, T>`
- **Calls**:
  - `keys.reduce`
### `objectOmit(obj: O, keys: T[], omitUndefined: boolean): Omit<O, T>`

<details><summary>Code</summary>

```ts
export function objectOmit<O extends object, T extends keyof O>(obj: O, keys: T[], omitUndefined = false) {
  return Object.fromEntries(Object.entries(obj).filter(([key, value]) => {
    return (!omitUndefined || value !== undefined) && !keys.includes(key as T)
  })) as Omit<O, T>
}
```
</details>

- **JSDoc**:
```ts
/**
 * Create a new subset object by omit giving keys
 */
```

- **Parameters**:
  - `obj: O`
  - `keys: T[]`
  - `omitUndefined: boolean`
- **Return Type**: `Omit<O, T>`
- **Calls**:
  - `Object.fromEntries`
  - `Object.entries(obj).filter`
  - `keys.includes`
### `objectEntries(obj: T): [keyof T, T[keyof T]][]`

<details><summary>Code</summary>

```ts
export function objectEntries<T extends object>(obj: T) {
  return Object.entries(obj) as Array<[keyof T, T[keyof T]]>
}
```
</details>

- **Parameters**:
  - `obj: T`
- **Return Type**: `[keyof T, T[keyof T]][]`
- **Calls**:
  - `Object.entries`
### `toArray(value: T | readonly T[]): readonly T[]`

<details><summary>Code</summary>

```ts
export function toArray<T>(value: T | readonly T[]): readonly T[]
```
</details>

- **Parameters**:
  - `value: T | readonly T[]`
- **Return Type**: `readonly T[]`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `SingletonPromiseReturn<T>`

<details><summary>Interface Code</summary>

```ts
export interface SingletonPromiseReturn<T> {
  (): Promise<T>
  /**
   * Reset current staled promise.
   * await it to have proper shutdown.
   */
  reset: () => Promise<void>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `reset` | `() => Promise<void>` | ✗ |  |


---

## Type Aliases

> No type aliases found in this file.


---