[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `directive.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 4
- **Interfaces**: 0
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useElementHover/directive.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ObjectDirective` | `vue` |
| `UseElementHoverOptions` | `./index` |
| `watch` | `vue` |
| `useElementHover` | `./index` |


---

## Functions

### `mounted(el: any, binding: any): void`

<details><summary>Code</summary>

```ts
mounted(el, binding) {
    const value = binding.value
    if (typeof value === 'function') {
      const isHovered = useElementHover(el)
      watch(isHovered, v => value(v))
    }
    else {
      const [handler, options] = value
      const isHovered = useElementHover(el, options)
      watch(isHovered, v => handler(v))
    }
  }
```
</details>

- **Parameters**:
  - `el: any`
  - `binding: any`
- **Return Type**: `void`
- **Calls**:
  - `useElementHover (from ./index)`
  - `watch (from vue)`
  - `value`
  - `handler`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `BindingValueFunction`

```ts
type BindingValueFunction = (state: boolean) => void;
```


---