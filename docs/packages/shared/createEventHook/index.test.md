[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 📦 Imports | 5 |
| 📊 Variables & Constants | 10 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/createEventHook/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `createEventHook` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `message` | `string` | let/var | `''` | ✗ |
| `timesFired` | `number` | let/var | `0` | ✗ |
| `timesFired` | `number` | let/var | `0` | ✗ |
| `values` | `Falsy[]` | const | `[false, 0, '', null, undefined]` | ✗ |
| `results` | `Falsy[]` | const | `[]` | ✗ |
| `message` | `string` | let/var | `''` | ✗ |
| `result` | `unknown[]` | let/var | `await exec()` | ✗ |
| `count` | `number` | let/var | `0` | ✗ |
| `id` | `string` | let/var | `''` | ✗ |
| `list` | `unknown[]` | const | `[]` | ✗ |


---

## Functions

### `myFunction(): { exec: () => Promise<unknown[]>; onResult: EventHookOn<string>; }`

<details><summary>Code</summary>

```ts
() => {
      const resultEvent = createEventHook<string>()
      const exec = () => resultEvent.trigger('Hello World')
      return {
        exec,
        onResult: resultEvent.on,
      }
    }
```
</details>

- **Return Type**: `{ exec: () => Promise<unknown[]>; onResult: EventHookOn<string>; }`
- **Calls**:
  - `createEventHook (from ./index)`
  - `resultEvent.trigger`
### `exec(): Promise<unknown[]>`

<details><summary>Code</summary>

```ts
() => resultEvent.trigger('Hello World')
```
</details>

- **Return Type**: `Promise<unknown[]>`
- **Calls**:
  - `resultEvent.trigger`
### `myFunction(): { exec: () => Promise<unknown[]>; onResult: EventHookOn<string>; }`

<details><summary>Code</summary>

```ts
() => {
      const resultEvent = createEventHook<string>()
      const exec = () => resultEvent.trigger('Hello World')
      return {
        exec,
        onResult: resultEvent.on,
      }
    }
```
</details>

- **Return Type**: `{ exec: () => Promise<unknown[]>; onResult: EventHookOn<string>; }`
- **Calls**:
  - `createEventHook (from ./index)`
  - `resultEvent.trigger`
### `exec(): Promise<unknown[]>`

<details><summary>Code</summary>

```ts
() => resultEvent.trigger('Hello World')
```
</details>

- **Return Type**: `Promise<unknown[]>`
- **Calls**:
  - `resultEvent.trigger`

---

## Type Aliases

### `Falsy`

```ts
type Falsy = false | 0 | '' | null | undefined;
```


---