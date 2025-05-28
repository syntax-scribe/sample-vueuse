[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useDeviceOrientation/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `shallowRef` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useEventListener` | `../useEventListener` |
| `useSupported` | `../useSupported` |


---

## Functions

### `useDeviceOrientation(options: ConfigurableWindow): { isSupported: any; isAbsolute: any; alpha: Ref<number>; beta: Ref<number>; gamma: Ref<number>; }`

<details><summary>Code</summary>

```ts
export function useDeviceOrientation(options: ConfigurableWindow = {}) {
  const { window = defaultWindow } = options
  const isSupported = useSupported(() => window && 'DeviceOrientationEvent' in window)

  const isAbsolute = shallowRef(false)
  const alpha: Ref<number | null> = shallowRef(null)
  const beta: Ref<number | null> = shallowRef(null)
  const gamma: Ref<number | null> = shallowRef(null)

  if (window && isSupported.value) {
    useEventListener(window, 'deviceorientation', (event) => {
      isAbsolute.value = event.absolute
      alpha.value = event.alpha
      beta.value = event.beta
      gamma.value = event.gamma
    }, { passive: true })
  }

  return {
    isSupported,
    isAbsolute,
    alpha,
    beta,
    gamma,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive DeviceOrientationEvent.
 *
 * @see https://vueuse.org/useDeviceOrientation
 * @param options
 */
```

- **Parameters**:
  - `options: ConfigurableWindow`
- **Return Type**: `{ isSupported: any; isAbsolute: any; alpha: Ref<number>; beta: Ref<number>; gamma: Ref<number>; }`
- **Calls**:
  - `useSupported (from ../useSupported)`
  - `shallowRef (from vue)`
  - `useEventListener (from ../useEventListener)`

---

## Type Aliases

### `UseDeviceOrientationReturn`

```ts
type UseDeviceOrientationReturn = ReturnType<typeof useDeviceOrientation>;
```


---