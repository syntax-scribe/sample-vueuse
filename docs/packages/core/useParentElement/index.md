[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 8 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

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

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


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