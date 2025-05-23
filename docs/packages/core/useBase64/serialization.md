[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `serialization.ts`

## 📚 Table of Contents

- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 16
- **Classes**: 0
- **Imports**: 0
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useBase64/serialization.ts`**

## 📦 Imports

> No imports found in this file.


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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---