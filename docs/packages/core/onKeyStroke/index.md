[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 6 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 3 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 3 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/onKeyStroke/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `toValue` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useEventListener` | `../useEventListener` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `key` | `KeyFilter` | let/var | `*not shown*` | ✗ |
| `handler` | `(event: KeyboardEvent) => void` | let/var | `*not shown*` | ✗ |
| `options` | `OnKeyStrokeOptions` | let/var | `{}` | ✗ |


---

## Functions

### `createKeyPredicate(keyFilter: KeyFilter): KeyPredicate`

<details><summary>Code</summary>

```ts
function createKeyPredicate(keyFilter: KeyFilter): KeyPredicate {
  if (typeof keyFilter === 'function')
    return keyFilter

  else if (typeof keyFilter === 'string')
    return (event: KeyboardEvent) => event.key === keyFilter

  else if (Array.isArray(keyFilter))
    return (event: KeyboardEvent) => keyFilter.includes(event.key)

  return () => true
}
```
</details>

- **Parameters**:
  - `keyFilter: KeyFilter`
- **Return Type**: `KeyPredicate`
- **Calls**:
  - `Array.isArray`
  - `keyFilter.includes`
### `onKeyStroke(key: KeyFilter, handler: (event: KeyboardEvent) => void, options: OnKeyStrokeOptions): () => void`

<details><summary>Code</summary>

```ts
export function onKeyStroke(key: KeyFilter, handler: (event: KeyboardEvent) => void, options?: OnKeyStrokeOptions): () => void
```
</details>

- **JSDoc**:
```ts
/**
 * Listen for keyboard keystrokes.
 *
 * @see https://vueuse.org/onKeyStroke
 */
```

- **Parameters**:
  - `key: KeyFilter`
  - `handler: (event: KeyboardEvent) => void`
  - `options: OnKeyStrokeOptions`
- **Return Type**: `() => void`
### `listener(e: KeyboardEvent): void`

<details><summary>Code</summary>

```ts
(e: KeyboardEvent) => {
    if (e.repeat && toValue(dedupe))
      return

    if (predicate(e))
      handler(e)
  }
```
</details>

- **Parameters**:
  - `e: KeyboardEvent`
- **Return Type**: `void`
- **Calls**:
  - `toValue (from vue)`
  - `predicate`
  - `handler`
### `onKeyDown(key: KeyFilter, handler: (event: KeyboardEvent) => void, options: Omit<OnKeyStrokeOptions, 'eventName'>): () => void`

<details><summary>Code</summary>

```ts
export function onKeyDown(key: KeyFilter, handler: (event: KeyboardEvent) => void, options: Omit<OnKeyStrokeOptions, 'eventName'> = {}) {
  return onKeyStroke(key, handler, { ...options, eventName: 'keydown' })
}
```
</details>

- **JSDoc**:
```ts
/**
 * Listen to the keydown event of the given key.
 *
 * @see https://vueuse.org/onKeyStroke
 * @param key
 * @param handler
 * @param options
 */
```

- **Parameters**:
  - `key: KeyFilter`
  - `handler: (event: KeyboardEvent) => void`
  - `options: Omit<OnKeyStrokeOptions, 'eventName'>`
- **Return Type**: `() => void`
- **Calls**:
  - `onKeyStroke`
### `onKeyPressed(key: KeyFilter, handler: (event: KeyboardEvent) => void, options: Omit<OnKeyStrokeOptions, 'eventName'>): () => void`

<details><summary>Code</summary>

```ts
export function onKeyPressed(key: KeyFilter, handler: (event: KeyboardEvent) => void, options: Omit<OnKeyStrokeOptions, 'eventName'> = {}) {
  return onKeyStroke(key, handler, { ...options, eventName: 'keypress' })
}
```
</details>

- **JSDoc**:
```ts
/**
 * Listen to the keypress event of the given key.
 *
 * @see https://vueuse.org/onKeyStroke
 * @param key
 * @param handler
 * @param options
 */
```

- **Parameters**:
  - `key: KeyFilter`
  - `handler: (event: KeyboardEvent) => void`
  - `options: Omit<OnKeyStrokeOptions, 'eventName'>`
- **Return Type**: `() => void`
- **Calls**:
  - `onKeyStroke`
### `onKeyUp(key: KeyFilter, handler: (event: KeyboardEvent) => void, options: Omit<OnKeyStrokeOptions, 'eventName'>): () => void`

<details><summary>Code</summary>

```ts
export function onKeyUp(key: KeyFilter, handler: (event: KeyboardEvent) => void, options: Omit<OnKeyStrokeOptions, 'eventName'> = {}) {
  return onKeyStroke(key, handler, { ...options, eventName: 'keyup' })
}
```
</details>

- **JSDoc**:
```ts
/**
 * Listen to the keyup event of the given key.
 *
 * @see https://vueuse.org/onKeyStroke
 * @param key
 * @param handler
 * @param options
 */
```

- **Parameters**:
  - `key: KeyFilter`
  - `handler: (event: KeyboardEvent) => void`
  - `options: Omit<OnKeyStrokeOptions, 'eventName'>`
- **Return Type**: `() => void`
- **Calls**:
  - `onKeyStroke`

---

## Interfaces

### `OnKeyStrokeOptions`

<details><summary>Interface Code</summary>

```ts
export interface OnKeyStrokeOptions {
  eventName?: KeyStrokeEventName
  target?: MaybeRefOrGetter<EventTarget | null | undefined>
  passive?: boolean
  /**
   * Set to `true` to ignore repeated events when the key is being held down.
   *
   * @default false
   */
  dedupe?: MaybeRefOrGetter<boolean>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `eventName` | `KeyStrokeEventName` | ✓ |  |
| `target` | `MaybeRefOrGetter<EventTarget | null | undefined>` | ✓ |  |
| `passive` | `boolean` | ✓ |  |
| `dedupe` | `MaybeRefOrGetter<boolean>` | ✓ |  |


---

## Type Aliases

### `KeyPredicate`

```ts
type KeyPredicate = (event: KeyboardEvent) => boolean;
```

### `KeyFilter`

```ts
type KeyFilter = true | string | string[] | KeyPredicate;
```

### `KeyStrokeEventName`

```ts
type KeyStrokeEventName = 'keydown' | 'keypress' | 'keyup';
```


---