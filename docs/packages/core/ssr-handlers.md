[⬅️ Back to Table of Contents](../../index.md)

# 📄 `ssr-handlers.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 2
- **Interfaces**: 3
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/ssr-handlers.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Awaitable` | `@vueuse/shared` |
| `MaybeElementRef` | `./unrefElement` |


---

## Functions

### `getHandlers(): Partial<SSRHandlersMap>`

<details><summary>Code</summary>

```ts
function getHandlers() {
  if (!(globalKey in _global))
    // @ts-expect-error inject global
    _global[globalKey] = _global[globalKey] || {}
  // @ts-expect-error inject global
  return _global[globalKey] as Partial<SSRHandlersMap>
}
```
</details>

- **Return Type**: `Partial<SSRHandlersMap>`
- **Internal Comments**:
```
// @ts-expect-error inject global (x5)
```

### `getSSRHandler(key: T, fallback: SSRHandlersMap[T]): SSRHandlersMap[T]`

<details><summary>Code</summary>

```ts
export function getSSRHandler<T extends keyof SSRHandlersMap>(key: T, fallback: SSRHandlersMap[T]): SSRHandlersMap[T]
```
</details>

- **Parameters**:
  - `key: T`
  - `fallback: SSRHandlersMap[T]`
- **Return Type**: `SSRHandlersMap[T]`
### `setSSRHandler(key: T, fn: SSRHandlersMap[T]): void`

<details><summary>Code</summary>

```ts
export function setSSRHandler<T extends keyof SSRHandlersMap>(key: T, fn: SSRHandlersMap[T]) {
  handlers[key] = fn
}
```
</details>

- **Parameters**:
  - `key: T`
  - `fn: SSRHandlersMap[T]`
- **Return Type**: `void`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `StorageLikeAsync`

<details><summary>Interface Code</summary>

```ts
export interface StorageLikeAsync {
  getItem: (key: string) => Awaitable<string | null>
  setItem: (key: string, value: string) => Awaitable<void>
  removeItem: (key: string) => Awaitable<void>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `getItem` | `(key: string) => Awaitable<string | null>` | ✗ |  |
| `setItem` | `(key: string, value: string) => Awaitable<void>` | ✗ |  |
| `removeItem` | `(key: string) => Awaitable<void>` | ✗ |  |

### `StorageLike`

<details><summary>Interface Code</summary>

```ts
export interface StorageLike {
  getItem: (key: string) => string | null
  setItem: (key: string, value: string) => void
  removeItem: (key: string) => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `getItem` | `(key: string) => string | null` | ✗ |  |
| `setItem` | `(key: string, value: string) => void` | ✗ |  |
| `removeItem` | `(key: string) => void` | ✗ |  |

### `SSRHandlersMap`

<details><summary>Interface Code</summary>

```ts
export interface SSRHandlersMap {
  getDefaultStorage: () => StorageLike | undefined
  getDefaultStorageAsync: () => StorageLikeAsync | undefined
  updateHTMLAttrs: (selector: string | MaybeElementRef, attribute: string, value: string) => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `getDefaultStorage` | `() => StorageLike | undefined` | ✗ |  |
| `getDefaultStorageAsync` | `() => StorageLikeAsync | undefined` | ✗ |  |
| `updateHTMLAttrs` | `(selector: string | MaybeElementRef, attribute: string, value: string) => void` | ✗ |  |


---

## Type Aliases

> No type aliases found in this file.


---