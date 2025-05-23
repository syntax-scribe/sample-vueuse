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
- **Type Aliases**: 4

## 🛠️ File Location:
📂 **`packages/core/useElementSize/directive.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ObjectDirective` | `vue` |
| `ElementSize` | `./index` |
| `watch` | `vue` |
| `useElementSize` | `./index` |


---

## Functions

### `mounted(el: any, binding: any): void`

<details><summary>Code</summary>

```ts
mounted(el, binding) {
    const handler = typeof binding.value === 'function' ? binding.value : binding.value?.[0]
    const options = (typeof binding.value === 'function' ? [] : binding.value.slice(1)) as RemoveFirstFromTuple<BindingValueArray>

    const { width, height } = useElementSize(el, ...options)
    watch([width, height], ([width, height]) => handler({ width, height }))
  }
```
</details>

- **Parameters**:
  - `el: any`
  - `binding: any`
- **Return Type**: `void`
- **Calls**:
  - `binding.value.slice`
  - `useElementSize (from ./index)`
  - `watch (from vue)`
  - `handler`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `RemoveFirstFromTuple<T extends any[] extends any[]>`

```ts
type RemoveFirstFromTuple<T extends any[] extends any[]> = T['length'] extends 0 ? undefined :
      (((...b: T) => void) extends (a: any, ...b: infer I) => void ? I : []);
```

### `BindingValueFunction`

```ts
type BindingValueFunction = (size: ElementSize) => void;
```

### `VElementSizeOptions`

```ts
type VElementSizeOptions = RemoveFirstFromTuple<Parameters<typeof useElementSize>>;
```

### `BindingValueArray`

```ts
type BindingValueArray = [BindingValueFunction, ...VElementSizeOptions];
```


---