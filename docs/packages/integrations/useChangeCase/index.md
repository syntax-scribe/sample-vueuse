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
- **Type Aliases**: 4

## 🛠️ File Location:
📂 **`packages/integrations/useChangeCase/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Options` | `change-case` |
| `ComputedRef` | `vue` |
| `MaybeRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `WritableComputedRef` | `vue` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `toValue` | `vue` |


---

## Functions

### `useChangeCase(input: MaybeRef<string>, type: MaybeRefOrGetter<ChangeCaseType>, options: MaybeRefOrGetter<Options> | undefined): WritableComputedRef<string>`

<details><summary>Code</summary>

```ts
export function useChangeCase(input: MaybeRef<string>, type: MaybeRefOrGetter<ChangeCaseType>, options?: MaybeRefOrGetter<Options> | undefined): WritableComputedRef<string>
```
</details>

- **Parameters**:
  - `input: MaybeRef<string>`
  - `type: MaybeRefOrGetter<ChangeCaseType>`
  - `options: MaybeRefOrGetter<Options> | undefined`
- **Return Type**: `WritableComputedRef<string>`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `EndsWithCase<T>`

```ts
type EndsWithCase<T> = T extends `${infer _}Case` ? T : never;
```

### `FilterKeys<T>`

```ts
type FilterKeys<T> = { [K in keyof T as K extends string ? K : never]: EndsWithCase<K> };
```

### `ChangeCaseKeys`

```ts
type ChangeCaseKeys = FilterKeys<typeof changeCase>;
```

### `ChangeCaseType`

```ts
type ChangeCaseType = ChangeCaseKeys[keyof ChangeCaseKeys];
```


---