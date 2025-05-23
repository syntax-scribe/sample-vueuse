[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 0
- **Type Aliases**: 2

## 🛠️ File Location:
📂 **`packages/shared/reactiveOmit/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `toRefs` | `vue` |
| `toValue` | `vue` |
| `reactiveComputed` | `../reactiveComputed` |


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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


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