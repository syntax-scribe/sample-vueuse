[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `is.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 11 |
| 📊 Variables & Constants | 3 |

## 📚 Table of Contents

- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/shared/utils/is.ts`**

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `isClient` | `boolean` | const | `typeof window !== 'undefined' && typeof document !== 'undefined'` | ✓ |
| `isWorker` | `boolean` | const | `typeof WorkerGlobalScope !== 'undefined' && globalThis instanceof WorkerGlobalScope` | ✓ |
| `toString` | `() => string` | const | `Object.prototype.toString` | ✗ |


---

## Functions

### `isDef(val: T): val is T`

<details><summary>Code</summary>

```ts
<T = any>(val?: T): val is T => typeof val !== 'undefined'
```
</details>

- **Parameters**:
  - `val: T`
- **Return Type**: `val is T`
### `notNullish(val: T | null | undefined): val is T`

<details><summary>Code</summary>

```ts
<T = any>(val?: T | null | undefined): val is T => val != null
```
</details>

- **Parameters**:
  - `val: T | null | undefined`
- **Return Type**: `val is T`
### `assert(condition: boolean, infos: any[]): void`

<details><summary>Code</summary>

```ts
(condition: boolean, ...infos: any[]) => {
  if (!condition)
    console.warn(...infos)
}
```
</details>

- **Parameters**:
  - `condition: boolean`
  - `infos: any[]`
- **Return Type**: `void`
- **Calls**:
  - `console.warn`
### `isObject(val: any): val is object`

<details><summary>Code</summary>

```ts
(val: any): val is object =>
  toString.call(val) === '[object Object]'
```
</details>

- **Parameters**:
  - `val: any`
- **Return Type**: `val is object`
### `now(): number`

<details><summary>Code</summary>

```ts
() => Date.now()
```
</details>

- **Return Type**: `number`
- **Calls**:
  - `Date.now`
### `timestamp(): number`

<details><summary>Code</summary>

```ts
() => +Date.now()
```
</details>

- **Return Type**: `number`
### `clamp(n: number, min: number, max: number): number`

<details><summary>Code</summary>

```ts
(n: number, min: number, max: number) => Math.min(max, Math.max(min, n))
```
</details>

- **Parameters**:
  - `n: number`
  - `min: number`
  - `max: number`
- **Return Type**: `number`
- **Calls**:
  - `Math.min`
### `noop(): void`

<details><summary>Code</summary>

```ts
() => {}
```
</details>

- **Return Type**: `void`
### `rand(min: number, max: number): number`

<details><summary>Code</summary>

```ts
(min: number, max: number) => {
  min = Math.ceil(min)
  max = Math.floor(max)
  return Math.floor(Math.random() * (max - min + 1)) + min
}
```
</details>

- **Parameters**:
  - `min: number`
  - `max: number`
- **Return Type**: `number`
- **Calls**:
  - `Math.ceil`
  - `Math.floor`
  - `Math.random`
### `hasOwn(val: T, key: K): key is K`

<details><summary>Code</summary>

```ts
<T extends object, K extends keyof T>(val: T, key: K): key is K => Object.prototype.hasOwnProperty.call(val, key)
```
</details>

- **Parameters**:
  - `val: T`
  - `key: K`
- **Return Type**: `key is K`
- **Calls**:
  - `Object.prototype.hasOwnProperty.call`
### `getIsIOS(): boolean`

<details><summary>Code</summary>

```ts
function getIsIOS() {
  return isClient && window?.navigator?.userAgent && (
    (/iP(?:ad|hone|od)/.test(window.navigator.userAgent))
    // The new iPad Pro Gen3 does not identify itself as iPad, but as Macintosh.
    // https://github.com/vueuse/vueuse/issues/3577
    || (window?.navigator?.maxTouchPoints > 2 && /iPad|Macintosh/.test(window?.navigator.userAgent))
  )
}
```
</details>

- **Return Type**: `boolean`
- **Calls**:
  - `/iP(?:ad|hone|od)/.test`
  - `/iPad|Macintosh/.test`
- **Internal Comments**:
```
// The new iPad Pro Gen3 does not identify itself as iPad, but as Macintosh.
// https://github.com/vueuse/vueuse/issues/3577
```


---