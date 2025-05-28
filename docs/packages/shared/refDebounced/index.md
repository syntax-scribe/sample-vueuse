[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 8 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/refDebounced/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `Ref` | `vue` |
| `DebounceFilterOptions` | `../utils` |
| `deepRef` | `vue` |
| `shallowReadonly` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `useDebounceFn` | `../useDebounceFn` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `debounced` | `Ref<T>` | const | `deepRef(toValue(value)) as Ref<T>` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


---

## Functions

### `refDebounced(value: Ref<T>, ms: MaybeRefOrGetter<number>, options: DebounceFilterOptions): RefDebouncedReturn<T>`

<details><summary>Code</summary>

```ts
export function refDebounced<T>(value: Ref<T>, ms: MaybeRefOrGetter<number> = 200, options: DebounceFilterOptions = {}): RefDebouncedReturn<T> {
  const debounced = deepRef(toValue(value)) as Ref<T>

  const updater = useDebounceFn(() => {
    debounced.value = value.value
  }, ms, options)

  watch(value, () => updater())

  return shallowReadonly(debounced)
}
```
</details>

- **JSDoc**:
```ts
/**
 * Debounce updates of a ref.
 *
 * @return A new debounced ref.
 */
```

- **Parameters**:
  - `value: Ref<T>`
  - `ms: MaybeRefOrGetter<number>`
  - `options: DebounceFilterOptions`
- **Return Type**: `RefDebouncedReturn<T>`
- **Calls**:
  - `deepRef (from vue)`
  - `toValue (from vue)`
  - `useDebounceFn (from ../useDebounceFn)`
  - `watch (from vue)`
  - `updater`
  - `shallowReadonly (from vue)`

---

## Type Aliases

### `RefDebouncedReturn<T = any = any>`

```ts
type RefDebouncedReturn<T = any = any> = Readonly<Ref<T>>;
```


---