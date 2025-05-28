[⬅️ Back to Table of Contents](../../index.md)

# 📄 `_resolve-element.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 0 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/_resolve-element.ts`**

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