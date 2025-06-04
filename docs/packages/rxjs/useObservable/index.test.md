[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 📦 Imports | 8 |
| 📊 Variables & Constants | 2 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/rxjs/useObservable/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Observable` | `rxjs` |
| `BehaviorSubject` | `rxjs` |
| `delay` | `rxjs/operators` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `useObservable` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `testDataSource` | `BehaviorSubject<TestPerson>` | let/var | `*not shown*` | ✗ |
| `delayedEmissionStream` | `Observable<TestPerson>` | let/var | `*not shown*` | ✗ |


---

## Interfaces

### `TestPerson`

<details><summary>Interface Code</summary>

```ts
interface TestPerson {
  fullName: string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `fullName` | `string` | ✗ |  |


---