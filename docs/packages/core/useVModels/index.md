[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useVModels/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ToRefs` | `vue` |
| `UseVModelOptions` | `../useVModel` |
| `useVModel` | `../useVModel` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `ret` | `any` | const | `{}` | ✗ |


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