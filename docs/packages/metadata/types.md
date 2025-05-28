[⬅️ Back to Table of Contents](../../index.md)

# 📄 `types.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 0 |
| 🧱 Classes | 0 |
| 📦 Imports | 0 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 6 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/metadata/types.ts`**

## 🔧 Functions

> No functions found in this file.


---

## Interfaces

### `PackageManifest`

<details><summary>Interface Code</summary>

```ts
export interface PackageManifest {
  name: string
  display: string
  addon?: boolean
  author?: string
  description?: string
  external?: string[]
  globals?: Record<string, string>
  manualImport?: boolean
  deprecated?: boolean
  submodules?: boolean
  build?: boolean
  iife?: boolean
  mjs?: boolean
  dts?: boolean
  target?: string
  utils?: boolean
  copy?: string[]
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `name` | `string` | ✗ |  |
| `display` | `string` | ✗ |  |
| `addon` | `boolean` | ✓ |  |
| `author` | `string` | ✓ |  |
| `description` | `string` | ✓ |  |
| `external` | `string[]` | ✓ |  |
| `globals` | `Record<string, string>` | ✓ |  |
| `manualImport` | `boolean` | ✓ |  |
| `deprecated` | `boolean` | ✓ |  |
| `submodules` | `boolean` | ✓ |  |
| `build` | `boolean` | ✓ |  |
| `iife` | `boolean` | ✓ |  |
| `mjs` | `boolean` | ✓ |  |
| `dts` | `boolean` | ✓ |  |
| `target` | `string` | ✓ |  |
| `utils` | `boolean` | ✓ |  |
| `copy` | `string[]` | ✓ |  |

### `VueUseFunction`

<details><summary>Interface Code</summary>

```ts
export interface VueUseFunction {
  name: string
  package: string
  importPath?: string
  lastUpdated?: number
  category?: string
  description?: string
  docs?: string
  deprecated?: boolean
  internal?: boolean
  component?: boolean
  directive?: boolean
  external?: string
  alias?: string[]
  related?: string[]
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `name` | `string` | ✗ |  |
| `package` | `string` | ✗ |  |
| `importPath` | `string` | ✓ |  |
| `lastUpdated` | `number` | ✓ |  |
| `category` | `string` | ✓ |  |
| `description` | `string` | ✓ |  |
| `docs` | `string` | ✓ |  |
| `deprecated` | `boolean` | ✓ |  |
| `internal` | `boolean` | ✓ |  |
| `component` | `boolean` | ✓ |  |
| `directive` | `boolean` | ✓ |  |
| `external` | `string` | ✓ |  |
| `alias` | `string[]` | ✓ |  |
| `related` | `string[]` | ✓ |  |

### `VueUsePackage`

<details><summary>Interface Code</summary>

```ts
export interface VueUsePackage extends PackageManifest {
  dir: string
  docs?: string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `dir` | `string` | ✗ |  |
| `docs` | `string` | ✓ |  |

### `PackageIndexes`

<details><summary>Interface Code</summary>

```ts
export interface PackageIndexes {
  packages: Record<string, VueUsePackage>
  categories: string[]
  functions: VueUseFunction[]
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `packages` | `Record<string, VueUsePackage>` | ✗ |  |
| `categories` | `string[]` | ✗ |  |
| `functions` | `VueUseFunction[]` | ✗ |  |

### `CommitInfo`

<details><summary>Interface Code</summary>

```ts
export interface CommitInfo {
  functions: string[]
  version?: string
  hash: string
  date: string
  message: string
  refs?: string
  body?: string
  author_name: string
  author_email: string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `functions` | `string[]` | ✗ |  |
| `version` | `string` | ✓ |  |
| `hash` | `string` | ✗ |  |
| `date` | `string` | ✗ |  |
| `message` | `string` | ✗ |  |
| `refs` | `string` | ✓ |  |
| `body` | `string` | ✓ |  |
| `author_name` | `string` | ✗ |  |
| `author_email` | `string` | ✗ |  |

### `ContributorInfo`

<details><summary>Interface Code</summary>

```ts
export interface ContributorInfo {
  name: string
  count: number
  hash: string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `name` | `string` | ✗ |  |
| `count` | `number` | ✗ |  |
| `hash` | `string` | ✗ |  |


---