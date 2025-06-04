[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 5 |
| 📊 Variables & Constants | 2 |
| 📑 Type Aliases | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `flatKeys` | `K[]` | const | `keys.flat() as K[]` | ✗ |
| `predicate` | `ReactivePickPredicate<T>` | const | `flatKeys[0] as unknown as ReactivePickPredicate<T>` | ✗ |


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