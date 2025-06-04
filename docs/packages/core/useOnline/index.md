[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useOnline/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableWindow` | `../_configurable` |
| `useNetwork` | `../useNetwork` |


---

## Functions

### `useOnline(options: ConfigurableWindow): ShallowRef<boolean>`

<details><summary>Code</summary>

```ts
export function useOnline(options: ConfigurableWindow = {}) {
  const { isOnline } = useNetwork(options)
  return isOnline
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive online state.
 *
 * @see https://vueuse.org/useOnline
 * @param options
 */
```

- **Parameters**:
  - `options: ConfigurableWindow`
- **Return Type**: `ShallowRef<boolean>`
- **Calls**:
  - `useNetwork (from ../useNetwork)`

---