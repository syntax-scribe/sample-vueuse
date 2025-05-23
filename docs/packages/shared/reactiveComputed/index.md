[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 4
- **Interfaces**: 0
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/shared/reactiveComputed/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedGetter` | `vue` |
| `UnwrapNestedRefs` | `vue` |
| `computed` | `vue` |
| `toReactive` | `../toReactive` |


---

## Functions

### `reactiveComputed(fn: ComputedGetter<T>): ReactiveComputedReturn<T>`

<details><summary>Code</summary>

```ts
export function reactiveComputed<T extends object>(fn: ComputedGetter<T>): ReactiveComputedReturn<T> {
  return toReactive<T>(computed<T>(fn))
}
```
</details>

- **JSDoc**:
```ts
/**
 * Computed reactive object.
 */
```

- **Parameters**:
  - `fn: ComputedGetter<T>`
- **Return Type**: `ReactiveComputedReturn<T>`
- **Calls**:
  - `toReactive (from ../toReactive)`
  - `computed (from vue)`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `ReactiveComputedReturn<T extends object extends object>`

```ts
type ReactiveComputedReturn<T extends object extends object> = UnwrapNestedRefs<T>;
```


---