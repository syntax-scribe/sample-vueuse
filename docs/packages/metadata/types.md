[⬅️ Back to Table of Contents](../../index.md)

# 📄 `types.ts`

## 📚 Table of Contents

- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 0
- **Classes**: 0
- **Imports**: 0
- **Interfaces**: 6
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/metadata/types.ts`**

## 📦 Imports

> No imports found in this file.


---

## 🔧 Functions

> No functions found in this file.


---

## Classes

> No classes found in this file.


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

## Type Aliases

> No type aliases found in this file.


---