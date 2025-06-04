[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 📦 Imports | 3 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/onStartTyping/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableDocument` | `../_configurable` |
| `defaultDocument` | `../_configurable` |
| `useEventListener` | `../useEventListener` |


---

## Functions

### `isFocusedElementEditable(): boolean`

<details><summary>Code</summary>

```ts
function isFocusedElementEditable() {
  const { activeElement, body } = document

  if (!activeElement)
    return false

  // If not element has focus, we assume it is not editable, too.
  if (activeElement === body)
    return false

  // Assume <input> and <textarea> elements are editable.
  switch (activeElement.tagName) {
    case 'INPUT':
    case 'TEXTAREA':
      return true
  }

  // Check if any other focused element id editable.
  return activeElement.hasAttribute('contenteditable')
}
```
</details>

- **Return Type**: `boolean`
- **Calls**:
  - `activeElement.hasAttribute`
- **Internal Comments**:
```
// If not element has focus, we assume it is not editable, too.
// Assume <input> and <textarea> elements are editable.
// Check if any other focused element id editable.
```

### `isTypedCharValid({
  keyCode,
  metaKey,
  ctrlKey,
  altKey,
}: KeyboardEvent): boolean`

<details><summary>Code</summary>

```ts
function isTypedCharValid({
  keyCode,
  metaKey,
  ctrlKey,
  altKey,
}: KeyboardEvent) {
  if (metaKey || ctrlKey || altKey)
    return false

  // 0...9
  if ((keyCode >= 48 && keyCode <= 57) || (keyCode >= 96 && keyCode <= 105))
    return true

  // A...Z
  if (keyCode >= 65 && keyCode <= 90)
    return true

  // All other keys.
  return false
}
```
</details>

- **Parameters**:
  - `{
  keyCode,
  metaKey,
  ctrlKey,
  altKey,
}: KeyboardEvent`
- **Return Type**: `boolean`
- **Internal Comments**:
```
// 0...9
// A...Z
// All other keys.
```

### `onStartTyping(callback: (event: KeyboardEvent) => void, options: ConfigurableDocument): void`

<details><summary>Code</summary>

```ts
export function onStartTyping(callback: (event: KeyboardEvent) => void, options: ConfigurableDocument = {}) {
  const { document = defaultDocument } = options

  const keydown = (event: KeyboardEvent) => {
    if (!isFocusedElementEditable() && isTypedCharValid(event)) {
      callback(event)
    }
  }

  if (document)
    useEventListener(document, 'keydown', keydown, { passive: true })
}
```
</details>

- **JSDoc**:
```ts
/**
 * Fires when users start typing on non-editable elements.
 *
 * @see https://vueuse.org/onStartTyping
 * @param callback
 * @param options
 */
```

- **Parameters**:
  - `callback: (event: KeyboardEvent) => void`
  - `options: ConfigurableDocument`
- **Return Type**: `void`
- **Calls**:
  - `isFocusedElementEditable`
  - `isTypedCharValid`
  - `callback`
  - `useEventListener (from ../useEventListener)`
### `keydown(event: KeyboardEvent): void`

<details><summary>Code</summary>

```ts
(event: KeyboardEvent) => {
    if (!isFocusedElementEditable() && isTypedCharValid(event)) {
      callback(event)
    }
  }
```
</details>

- **Parameters**:
  - `event: KeyboardEvent`
- **Return Type**: `void`
- **Calls**:
  - `isFocusedElementEditable`
  - `isTypedCharValid`
  - `callback`

---