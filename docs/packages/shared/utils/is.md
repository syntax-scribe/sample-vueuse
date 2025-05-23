[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `is.ts`

## 📚 Table of Contents

- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 11
- **Classes**: 0
- **Imports**: 0
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/shared/utils/is.ts`**

## 📦 Imports

> No imports found in this file.


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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---