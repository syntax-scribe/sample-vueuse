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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---