[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 2 |
| 📑 Type Aliases | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/reactiveOmit/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `toRefs` | `vue` |
| `toValue` | `vue` |
| `reactiveComputed` | `../reactiveComputed` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `flatKeys` | `K[]` | const | `keys.flat() as K[]` | ✗ |
| `predicate` | `ReactiveOmitPredicate<T>` | const | `flatKeys[0] as unknown as ReactiveOmitPredicate<T>` | ✗ |


---

## Functions

### `reactiveOmit(obj: T, keys: (K | K[])[]): ReactiveOmitReturn<T, K>`

<details><summary>Code</summary>

```ts
export function reactiveOmit<T extends object, K extends keyof T>(
  obj: T,
  ...keys: (K | K[])[]
): ReactiveOmitReturn<T, K>
```
</details>

- **Parameters**:
  - `obj: T`
  - `keys: (K | K[])[]`
- **Return Type**: `ReactiveOmitReturn<T, K>`

---

## Type Aliases

### `ReactiveOmitReturn<T extends object extends object, K extends keyof T | undefined = undefined extends keyof T | undefined = undefined>`

```ts
type ReactiveOmitReturn<T extends object extends object, K extends keyof T | undefined = undefined extends keyof T | undefined = undefined> = [K] extends [undefined]
    ? Partial<T>
    : Omit<T, Extract<K, keyof T>>;
```

### `ReactiveOmitPredicate<T>`

```ts
type ReactiveOmitPredicate<T> = (value: T[keyof T], key: keyof T) => boolean;
```


---