[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 🧱 Classes | 0 |
| 📦 Imports | 10 |
| 📊 Variables & Constants | 6 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 1 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 3 |
| 📐 Interfaces | 2 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Re-exports](#re-exports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `obj` | `{ toJSON(): {}; current: any; }` | const | `{
    toJSON() { return {} },
    current,
  }` | ✗ |
| `refs` | `Record<string, any>` | const | `useReactive ? reactive(obj) : obj` | ✗ |
| `metaDeps` | `Set<string>` | const | `new Set<string>()` | ✗ |
| `shiftDeps` | `Set<string>` | const | `new Set<string>()` | ✗ |
| `usedKeys` | `Set<string>` | const | `new Set<string>()` | ✗ |
| `proxy` | `Record<string, any>` | const | `new Proxy(
    refs,
    {
      get(target, prop, rec) {
        if (typeof prop !== 'string')
          return Reflect.get(target, prop, rec)

        prop = prop.toLowerCase()
        // alias
        if (prop in aliasMap)
          prop = aliasMap[prop]
        // create new tracking
        if (!(prop in refs)) {
          if (/[+_-]/.test(prop)) {
            const keys = prop.split(/[+_-]/g).map(i => i.trim())
            refs[prop] = computed(() => keys.map(key => toValue(proxy[key])).every(Boolean))
          }
          else {
            refs[prop] = shallowRef(false)
          }
        }
        const r = Reflect.get(target, prop, rec)
        return useReactive ? toValue(r) : r
      },
    },
  )` | ✗ |


---

## Re-exports

| Type | Source | Exported Names |
|------|--------|----------------|
| named | `./aliasMap` | DefaultMagicKeysAliasMap |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `reactive` | reactive | *none* | *none* |
| `reactive` | reactive | *none* | *none* |
| `computed` | computed | *none* | *none* |


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