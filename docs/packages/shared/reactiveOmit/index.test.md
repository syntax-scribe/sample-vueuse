[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 📦 Imports | 5 |
| 🟢 Vue Composition API | 2 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/shared/reactiveOmit/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `reactive` | `vue` |
| `reactiveOmit` | `./index` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `reactive` | reactive | *none* | *none* |
| `reactive` | reactive | *none* | *none* |


---

## Interfaces

### `TargetObject`

<details><summary>Interface Code</summary>

```ts
interface TargetObject {
  foo: string
  bar: string
  baz?: string
  qux?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `foo` | `string` | ✗ |  |
| `bar` | `string` | ✗ |  |
| `baz` | `string` | ✓ |  |
| `qux` | `boolean` | ✓ |  |


---