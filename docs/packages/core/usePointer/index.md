[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 11 |
| 📊 Variables & Constants | 4 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 2 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/usePointer/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRef` | `vue` |
| `Ref` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `PointerType` | `../types` |
| `Position` | `../types` |
| `objectPick` | `@vueuse/shared` |
| `toRefs` | `@vueuse/shared` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useEventListener` | `../useEventListener` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `defaultState` | `UsePointerState` | const | `{
  x: 0,
  y: 0,
  pointerId: 0,
  pressure: 0,
  tiltX: 0,
  tiltY: 0,
  width: 0,
  height: 0,
  twist: 0,
  pointerType: null,
}` | ✗ |
| `keys` | `(keyof UsePointerState)[]` | const | `Object.keys(defaultState) as (keyof UsePointerState)[]` | ✗ |
| `state` | `Ref<UsePointerState>` | const | `deepRef(options.initialValue || {}) as unknown as Ref<UsePointerState>` | ✗ |
| `listenerOptions` | `{ passive: boolean; }` | const | `{ passive: true }` | ✗ |


---

## Functions

### `usePointer(options: UsePointerOptions): any`

<details><summary>Code</summary>

```ts
export function usePointer(options: UsePointerOptions = {}) {
  const {
    target = defaultWindow,
  } = options

  const isInside = shallowRef(false)
  const state = deepRef(options.initialValue || {}) as unknown as Ref<UsePointerState>
  Object.assign(state.value, defaultState, state.value)

  const handler = (event: PointerEvent) => {
    isInside.value = true
    if (options.pointerTypes && !options.pointerTypes.includes(event.pointerType as PointerType))
      return

    state.value = objectPick(event, keys, false) as UsePointerState
  }

  if (target) {
    const listenerOptions = { passive: true }
    useEventListener(target, ['pointerdown', 'pointermove', 'pointerup'], handler, listenerOptions)
    useEventListener(target, 'pointerleave', () => isInside.value = false, listenerOptions)
  }

  return {
    ...toRefs(state),
    isInside,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive pointer state.
 *
 * @see https://vueuse.org/usePointer
 * @param options
 */
```

- **Parameters**:
  - `options: UsePointerOptions`
- **Return Type**: `any`
- **Calls**:
  - `shallowRef (from vue)`
  - `deepRef (from vue)`
  - `Object.assign`
  - `options.pointerTypes.includes`
  - `objectPick (from @vueuse/shared)`
  - `useEventListener (from ../useEventListener)`
  - `toRefs (from @vueuse/shared)`
### `handler(event: PointerEvent): void`

<details><summary>Code</summary>

```ts
(event: PointerEvent) => {
    isInside.value = true
    if (options.pointerTypes && !options.pointerTypes.includes(event.pointerType as PointerType))
      return

    state.value = objectPick(event, keys, false) as UsePointerState
  }
```
</details>

- **Parameters**:
  - `event: PointerEvent`
- **Return Type**: `void`
- **Calls**:
  - `options.pointerTypes.includes`
  - `objectPick (from @vueuse/shared)`

---

## Interfaces

### `UsePointerState`

<details><summary>Interface Code</summary>

```ts
export interface UsePointerState extends Position {
  pressure: number
  pointerId: number
  tiltX: number
  tiltY: number
  width: number
  height: number
  twist: number
  pointerType: PointerType | null
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `pressure` | `number` | ✗ |  |
| `pointerId` | `number` | ✗ |  |
| `tiltX` | `number` | ✗ |  |
| `tiltY` | `number` | ✗ |  |
| `width` | `number` | ✗ |  |
| `height` | `number` | ✗ |  |
| `twist` | `number` | ✗ |  |
| `pointerType` | `PointerType | null` | ✗ |  |

### `UsePointerOptions`

<details><summary>Interface Code</summary>

```ts
export interface UsePointerOptions extends ConfigurableWindow {
  /**
   * Pointer types that listen to.
   *
   * @default ['mouse', 'touch', 'pen']
   */
  pointerTypes?: PointerType[]

  /**
   * Initial values
   */
  initialValue?: MaybeRef<Partial<UsePointerState>>

  /**
   * @default window
   */
  target?: MaybeRef<EventTarget | null | undefined> | Document | Window
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `pointerTypes` | `PointerType[]` | ✓ |  |
| `initialValue` | `MaybeRef<Partial<UsePointerState>>` | ✓ |  |
| `target` | `MaybeRef<EventTarget | null | undefined> | Document | Window` | ✓ |  |


---

## Type Aliases

### `UsePointerReturn`

```ts
type UsePointerReturn = ReturnType<typeof usePointer>;
```


---