[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 4
- **Classes**: 0
- **Imports**: 10
- **Interfaces**: 2
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useMagicKeys/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `noop` | `@vueuse/shared` |
| `computed` | `vue` |
| `reactive` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useEventListener` | `../useEventListener` |
| `DefaultMagicKeysAliasMap` | `./aliasMap` |


---

## Functions

### `useMagicKeys(options: UseMagicKeysOptions<false>): UseMagicKeysReturn<false>`

<details><summary>Code</summary>

```ts
export function useMagicKeys(options?: UseMagicKeysOptions<false>): UseMagicKeysReturn<false>
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive keys pressed state, with magical keys combination support.
 *
 * @see https://vueuse.org/useMagicKeys
 */
```

- **Parameters**:
  - `options: UseMagicKeysOptions<false>`
- **Return Type**: `UseMagicKeysReturn<false>`
### `setRefs(key: string, value: boolean): void`

<details><summary>Code</summary>

```ts
function setRefs(key: string, value: boolean) {
    if (key in refs) {
      if (useReactive)
        refs[key] = value
      else
        refs[key].value = value
    }
  }
```
</details>

- **Parameters**:
  - `key: string`
  - `value: boolean`
- **Return Type**: `void`
### `reset(): void`

<details><summary>Code</summary>

```ts
function reset() {
    current.clear()
    for (const key of usedKeys)
      setRefs(key, false)
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `current.clear`
  - `setRefs`
### `updateRefs(e: KeyboardEvent, value: boolean): void`

<details><summary>Code</summary>

```ts
function updateRefs(e: KeyboardEvent, value: boolean) {
    const key = e.key?.toLowerCase()
    const code = e.code?.toLowerCase()
    const values = [code, key].filter(Boolean)

    // current set
    if (key) {
      if (value)
        current.add(key)
      else
        current.delete(key)
    }

    for (const key of values) {
      usedKeys.add(key)
      setRefs(key, value)
    }
    if (key === 'shift' && !value) {
      shiftDeps.forEach((key) => {
        current.delete(key)
        setRefs(key, false)
      })
      shiftDeps.clear()
    }
    else if (typeof e.getModifierState === 'function' && e.getModifierState('Shift') && value) {
      [...current, ...values].forEach(key => shiftDeps.add(key))
    }
    // #1312
    // In macOS, keys won't trigger "keyup" event when Meta key is released
    // We track it's combination and release manually
    if (key === 'meta' && !value) {
      // Meta key released
      metaDeps.forEach((key) => {
        current.delete(key)
        setRefs(key, false)
      })
      metaDeps.clear()
    }
    else if (typeof e.getModifierState === 'function' && e.getModifierState('Meta') && value) {
      [...current, ...values].forEach(key => metaDeps.add(key))
    }
  }
```
</details>

- **Parameters**:
  - `e: KeyboardEvent`
  - `value: boolean`
- **Return Type**: `void`
- **Calls**:
  - `e.key?.toLowerCase`
  - `e.code?.toLowerCase`
  - `[code, key].filter`
  - `current.add`
  - `current.delete`
  - `usedKeys.add`
  - `setRefs`
  - `shiftDeps.forEach`
  - `shiftDeps.clear`
  - `e.getModifierState`
  - `[...current, ...values].forEach`
  - `shiftDeps.add`
  - `metaDeps.forEach`
  - `metaDeps.clear`
  - `metaDeps.add`
- **Internal Comments**:
```
// current set
// #1312
// In macOS, keys won't trigger "keyup" event when Meta key is released
// We track it's combination and release manually
// Meta key released (x4)
```


---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseMagicKeysOptions<Reactive extends boolean>`

<details><summary>Interface Code</summary>

```ts
export interface UseMagicKeysOptions<Reactive extends boolean> {
  /**
   * Returns a reactive object instead of an object of refs
   *
   * @default false
   */
  reactive?: Reactive

  /**
   * Target for listening events
   *
   * @default window
   */
  target?: MaybeRefOrGetter<EventTarget>

  /**
   * Alias map for keys, all the keys should be lowercase
   * { target: keycode }
   *
   * @example { ctrl: "control" }
   * @default <predefined-map>
   */
  aliasMap?: Record<string, string>

  /**
   * Register passive listener
   *
   * @default true
   */
  passive?: boolean

  /**
   * Custom event handler for keydown/keyup event.
   * Useful when you want to apply custom logic.
   *
   * When using `e.preventDefault()`, you will need to pass `passive: false` to useMagicKeys().
   */
  onEventFired?: (e: KeyboardEvent) => void | boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `reactive` | `Reactive` | ✓ |  |
| `target` | `MaybeRefOrGetter<EventTarget>` | ✓ |  |
| `aliasMap` | `Record<string, string>` | ✓ |  |
| `passive` | `boolean` | ✓ |  |
| `onEventFired` | `(e: KeyboardEvent) => void | boolean` | ✓ |  |

### `MagicKeysInternal`

<details><summary>Interface Code</summary>

```ts
export interface MagicKeysInternal {
  /**
   * A Set of currently pressed keys,
   * Stores raw keyCodes.
   *
   * @see https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/key
   */
  current: Set<string>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `current` | `Set<string>` | ✗ |  |


---

## Type Aliases

### `UseMagicKeysReturn<Reactive extends boolean extends boolean>`

```ts
type UseMagicKeysReturn<Reactive extends boolean extends boolean> = Readonly<
    Omit<Reactive extends true
      ? Record<string, boolean>
      : Record<string, ComputedRef<boolean>>, keyof MagicKeysInternal>
      & MagicKeysInternal
  >;
```


---