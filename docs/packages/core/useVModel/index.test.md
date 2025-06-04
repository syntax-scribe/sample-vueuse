[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 🧱 Classes | 1 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 14 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Classes](#classes)

## 🛠️ File Location:
📂 **`packages/core/useVModel/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `nextTick` | `vue` |
| `useVModel` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `defaultKey` | `"modelValue"` | const | `'modelValue'` | ✗ |
| `defaultValue` | `"default"` | const | `'default'` | ✗ |
| `props` | `{ data: string; modelValue: string; }` | const | `{
      ...defaultProps(),
      data: 'data',
    }` | ✗ |
| `props` | `{ age: number; modelValue: string; }` | let/var | `{
      ...defaultProps(),
      age: 18,
    }` | ✗ |
| `props` | `{ data: { age: number; }; modelValue: string; }` | let/var | `{
      ...defaultProps(),
      data: {
        age: 18,
      },
    }` | ✗ |
| `props` | `{ data: { hobbies: string[]; }; modelValue: string; }` | let/var | `{
      ...defaultProps(),
      data: {
        hobbies: ['coding'],
      },
    }` | ✗ |
| `props` | `Record<string, unknown>` | const | `{
      ...defaultProps(),
      a: 0,
      b: '',
      c: false,
      d: null,
      e: undefined,
    }` | ✗ |
| `props` | `Record<string, unknown>` | const | `{
      ...defaultProps(),
      a: 0,
      b: '',
      c: false,
      d: null as string | null,
      e: undefined as string | undefined,
    }` | ✗ |
| `props` | `{ cl: SomeClass; }` | let/var | `{ cl: new SomeClass() }` | ✗ |
| `emitValue` | `any` | let/var | `emitMock.mock.calls[0][1]` | ✗ |
| `props` | `{ person: { age: number; child: { age: number; }; }; }` | let/var | `{
      person: {
        age: 18,
        child: { age: 2 },
      },
    }` | ✗ |
| `props` | `{ person: { age: number; child: { age: number; }; }; }` | let/var | `{
      person: {
        age: 18,
        child: { age: 2 },
      },
    }` | ✗ |
| `res` | `string` | let/var | `''` | ✗ |
| `res` | `string` | let/var | `''` | ✗ |


---

## Functions

### `defaultProps(): { modelValue: string; }`

<details><summary>Code</summary>

```ts
() => ({
    [defaultKey]: defaultValue,
  })
```
</details>

- **Return Type**: `{ modelValue: string; }`
### `SomeClass.someMethod(): void`

<details><summary>Code</summary>

```ts
someMethod() {}
```
</details>

- **Return Type**: `void`
### `beforeEmit(value: string): boolean`

<details><summary>Code</summary>

```ts
(value: string) => {
      res = value
      beforeEmitMock()
      return true
    }
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `boolean`
- **Calls**:
  - `beforeEmitMock`
### `beforeEmit(value: string): boolean`

<details><summary>Code</summary>

```ts
(value: string) => {
      res = value
      beforeEmitMock()
      return false
    }
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `boolean`
- **Calls**:
  - `beforeEmitMock`

---

## Classes

### `SomeClass`

<details><summary>Class Code</summary>

```ts
class SomeClass {
      num1 = 1

      someMethod() {}
    }
```
</details>

#### Methods

##### `someMethod(): void`

<details><summary>Code</summary>

```ts
someMethod() {}
```
</details>


---