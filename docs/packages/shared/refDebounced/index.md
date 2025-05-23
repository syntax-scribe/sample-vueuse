[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 8
- **Interfaces**: 0
- **Type Aliases**: 1

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `RefDebouncedReturn<T = any = any>`

```ts
type RefDebouncedReturn<T = any = any> = Readonly<Ref<T>>;
```


---