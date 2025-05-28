[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 8 |
| 📊 Variables & Constants | 1 |
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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `mockElementScrollHeight` | `100` | let/var | `100` | ✗ |


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