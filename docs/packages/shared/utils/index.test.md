[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 🧱 Classes | 2 |
| 📦 Imports | 27 |
| 📊 Variables & Constants | 7 |
| ⚡ Async/Await Patterns | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)
- [Classes](#classes)

## 🛠️ File Location:
📂 **`packages/shared/utils/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MockInstance` | `vitest` |
| `afterEach` | `vitest` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `shallowRef` | `vue` |
| `createSingletonPromise` | `./general` |
| `increaseWithUnit` | `./general` |
| `objectOmit` | `./general` |
| `objectPick` | `./general` |
| `promiseTimeout` | `./general` |
| `assert` | `./index` |
| `clamp` | `./index` |
| `createFilterWrapper` | `./index` |
| `debounceFilter` | `./index` |
| `hasOwn` | `./index` |
| `isClient` | `./index` |
| `isDef` | `./index` |
| `isIOS` | `./index` |
| `isObject` | `./index` |
| `noop` | `./index` |
| `now` | `./index` |
| `rand` | `./index` |
| `throttleFilter` | `./index` |
| `timestamp` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `obj` | `{ a: number; b: number; c: number; }` | const | `{ a: 1, b: 2, c: 3 }` | ✗ |
| `value` | `number` | let/var | `await promise1` | ✗ |
| `nine` | `any` | let/var | `*not shown*` | ✗ |
| `warnSpy` | `MockInstance` | let/var | `*not shown*` | ✗ |
| `obj1` | `any` | const | `{ a: 1 } as any` | ✗ |
| `obj2` | `any` | const | `new Child() as any` | ✗ |
| `obj3` | `any` | const | `new F() as any` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| promise-chain | `createPromise` | *none* | Promise.resolve |
| promise-chain | `createPromise` | *none* | Promise.resolve(0).then, Promise.resolve |


---

## Functions

### `createPromise(): Promise<number>`

<details><summary>Code</summary>

```ts
() => Promise.resolve(0)
```
</details>

- **Return Type**: `Promise<number>`
- **Calls**:
  - `Promise.resolve`
### `createPromise(): Promise<number>`

<details><summary>Code</summary>

```ts
() => Promise.resolve(0).then(cb)
```
</details>

- **Return Type**: `Promise<number>`
- **Calls**:
  - `Promise.resolve(0).then`
### `F(): void`

<details><summary>Code</summary>

```ts
function F() {}
```
</details>

- **Return Type**: `void`

---

## Classes

### `Parent`

<details><summary>Class Code</summary>

```ts
class Parent {a = 1}
```
</details>

### `Child`

<details><summary>Class Code</summary>

```ts
class Child extends Parent {}
```
</details>


---