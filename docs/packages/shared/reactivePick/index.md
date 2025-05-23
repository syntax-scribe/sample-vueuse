[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 5
- **Interfaces**: 0
- **Type Aliases**: 2

## 🛠️ File Location:
📂 **`packages/shared/reactivePick/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `UnwrapRef` | `vue` |
| `toRefs` | `vue` |
| `toValue` | `vue` |
| `reactiveComputed` | `../reactiveComputed` |
| `toRef` | `../toRef` |


---

## Functions

### `reactivePick(obj: T, keys: (K | K[])[]): ReactivePickReturn<T, K>`

<details><summary>Code</summary>

```ts
export function reactivePick<T extends object, K extends keyof T>(
  obj: T,
  ...keys: (K | K[])[]
): ReactivePickReturn<T, K>
```
</details>

- **Parameters**:
  - `obj: T`
  - `keys: (K | K[])[]`
- **Return Type**: `ReactivePickReturn<T, K>`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `ReactivePickReturn<T extends object extends object, K extends keyof T extends keyof T>`

```ts
type ReactivePickReturn<T extends object extends object, K extends keyof T extends keyof T> = { [S in K]: UnwrapRef<T[S]> };
```

### `ReactivePickPredicate<T>`

```ts
type ReactivePickPredicate<T> = (value: T[keyof T], key: keyof T) => boolean;
```


---