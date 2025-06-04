[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 9 |
| 📊 Variables & Constants | 3 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/onKeyStroke/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `KeyStrokeEventName` | `./index` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `shallowRef` | `vue` |
| `onKeyStroke` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `element` | `Ref<HTMLElement>` | let/var | `*not shown*` | ✗ |
| `callBackFn` | `any` | let/var | `*not shown*` | ✗ |
| `ev` | `KeyboardEvent` | const | `new KeyboardEvent(type, { key, repeat })` | ✗ |


---

## Functions

### `createKeyEvent(key: string, type: KeyStrokeEventName, repeat: boolean): void`

<details><summary>Code</summary>

```ts
function createKeyEvent(key: string, type: KeyStrokeEventName, repeat = false) {
    const ev = new KeyboardEvent(type, { key, repeat })
    element.value.dispatchEvent(ev)
  }
```
</details>

- **Parameters**:
  - `key: string`
  - `type: KeyStrokeEventName`
  - `repeat: boolean`
- **Return Type**: `void`
- **Calls**:
  - `element.value.dispatchEvent`
### `filter(event: KeyboardEvent): boolean`

<details><summary>Code</summary>

```ts
(event: KeyboardEvent) => {
      return event.key === 'A'
    }
```
</details>

- **Parameters**:
  - `event: KeyboardEvent`
- **Return Type**: `boolean`

---