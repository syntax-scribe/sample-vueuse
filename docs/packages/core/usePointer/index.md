[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 11
- **Interfaces**: 2
- **Type Aliases**: 1

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

## Classes

> No classes found in this file.


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