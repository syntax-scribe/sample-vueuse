[⬅️ Back to Table of Contents](../index.md)

# 📄 `contributors.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 1 |
| 📊 Variables & Constants | 2 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 2 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/contributors.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `contributorsGenerated` | `./contributors.json` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `contributorsAvatars` | `Record<string, string>` | const | `{}` | ✗ |
| `emeriti` | `TeamMember[]` | const | `[
  {
    avatar: contributorsAvatars.egoist,
    name: 'EGOIST',
    github: 'egoist',
    twitter: '_egoistlily',
    bluesky: 'egoist.dev',
    sponsors: true,
    description: '',
    packages: ['head'],
  },
  {
    avatar: contributorsAvatars.webfansplz,
    name: 'webfansplz',
    github: 'webfansplz',
    twitter: 'webfansplz',
    sponsors: false,
    functions: [
      'useDateFormat',
      'useAsyncQueue',
    ],
    description: 'FE Developer<br>Love open source',
  },
  {
    avatar: contributorsAvatars.anteriovieira,
    name: 'anteriovieira',
    github: 'anteriovieira',
    twitter: 'anteriovieira',
    sponsors: false,
    description: '',
  },
  {
    avatar: contributorsAvatars['cawa-93'],
    name: 'Alex Kozack',
    github: 'cawa-93',
    twitter: 'alex_kozack',
    bluesky: 'kozack.me',
    sponsors: false,
    functions: ['useMediaControls'],
    description: 'Open Source Contributor from Ukraine',
  },
  {
    avatar: contributorsAvatars.scottbedard,
    name: 'Scott Bedard',
    github: 'scottbedard',
    bluesky: 'scottbedard.net',
    sponsors: false,
    functions: [
      'useTransition',
      'useDocumentVisibility',
      'useElementVisibility',
    ],
    description: '',
  },
  {
    avatar: contributorsAvatars.sibbng,
    name: 'sibbng',
    github: 'sibbng',
    sponsors: false,
    description: '',
    functions: [
      'onClickOutside',
      'useStyleTag',
    ],
  },
  {
    avatar: contributorsAvatars.okxiaoliang4,
    name: 'Jelf',
    github: 'okxiaoliang4',
    twitter: 'okxiaoliang4',
    sponsors: false,
    functions: [
      'useElementByPoint',
      'useScreenSafeArea',
    ],
    description: '',
  },
  {
    avatar: contributorsAvatars.lstoeferle,
    name: 'lstoeferle',
    github: 'lstoeferle',
    twitter: '54ku1',
    sponsors: false,
    functions: [
      'useSwipe',
      'useUrlSearchParams',
    ],
    description: '',
  },
]` | ✓ |


---

## Functions

### `getAvatarUrl(name: string): string`

<details><summary>Code</summary>

```ts
function getAvatarUrl(name: string) {
  return `https://avatars.githubusercontent.com/${name}?v=4`
}
```
</details>

- **Parameters**:
  - `name: string`
- **Return Type**: `string`

---

## Interfaces

### `Contributor`

<details><summary>Interface Code</summary>

```ts
export interface Contributor {
  name: string
  avatar: string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `name` | `string` | ✗ |  |
| `avatar` | `string` | ✗ |  |

### `TeamMember`

<details><summary>Interface Code</summary>

```ts
export interface TeamMember {
  avatar: string
  name: string
  github: string
  twitter?: string
  bluesky?: string
  sponsors?: boolean
  description: string
  packages?: string[]
  functions?: string[]
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `avatar` | `string` | ✗ |  |
| `name` | `string` | ✗ |  |
| `github` | `string` | ✗ |  |
| `twitter` | `string` | ✓ |  |
| `bluesky` | `string` | ✓ |  |
| `sponsors` | `boolean` | ✓ |  |
| `description` | `string` | ✗ |  |
| `packages` | `string[]` | ✓ |  |
| `functions` | `string[]` | ✓ |  |


---