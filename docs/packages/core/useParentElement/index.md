[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 8
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useParentElement/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `ShallowRef` | `vue` |
| `tryOnMounted` | `@vueuse/shared` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `unrefElement` | `../unrefElement` |
| `useCurrentElement` | `../useCurrentElement` |


---

## Functions

### `useParentElement(element: MaybeRefOrGetter<HTMLElement | SVGElement | null | undefined>): Readonly<ShallowRef<HTMLElement | SVGElement | null | undefined>>`

<details><summary>Code</summary>

```ts
export function useParentElement(
  element: MaybeRefOrGetter<HTMLElement | SVGElement | null | undefined> = useCurrentElement<HTMLElement | SVGAElement>(),
): Readonly<ShallowRef<HTMLElement | SVGElement | null | undefined>> {
  const parentElement = shallowRef<HTMLElement | SVGElement | null | undefined>()

  const update = () => {
    const el = unrefElement(element)
    if (el)
      parentElement.value = el.parentElement
  }

  tryOnMounted(update)
  watch(() => toValue(element), update)

  return parentElement
}
```
</details>

- **Parameters**:
  - `element: MaybeRefOrGetter<HTMLElement | SVGElement | null | undefined>`
- **Return Type**: `Readonly<ShallowRef<HTMLElement | SVGElement | null | undefined>>`
- **Calls**:
  - `shallowRef (from vue)`
  - `unrefElement (from ../unrefElement)`
  - `tryOnMounted (from @vueuse/shared)`
  - `watch (from vue)`
  - `toValue (from vue)`
### `update(): void`

<details><summary>Code</summary>

```ts
() => {
    const el = unrefElement(element)
    if (el)
      parentElement.value = el.parentElement
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `unrefElement (from ../unrefElement)`

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