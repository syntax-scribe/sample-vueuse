[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 12
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useCssVar/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `defaultWindow` | `@vueuse/core` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `defineComponent` | `vue` |
| `h` | `vue` |
| `nextTick` | `vue` |
| `onMounted` | `vue` |
| `shallowRef` | `vue` |
| `useTemplateRef` | `vue` |
| `mount` | `../../.test` |
| `useCssVar` | `./index` |


---

## Functions

### `switchTarget(): void`

<details><summary>Code</summary>

```ts
function switchTarget() {
          if (target.value === el.value)
            target.value = el2.value
          else
            target.value = el.value
        }
```
</details>

- **Return Type**: `void`
### `changeVar(): void`

<details><summary>Code</summary>

```ts
function changeVar() {
          if (key.value === '--color')
            key.value = '--color-one'
          else
            key.value = '--color'
        }
```
</details>

- **Return Type**: `void`

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