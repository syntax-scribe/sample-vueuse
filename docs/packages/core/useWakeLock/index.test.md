[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 6 |
| 🧱 Classes | 2 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 4 |
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
- [Classes](#classes)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `sentinel` | `MockWakeLockSentinel` | const | `new MockWakeLockSentinel()` | ✗ |
| `mockDocument` | `MockDocument` | let/var | `new MockDocument()` | ✗ |
| `mockDocument` | `MockDocument` | let/var | `new MockDocument()` | ✗ |
| `mockDocument` | `MockDocument` | let/var | `new MockDocument()` | ✗ |


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