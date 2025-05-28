[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 9 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useCurrentElement/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `IsAny` | `@vueuse/shared` |
| `MaybeElement` | `../unrefElement` |
| `MaybeElementRef` | `../unrefElement` |
| `VueInstance` | `../unrefElement` |
| `computedWithControl` | `@vueuse/shared` |
| `getCurrentInstance` | `vue` |
| `onMounted` | `vue` |
| `onUpdated` | `vue` |
| `unrefElement` | `../unrefElement` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `vm` | `any` | const | `getCurrentInstance()!` | ✗ |


---

## Functions

### `useCurrentElement(rootComponent: MaybeElementRef<R>): any`

<details><summary>Code</summary>

```ts
export function useCurrentElement<
  T extends MaybeElement = MaybeElement,
  R extends VueInstance = VueInstance,
  E extends MaybeElement = MaybeElement extends T ? IsAny<R['$el']> extends false ? R['$el'] : T : T,
>(
  rootComponent?: MaybeElementRef<R>,
) {
  const vm = getCurrentInstance()!
  const currentElement = computedWithControl(
    () => null,
    () => (rootComponent ? unrefElement(rootComponent) : vm.proxy!.$el) as E,
  )

  onUpdated(currentElement.trigger)
  onMounted(currentElement.trigger)

  return currentElement
}
```
</details>

- **Parameters**:
  - `rootComponent: MaybeElementRef<R>`
- **Return Type**: `any`
- **Calls**:
  - `getCurrentInstance (from vue)`
  - `computedWithControl (from @vueuse/shared)`
  - `unrefElement (from ../unrefElement)`
  - `onUpdated (from vue)`
  - `onMounted (from vue)`

---