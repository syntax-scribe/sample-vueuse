[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 📦 Imports | 11 |
| 📊 Variables & Constants | 2 |
| 🟢 Vue Composition API | 3 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useTextareaAutosize/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Fn` | `@vueuse/shared` |
| `MaybeRef` | `vue` |
| `WatchSource` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `toRef` | `@vueuse/shared` |
| `nextTick` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useResizeObserver` | `../useResizeObserver` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `styleProp` | `"height" | "minHeight"` | const | `options?.styleProp ?? 'height'` | ✗ |
| `height` | `string` | let/var | `''` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |
| `watch` | watch | *none* | *none* |
| `watch` | watch | *none* | *none* |


---

## Functions

### `tryRequestAnimationFrame(window: Window | undefined, fn: Fn): void`

<details><summary>Code</summary>

```ts
function tryRequestAnimationFrame(
  window: Window | undefined = defaultWindow,
  fn: Fn,
) {
  if (window && typeof window.requestAnimationFrame === 'function') {
    window.requestAnimationFrame(fn)
  }
  else {
    fn()
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Call window.requestAnimationFrame(), if not available, just call the function
 *
 * @param window
 * @param fn
 */
```

- **Parameters**:
  - `window: Window | undefined`
  - `fn: Fn`
- **Return Type**: `void`
- **Calls**:
  - `window.requestAnimationFrame`
  - `fn`
### `useTextareaAutosize(options: UseTextareaAutosizeOptions): { textarea: any; input: any; triggerResize: () => void; }`

<details><summary>Code</summary>

```ts
export function useTextareaAutosize(options: UseTextareaAutosizeOptions = {}) {
  const { window = defaultWindow } = options
  const textarea = toRef(options?.element)
  const input = toRef(options?.input ?? '')
  const styleProp = options?.styleProp ?? 'height'
  const textareaScrollHeight = shallowRef(1)
  const textareaOldWidth = shallowRef(0)

  function triggerResize() {
    if (!textarea.value)
      return

    let height = ''

    textarea.value.style[styleProp] = '1px'
    textareaScrollHeight.value = textarea.value?.scrollHeight
    const _styleTarget = toValue(options?.styleTarget)
    // If style target is provided update its height
    if (_styleTarget)
      _styleTarget.style[styleProp] = `${textareaScrollHeight.value}px`
    // else update textarea's height by updating height variable
    else
      height = `${textareaScrollHeight.value}px`

    textarea.value.style[styleProp] = height
  }

  watch([input, textarea], () => nextTick(triggerResize), { immediate: true })

  watch(textareaScrollHeight, () => options?.onResize?.())

  useResizeObserver(textarea, ([{ contentRect }]) => {
    if (textareaOldWidth.value === contentRect.width)
      return

    tryRequestAnimationFrame(window, () => {
      textareaOldWidth.value = contentRect.width
      triggerResize()
    })
  })

  if (options?.watch)
    watch(options.watch, triggerResize, { immediate: true, deep: true })

  return {
    textarea,
    input,
    triggerResize,
  }
}
```
</details>

- **Parameters**:
  - `options: UseTextareaAutosizeOptions`
- **Return Type**: `{ textarea: any; input: any; triggerResize: () => void; }`
- **Calls**:
  - `toRef (from @vueuse/shared)`
  - `shallowRef (from vue)`
  - `toValue (from vue)`
  - `watch (from vue)`
  - `nextTick (from vue)`
  - `options?.onResize`
  - `useResizeObserver (from ../useResizeObserver)`
  - `tryRequestAnimationFrame`
  - `triggerResize`
- **Internal Comments**:
```
// If style target is provided update its height
```

### `triggerResize(): void`

<details><summary>Code</summary>

```ts
function triggerResize() {
    if (!textarea.value)
      return

    let height = ''

    textarea.value.style[styleProp] = '1px'
    textareaScrollHeight.value = textarea.value?.scrollHeight
    const _styleTarget = toValue(options?.styleTarget)
    // If style target is provided update its height
    if (_styleTarget)
      _styleTarget.style[styleProp] = `${textareaScrollHeight.value}px`
    // else update textarea's height by updating height variable
    else
      height = `${textareaScrollHeight.value}px`

    textarea.value.style[styleProp] = height
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `toValue (from vue)`
- **Internal Comments**:
```
// If style target is provided update its height
```


---

## Interfaces

### `UseTextareaAutosizeOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseTextareaAutosizeOptions extends ConfigurableWindow {
  /** Textarea element to autosize. */
  element?: MaybeRef<HTMLTextAreaElement | undefined | null>
  /** Textarea content. */
  input?: MaybeRef<string>
  /** Watch sources that should trigger a textarea resize. */
  watch?: WatchSource | Array<WatchSource>
  /** Function called when the textarea size changes. */
  onResize?: () => void
  /** Specify style target to apply the height based on textarea content. If not provided it will use textarea it self.  */
  styleTarget?: MaybeRef<HTMLElement | undefined>
  /** Specify the style property that will be used to manipulate height. Can be `height | minHeight`. Default value is `height`. */
  styleProp?: 'height' | 'minHeight'
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `element` | `MaybeRef<HTMLTextAreaElement | undefined | null>` | ✓ |  |
| `input` | `MaybeRef<string>` | ✓ |  |
| `watch` | `WatchSource | Array<WatchSource>` | ✓ |  |
| `onResize` | `() => void` | ✓ |  |
| `styleTarget` | `MaybeRef<HTMLElement | undefined>` | ✓ |  |
| `styleProp` | `'height' | 'minHeight'` | ✓ |  |


---

## Type Aliases

### `UseTextareaAutosizeReturn`

```ts
type UseTextareaAutosizeReturn = ReturnType<typeof useTextareaAutosize>;
```


---