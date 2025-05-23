[⬅️ Back to Table of Contents](../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 0
- **Classes**: 0
- **Imports**: 8
- **Interfaces**: 3
- **Type Aliases**: 0

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

## 🔧 Functions

> No functions found in this file.


---

## Classes

> No classes found in this file.


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

## Type Aliases

> No type aliases found in this file.


---