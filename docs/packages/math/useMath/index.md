[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 3 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/math/useMath/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ArgumentsType` | `@vueuse/shared` |
| `Reactified` | `@vueuse/shared` |
| `reactify` | `@vueuse/shared` |


---

## Functions

### `useMath(key: K, args: ArgumentsType<Reactified<Math[K], true>>): ReturnType<Reactified<Math[K], true>>`

<details><summary>Code</summary>

```ts
export function useMath<K extends keyof Math>(
  key: K,
  ...args: ArgumentsType<Reactified<Math[K], true>>
): ReturnType<Reactified<Math[K], true>> {
  return reactify(Math[key] as any)(...args) as any
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive `Math` methods.
 *
 * @see https://vueuse.org/useMath
 */
```

- **Parameters**:
  - `key: K`
  - `args: ArgumentsType<Reactified<Math[K], true>>`
- **Return Type**: `ReturnType<Reactified<Math[K], true>>`
- **Calls**:
  - `complex_call_459`

---

## Type Aliases

### `UseMathKeys`

```ts
type UseMathKeys = keyof { [K in keyof Math as Math[K] extends (...args: any) => any ? K : never]: unknown };
```


---