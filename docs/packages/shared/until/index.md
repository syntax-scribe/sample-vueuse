[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 11
- **Classes**: 0
- **Imports**: 10
- **Interfaces**: 4
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/shared/until/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `WatchOptions` | `vue` |
| `WatchSource` | `vue` |
| `ElementOf` | `../utils` |
| `ShallowUnwrapRef` | `../utils` |
| `isRef` | `vue` |
| `nextTick` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `promiseTimeout` | `../utils` |


---

## Functions

### `createUntil(r: any, isNot: boolean): UntilArrayInstance<T> | UntilValueInstance<T, boolean>`

<details><summary>Code</summary>

```ts
function createUntil<T>(r: any, isNot = false) {
  function toMatch(
    condition: (v: any) => boolean,
    { flush = 'sync', deep = false, timeout, throwOnTimeout }: UntilToMatchOptions = {},
  ): Promise<T> {
    let stop: (() => void) | null = null
    const watcher = new Promise<T>((resolve) => {
      stop = watch(
        r,
        (v) => {
          if (condition(v) !== isNot) {
            if (stop)
              stop()
            else
              nextTick(() => stop?.())
            resolve(v)
          }
        },
        {
          flush,
          deep,
          immediate: true,
        },
      )
    })

    const promises = [watcher]
    if (timeout != null) {
      promises.push(
        promiseTimeout(timeout, throwOnTimeout)
          .then(() => toValue(r))
          .finally(() => stop?.()),
      )
    }

    return Promise.race(promises)
  }

  function toBe<P>(value: MaybeRefOrGetter<P | T>, options?: UntilToMatchOptions) {
    if (!isRef(value))
      return toMatch(v => v === value, options)

    const { flush = 'sync', deep = false, timeout, throwOnTimeout } = options ?? {}
    let stop: (() => void) | null = null
    const watcher = new Promise<T>((resolve) => {
      stop = watch(
        [r, value],
        ([v1, v2]) => {
          if (isNot !== (v1 === v2)) {
            if (stop)
              stop()
            else
              nextTick(() => stop?.())
            resolve(v1)
          }
        },
        {
          flush,
          deep,
          immediate: true,
        },
      )
    })

    const promises = [watcher]
    if (timeout != null) {
      promises.push(
        promiseTimeout(timeout, throwOnTimeout)
          .then(() => toValue(r))
          .finally(() => {
            stop?.()
            return toValue(r)
          }),
      )
    }

    return Promise.race(promises)
  }

  function toBeTruthy(options?: UntilToMatchOptions) {
    return toMatch(v => Boolean(v), options)
  }

  function toBeNull(options?: UntilToMatchOptions) {
    return toBe<null>(null, options)
  }

  function toBeUndefined(options?: UntilToMatchOptions) {
    return toBe<undefined>(undefined, options)
  }

  function toBeNaN(options?: UntilToMatchOptions) {
    return toMatch(Number.isNaN, options)
  }

  function toContains(
    value: any,
    options?: UntilToMatchOptions,
  ) {
    return toMatch((v) => {
      const array = Array.from(v as any)
      return array.includes(value) || array.includes(toValue(value))
    }, options)
  }

  function changed(options?: UntilToMatchOptions) {
    return changedTimes(1, options)
  }

  function changedTimes(n = 1, options?: UntilToMatchOptions) {
    let count = -1 // skip the immediate check
    return toMatch(() => {
      count += 1
      return count >= n
    }, options)
  }

  if (Array.isArray(toValue(r))) {
    const instance: UntilArrayInstance<T> = {
      toMatch: toMatch as any,
      toContains,
      changed,
      changedTimes,
      get not() {
        return createUntil(r, !isNot) as UntilArrayInstance<T>
      },
    }
    return instance
  }
  else {
    const instance: UntilValueInstance<T, boolean> = {
      toMatch: toMatch as any,
      toBe,
      toBeTruthy: toBeTruthy as any,
      toBeNull: toBeNull as any,
      toBeNaN,
      toBeUndefined: toBeUndefined as any,
      changed,
      changedTimes,
      get not() {
        return createUntil(r, !isNot) as UntilValueInstance<T, boolean>
      },
    }

    return instance
  }
}
```
</details>

- **Parameters**:
  - `r: any`
  - `isNot: boolean`
- **Return Type**: `UntilArrayInstance<T> | UntilValueInstance<T, boolean>`
- **Calls**:
  - `watch (from vue)`
  - `condition`
  - `stop`
  - `nextTick (from vue)`
  - `resolve`
  - `promises.push`
  - `promiseTimeout(timeout, throwOnTimeout)
          .then(() => toValue(r))
          .finally`
  - `Promise.race`
  - `isRef (from vue)`
  - `toMatch`
  - `toValue (from vue)`
  - `Boolean`
  - `toBe`
  - `Array.from`
  - `array.includes`
  - `changedTimes`
  - `Array.isArray`
  - `createUntil`
### `toMatch(condition: (v: any) => boolean, { flush = 'sync', deep = false, timeout, throwOnTimeout }: UntilToMatchOptions): Promise<T>`

<details><summary>Code</summary>

```ts
function toMatch(
    condition: (v: any) => boolean,
    { flush = 'sync', deep = false, timeout, throwOnTimeout }: UntilToMatchOptions = {},
  ): Promise<T> {
    let stop: (() => void) | null = null
    const watcher = new Promise<T>((resolve) => {
      stop = watch(
        r,
        (v) => {
          if (condition(v) !== isNot) {
            if (stop)
              stop()
            else
              nextTick(() => stop?.())
            resolve(v)
          }
        },
        {
          flush,
          deep,
          immediate: true,
        },
      )
    })

    const promises = [watcher]
    if (timeout != null) {
      promises.push(
        promiseTimeout(timeout, throwOnTimeout)
          .then(() => toValue(r))
          .finally(() => stop?.()),
      )
    }

    return Promise.race(promises)
  }
```
</details>

- **Parameters**:
  - `condition: (v: any) => boolean`
  - `{ flush = 'sync', deep = false, timeout, throwOnTimeout }: UntilToMatchOptions`
- **Return Type**: `Promise<T>`
- **Calls**:
  - `watch (from vue)`
  - `condition`
  - `stop`
  - `nextTick (from vue)`
  - `resolve`
  - `promises.push`
  - `promiseTimeout(timeout, throwOnTimeout)
          .then(() => toValue(r))
          .finally`
  - `Promise.race`
### `toBe(value: MaybeRefOrGetter<P | T>, options: UntilToMatchOptions): Promise<T>`

<details><summary>Code</summary>

```ts
function toBe<P>(value: MaybeRefOrGetter<P | T>, options?: UntilToMatchOptions) {
    if (!isRef(value))
      return toMatch(v => v === value, options)

    const { flush = 'sync', deep = false, timeout, throwOnTimeout } = options ?? {}
    let stop: (() => void) | null = null
    const watcher = new Promise<T>((resolve) => {
      stop = watch(
        [r, value],
        ([v1, v2]) => {
          if (isNot !== (v1 === v2)) {
            if (stop)
              stop()
            else
              nextTick(() => stop?.())
            resolve(v1)
          }
        },
        {
          flush,
          deep,
          immediate: true,
        },
      )
    })

    const promises = [watcher]
    if (timeout != null) {
      promises.push(
        promiseTimeout(timeout, throwOnTimeout)
          .then(() => toValue(r))
          .finally(() => {
            stop?.()
            return toValue(r)
          }),
      )
    }

    return Promise.race(promises)
  }
```
</details>

- **Parameters**:
  - `value: MaybeRefOrGetter<P | T>`
  - `options: UntilToMatchOptions`
- **Return Type**: `Promise<T>`
- **Calls**:
  - `isRef (from vue)`
  - `toMatch`
  - `watch (from vue)`
  - `stop`
  - `nextTick (from vue)`
  - `resolve`
  - `promises.push`
  - `promiseTimeout(timeout, throwOnTimeout)
          .then(() => toValue(r))
          .finally`
  - `toValue (from vue)`
  - `Promise.race`
### `toBeTruthy(options: UntilToMatchOptions): Promise<T>`

<details><summary>Code</summary>

```ts
function toBeTruthy(options?: UntilToMatchOptions) {
    return toMatch(v => Boolean(v), options)
  }
```
</details>

- **Parameters**:
  - `options: UntilToMatchOptions`
- **Return Type**: `Promise<T>`
- **Calls**:
  - `toMatch`
  - `Boolean`
### `toBeNull(options: UntilToMatchOptions): Promise<T>`

<details><summary>Code</summary>

```ts
function toBeNull(options?: UntilToMatchOptions) {
    return toBe<null>(null, options)
  }
```
</details>

- **Parameters**:
  - `options: UntilToMatchOptions`
- **Return Type**: `Promise<T>`
- **Calls**:
  - `toBe`
### `toBeUndefined(options: UntilToMatchOptions): Promise<T>`

<details><summary>Code</summary>

```ts
function toBeUndefined(options?: UntilToMatchOptions) {
    return toBe<undefined>(undefined, options)
  }
```
</details>

- **Parameters**:
  - `options: UntilToMatchOptions`
- **Return Type**: `Promise<T>`
- **Calls**:
  - `toBe`
### `toBeNaN(options: UntilToMatchOptions): Promise<T>`

<details><summary>Code</summary>

```ts
function toBeNaN(options?: UntilToMatchOptions) {
    return toMatch(Number.isNaN, options)
  }
```
</details>

- **Parameters**:
  - `options: UntilToMatchOptions`
- **Return Type**: `Promise<T>`
- **Calls**:
  - `toMatch`
### `toContains(value: any, options: UntilToMatchOptions): Promise<T>`

<details><summary>Code</summary>

```ts
function toContains(
    value: any,
    options?: UntilToMatchOptions,
  ) {
    return toMatch((v) => {
      const array = Array.from(v as any)
      return array.includes(value) || array.includes(toValue(value))
    }, options)
  }
```
</details>

- **Parameters**:
  - `value: any`
  - `options: UntilToMatchOptions`
- **Return Type**: `Promise<T>`
- **Calls**:
  - `toMatch`
  - `Array.from`
  - `array.includes`
  - `toValue (from vue)`
### `changed(options: UntilToMatchOptions): Promise<T>`

<details><summary>Code</summary>

```ts
function changed(options?: UntilToMatchOptions) {
    return changedTimes(1, options)
  }
```
</details>

- **Parameters**:
  - `options: UntilToMatchOptions`
- **Return Type**: `Promise<T>`
- **Calls**:
  - `changedTimes`
### `changedTimes(n: number, options: UntilToMatchOptions): Promise<T>`

<details><summary>Code</summary>

```ts
function changedTimes(n = 1, options?: UntilToMatchOptions) {
    let count = -1 // skip the immediate check
    return toMatch(() => {
      count += 1
      return count >= n
    }, options)
  }
```
</details>

- **Parameters**:
  - `n: number`
  - `options: UntilToMatchOptions`
- **Return Type**: `Promise<T>`
- **Calls**:
  - `toMatch`
### `until(r: WatchSource<T> | MaybeRefOrGetter<T>): UntilArrayInstance<T>`

<details><summary>Code</summary>

```ts
export function until<T extends unknown[]>(r: WatchSource<T> | MaybeRefOrGetter<T>): UntilArrayInstance<T>
```
</details>

- **JSDoc**:
```ts
/**
 * Promised one-time watch for changes
 *
 * @see https://vueuse.org/until
 * @example
 * ```
 * const { count } = useCounter()
 *
 * await until(count).toMatch(v => v > 7)
 *
 * alert('Counter is now larger than 7!')
 * ```
 */
```

- **Parameters**:
  - `r: WatchSource<T> | MaybeRefOrGetter<T>`
- **Return Type**: `UntilArrayInstance<T>`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UntilToMatchOptions`

<details><summary>Interface Code</summary>

```ts
export interface UntilToMatchOptions {
  /**
   * Milliseconds timeout for promise to resolve/reject if the when condition does not meet.
   * 0 for never timed out
   *
   * @default 0
   */
  timeout?: number

  /**
   * Reject the promise when timeout
   *
   * @default false
   */
  throwOnTimeout?: boolean

  /**
   * `flush` option for internal watch
   *
   * @default 'sync'
   */
  flush?: WatchOptions['flush']

  /**
   * `deep` option for internal watch
   *
   * @default 'false'
   */
  deep?: WatchOptions['deep']
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `timeout` | `number` | ✓ |  |
| `throwOnTimeout` | `boolean` | ✓ |  |
| `flush` | `WatchOptions['flush']` | ✓ |  |
| `deep` | `WatchOptions['deep']` | ✓ |  |

### `UntilBaseInstance<T, Not extends boolean = false>`

<details><summary>Interface Code</summary>

```ts
export interface UntilBaseInstance<T, Not extends boolean = false> {
  toMatch: (<U extends T = T>(
    condition: (v: T) => v is U,
    options?: UntilToMatchOptions
  ) => Not extends true ? Promise<Exclude<T, U>> : Promise<U>) & ((
    condition: (v: T) => boolean,
    options?: UntilToMatchOptions
  ) => Promise<T>)
  changed: (options?: UntilToMatchOptions) => Promise<T>
  changedTimes: (n?: number, options?: UntilToMatchOptions) => Promise<T>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `toMatch` | `(<U extends T = T>(
    condition: (v: T) => v is U,
    options?: UntilToMatchOptions
  ) => Not extends true ? Promise<Exclude<T, U>> : Promise<U>) & ((
    condition: (v: T) => boolean,
    options?: UntilToMatchOptions
  ) => Promise<T>)` | ✗ |  |
| `changed` | `(options?: UntilToMatchOptions) => Promise<T>` | ✗ |  |
| `changedTimes` | `(n?: number, options?: UntilToMatchOptions) => Promise<T>` | ✗ |  |

### `UntilValueInstance<T, Not extends boolean = false>`

<details><summary>Interface Code</summary>

```ts
export interface UntilValueInstance<T, Not extends boolean = false> extends UntilBaseInstance<T, Not> {
  readonly not: UntilValueInstance<T, Not extends true ? false : true>

  toBe: <P = T>(value: MaybeRefOrGetter<P>, options?: UntilToMatchOptions) => Not extends true ? Promise<T> : Promise<P>
  toBeTruthy: (options?: UntilToMatchOptions) => Not extends true ? Promise<T & Falsy> : Promise<Exclude<T, Falsy>>
  toBeNull: (options?: UntilToMatchOptions) => Not extends true ? Promise<Exclude<T, null>> : Promise<null>
  toBeUndefined: (options?: UntilToMatchOptions) => Not extends true ? Promise<Exclude<T, undefined>> : Promise<undefined>
  toBeNaN: (options?: UntilToMatchOptions) => Promise<T>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `not` | `UntilValueInstance<T, Not extends true ? false : true>` | ✗ |  |
| `toBe` | `<P = T>(value: MaybeRefOrGetter<P>, options?: UntilToMatchOptions) => Not extends true ? Promise<T> : Promise<P>` | ✗ |  |
| `toBeTruthy` | `(options?: UntilToMatchOptions) => Not extends true ? Promise<T & Falsy> : Promise<Exclude<T, Falsy>>` | ✗ |  |
| `toBeNull` | `(options?: UntilToMatchOptions) => Not extends true ? Promise<Exclude<T, null>> : Promise<null>` | ✗ |  |
| `toBeUndefined` | `(options?: UntilToMatchOptions) => Not extends true ? Promise<Exclude<T, undefined>> : Promise<undefined>` | ✗ |  |
| `toBeNaN` | `(options?: UntilToMatchOptions) => Promise<T>` | ✗ |  |

### `UntilArrayInstance<T>`

<details><summary>Interface Code</summary>

```ts
export interface UntilArrayInstance<T> extends UntilBaseInstance<T> {
  readonly not: UntilArrayInstance<T>

  toContains: (value: MaybeRefOrGetter<ElementOf<ShallowUnwrapRef<T>>>, options?: UntilToMatchOptions) => Promise<T>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `not` | `UntilArrayInstance<T>` | ✗ |  |
| `toContains` | `(value: MaybeRefOrGetter<ElementOf<ShallowUnwrapRef<T>>>, options?: UntilToMatchOptions) => Promise<T>` | ✗ |  |


---

## Type Aliases

### `Falsy`

```ts
type Falsy = false | void | null | undefined | 0 | 0n | '';
```


---