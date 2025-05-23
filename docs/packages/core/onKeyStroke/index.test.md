[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 9
- **Interfaces**: 0
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---