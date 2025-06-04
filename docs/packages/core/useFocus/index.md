[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 5 |
| 📦 Imports | 8 |
| 📊 Variables & Constants | 1 |
| 🟢 Vue Composition API | 3 |
| 📐 Interfaces | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useFocus/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `WritableComputedRef` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `MaybeElementRef` | `../unrefElement` |
| `computed` | `vue` |
| `shallowRef` | `vue` |
| `watch` | `vue` |
| `unrefElement` | `../unrefElement` |
| `useEventListener` | `../useEventListener` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `listenerOptions` | `{ passive: boolean; }` | const | `{ passive: true }` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `watch` | watch | *none* | *none* |


---

## Functions

### `useFocus(target: MaybeElementRef, options: UseFocusOptions): UseFocusReturn`

<details><summary>Code</summary>

```ts
export function useFocus(target: MaybeElementRef, options: UseFocusOptions = {}): UseFocusReturn {
  const { initialValue = false, focusVisible = false, preventScroll = false } = options

  const innerFocused = shallowRef(false)
  const targetElement = computed(() => unrefElement(target))

  const listenerOptions = { passive: true }
  useEventListener(targetElement, 'focus', (event) => {
    if (!focusVisible || (event.target as HTMLElement).matches?.(':focus-visible'))
      innerFocused.value = true
  }, listenerOptions)
  useEventListener(targetElement, 'blur', () => innerFocused.value = false, listenerOptions)

  const focused = computed({
    get: () => innerFocused.value,
    set(value: boolean) {
      if (!value && innerFocused.value)
        targetElement.value?.blur()
      else if (value && !innerFocused.value)
        targetElement.value?.focus({ preventScroll })
    },
  })

  watch(
    targetElement,
    () => {
      focused.value = initialValue
    },
    { immediate: true, flush: 'post' },
  )

  return { focused }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Track or set the focus state of a DOM element.
 *
 * @see https://vueuse.org/useFocus
 * @param target The target element for the focus and blur events.
 * @param options
 */
```

- **Parameters**:
  - `target: MaybeElementRef`
  - `options: UseFocusOptions`
- **Return Type**: `UseFocusReturn`
- **Calls**:
  - `shallowRef (from vue)`
  - `computed (from vue)`
  - `unrefElement (from ../unrefElement)`
  - `useEventListener (from ../useEventListener)`
  - `(event.target as HTMLElement).matches`
  - `targetElement.value?.blur`
  - `targetElement.value?.focus`
  - `watch (from vue)`
### `get(): any`

<details><summary>Code</summary>

```ts
() => innerFocused.value
```
</details>

- **Return Type**: `any`
### `get(): any`

<details><summary>Code</summary>

```ts
() => innerFocused.value
```
</details>

- **Return Type**: `any`
### `get(): any`

<details><summary>Code</summary>

```ts
() => innerFocused.value
```
</details>

- **Return Type**: `any`
### `get(): any`

<details><summary>Code</summary>

```ts
() => innerFocused.value
```
</details>

- **Return Type**: `any`

---

## Interfaces

### `UseFocusOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseFocusOptions extends ConfigurableWindow {
  /**
   * Initial value. If set true, then focus will be set on the target
   *
   * @default false
   */
  initialValue?: boolean

  /**
   * Replicate the :focus-visible behavior of CSS
   *
   * @default false
   */
  focusVisible?: boolean

  /**
   * Prevent scrolling to the element when it is focused.
   *
   * @default false
   */
  preventScroll?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `initialValue` | `boolean` | ✓ |  |
| `focusVisible` | `boolean` | ✓ |  |
| `preventScroll` | `boolean` | ✓ |  |

### `UseFocusReturn`

<details><summary>Interface Code</summary>

```ts
export interface UseFocusReturn {
  /**
   * If read as true, then the element has focus. If read as false, then the element does not have focus
   * If set to true, then the element will be focused. If set to false, the element will be blurred.
   */
  focused: WritableComputedRef<boolean>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `focused` | `WritableComputedRef<boolean>` | ✗ |  |


---