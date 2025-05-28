[⬅️ Back to Table of Contents](../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 0 |
| 🧱 Classes | 0 |
| 📦 Imports | 8 |
| 📊 Variables & Constants | 3 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 3 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/nuxt/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Import` | `unimport` |
| `Preset` | `unimport` |
| `dirname` | `node:path` |
| `resolve` | `node:path` |
| `fileURLToPath` | `node:url` |
| `defineNuxtModule` | `@nuxt/kit` |
| `metadata` | `@vueuse/metadata` |
| `isPackageExists` | `local-pkg` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `disabledFunctions` | `string[]` | const | `[
  // Vue 3 built-in
  'toRefs',
  'toRef',
  'toValue',

  // Nuxt built-in
  'useFetch',
  'useCookie',
  'useHead',
  'useStorage',
  'useImage',
]` | ✗ |
| `packages` | `string[]` | const | `[
  'core',
  'shared',
  'components',
  'motion',
  'firebase',
  'rxjs',
  'sound',
  'math',
  'router',
]` | ✗ |
| `names` | `any[]` | const | `[i.name, ...i.alias || []]` | ✗ |


---

## 🔧 Functions

> No functions found in this file.


---

## Interfaces

### `VueUseNuxtOptions`

<details><summary>Interface Code</summary>

```ts
export interface VueUseNuxtOptions {
  /**
   * @default true
   */
  autoImports?: boolean

  /**
   * @experimental
   * @default false
   */
  ssrHandlers?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `autoImports` | `boolean` | ✓ |  |
| `ssrHandlers` | `boolean` | ✓ |  |

### `NuxtConfig`

<details><summary>Interface Code</summary>

```ts
interface NuxtConfig {
    vueuse?: VueUseNuxtOptions
  }
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `vueuse` | `VueUseNuxtOptions` | ✓ |  |

### `NuxtOptions`

<details><summary>Interface Code</summary>

```ts
interface NuxtOptions {
    vueuse?: VueUseNuxtOptions
  }
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `vueuse` | `VueUseNuxtOptions` | ✓ |  |


---