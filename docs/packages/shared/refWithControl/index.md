[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 7 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 5 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/shared/refWithControl/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Fn` | `../utils` |
| `customRef` | `vue` |
| `extendRef` | `../extendRef` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `source` | `T` | let/var | `initial` | ✗ |
| `track` | `Fn` | let/var | `*not shown*` | ✗ |
| `trigger` | `Fn` | let/var | `*not shown*` | ✗ |
| `old` | `T` | const | `source` | ✗ |
| `controlledRef` | `<T>(initial: T, options?: ControlledRefOptions<T>) => any` | const | `refWithControl` | ✓ |


---

## Functions

### `refWithControl(initial: T, options: ControlledRefOptions<T>): any`

<details><summary>Code</summary>

```ts
export function refWithControl<T>(
  initial: T,
  options: ControlledRefOptions<T> = {},
) {
  let source = initial
  let track: Fn
  let trigger: Fn

  const ref = customRef<T>((_track, _trigger) => {
    track = _track
    trigger = _trigger

    return {
      get() {
        return get()
      },
      set(v) {
        set(v)
      },
    }
  })

  function get(tracking = true) {
    if (tracking)
      track()
    return source
  }

  function set(value: T, triggering = true) {
    if (value === source)
      return

    const old = source
    if (options.onBeforeChange?.(value, old) === false)
      return // dismissed

    source = value

    options.onChanged?.(value, old)

    if (triggering)
      trigger()
  }

  /**
   * Get the value without tracked in the reactivity system
   */
  const untrackedGet = () => get(false)
  /**
   * Set the value without triggering the reactivity system
   */
  const silentSet = (v: T) => set(v, false)

  /**
   * Get the value without tracked in the reactivity system.
   *
   * Alias for `untrackedGet()`
   */
  const peek = () => get(false)

  /**
   * Set the value without triggering the reactivity system
   *
   * Alias for `silentSet(v)`
   */
  const lay = (v: T) => set(v, false)

  return extendRef(
    ref,
    {
      get,
      set,
      untrackedGet,
      silentSet,
      peek,
      lay,
    },
    { enumerable: true },
  )
}
```
</details>

- **JSDoc**:
```ts
/**
 * Fine-grained controls over ref and its reactivity.
 */
```

- **Parameters**:
  - `initial: T`
  - `options: ControlledRefOptions<T>`
- **Return Type**: `any`
- **Calls**:
  - `customRef (from vue)`
  - `get`
  - `set`
  - `track`
  - `options.onBeforeChange`
  - `options.onChanged`
  - `trigger`
  - `extendRef (from ../extendRef)`
- **Internal Comments**:
```
/**
   * Get the value without tracked in the reactivity system
   */ (x2)
/**
   * Set the value without triggering the reactivity system
   */ (x2)
/**
   * Get the value without tracked in the reactivity system.
   *
   * Alias for `untrackedGet()`
   */ (x2)
/**
   * Set the value without triggering the reactivity system
   *
   * Alias for `silentSet(v)`
   */ (x2)
```

### `get(tracking: boolean): T`

<details><summary>Code</summary>

```ts
function get(tracking = true) {
    if (tracking)
      track()
    return source
  }
```
</details>

- **Parameters**:
  - `tracking: boolean`
- **Return Type**: `T`
- **Calls**:
  - `track`
### `set(value: T, triggering: boolean): void`

<details><summary>Code</summary>

```ts
function set(value: T, triggering = true) {
    if (value === source)
      return

    const old = source
    if (options.onBeforeChange?.(value, old) === false)
      return // dismissed

    source = value

    options.onChanged?.(value, old)

    if (triggering)
      trigger()
  }
```
</details>

- **Parameters**:
  - `value: T`
  - `triggering: boolean`
- **Return Type**: `void`
- **Calls**:
  - `options.onBeforeChange`
  - `options.onChanged`
  - `trigger`
### `untrackedGet(): T`

<details><summary>Code</summary>

```ts
() => get(false)
```
</details>

- **Return Type**: `T`
- **Calls**:
  - `get`
### `silentSet(v: T): void`

<details><summary>Code</summary>

```ts
(v: T) => set(v, false)
```
</details>

- **Parameters**:
  - `v: T`
- **Return Type**: `void`
- **Calls**:
  - `set`
### `peek(): T`

<details><summary>Code</summary>

```ts
() => get(false)
```
</details>

- **Return Type**: `T`
- **Calls**:
  - `get`
### `lay(v: T): void`

<details><summary>Code</summary>

```ts
(v: T) => set(v, false)
```
</details>

- **Parameters**:
  - `v: T`
- **Return Type**: `void`
- **Calls**:
  - `set`

---

## Interfaces

### `ControlledRefOptions<T>`

<details><summary>Interface Code</summary>

```ts
export interface ControlledRefOptions<T> {
  /**
   * Callback function before the ref changing.
   *
   * Returning `false` to dismiss the change.
   */
  onBeforeChange?: (value: T, oldValue: T) => void | boolean

  /**
   * Callback function after the ref changed
   *
   * This happens synchronously, with less overhead compare to `watch`
   */
  onChanged?: (value: T, oldValue: T) => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `onBeforeChange` | `(value: T, oldValue: T) => void | boolean` | ✓ |  |
| `onChanged` | `(value: T, oldValue: T) => void` | ✓ |  |


---