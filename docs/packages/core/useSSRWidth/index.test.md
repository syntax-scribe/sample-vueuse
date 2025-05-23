[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 14
- **Classes**: 0
- **Imports**: 8
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useSSRWidth/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `mount` | `@vue/test-utils` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `createSSRApp` | `vue` |
| `h` | `vue` |
| `provideSSRWidth` | `./index` |
| `useSSRWidth` | `./index` |


---

## Functions

### `render(): string`

<details><summary>Code</summary>

```ts
() => ''
```
</details>

- **Return Type**: `string`
### `render(): string`

<details><summary>Code</summary>

```ts
() => ''
```
</details>

- **Return Type**: `string`
### `setup(): () => any`

<details><summary>Code</summary>

```ts
() => {
      provideSSRWidth(700)
      return () => h({ render: () => {
        return useSSRWidth()
      } })
    }
```
</details>

- **Return Type**: `() => any`
- **Calls**:
  - `provideSSRWidth (from ./index)`
  - `h (from vue)`
  - `useSSRWidth (from ./index)`
### `render(): number`

<details><summary>Code</summary>

```ts
() => {
        return useSSRWidth()
      }
```
</details>

- **Return Type**: `number`
- **Calls**:
  - `useSSRWidth (from ./index)`
### `render(): number`

<details><summary>Code</summary>

```ts
() => {
        return useSSRWidth()
      }
```
</details>

- **Return Type**: `number`
- **Calls**:
  - `useSSRWidth (from ./index)`
### `setup(): () => any`

<details><summary>Code</summary>

```ts
() => {
      provideSSRWidth(700)
      return () => h({ render: () => {
        return useSSRWidth()
      } })
    }
```
</details>

- **Return Type**: `() => any`
- **Calls**:
  - `provideSSRWidth (from ./index)`
  - `h (from vue)`
  - `useSSRWidth (from ./index)`
### `render(): number`

<details><summary>Code</summary>

```ts
() => {
        return useSSRWidth()
      }
```
</details>

- **Return Type**: `number`
- **Calls**:
  - `useSSRWidth (from ./index)`
### `render(): number`

<details><summary>Code</summary>

```ts
() => {
        return useSSRWidth()
      }
```
</details>

- **Return Type**: `number`
- **Calls**:
  - `useSSRWidth (from ./index)`
### `setup(): () => any`

<details><summary>Code</summary>

```ts
() => {
      provideSSRWidth(800)
      const ssrWidth = useSSRWidth()
      return () => h({ render: () => {
        return ssrWidth
      } })
    }
```
</details>

- **Return Type**: `() => any`
- **Calls**:
  - `provideSSRWidth (from ./index)`
  - `useSSRWidth (from ./index)`
  - `h (from vue)`
### `render(): number`

<details><summary>Code</summary>

```ts
() => {
        return ssrWidth
      }
```
</details>

- **Return Type**: `number`
### `render(): number`

<details><summary>Code</summary>

```ts
() => {
        return ssrWidth
      }
```
</details>

- **Return Type**: `number`
### `setup(): () => any`

<details><summary>Code</summary>

```ts
() => {
      provideSSRWidth(800)
      const ssrWidth = useSSRWidth()
      return () => h({ render: () => {
        return ssrWidth
      } })
    }
```
</details>

- **Return Type**: `() => any`
- **Calls**:
  - `provideSSRWidth (from ./index)`
  - `useSSRWidth (from ./index)`
  - `h (from vue)`
### `render(): number`

<details><summary>Code</summary>

```ts
() => {
        return ssrWidth
      }
```
</details>

- **Return Type**: `number`
### `render(): number`

<details><summary>Code</summary>

```ts
() => {
        return ssrWidth
      }
```
</details>

- **Return Type**: `number`

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