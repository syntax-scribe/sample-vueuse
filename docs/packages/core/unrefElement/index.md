[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 4
- **Interfaces**: 0
- **Type Aliases**: 5

## 🛠️ File Location:
📂 **`packages/core/unrefElement/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComponentPublicInstance` | `vue` |
| `MaybeRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `toValue` | `vue` |


---

## Functions

### `unrefElement(elRef: MaybeComputedElementRef<T>): UnRefElementReturn<T>`

<details><summary>Code</summary>

```ts
export function unrefElement<T extends MaybeElement>(elRef: MaybeComputedElementRef<T>): UnRefElementReturn<T> {
  const plain = toValue(elRef)
  return (plain as VueInstance)?.$el ?? plain
}
```
</details>

- **JSDoc**:
```ts
/**
 * Get the dom element of a ref of element or Vue component instance
 *
 * @param elRef
 */
```

- **Parameters**:
  - `elRef: MaybeComputedElementRef<T>`
- **Return Type**: `UnRefElementReturn<T>`
- **Calls**:
  - `toValue (from vue)`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `VueInstance`

```ts
type VueInstance = ComponentPublicInstance;
```

### `MaybeElementRef<T extends MaybeElement = MaybeElement extends MaybeElement = MaybeElement>`

```ts
type MaybeElementRef<T extends MaybeElement = MaybeElement extends MaybeElement = MaybeElement> = MaybeRef<T>;
```

### `MaybeComputedElementRef<T extends MaybeElement = MaybeElement extends MaybeElement = MaybeElement>`

```ts
type MaybeComputedElementRef<T extends MaybeElement = MaybeElement extends MaybeElement = MaybeElement> = MaybeRefOrGetter<T>;
```

### `MaybeElement`

```ts
type MaybeElement = HTMLElement | SVGElement | VueInstance | undefined | null;
```

### `UnRefElementReturn<T extends MaybeElement = MaybeElement extends MaybeElement = MaybeElement>`

```ts
type UnRefElementReturn<T extends MaybeElement = MaybeElement extends MaybeElement = MaybeElement> = T extends VueInstance ? Exclude<MaybeElement, VueInstance> : T | undefined;
```


---