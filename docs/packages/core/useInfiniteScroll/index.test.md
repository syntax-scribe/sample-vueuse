[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 8
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useInfiniteScroll/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `flushPromises` | `@vue/test-utils` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `deepRef` | `vue` |
| `useElementVisibility` | `../useElementVisibility` |
| `useInfiniteScroll` | `./index` |


---

## Functions

### `givenMockElement({
    scrollHeight = 0,
  }: any): HTMLDivElement`

<details><summary>Code</summary>

```ts
function givenMockElement({
    scrollHeight = 0,
  } = {}): HTMLDivElement {
    const mockElement = document.createElement('div')
    Object.defineProperty(mockElement, 'scrollHeight', {
      value: scrollHeight,
    })
    return mockElement
  }
```
</details>

- **Parameters**:
  - `{
    scrollHeight = 0,
  }: any`
- **Return Type**: `HTMLDivElement`
- **Calls**:
  - `document.createElement`
  - `Object.defineProperty`
### `givenElementVisibilityRefMock(defaultValue: boolean): any`

<details><summary>Code</summary>

```ts
function givenElementVisibilityRefMock(defaultValue: boolean) {
    const mockVisibilityRef = deepRef(defaultValue)
    vi.mocked(useElementVisibility).mockReturnValue(mockVisibilityRef)
    return mockVisibilityRef
  }
```
</details>

- **Parameters**:
  - `defaultValue: boolean`
- **Return Type**: `any`
- **Calls**:
  - `deepRef (from vue)`
  - `vi.mocked(useElementVisibility).mockReturnValue`

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