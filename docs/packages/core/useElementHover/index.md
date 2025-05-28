[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 10 |
| 📊 Variables & Constants | 2 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useElementHover/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `ShallowRef` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `MaybeComputedElementRef` | `../unrefElement` |
| `computed` | `vue` |
| `shallowRef` | `vue` |
| `defaultWindow` | `../_configurable` |
| `onElementRemoval` | `../onElementRemoval` |
| `unrefElement` | `../unrefElement` |
| `useEventListener` | `../useEventListener` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `timer` | `ReturnType<typeof setTimeout> | undefined` | let/var | `*not shown*` | ✗ |
| `delay` | `number` | const | `entering ? delayEnter : delayLeave` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `useElementHover(el: MaybeRefOrGetter<EventTarget | null | undefined>, options: UseElementHoverOptions): ShallowRef<boolean>`

<details><summary>Code</summary>

```ts
export function useElementHover(el: MaybeRefOrGetter<EventTarget | null | undefined>, options: UseElementHoverOptions = {}): ShallowRef<boolean> {
  const {
    delayEnter = 0,
    delayLeave = 0,
    triggerOnRemoval = false,
    window = defaultWindow,
  } = options

  const isHovered = shallowRef(false)
  let timer: ReturnType<typeof setTimeout> | undefined

  const toggle = (entering: boolean) => {
    const delay = entering ? delayEnter : delayLeave
    if (timer) {
      clearTimeout(timer)
      timer = undefined
    }

    if (delay)
      timer = setTimeout(() => isHovered.value = entering, delay)
    else
      isHovered.value = entering
  }

  if (!window)
    return isHovered

  useEventListener(el, 'mouseenter', () => toggle(true), { passive: true })
  useEventListener(el, 'mouseleave', () => toggle(false), { passive: true })

  if (triggerOnRemoval) {
    onElementRemoval(
      computed(() => unrefElement(el as MaybeComputedElementRef)),
      () => toggle(false),
    )
  }

  return isHovered
}
```
</details>

- **Parameters**:
  - `el: MaybeRefOrGetter<EventTarget | null | undefined>`
  - `options: UseElementHoverOptions`
- **Return Type**: `ShallowRef<boolean>`
- **Calls**:
  - `shallowRef (from vue)`
  - `clearTimeout`
  - `setTimeout`
  - `useEventListener (from ../useEventListener)`
  - `toggle`
  - `onElementRemoval (from ../onElementRemoval)`
  - `computed (from vue)`
  - `unrefElement (from ../unrefElement)`
### `toggle(entering: boolean): void`

<details><summary>Code</summary>

```ts
(entering: boolean) => {
    const delay = entering ? delayEnter : delayLeave
    if (timer) {
      clearTimeout(timer)
      timer = undefined
    }

    if (delay)
      timer = setTimeout(() => isHovered.value = entering, delay)
    else
      isHovered.value = entering
  }
```
</details>

- **Parameters**:
  - `entering: boolean`
- **Return Type**: `void`
- **Calls**:
  - `clearTimeout`
  - `setTimeout`

---

## Interfaces

### `UseElementHoverOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseElementHoverOptions extends ConfigurableWindow {
  delayEnter?: number
  delayLeave?: number
  triggerOnRemoval?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `delayEnter` | `number` | ✓ |  |
| `delayLeave` | `number` | ✓ |  |
| `triggerOnRemoval` | `boolean` | ✓ |  |


---