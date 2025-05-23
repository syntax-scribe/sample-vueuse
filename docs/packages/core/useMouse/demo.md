[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useMouse/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `UseMouseEventExtractor` | `@vueuse/core` |
| `reactify` | `@vueuse/core` |
| `useMouse` | `@vueuse/core` |
| `useParentElement` | `@vueuse/core` |
| `reactive` | `vue` |
| `YAML` | `yaml` |


---

## Functions

### `extractor(event: any): number[]`

<details><summary>Code</summary>

```ts
(event) => {
  if (event instanceof MouseEvent)
    return [event.offsetX, event.offsetY]
  else
    return null
}
```
</details>

- **Parameters**:
  - `event: any`
- **Return Type**: `number[]`

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