[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 🧱 Classes | 0 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 5 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useFocusWithin/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `shallowRef` | `vue` |
| `useFocusWithin` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `parent` | `Ref<HTMLFormElement>` | let/var | `*not shown*` | ✗ |
| `child` | `Ref<HTMLDivElement>` | let/var | `*not shown*` | ✗ |
| `child2` | `Ref<HTMLDivElement>` | let/var | `*not shown*` | ✗ |
| `grandchild` | `Ref<HTMLInputElement>` | let/var | `*not shown*` | ✗ |
| `mockWindow` | `Window & typeof globalThis` | const | `new Proxy(window, {
      get: (target, prop: any) => {
        if (prop === 'document')
          return { ...document, activeElement: null }

        return window[prop]
      },
    })` | ✗ |


---

## Functions

### `get(target: Window & typeof globalThis, prop: any): Window | { activeElement: any; URL: string; alinkColor: string; all: HTMLAllCollection; anchors: HTMLCollectionOf<HTMLAnchorElement>; ... 259 more ...; evaluate(expression: string, contextNode: Node, resolver?: XPathNSResolver, type?: number, result?: XPathResult): XPathResult; }`

<details><summary>Code</summary>

```ts
(target, prop: any) => {
        if (prop === 'document')
          return { ...document, activeElement: null }

        return window[prop]
      }
```
</details>

- **Parameters**:
  - `target: Window & typeof globalThis`
  - `prop: any`
- **Return Type**: `Window | { activeElement: any; URL: string; alinkColor: string; all: HTMLAllCollection; anchors: HTMLCollectionOf<HTMLAnchorElement>; ... 259 more ...; evaluate(expression: string, contextNode: Node, resolver?: XPathNSResolver, type?: number, result?: XPathResult): XPathResult; }`
### `get(target: Window & typeof globalThis, prop: any): Window | { activeElement: any; URL: string; alinkColor: string; all: HTMLAllCollection; anchors: HTMLCollectionOf<HTMLAnchorElement>; ... 259 more ...; evaluate(expression: string, contextNode: Node, resolver?: XPathNSResolver, type?: number, result?: XPathResult): XPathResult; }`

<details><summary>Code</summary>

```ts
(target, prop: any) => {
        if (prop === 'document')
          return { ...document, activeElement: null }

        return window[prop]
      }
```
</details>

- **Parameters**:
  - `target: Window & typeof globalThis`
  - `prop: any`
- **Return Type**: `Window | { activeElement: any; URL: string; alinkColor: string; all: HTMLAllCollection; anchors: HTMLCollectionOf<HTMLAnchorElement>; ... 259 more ...; evaluate(expression: string, contextNode: Node, resolver?: XPathNSResolver, type?: number, result?: XPathResult): XPathResult; }`
### `get(target: Window & typeof globalThis, prop: any): Window | { activeElement: any; URL: string; alinkColor: string; all: HTMLAllCollection; anchors: HTMLCollectionOf<HTMLAnchorElement>; ... 259 more ...; evaluate(expression: string, contextNode: Node, resolver?: XPathNSResolver, type?: number, result?: XPathResult): XPathResult; }`

<details><summary>Code</summary>

```ts
(target, prop: any) => {
        if (prop === 'document')
          return { ...document, activeElement: null }

        return window[prop]
      }
```
</details>

- **Parameters**:
  - `target: Window & typeof globalThis`
  - `prop: any`
- **Return Type**: `Window | { activeElement: any; URL: string; alinkColor: string; all: HTMLAllCollection; anchors: HTMLCollectionOf<HTMLAnchorElement>; ... 259 more ...; evaluate(expression: string, contextNode: Node, resolver?: XPathNSResolver, type?: number, result?: XPathResult): XPathResult; }`
### `get(target: Window & typeof globalThis, prop: any): Window | { activeElement: any; URL: string; alinkColor: string; all: HTMLAllCollection; anchors: HTMLCollectionOf<HTMLAnchorElement>; ... 259 more ...; evaluate(expression: string, contextNode: Node, resolver?: XPathNSResolver, type?: number, result?: XPathResult): XPathResult; }`

<details><summary>Code</summary>

```ts
(target, prop: any) => {
        if (prop === 'document')
          return { ...document, activeElement: null }

        return window[prop]
      }
```
</details>

- **Parameters**:
  - `target: Window & typeof globalThis`
  - `prop: any`
- **Return Type**: `Window | { activeElement: any; URL: string; alinkColor: string; all: HTMLAllCollection; anchors: HTMLCollectionOf<HTMLAnchorElement>; ... 259 more ...; evaluate(expression: string, contextNode: Node, resolver?: XPathNSResolver, type?: number, result?: XPathResult): XPathResult; }`

---