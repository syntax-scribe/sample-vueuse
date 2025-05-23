[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 7
- **Interfaces**: 0
- **Type Aliases**: 0

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

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---