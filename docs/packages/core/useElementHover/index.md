[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 10
- **Interfaces**: 1
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


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

## Type Aliases

> No type aliases found in this file.


---