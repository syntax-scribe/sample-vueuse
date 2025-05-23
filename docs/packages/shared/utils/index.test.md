[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Classes](#classes)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 2
- **Imports**: 27
- **Interfaces**: 0
- **Type Aliases**: 0

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

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---