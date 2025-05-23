[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 2
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/onElementRemoval/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `onElementRemoval` | `@vueuse/core` |
| `shallowRef` | `vue` |


---

## Functions

### `demo1BtnOnClick(): void`

<details><summary>Code</summary>

```ts
function demo1BtnOnClick() {
  demo1State.value = !demo1State.value
}
```
</details>

- **Return Type**: `void`
### `demo2BtnOnClick(): void`

<details><summary>Code</summary>

```ts
function demo2BtnOnClick() {
  demo2State.value = !demo2State.value
  if (demo2State.value) {
    demo2ParentRef.value?.appendChild(demo2Ref.value!)
  }
  else {
    demo2Ref.value?.remove()
  }
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `demo2ParentRef.value?.appendChild`
  - `demo2Ref.value?.remove`

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