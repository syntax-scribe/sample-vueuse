[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `directive.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 5
- **Interfaces**: 0
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/onClickOutside/directive.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Fn` | `@vueuse/shared` |
| `ObjectDirective` | `vue` |
| `OnClickOutsideHandler` | `./index` |
| `OnClickOutsideOptions` | `./index` |
| `onClickOutside` | `./index` |


---

## Functions

### `mounted(el: any, binding: any): void`

<details><summary>Code</summary>

```ts
mounted(el, binding) {
    const capture = !binding.modifiers.bubble
    let stop: StopHandle
    if (typeof binding.value === 'function') {
      stop = onClickOutside(el, binding.value, { capture })
    }
    else {
      const [handler, options] = binding.value
      stop = onClickOutside(el, handler, Object.assign({ capture }, options))
    }
    stopClickOutsideMap.set(el, stop)
  }
```
</details>

- **Parameters**:
  - `el: any`
  - `binding: any`
- **Return Type**: `void`
- **Calls**:
  - `onClickOutside (from ./index)`
  - `Object.assign`
  - `stopClickOutsideMap.set`
### `unmounted(el: any): void`

<details><summary>Code</summary>

```ts
unmounted(el) {
    const stop = stopClickOutsideMap.get(el)
    if (stop && typeof stop === 'function') {
      stop()
    }
    else {
      stop?.stop()
    }
    stopClickOutsideMap.delete(el)
  }
```
</details>

- **Parameters**:
  - `el: any`
- **Return Type**: `void`
- **Calls**:
  - `stopClickOutsideMap.get`
  - `stop`
  - `stop?.stop`
  - `stopClickOutsideMap.delete`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `StopHandle`

```ts
type StopHandle = Fn | { stop: Fn, cancel: Fn, trigger: (event: Event) => void };
```


---