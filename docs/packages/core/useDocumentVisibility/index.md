[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 5 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useDocumentVisibility/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ShallowRef` | `vue` |
| `ConfigurableDocument` | `../_configurable` |
| `shallowRef` | `vue` |
| `defaultDocument` | `../_configurable` |
| `useEventListener` | `../useEventListener` |


---

## Functions

### `useDocumentVisibility(options: ConfigurableDocument): ShallowRef<DocumentVisibilityState>`

<details><summary>Code</summary>

```ts
export function useDocumentVisibility(options: ConfigurableDocument = {}): ShallowRef<DocumentVisibilityState> {
  const { document = defaultDocument } = options
  if (!document)
    return shallowRef('visible')

  const visibility = shallowRef(document.visibilityState)

  useEventListener(document, 'visibilitychange', () => {
    visibility.value = document.visibilityState
  }, { passive: true })

  return visibility
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactively track `document.visibilityState`.
 *
 * @see https://vueuse.org/useDocumentVisibility
 */
```

- **Parameters**:
  - `options: ConfigurableDocument`
- **Return Type**: `ShallowRef<DocumentVisibilityState>`
- **Calls**:
  - `shallowRef (from vue)`
  - `useEventListener (from ../useEventListener)`

---