[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Classes](#classes)

## 📊 Analysis Summary

- **Functions**: 6
- **Classes**: 2
- **Imports**: 7
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useWakeLock/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `WakeLockSentinel` | `./index` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `nextTick` | `vue` |
| `useWakeLock` | `./index` |


---

## Functions

### `MockWakeLockSentinel.release(): Promise<void>`

<details><summary>Code</summary>

```ts
release() {
    this.released = true
    return Promise.resolve()
  }
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `Promise.resolve`
### `defineWakeLockAPI(): MockWakeLockSentinel`

<details><summary>Code</summary>

```ts
function defineWakeLockAPI() {
  const sentinel = new MockWakeLockSentinel()
  Object.defineProperty(navigator, 'wakeLock', {
    value: { request: async () => sentinel as WakeLockSentinel },
    writable: true,
  })
  return sentinel
}
```
</details>

- **Return Type**: `MockWakeLockSentinel`
- **Calls**:
  - `Object.defineProperty`
### `request(): Promise<WakeLockSentinel>`

<details><summary>Code</summary>

```ts
async () => sentinel as WakeLockSentinel
```
</details>

- **Return Type**: `Promise<WakeLockSentinel>`
### `request(): Promise<WakeLockSentinel>`

<details><summary>Code</summary>

```ts
async () => sentinel as WakeLockSentinel
```
</details>

- **Return Type**: `Promise<WakeLockSentinel>`
### `request(): Promise<WakeLockSentinel>`

<details><summary>Code</summary>

```ts
async () => sentinel as WakeLockSentinel
```
</details>

- **Return Type**: `Promise<WakeLockSentinel>`
### `request(): Promise<WakeLockSentinel>`

<details><summary>Code</summary>

```ts
async () => sentinel as WakeLockSentinel
```
</details>

- **Return Type**: `Promise<WakeLockSentinel>`

---

## Classes

### `MockWakeLockSentinel`

<details><summary>Class Code</summary>

```ts
class MockWakeLockSentinel extends EventTarget {
  released = false
  release() {
    this.released = true
    return Promise.resolve()
  }
}
```
</details>

#### Methods

##### `release(): Promise<void>`

<details><summary>Code</summary>

```ts
release() {
    this.released = true
    return Promise.resolve()
  }
```
</details>

### `MockDocument`

<details><summary>Class Code</summary>

```ts
class MockDocument extends EventTarget {
  visibilityState = 'hidden'
}
```
</details>


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---