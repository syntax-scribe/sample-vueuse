[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `serialization.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 31 |
| 🧱 Classes | 0 |
| 📦 Imports | 0 |
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

- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useBase64/serialization.ts`**

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `defaults` | `{ array: (v: unknown[]) => string; object: (v: Record<string, unknown>) => string; set: (v: Set<unknown>) => string; map: (v: Map<string, unknown>) => string; null: () => string; }` | const | `{
  array: (v: unknown[]) => JSON.stringify(v),
  object: (v: Record<string, unknown>) => JSON.stringify(v),
  set: (v: Set<unknown>) => JSON.stringify(Array.from(v)),
  map: (v: Map<string, unknown>) => JSON.stringify(Object.fromEntries(v)),
  null: () => '',
}` | ✗ |


---

## Functions

### `array(v: unknown[]): string`

<details><summary>Code</summary>

```ts
(v: unknown[]) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: unknown[]`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `object(v: Record<string, unknown>): string`

<details><summary>Code</summary>

```ts
(v: Record<string, unknown>) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: Record<string, unknown>`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `set(v: Set<unknown>): string`

<details><summary>Code</summary>

```ts
(v: Set<unknown>) => JSON.stringify(Array.from(v))
```
</details>

- **Parameters**:
  - `v: Set<unknown>`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `map(v: Map<string, unknown>): string`

<details><summary>Code</summary>

```ts
(v: Map<string, unknown>) => JSON.stringify(Object.fromEntries(v))
```
</details>

- **Parameters**:
  - `v: Map<string, unknown>`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `null(): string`

<details><summary>Code</summary>

```ts
() => ''
```
</details>

- **Return Type**: `string`
### `array(v: unknown[]): string`

<details><summary>Code</summary>

```ts
(v: unknown[]) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: unknown[]`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `object(v: Record<string, unknown>): string`

<details><summary>Code</summary>

```ts
(v: Record<string, unknown>) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: Record<string, unknown>`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `set(v: Set<unknown>): string`

<details><summary>Code</summary>

```ts
(v: Set<unknown>) => JSON.stringify(Array.from(v))
```
</details>

- **Parameters**:
  - `v: Set<unknown>`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `map(v: Map<string, unknown>): string`

<details><summary>Code</summary>

```ts
(v: Map<string, unknown>) => JSON.stringify(Object.fromEntries(v))
```
</details>

- **Parameters**:
  - `v: Map<string, unknown>`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `null(): string`

<details><summary>Code</summary>

```ts
() => ''
```
</details>

- **Return Type**: `string`
### `array(v: unknown[]): string`

<details><summary>Code</summary>

```ts
(v: unknown[]) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: unknown[]`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `object(v: Record<string, unknown>): string`

<details><summary>Code</summary>

```ts
(v: Record<string, unknown>) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: Record<string, unknown>`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `set(v: Set<unknown>): string`

<details><summary>Code</summary>

```ts
(v: Set<unknown>) => JSON.stringify(Array.from(v))
```
</details>

- **Parameters**:
  - `v: Set<unknown>`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `map(v: Map<string, unknown>): string`

<details><summary>Code</summary>

```ts
(v: Map<string, unknown>) => JSON.stringify(Object.fromEntries(v))
```
</details>

- **Parameters**:
  - `v: Map<string, unknown>`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `null(): string`

<details><summary>Code</summary>

```ts
() => ''
```
</details>

- **Return Type**: `string`
### `array(v: unknown[]): string`

<details><summary>Code</summary>

```ts
(v: unknown[]) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: unknown[]`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `object(v: Record<string, unknown>): string`

<details><summary>Code</summary>

```ts
(v: Record<string, unknown>) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: Record<string, unknown>`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `set(v: Set<unknown>): string`

<details><summary>Code</summary>

```ts
(v: Set<unknown>) => JSON.stringify(Array.from(v))
```
</details>

- **Parameters**:
  - `v: Set<unknown>`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `map(v: Map<string, unknown>): string`

<details><summary>Code</summary>

```ts
(v: Map<string, unknown>) => JSON.stringify(Object.fromEntries(v))
```
</details>

- **Parameters**:
  - `v: Map<string, unknown>`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `null(): string`

<details><summary>Code</summary>

```ts
() => ''
```
</details>

- **Return Type**: `string`
### `array(v: unknown[]): string`

<details><summary>Code</summary>

```ts
(v: unknown[]) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: unknown[]`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `object(v: Record<string, unknown>): string`

<details><summary>Code</summary>

```ts
(v: Record<string, unknown>) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: Record<string, unknown>`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `set(v: Set<unknown>): string`

<details><summary>Code</summary>

```ts
(v: Set<unknown>) => JSON.stringify(Array.from(v))
```
</details>

- **Parameters**:
  - `v: Set<unknown>`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `map(v: Map<string, unknown>): string`

<details><summary>Code</summary>

```ts
(v: Map<string, unknown>) => JSON.stringify(Object.fromEntries(v))
```
</details>

- **Parameters**:
  - `v: Map<string, unknown>`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `null(): string`

<details><summary>Code</summary>

```ts
() => ''
```
</details>

- **Return Type**: `string`
### `array(v: unknown[]): string`

<details><summary>Code</summary>

```ts
(v: unknown[]) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: unknown[]`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `object(v: Record<string, unknown>): string`

<details><summary>Code</summary>

```ts
(v: Record<string, unknown>) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: Record<string, unknown>`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `set(v: Set<unknown>): string`

<details><summary>Code</summary>

```ts
(v: Set<unknown>) => JSON.stringify(Array.from(v))
```
</details>

- **Parameters**:
  - `v: Set<unknown>`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `map(v: Map<string, unknown>): string`

<details><summary>Code</summary>

```ts
(v: Map<string, unknown>) => JSON.stringify(Object.fromEntries(v))
```
</details>

- **Parameters**:
  - `v: Map<string, unknown>`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `null(): string`

<details><summary>Code</summary>

```ts
() => ''
```
</details>

- **Return Type**: `string`
### `getDefaultSerialization(target: T): ((v: unknown[]) => string) | ((v: Record<string, unknown>) => string) | ((v: Set<unknown>) => string) | ((v: Map<string, unknown>) => string)`

<details><summary>Code</summary>

```ts
export function getDefaultSerialization<T extends object>(target: T) {
  if (!target)
    return defaults.null

  if (target instanceof Map)
    return defaults.map
  else if (target instanceof Set)
    return defaults.set
  else if (Array.isArray(target))
    return defaults.array
  else
    return defaults.object
}
```
</details>

- **Parameters**:
  - `target: T`
- **Return Type**: `((v: unknown[]) => string) | ((v: Record<string, unknown>) => string) | ((v: Set<unknown>) => string) | ((v: Map<string, unknown>) => string)`
- **Calls**:
  - `Array.isArray`

---