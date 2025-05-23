[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 4
- **Classes**: 0
- **Imports**: 5
- **Interfaces**: 0
- **Type Aliases**: 1

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `Falsy`

```ts
type Falsy = false | 0 | '' | null | undefined;
```


---