[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useVModels/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ToRefs` | `vue` |
| `UseVModelOptions` | `../useVModel` |
| `useVModel` | `../useVModel` |


---

## Functions

### `useVModels(props: P, emit: (name: Name, ...args: any[]) => void, options: UseVModelOptions<any, true>): ToRefs<P>`

<details><summary>Code</summary>

```ts
export function useVModels<P extends object, Name extends string>(
  props: P,
  emit?: (name: Name, ...args: any[]) => void,
  options?: UseVModelOptions<any, true>,
): ToRefs<P>
```
</details>

- **JSDoc**:
```ts
/**
 * Shorthand for props v-model binding. Think like `toRefs(props)` but changes will also emit out.
 *
 * @see https://vueuse.org/useVModels
 * @param props
 * @param emit
 * @param options
 */
```

- **Parameters**:
  - `props: P`
  - `emit: (name: Name, ...args: any[]) => void`
  - `options: UseVModelOptions<any, true>`
- **Return Type**: `ToRefs<P>`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---