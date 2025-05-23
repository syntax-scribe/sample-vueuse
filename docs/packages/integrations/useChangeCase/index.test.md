[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 7
- **Interfaces**: 1
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/integrations/useChangeCase/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Options` | `change-case` |
| `ChangeCaseType` | `./index` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `deepRef` | `vue` |
| `useChangeCase` | `./index` |


---

## Functions

### `input(): string`

<details><summary>Code</summary>

```ts
() => helloWorld
```
</details>

- **Return Type**: `string`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `objectValue`

<details><summary>Interface Code</summary>

```ts
interface objectValue {
    helloWorld: string
    vueuse: string
    delimiterHelloWorld: string
    delimiterVueuse: string
  }
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `helloWorld` | `string` | ✗ |  |
| `vueuse` | `string` | ✗ |  |
| `delimiterHelloWorld` | `string` | ✗ |  |
| `delimiterVueuse` | `string` | ✗ |  |


---

## Type Aliases

### `ObjectTypes`

```ts
type ObjectTypes = Omit<Record<ChangeCaseType, objectValue>, 'camelCase'>;
```


---