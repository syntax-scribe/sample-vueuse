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
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useTemplateRefsList/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `deepRef` | `vue` |
| `onBeforeUpdate` | `vue` |


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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `TemplateRefsList<T>`

```ts
type TemplateRefsList<T> = T[] & {
  set: (el: object | null) => void
};
```


---