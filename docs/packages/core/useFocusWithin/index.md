[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 9 |
| 📊 Variables & Constants | 4 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 2 |
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
📂 **`packages/core/useFocusWithin/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `MaybeElementRef` | `../unrefElement` |
| `computed` | `vue` |
| `shallowRef` | `vue` |
| `defaultWindow` | `../_configurable` |
| `unrefElement` | `../unrefElement` |
| `useActiveElement` | `../useActiveElement` |
| `useEventListener` | `../useEventListener` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `EVENT_FOCUS_IN` | `"focusin"` | const | `'focusin'` | ✗ |
| `EVENT_FOCUS_OUT` | `"focusout"` | const | `'focusout'` | ✗ |
| `PSEUDO_CLASS_FOCUS_WITHIN` | `":focus-within"` | const | `':focus-within'` | ✗ |
| `listenerOptions` | `{ passive: boolean; }` | const | `{ passive: true }` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |


---

## Functions

### `useFocusWithin(target: MaybeElementRef, options: ConfigurableWindow): UseFocusWithinReturn`

<details><summary>Code</summary>

```ts
export function useFocusWithin(target: MaybeElementRef, options: ConfigurableWindow = {}): UseFocusWithinReturn {
  const { window = defaultWindow } = options
  const targetElement = computed(() => unrefElement(target))
  const _focused = shallowRef(false)
  const focused = computed(() => _focused.value)
  const activeElement = useActiveElement(options)

  if (!window || !activeElement.value) {
    return { focused }
  }

  const listenerOptions = { passive: true }
  useEventListener(targetElement, EVENT_FOCUS_IN, () => _focused.value = true, listenerOptions)
  useEventListener(targetElement, EVENT_FOCUS_OUT, () =>
    _focused.value = targetElement.value?.matches?.(PSEUDO_CLASS_FOCUS_WITHIN) ?? false, listenerOptions)

  return { focused }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Track if focus is contained within the target element
 *
 * @see https://vueuse.org/useFocusWithin
 * @param target The target element to track
 * @param options Focus within options
 */
```

- **Parameters**:
  - `target: MaybeElementRef`
  - `options: ConfigurableWindow`
- **Return Type**: `UseFocusWithinReturn`
- **Calls**:
  - `computed (from vue)`
  - `unrefElement (from ../unrefElement)`
  - `shallowRef (from vue)`
  - `useActiveElement (from ../useActiveElement)`
  - `useEventListener (from ../useEventListener)`
  - `targetElement.value?.matches`

---

## Interfaces

### `UseFocusWithinReturn`

<details><summary>Interface Code</summary>

```ts
export interface UseFocusWithinReturn {
  /**
   * True if the element or any of its descendants are focused
   */
  focused: ComputedRef<boolean>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `focused` | `ComputedRef<boolean>` | ✗ |  |


---