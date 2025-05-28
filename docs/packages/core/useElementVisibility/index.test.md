[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 4 |
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
📂 **`packages/core/useElementVisibility/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `beforeAll` | `vitest` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `useElementVisibility` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `el` | `HTMLDivElement` | let/var | `*not shown*` | ✗ |
| `callback` | `any` | const | `vi.mocked(useIntersectionObserver).mock.lastCall?.[1]` | ✗ |
| `callback` | `any` | const | `vi.mocked(useIntersectionObserver).mock.lastCall?.[1]` | ✗ |
| `mockWindow` | `Window` | const | `{} as Window` | ✗ |


---

## Functions

### `callMockCallbackWithIsIntersectingValue(isIntersecting: boolean): any`

<details><summary>Code</summary>

```ts
(isIntersecting: boolean) => callback?.([{ isIntersecting, time: 1 } as IntersectionObserverEntry], {} as IntersectionObserver)
```
</details>

- **Parameters**:
  - `isIntersecting: boolean`
- **Return Type**: `any`
- **Calls**:
  - `callback`
### `callMockCallbackWithIsIntersectingValues(entries: { isIntersecting: boolean, time: number }[]): void`

<details><summary>Code</summary>

```ts
(...entries: { isIntersecting: boolean, time: number }[]) => {
        callback?.(entries as IntersectionObserverEntry[], {} as IntersectionObserver)
      }
```
</details>

- **Parameters**:
  - `entries: { isIntersecting: boolean, time: number }[]`
- **Return Type**: `void`
- **Calls**:
  - `callback`

---