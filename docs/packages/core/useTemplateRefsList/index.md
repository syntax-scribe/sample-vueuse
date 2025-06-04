[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useTemplateRefsList/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `deepRef` | `vue` |
| `onBeforeUpdate` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `refs` | `Ref<TemplateRefsList<T>>` | const | `deepRef<unknown>([]) as Ref<TemplateRefsList<T>>` | ✗ |


---

## Functions

### `useTemplateRefsList(): Readonly<Ref<Readonly<TemplateRefsList<T>>>>`

<details><summary>Code</summary>

```ts
export function useTemplateRefsList<T = Element>(): Readonly<Ref<Readonly<TemplateRefsList<T>>>> {
  const refs = deepRef<unknown>([]) as Ref<TemplateRefsList<T>>
  refs.value.set = (el: object | null) => {
    if (el)
      refs.value.push(el as T)
  }
  onBeforeUpdate(() => {
    refs.value.length = 0
  })
  return refs
}
```
</details>

- **Return Type**: `Readonly<Ref<Readonly<TemplateRefsList<T>>>>`
- **Calls**:
  - `deepRef (from vue)`
  - `refs.value.push`
  - `onBeforeUpdate (from vue)`

---

## Type Aliases

### `TemplateRefsList<T>`

```ts
type TemplateRefsList<T> = T[] & {
  set: (el: object | null) => void
};
```


---