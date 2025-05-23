[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `component.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 0
- **Classes**: 0
- **Imports**: 5
- **Interfaces**: 1
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useTimeAgo/component.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `UseTimeAgoOptions` | `@vueuse/core` |
| `MaybeRef` | `vue` |
| `useTimeAgo` | `@vueuse/core` |
| `defineComponent` | `vue` |
| `reactive` | `vue` |


---

## 🔧 Functions

> No functions found in this file.


---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseTimeAgoComponentOptions`

<details><summary>Interface Code</summary>

```ts
interface UseTimeAgoComponentOptions extends Omit<UseTimeAgoOptions<true>, 'controls'> {
  time: MaybeRef<Date | number | string>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `time` | `MaybeRef<Date | number | string>` | ✗ |  |


---

## Type Aliases

> No type aliases found in this file.


---