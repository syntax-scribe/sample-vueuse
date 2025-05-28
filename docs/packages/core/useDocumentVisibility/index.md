[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 5 |
| 📊 Variables & Constants | 0 |
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