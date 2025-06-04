[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 5 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 1 |
| 🟢 Vue Composition API | 2 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useDark/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `BasicColorSchema` | `../useColorMode` |
| `UseColorModeOptions` | `../useColorMode` |
| `computed` | `vue` |
| `useColorMode` | `../useColorMode` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `modeVal` | `"light" | "dark"` | const | `v ? 'dark' : 'light'` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |


---

## Functions

### `useDark(options: UseDarkOptions): any`

<details><summary>Code</summary>

```ts
export function useDark(options: UseDarkOptions = {}) {
  const {
    valueDark = 'dark',
    valueLight = '',
  } = options

  const mode = useColorMode({
    ...options,
    onChanged: (mode, defaultHandler) => {
      if (options.onChanged)
        options.onChanged?.(mode === 'dark', defaultHandler, mode)
      else
        defaultHandler(mode)
    },
    modes: {
      dark: valueDark,
      light: valueLight,
    },
  })

  const system = computed(() => mode.system.value)

  const isDark = computed<boolean>({
    get() {
      return mode.value === 'dark'
    },
    set(v) {
      const modeVal = v ? 'dark' : 'light'
      if (system.value === modeVal)
        mode.value = 'auto'
      else
        mode.value = modeVal
    },
  })

  return isDark
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive dark mode with auto data persistence.
 *
 * @see https://vueuse.org/useDark
 * @param options
 */
```

- **Parameters**:
  - `options: UseDarkOptions`
- **Return Type**: `any`
- **Calls**:
  - `useColorMode (from ../useColorMode)`
  - `options.onChanged`
  - `defaultHandler`
  - `computed (from vue)`
### `onChanged(mode: BasicColorMode | "auto", defaultHandler: (mode: BasicColorMode | "auto") => void): void`

<details><summary>Code</summary>

```ts
(mode, defaultHandler) => {
      if (options.onChanged)
        options.onChanged?.(mode === 'dark', defaultHandler, mode)
      else
        defaultHandler(mode)
    }
```
</details>

- **Parameters**:
  - `mode: BasicColorMode | "auto"`
  - `defaultHandler: (mode: BasicColorMode | "auto") => void`
- **Return Type**: `void`
- **Calls**:
  - `options.onChanged`
  - `defaultHandler`
### `onChanged(mode: BasicColorMode | "auto", defaultHandler: (mode: BasicColorMode | "auto") => void): void`

<details><summary>Code</summary>

```ts
(mode, defaultHandler) => {
      if (options.onChanged)
        options.onChanged?.(mode === 'dark', defaultHandler, mode)
      else
        defaultHandler(mode)
    }
```
</details>

- **Parameters**:
  - `mode: BasicColorMode | "auto"`
  - `defaultHandler: (mode: BasicColorMode | "auto") => void`
- **Return Type**: `void`
- **Calls**:
  - `options.onChanged`
  - `defaultHandler`
### `onChanged(mode: BasicColorMode | "auto", defaultHandler: (mode: BasicColorMode | "auto") => void): void`

<details><summary>Code</summary>

```ts
(mode, defaultHandler) => {
      if (options.onChanged)
        options.onChanged?.(mode === 'dark', defaultHandler, mode)
      else
        defaultHandler(mode)
    }
```
</details>

- **Parameters**:
  - `mode: BasicColorMode | "auto"`
  - `defaultHandler: (mode: BasicColorMode | "auto") => void`
- **Return Type**: `void`
- **Calls**:
  - `options.onChanged`
  - `defaultHandler`
### `onChanged(mode: BasicColorMode | "auto", defaultHandler: (mode: BasicColorMode | "auto") => void): void`

<details><summary>Code</summary>

```ts
(mode, defaultHandler) => {
      if (options.onChanged)
        options.onChanged?.(mode === 'dark', defaultHandler, mode)
      else
        defaultHandler(mode)
    }
```
</details>

- **Parameters**:
  - `mode: BasicColorMode | "auto"`
  - `defaultHandler: (mode: BasicColorMode | "auto") => void`
- **Return Type**: `void`
- **Calls**:
  - `options.onChanged`
  - `defaultHandler`

---

## Interfaces

### `UseDarkOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseDarkOptions extends Omit<UseColorModeOptions<BasicColorSchema>, 'modes' | 'onChanged'> {
  /**
   * Value applying to the target element when isDark=true
   *
   * @default 'dark'
   */
  valueDark?: string

  /**
   * Value applying to the target element when isDark=false
   *
   * @default ''
   */
  valueLight?: string

  /**
   * A custom handler for handle the updates.
   * When specified, the default behavior will be overridden.
   *
   * @default undefined
   */
  onChanged?: (isDark: boolean, defaultHandler: ((mode: BasicColorSchema) => void), mode: BasicColorSchema) => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `valueDark` | `string` | ✓ |  |
| `valueLight` | `string` | ✓ |  |
| `onChanged` | `(isDark: boolean, defaultHandler: ((mode: BasicColorSchema) => void), mode: BasicColorSchema) => void` | ✓ |  |


---