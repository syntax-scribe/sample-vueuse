[⬅️ Back to Table of Contents](../../index.md)

# 📄 `_resolve-element.ts`

## 📚 Table of Contents

- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 0
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/_resolve-element.ts`**

## 📦 Imports

> No imports found in this file.


---

## Functions

### `resolveElement(el: HTMLElement | SVGElement | Window | Document | null | undefined): HTMLElement | SVGElement | null | undefined`

<details><summary>Code</summary>

```ts
export function resolveElement(
  el: HTMLElement | SVGElement | Window | Document | null | undefined,
): HTMLElement | SVGElement | null | undefined {
  if (typeof Window !== 'undefined' && el instanceof Window)
    return el.document.documentElement

  if (typeof Document !== 'undefined' && el instanceof Document)
    return el.documentElement

  return el as HTMLElement | SVGElement | null | undefined
}
```
</details>

- **JSDoc**:
```ts
/**
 * Resolves an element from a given element, window, or document.
 *
 * @internal
 */
```

- **Parameters**:
  - `el: HTMLElement | SVGElement | Window | Document | null | undefined`
- **Return Type**: `HTMLElement | SVGElement | null | undefined`

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