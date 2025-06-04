[⬅️ Back to Table of Contents](../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 📦 Imports | 8 |
| 📊 Variables & Constants | 3 |
| 📐 Interfaces | 3 |

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