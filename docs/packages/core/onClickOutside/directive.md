[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `directive.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 5 |
| 📊 Variables & Constants | 4 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `stopClickOutsideMap` | `WeakMap<HTMLElement, any>` | const | `new WeakMap<HTMLElement, StopHandle>()` | ✗ |
| `capture` | `boolean` | const | `!binding.modifiers.bubble` | ✗ |
| `stop` | `StopHandle` | let/var | `*not shown*` | ✗ |
| `vOnClickOutside` | `ObjectDirective<
  HTMLElement,
  OnClickOutsideHandler | [(evt: any) => void, Omit<OnClickOutsideOptions, 'controls'>]
>` | const | `{
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
  },
  unmounted(el) {
    const stop = stopClickOutsideMap.get(el)
    if (stop && typeof stop === 'function') {
      stop()
    }
    else {
      stop?.stop()
    }
    stopClickOutsideMap.delete(el)
  },
}` | ✓ |


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

## Type Aliases

### `StopHandle`

```ts
type StopHandle = Fn | { stop: Fn, cancel: Fn, trigger: (event: Event) => void };
```


---