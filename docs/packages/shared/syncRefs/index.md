[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 5 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/shared/syncRefs/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `WatchSource` | `vue` |
| `ConfigurableFlushSync` | `../utils` |
| `watch` | `vue` |
| `toArray` | `../utils` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


---

## Functions

### `syncRefs(source: WatchSource<T>, targets: Ref<T> | Ref<T>[], options: SyncRefsOptions): any`

<details><summary>Code</summary>

```ts
export function syncRefs<T>(
  source: WatchSource<T>,
  targets: Ref<T> | Ref<T>[],
  options: SyncRefsOptions = {},
) {
  const {
    flush = 'sync',
    deep = false,
    immediate = true,
  } = options

  const targetsArray = toArray(targets)

  return watch(
    source,
    newValue => targetsArray.forEach(target => target.value = newValue),
    { flush, deep, immediate },
  )
}
```
</details>

- **JSDoc**:
```ts
/**
 * Keep target ref(s) in sync with the source ref
 *
 * @param source source ref
 * @param targets
 */
```

- **Parameters**:
  - `source: WatchSource<T>`
  - `targets: Ref<T> | Ref<T>[]`
  - `options: SyncRefsOptions`
- **Return Type**: `any`
- **Calls**:
  - `toArray (from ../utils)`
  - `watch (from vue)`
  - `targetsArray.forEach`

---

## Interfaces

### `SyncRefsOptions`

<details><summary>Interface Code</summary>

```ts
export interface SyncRefsOptions extends ConfigurableFlushSync {
  /**
   * Watch deeply
   *
   * @default false
   */
  deep?: boolean
  /**
   * Sync values immediately
   *
   * @default true
   */
  immediate?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `deep` | `boolean` | ✓ |  |
| `immediate` | `boolean` | ✓ |  |


---