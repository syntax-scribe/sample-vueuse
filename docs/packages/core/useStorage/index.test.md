[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 16 |
| 🧱 Classes | 0 |
| 📦 Imports | 16 |
| 📊 Variables & Constants | 8 |
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
📂 **`packages/core/useStorage/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `debounceFilter` | `@vueuse/shared` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `deepRef` | `vue` |
| `defineComponent` | `vue` |
| `nextTick` | `vue` |
| `toRaw` | `vue` |
| `mount` | `../../.test` |
| `nextTwoTick` | `../../.test` |
| `useSetup` | `../../.test` |
| `customStorageEventName` | `./index` |
| `StorageSerializers` | `./index` |
| `useStorage` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `KEY` | `"custom-key"` | const | `'custom-key'` | ✗ |
| `ANOTHER_KEY` | `"another-key"` | const | `'another-key'` | ✗ |
| `storageState` | `Map<string, string | number>` | const | `new Map<string, string | number | undefined>()` | ✗ |
| `storageMock` | `{ getItem: any; setItem: any; removeItem: any; clear: any; }` | const | `{
    getItem: vi.fn(x => storageState.get(x)),
    setItem: vi.fn((x, v) => storageState.set(x, v)),
    removeItem: vi.fn(x => storageState.delete(x)),
    clear: vi.fn(() => storageState.clear()),
  }` | ✗ |
| `storage` | `Storage` | const | `storageMock as any as Storage` | ✗ |
| `call` | `[CustomEvent<any>]` | let/var | `eventFn.mock.calls[0] as [CustomEvent]` | ✗ |
| `call2` | `[CustomEvent<any>]` | let/var | `eventFn.mock.calls[1] as [CustomEvent]` | ✗ |
| `customStorage` | `{ getItem: (key: string) => string; setItem: (key: string, value: string) => void; removeItem: (key: string) => void; }` | let/var | `{
      getItem: storage.getItem,
      setItem: storage.setItem,
      removeItem: storage.removeItem,
    }` | ✗ |


---

## Functions

### `mergeDefaults(value: string, initial: string): string[]`

<details><summary>Code</summary>

```ts
(value, initial) => [...initial, ...value]
```
</details>

- **Parameters**:
  - `value: string`
  - `initial: string`
- **Return Type**: `string[]`
### `mergeDefaults(value: string, initial: string): string[]`

<details><summary>Code</summary>

```ts
(value, initial) => [...initial, ...value]
```
</details>

- **Parameters**:
  - `value: string`
  - `initial: string`
- **Return Type**: `string[]`
### `mergeDefaults(value: string, initial: string): string[]`

<details><summary>Code</summary>

```ts
(value, initial) => [...initial, ...value]
```
</details>

- **Parameters**:
  - `value: string`
  - `initial: string`
- **Return Type**: `string[]`
### `mergeDefaults(value: string, initial: string): string[]`

<details><summary>Code</summary>

```ts
(value, initial) => [...initial, ...value]
```
</details>

- **Parameters**:
  - `value: string`
  - `initial: string`
- **Return Type**: `string[]`
### `mergeDefaults(value: string, initial: string): string`

<details><summary>Code</summary>

```ts
(value, initial) => value + initial
```
</details>

- **Parameters**:
  - `value: string`
  - `initial: string`
- **Return Type**: `string`
### `mergeDefaults(value: string, initial: string): string`

<details><summary>Code</summary>

```ts
(value, initial) => value + initial
```
</details>

- **Parameters**:
  - `value: string`
  - `initial: string`
- **Return Type**: `string`
### `mergeDefaults(value: string, initial: string): string`

<details><summary>Code</summary>

```ts
(value, initial) => value + initial
```
</details>

- **Parameters**:
  - `value: string`
  - `initial: string`
- **Return Type**: `string`
### `mergeDefaults(value: string, initial: string): string`

<details><summary>Code</summary>

```ts
(value, initial) => value + initial
```
</details>

- **Parameters**:
  - `value: string`
  - `initial: string`
- **Return Type**: `string`
### `getItem(): any`

<details><summary>Code</summary>

```ts
() => null
```
</details>

- **Return Type**: `any`
### `setItem(): never`

<details><summary>Code</summary>

```ts
() => { throw new Error('write item error') }
```
</details>

- **Return Type**: `never`
### `getItem(): any`

<details><summary>Code</summary>

```ts
() => null
```
</details>

- **Return Type**: `any`
### `setItem(): never`

<details><summary>Code</summary>

```ts
() => { throw new Error('write item error') }
```
</details>

- **Return Type**: `never`
### `getItem(): any`

<details><summary>Code</summary>

```ts
() => null
```
</details>

- **Return Type**: `any`
### `setItem(): never`

<details><summary>Code</summary>

```ts
() => { throw new Error('write item error') }
```
</details>

- **Return Type**: `never`
### `getItem(): any`

<details><summary>Code</summary>

```ts
() => null
```
</details>

- **Return Type**: `any`
### `setItem(): never`

<details><summary>Code</summary>

```ts
() => { throw new Error('write item error') }
```
</details>

- **Return Type**: `never`

---