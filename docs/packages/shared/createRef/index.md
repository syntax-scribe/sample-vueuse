[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 4 |
| 📑 Type Aliases | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/createRef/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `ShallowRef` | `vue` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |


---

## Functions

### `createRef(value: T, deep: D): CreateRefReturn<T, D>`

<details><summary>Code</summary>

```ts
export function createRef<T = any, D extends boolean = false>(value: T, deep?: D): CreateRefReturn<T, D> {
  if (deep === true) {
    return deepRef(value) as CreateRefReturn<T, D>
  }
  else {
    return shallowRef(value) as CreateRefReturn<T, D>
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Returns a `deepRef` or `shallowRef` depending on the `deep` param.
 *
 * @example createRef(1) // ShallowRef<number>
 * @example createRef(1, false) // ShallowRef<number>
 * @example createRef(1, true) // Ref<number>
 * @example createRef("string") // ShallowRef<string>
 * @example createRef<"A"|"B">("A", true) // Ref<"A"|"B">
 *
 * @param value
 * @param deep
 * @returns the `deepRef` or `shallowRef`
 */
```

- **Parameters**:
  - `value: T`
  - `deep: D`
- **Return Type**: `CreateRefReturn<T, D>`
- **Calls**:
  - `deepRef (from vue)`
  - `shallowRef (from vue)`

---

## Type Aliases

### `CreateRefReturn<T = any = any, D extends boolean = false extends boolean = false>`

```ts
type CreateRefReturn<T = any = any, D extends boolean = false extends boolean = false> = ShallowOrDeepRef<T, D>;
```

### `ShallowOrDeepRef<T = any = any, D extends boolean = false extends boolean = false>`

```ts
type ShallowOrDeepRef<T = any = any, D extends boolean = false extends boolean = false> = D extends true ? Ref<T> : ShallowRef<T>;
```


---