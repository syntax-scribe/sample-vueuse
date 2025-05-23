[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 7
- **Interfaces**: 0
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useDevicePixelRatio/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableWindow` | `../_configurable` |
| `noop` | `@vueuse/shared` |
| `watchImmediate` | `@vueuse/shared` |
| `readonly` | `vue` |
| `shallowRef` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useMediaQuery` | `../useMediaQuery` |


---

## Functions

### `useDevicePixelRatio(options: ConfigurableWindow): { pixelRatio: any; stop: any; }`

<details><summary>Code</summary>

```ts
export function useDevicePixelRatio(options: ConfigurableWindow = {}) {
  const {
    window = defaultWindow,
  } = options

  const pixelRatio = shallowRef(1)
  const query = useMediaQuery(() => `(resolution: ${pixelRatio.value}dppx)`, options)
  let stop = noop

  if (window) {
    stop = watchImmediate(query, () => pixelRatio.value = window!.devicePixelRatio)
  }

  return {
    pixelRatio: readonly(pixelRatio),
    stop,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactively track `window.devicePixelRatio`.
 *
 * @see https://vueuse.org/useDevicePixelRatio
 */
```

- **Parameters**:
  - `options: ConfigurableWindow`
- **Return Type**: `{ pixelRatio: any; stop: any; }`
- **Calls**:
  - `shallowRef (from vue)`
  - `useMediaQuery (from ../useMediaQuery)`
  - `watchImmediate (from @vueuse/shared)`
  - `readonly (from vue)`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `UseDevicePixelRatioReturn`

```ts
type UseDevicePixelRatioReturn = ReturnType<typeof useDevicePixelRatio>;
```


---