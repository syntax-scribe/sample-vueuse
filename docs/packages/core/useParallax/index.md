[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 9
- **Interfaces**: 2
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useParallax/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `MaybeElementRef` | `../unrefElement` |
| `computed` | `vue` |
| `reactive` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useDeviceOrientation` | `../useDeviceOrientation` |
| `useMouseInElement` | `../useMouseInElement` |
| `useScreenOrientation` | `../useScreenOrientation` |


---

## Functions

### `useParallax(target: MaybeElementRef, options: UseParallaxOptions): UseParallaxReturn`

<details><summary>Code</summary>

```ts
export function useParallax(
  target: MaybeElementRef,
  options: UseParallaxOptions = {},
): UseParallaxReturn {
  const {
    deviceOrientationTiltAdjust = i => i,
    deviceOrientationRollAdjust = i => i,
    mouseTiltAdjust = i => i,
    mouseRollAdjust = i => i,
    window = defaultWindow,
  } = options

  const orientation = reactive(useDeviceOrientation({ window }))
  const screenOrientation = reactive(useScreenOrientation({ window }))
  const {
    elementX: x,
    elementY: y,
    elementWidth: width,
    elementHeight: height,
  } = useMouseInElement(target, { handleOutside: false, window })

  const source = computed(() => {
    if (orientation.isSupported
      && ((orientation.alpha != null && orientation.alpha !== 0) || (orientation.gamma != null && orientation.gamma !== 0))
    ) {
      return 'deviceOrientation'
    }
    return 'mouse'
  })

  const roll = computed(() => {
    if (source.value === 'deviceOrientation') {
      let value: number
      switch (screenOrientation.orientation) {
        case 'landscape-primary':
          value = orientation.gamma! / 90
          break
        case 'landscape-secondary':
          value = -orientation.gamma! / 90
          break
        case 'portrait-primary':
          value = -orientation.beta! / 90
          break
        case 'portrait-secondary':
          value = orientation.beta! / 90
          break
        default:
          value = -orientation.beta! / 90
      }
      return deviceOrientationRollAdjust(value)
    }
    else {
      const value = -(y.value - height.value / 2) / height.value
      return mouseRollAdjust(value)
    }
  })

  const tilt = computed(() => {
    if (source.value === 'deviceOrientation') {
      let value: number
      switch (screenOrientation.orientation) {
        case 'landscape-primary':
          value = orientation.beta! / 90
          break
        case 'landscape-secondary':
          value = -orientation.beta! / 90
          break
        case 'portrait-primary':
          value = orientation.gamma! / 90
          break
        case 'portrait-secondary':
          value = -orientation.gamma! / 90
          break
        default:
          value = orientation.gamma! / 90
      }
      return deviceOrientationTiltAdjust(value)
    }
    else {
      const value = (x.value - width.value / 2) / width.value
      return mouseTiltAdjust(value)
    }
  })

  return { roll, tilt, source }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Create parallax effect easily. It uses `useDeviceOrientation` and fallback to `useMouse`
 * if orientation is not supported.
 *
 * @param target
 * @param options
 */
```

- **Parameters**:
  - `target: MaybeElementRef`
  - `options: UseParallaxOptions`
- **Return Type**: `UseParallaxReturn`
- **Calls**:
  - `reactive (from vue)`
  - `useDeviceOrientation (from ../useDeviceOrientation)`
  - `useScreenOrientation (from ../useScreenOrientation)`
  - `useMouseInElement (from ../useMouseInElement)`
  - `computed (from vue)`
  - `deviceOrientationRollAdjust`
  - `mouseRollAdjust`
  - `deviceOrientationTiltAdjust`
  - `mouseTiltAdjust`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseParallaxOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseParallaxOptions extends ConfigurableWindow {
  deviceOrientationTiltAdjust?: (i: number) => number
  deviceOrientationRollAdjust?: (i: number) => number
  mouseTiltAdjust?: (i: number) => number
  mouseRollAdjust?: (i: number) => number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `deviceOrientationTiltAdjust` | `(i: number) => number` | ✓ |  |
| `deviceOrientationRollAdjust` | `(i: number) => number` | ✓ |  |
| `mouseTiltAdjust` | `(i: number) => number` | ✓ |  |
| `mouseRollAdjust` | `(i: number) => number` | ✓ |  |

### `UseParallaxReturn`

<details><summary>Interface Code</summary>

```ts
export interface UseParallaxReturn {
  /**
   * Roll value. Scaled to `-0.5 ~ 0.5`
   */
  roll: ComputedRef<number>
  /**
   * Tilt value. Scaled to `-0.5 ~ 0.5`
   */
  tilt: ComputedRef<number>
  /**
   * Sensor source, can be `mouse` or `deviceOrientation`
   */
  source: ComputedRef<'deviceOrientation' | 'mouse'>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `roll` | `ComputedRef<number>` | ✗ |  |
| `tilt` | `ComputedRef<number>` | ✗ |  |
| `source` | `ComputedRef<'deviceOrientation' | 'mouse'>` | ✗ |  |


---

## Type Aliases

> No type aliases found in this file.


---