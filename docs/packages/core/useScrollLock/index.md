[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 5 |
| 📦 Imports | 11 |
| 📊 Variables & Constants | 7 |
| 🟢 Vue Composition API | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useScrollLock/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Fn` | `@vueuse/shared` |
| `MaybeRefOrGetter` | `vue` |
| `isIOS` | `@vueuse/shared` |
| `toRef` | `@vueuse/shared` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `computed` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `resolveElement` | `../_resolve-element` |
| `useEventListener` | `../useEventListener` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `parent` | `Element` | const | `ele.parentNode as Element` | ✗ |
| `e` | `Event` | const | `rawEvent || window.event` | ✗ |
| `_target` | `Element` | const | `e.target as Element` | ✗ |
| `elInitialOverflow` | `WeakMap<HTMLElement, string>` | const | `new WeakMap<HTMLElement, CSSStyleDeclaration['overflow']>()` | ✗ |
| `stopTouchMoveListener` | `Fn | null` | let/var | `null` | ✗ |
| `initialOverflow` | `CSSStyleDeclaration['overflow']` | let/var | `''` | ✗ |
| `ele` | `HTMLElement` | const | `target as HTMLElement` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |
| `computed` | computed | *none* | *none* |


---

## Functions

### `checkOverflowScroll(ele: Element): boolean`

<details><summary>Code</summary>

```ts
function checkOverflowScroll(ele: Element): boolean {
  const style = window.getComputedStyle(ele)
  if (
    style.overflowX === 'scroll'
    || style.overflowY === 'scroll'
    || (style.overflowX === 'auto' && ele.clientWidth < ele.scrollWidth)
    || (style.overflowY === 'auto' && ele.clientHeight < ele.scrollHeight)
  ) {
    return true
  }
  else {
    const parent = ele.parentNode as Element

    if (!parent || parent.tagName === 'BODY')
      return false

    return checkOverflowScroll(parent)
  }
}
```
</details>

- **Parameters**:
  - `ele: Element`
- **Return Type**: `boolean`
- **Calls**:
  - `window.getComputedStyle`
  - `checkOverflowScroll`
### `preventDefault(rawEvent: TouchEvent): boolean`

<details><summary>Code</summary>

```ts
function preventDefault(rawEvent: TouchEvent): boolean {
  const e = rawEvent || window.event

  const _target = e.target as Element

  // Do not prevent if element or parentNodes have overflow: scroll set.
  if (checkOverflowScroll(_target))
    return false

  // Do not prevent if the event has more than one touch (usually meaning this is a multi touch gesture like pinch to zoom).
  if (e.touches.length > 1)
    return true

  if (e.preventDefault)
    e.preventDefault()

  return false
}
```
</details>

- **Parameters**:
  - `rawEvent: TouchEvent`
- **Return Type**: `boolean`
- **Calls**:
  - `checkOverflowScroll`
  - `e.preventDefault`
- **Internal Comments**:
```
// Do not prevent if element or parentNodes have overflow: scroll set.
// Do not prevent if the event has more than one touch (usually meaning this is a multi touch gesture like pinch to zoom).
```

### `useScrollLock(element: MaybeRefOrGetter<HTMLElement | SVGElement | Window | Document | null | undefined>, initialState: boolean): any`

<details><summary>Code</summary>

```ts
export function useScrollLock(
  element: MaybeRefOrGetter<HTMLElement | SVGElement | Window | Document | null | undefined>,
  initialState = false,
) {
  const isLocked = shallowRef(initialState)
  let stopTouchMoveListener: Fn | null = null
  let initialOverflow: CSSStyleDeclaration['overflow'] = ''

  watch(toRef(element), (el) => {
    const target = resolveElement(toValue(el))
    if (target) {
      const ele = target as HTMLElement
      if (!elInitialOverflow.get(ele))
        elInitialOverflow.set(ele, ele.style.overflow)

      if (ele.style.overflow !== 'hidden')
        initialOverflow = ele.style.overflow

      if (ele.style.overflow === 'hidden')
        return isLocked.value = true

      if (isLocked.value)
        return ele.style.overflow = 'hidden'
    }
  }, {
    immediate: true,
  })

  const lock = () => {
    const el = resolveElement(toValue(element))
    if (!el || isLocked.value)
      return
    if (isIOS) {
      stopTouchMoveListener = useEventListener(
        el,
        'touchmove',
        (e) => { preventDefault(e as TouchEvent) },
        { passive: false },
      )
    }
    el.style.overflow = 'hidden'
    isLocked.value = true
  }

  const unlock = () => {
    const el = resolveElement(toValue(element))
    if (!el || !isLocked.value)
      return
    if (isIOS)
      stopTouchMoveListener?.()
    el.style.overflow = initialOverflow
    elInitialOverflow.delete(el as HTMLElement)
    isLocked.value = false
  }

  tryOnScopeDispose(unlock)

  return computed<boolean>({
    get() {
      return isLocked.value
    },
    set(v) {
      if (v)
        lock()
      else unlock()
    },
  })
}
```
</details>

- **JSDoc**:
```ts
/**
 * Lock scrolling of the element.
 *
 * @see https://vueuse.org/useScrollLock
 * @param element
 */
```

- **Parameters**:
  - `element: MaybeRefOrGetter<HTMLElement | SVGElement | Window | Document | null | undefined>`
  - `initialState: boolean`
- **Return Type**: `any`
- **Calls**:
  - `shallowRef (from vue)`
  - `watch (from vue)`
  - `toRef (from @vueuse/shared)`
  - `resolveElement (from ../_resolve-element)`
  - `toValue (from vue)`
  - `elInitialOverflow.get`
  - `elInitialOverflow.set`
  - `useEventListener (from ../useEventListener)`
  - `preventDefault`
  - `stopTouchMoveListener`
  - `elInitialOverflow.delete`
  - `tryOnScopeDispose (from @vueuse/shared)`
  - `computed (from vue)`
  - `lock`
  - `unlock`
### `lock(): void`

<details><summary>Code</summary>

```ts
() => {
    const el = resolveElement(toValue(element))
    if (!el || isLocked.value)
      return
    if (isIOS) {
      stopTouchMoveListener = useEventListener(
        el,
        'touchmove',
        (e) => { preventDefault(e as TouchEvent) },
        { passive: false },
      )
    }
    el.style.overflow = 'hidden'
    isLocked.value = true
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `resolveElement (from ../_resolve-element)`
  - `toValue (from vue)`
  - `useEventListener (from ../useEventListener)`
  - `preventDefault`
### `unlock(): void`

<details><summary>Code</summary>

```ts
() => {
    const el = resolveElement(toValue(element))
    if (!el || !isLocked.value)
      return
    if (isIOS)
      stopTouchMoveListener?.()
    el.style.overflow = initialOverflow
    elInitialOverflow.delete(el as HTMLElement)
    isLocked.value = false
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `resolveElement (from ../_resolve-element)`
  - `toValue (from vue)`
  - `stopTouchMoveListener`
  - `elInitialOverflow.delete`

---