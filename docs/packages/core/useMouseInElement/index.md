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
- **Imports**: 8
- **Interfaces**: 1
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useMouseInElement/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeElementRef` | `../unrefElement` |
| `UseMouseOptions` | `../useMouse` |
| `shallowRef` | `vue` |
| `watch` | `vue` |
| `defaultWindow` | `../_configurable` |
| `unrefElement` | `../unrefElement` |
| `useEventListener` | `../useEventListener` |
| `useMouse` | `../useMouse` |


---

## Functions

### `useMouseInElement(target: MaybeElementRef, options: MouseInElementOptions): { x: any; y: any; sourceType: any; elementX: any; elementY: any; elementPositionX: any; elementPositionY: any; elementHeight: any; elementWidth: any; isOutside: any; stop: () => void; }`

<details><summary>Code</summary>

```ts
export function useMouseInElement(
  target?: MaybeElementRef,
  options: MouseInElementOptions = {},
) {
  const {
    handleOutside = true,
    window = defaultWindow,
  } = options
  const type = options.type || 'page'

  const { x, y, sourceType } = useMouse(options)

  const targetRef = shallowRef(target ?? window?.document.body)
  const elementX = shallowRef(0)
  const elementY = shallowRef(0)
  const elementPositionX = shallowRef(0)
  const elementPositionY = shallowRef(0)
  const elementHeight = shallowRef(0)
  const elementWidth = shallowRef(0)
  const isOutside = shallowRef(true)

  let stop = () => {}

  if (window) {
    stop = watch(
      [targetRef, x, y],
      () => {
        const el = unrefElement(targetRef)
        if (!el || !(el instanceof Element))
          return

        const {
          left,
          top,
          width,
          height,
        } = el.getBoundingClientRect()

        elementPositionX.value = left + (type === 'page' ? window.pageXOffset : 0)
        elementPositionY.value = top + (type === 'page' ? window.pageYOffset : 0)
        elementHeight.value = height
        elementWidth.value = width

        const elX = x.value - elementPositionX.value
        const elY = y.value - elementPositionY.value
        isOutside.value = width === 0 || height === 0
          || elX < 0 || elY < 0
          || elX > width || elY > height

        if (handleOutside || !isOutside.value) {
          elementX.value = elX
          elementY.value = elY
        }
      },
      { immediate: true },
    )

    useEventListener(
      document,
      'mouseleave',
      () => isOutside.value = true,
      { passive: true },
    )
  }

  return {
    x,
    y,
    sourceType,
    elementX,
    elementY,
    elementPositionX,
    elementPositionY,
    elementHeight,
    elementWidth,
    isOutside,
    stop,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive mouse position related to an element.
 *
 * @see https://vueuse.org/useMouseInElement
 * @param target
 * @param options
 */
```

- **Parameters**:
  - `target: MaybeElementRef`
  - `options: MouseInElementOptions`
- **Return Type**: `{ x: any; y: any; sourceType: any; elementX: any; elementY: any; elementPositionX: any; elementPositionY: any; elementHeight: any; elementWidth: any; isOutside: any; stop: () => void; }`
- **Calls**:
  - `useMouse (from ../useMouse)`
  - `shallowRef (from vue)`
  - `watch (from vue)`
  - `unrefElement (from ../unrefElement)`
  - `el.getBoundingClientRect`
  - `useEventListener (from ../useEventListener)`
### `stop(): void`

<details><summary>Code</summary>

```ts
() => {}
```
</details>

- **Return Type**: `void`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `MouseInElementOptions`

<details><summary>Interface Code</summary>

```ts
export interface MouseInElementOptions extends UseMouseOptions {
  handleOutside?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `handleOutside` | `boolean` | ✓ |  |


---

## Type Aliases

### `UseMouseInElementReturn`

```ts
type UseMouseInElementReturn = ReturnType<typeof useMouseInElement>;
```


---