[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 📦 Imports | 5 |
| 📊 Variables & Constants | 1 |
| 🟢 Vue Composition API | 3 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useTextSelection/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableWindow` | `../_configurable` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useEventListener` | `../useEventListener` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `rangeCount` | `number` | const | `selection.rangeCount ?? 0` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |


---

## Functions

### `getRangesFromSelection(selection: Selection): Range[]`

<details><summary>Code</summary>

```ts
function getRangesFromSelection(selection: Selection) {
  const rangeCount = selection.rangeCount ?? 0
  return Array.from({ length: rangeCount }, (_, i) => selection.getRangeAt(i))
}
```
</details>

- **Parameters**:
  - `selection: Selection`
- **Return Type**: `Range[]`
- **Calls**:
  - `Array.from`
  - `selection.getRangeAt`
### `useTextSelection(options: ConfigurableWindow): { text: any; rects: any; ranges: any; selection: any; }`

<details><summary>Code</summary>

```ts
export function useTextSelection(options: ConfigurableWindow = {}) {
  const {
    window = defaultWindow,
  } = options

  const selection = deepRef<Selection | null>(null)
  const text = computed(() => selection.value?.toString() ?? '')
  const ranges = computed<Range[]>(() => selection.value ? getRangesFromSelection(selection.value) : [])
  const rects = computed(() => ranges.value.map(range => range.getBoundingClientRect()))

  function onSelectionChange() {
    selection.value = null // trigger computed update
    if (window)
      selection.value = window.getSelection()
  }

  if (window)
    useEventListener(window.document, 'selectionchange', onSelectionChange, { passive: true })

  return {
    text,
    rects,
    ranges,
    selection,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactively track user text selection based on [`Window.getSelection`](https://developer.mozilla.org/en-US/docs/Web/API/Window/getSelection).
 *
 * @see https://vueuse.org/useTextSelection
 */
```

- **Parameters**:
  - `options: ConfigurableWindow`
- **Return Type**: `{ text: any; rects: any; ranges: any; selection: any; }`
- **Calls**:
  - `deepRef (from vue)`
  - `computed (from vue)`
  - `selection.value?.toString`
  - `getRangesFromSelection`
  - `ranges.value.map`
  - `range.getBoundingClientRect`
  - `window.getSelection`
  - `useEventListener (from ../useEventListener)`
### `onSelectionChange(): void`

<details><summary>Code</summary>

```ts
function onSelectionChange() {
    selection.value = null // trigger computed update
    if (window)
      selection.value = window.getSelection()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `window.getSelection`

---

## Type Aliases

### `UseTextSelectionReturn`

```ts
type UseTextSelectionReturn = ReturnType<typeof useTextSelection>;
```


---