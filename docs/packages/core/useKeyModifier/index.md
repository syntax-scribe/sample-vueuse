[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 1
- **Type Aliases**: 2

## 🛠️ File Location:
📂 **`packages/core/useKeyModifier/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ShallowRef` | `vue` |
| `ConfigurableDocument` | `../_configurable` |
| `WindowEventName` | `../useEventListener` |
| `shallowRef` | `vue` |
| `defaultDocument` | `../_configurable` |
| `useEventListener` | `../useEventListener` |


---

## Functions

### `useKeyModifier(modifier: KeyModifier, options: UseModifierOptions<Initial>): UseKeyModifierReturn<Initial>`

<details><summary>Code</summary>

```ts
export function useKeyModifier<Initial extends boolean | null>(modifier: KeyModifier, options: UseModifierOptions<Initial> = {}): UseKeyModifierReturn<Initial> {
  const {
    events = defaultEvents,
    document = defaultDocument,
    initial = null,
  } = options

  const state = shallowRef(initial) as ShallowRef<boolean>

  if (document) {
    events.forEach((listenerEvent) => {
      useEventListener(document, listenerEvent, (evt: KeyboardEvent | MouseEvent) => {
        if (typeof evt.getModifierState === 'function')
          state.value = evt.getModifierState(modifier)
      }, { passive: true })
    })
  }

  return state
}
```
</details>

- **Parameters**:
  - `modifier: KeyModifier`
  - `options: UseModifierOptions<Initial>`
- **Return Type**: `UseKeyModifierReturn<Initial>`
- **Calls**:
  - `shallowRef (from vue)`
  - `events.forEach`
  - `useEventListener (from ../useEventListener)`
  - `evt.getModifierState`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseModifierOptions<Initial>`

<details><summary>Interface Code</summary>

```ts
export interface UseModifierOptions<Initial> extends ConfigurableDocument {
  /**
   * Event names that will prompt update to modifier states
   *
   * @default ['mousedown', 'mouseup', 'keydown', 'keyup']
   */
  events?: WindowEventName[]

  /**
   * Initial value of the returned ref
   *
   * @default null
   */
  initial?: Initial
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `events` | `WindowEventName[]` | ✓ |  |
| `initial` | `Initial` | ✓ |  |


---

## Type Aliases

### `KeyModifier`

```ts
type KeyModifier = 'Alt' | 'AltGraph' | 'CapsLock' | 'Control' | 'Fn' | 'FnLock' | 'Meta' | 'NumLock' | 'ScrollLock' | 'Shift' | 'Symbol' | 'SymbolLock';
```

### `UseKeyModifierReturn<Initial>`

```ts
type UseKeyModifierReturn<Initial> = ShallowRef<Initial extends boolean ? boolean : boolean | null>;
```


---