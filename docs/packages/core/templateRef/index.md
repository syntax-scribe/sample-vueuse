[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/templateRef/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Component` | `vue` |
| `Ref` | `vue` |
| `tryOnMounted` | `@vueuse/shared` |
| `customRef` | `vue` |
| `getCurrentInstance` | `vue` |
| `onUpdated` | `vue` |


---

## Functions

### `templateRef(key: Keys, initialValue: T | null): Readonly<Ref<T>>`

<details><summary>Code</summary>

```ts
export function templateRef<T extends HTMLElement | SVGElement | Component | null, Keys extends string = string>(
  key: Keys,
  initialValue: T | null = null,
): Readonly<Ref<T>> {
  const instance = getCurrentInstance()
  let _trigger = () => {}

  const element = customRef((track, trigger) => {
    _trigger = trigger
    return {
      get() {
        track()
        return instance?.proxy?.$refs[key] ?? initialValue
      },
      set() {},
    }
  })

  tryOnMounted(_trigger)
  onUpdated(_trigger)

  return element as Readonly<Ref<T>>
}
```
</details>

- **JSDoc**:
```ts
/**
 * Shorthand for binding ref to template element.
 *
 * @see https://vueuse.org/templateRef
 * @param key
 * @param initialValue
 */
```

- **Parameters**:
  - `key: Keys`
  - `initialValue: T | null`
- **Return Type**: `Readonly<Ref<T>>`
- **Calls**:
  - `getCurrentInstance (from vue)`
  - `customRef (from vue)`
  - `track`
  - `tryOnMounted (from @vueuse/shared)`
  - `onUpdated (from vue)`
### `_trigger(): void`

<details><summary>Code</summary>

```ts
() => {}
```
</details>

- **Return Type**: `void`

---