[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 📦 Imports | 8 |
| 📊 Variables & Constants | 2 |
| 🟢 Vue Composition API | 2 |
| 📐 Interfaces | 2 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useCloned/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `Ref` | `vue` |
| `WatchOptions` | `vue` |
| `deepRef` | `vue` |
| `isRef` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `cloned` | `Ref<T>` | const | `deepRef({} as T) as Ref<T>` | ✗ |
| `_lastSync` | `boolean` | let/var | `false` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |
| `watch` | watch | *none* | *none* |


---

## Functions

### `cloneFnJSON(source: T): T`

<details><summary>Code</summary>

```ts
export function cloneFnJSON<T>(source: T): T {
  return JSON.parse(JSON.stringify(source))
}
```
</details>

- **Parameters**:
  - `source: T`
- **Return Type**: `T`
- **Calls**:
  - `JSON.parse`
  - `JSON.stringify`
### `useCloned(source: MaybeRefOrGetter<T>, options: UseClonedOptions): UseClonedReturn<T>`

<details><summary>Code</summary>

```ts
export function useCloned<T>(
  source: MaybeRefOrGetter<T>,
  options: UseClonedOptions = {},
): UseClonedReturn<T> {
  const cloned = deepRef({} as T) as Ref<T>
  const isModified = shallowRef<boolean>(false)
  let _lastSync = false

  const {
    manual,
    clone = cloneFnJSON,
    // watch options
    deep = true,
    immediate = true,
  } = options

  watch(cloned, () => {
    if (_lastSync) {
      _lastSync = false
      return
    }
    isModified.value = true
  }, {
    deep: true,
    flush: 'sync',
  })

  function sync() {
    _lastSync = true
    isModified.value = false

    cloned.value = clone(toValue(source))
  }

  if (!manual && (isRef(source) || typeof source === 'function')) {
    watch(source, sync, {
      ...options,
      deep,
      immediate,
    })
  }
  else {
    sync()
  }

  return { cloned, isModified, sync }
}
```
</details>

- **Parameters**:
  - `source: MaybeRefOrGetter<T>`
  - `options: UseClonedOptions`
- **Return Type**: `UseClonedReturn<T>`
- **Calls**:
  - `deepRef (from vue)`
  - `shallowRef (from vue)`
  - `watch (from vue)`
  - `clone`
  - `toValue (from vue)`
  - `isRef (from vue)`
  - `sync`
- **Internal Comments**:
```
// watch options (x2)
```

### `sync(): void`

<details><summary>Code</summary>

```ts
function sync() {
    _lastSync = true
    isModified.value = false

    cloned.value = clone(toValue(source))
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `clone`
  - `toValue (from vue)`

---

## Interfaces

### `UseClonedOptions<T = any>`

<details><summary>Interface Code</summary>

```ts
export interface UseClonedOptions<T = any> extends WatchOptions {
  /**
   * Custom clone function.
   *
   * By default, it use `JSON.parse(JSON.stringify(value))` to clone.
   */
  clone?: (source: T) => T

  /**
   * Manually sync the ref
   *
   * @default false
   */
  manual?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `clone` | `(source: T) => T` | ✓ |  |
| `manual` | `boolean` | ✓ |  |

### `UseClonedReturn<T>`

<details><summary>Interface Code</summary>

```ts
export interface UseClonedReturn<T> {
  /**
   * Cloned ref
   */
  cloned: Ref<T>
  /**
   * Ref indicates whether the cloned data is modified
   */
  isModified: Ref<boolean>
  /**
   * Sync cloned data with source manually
   */
  sync: () => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `cloned` | `Ref<T>` | ✗ |  |
| `isModified` | `Ref<boolean>` | ✗ |  |
| `sync` | `() => void` | ✗ |  |


---

## Type Aliases

### `CloneFn<F, T = F = F>`

```ts
type CloneFn<F, T = F = F> = (x: F) => T;
```


---