[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `stop` | `any` | let/var | `noop` | ✗ |


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

## Type Aliases

### `UseDevicePixelRatioReturn`

```ts
type UseDevicePixelRatioReturn = ReturnType<typeof useDevicePixelRatio>;
```


---