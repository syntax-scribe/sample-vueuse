[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useWindowScroll/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableWindow` | `../_configurable` |
| `UseScrollOptions` | `../useScroll` |
| `defaultWindow` | `../_configurable` |
| `useScroll` | `../useScroll` |


---

## Functions

### `useWindowScroll(options: UseWindowScrollOptions): { x: any; y: any; isScrolling: any; arrivedState: any; directions: any; measure(): void; }`

<details><summary>Code</summary>

```ts
export function useWindowScroll(options: UseWindowScrollOptions = {}) {
  const { window = defaultWindow, ...rest } = options
  return useScroll(window, rest)
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive window scroll.
 *
 * @see https://vueuse.org/useWindowScroll
 * @param options
 */
```

- **Parameters**:
  - `options: UseWindowScrollOptions`
- **Return Type**: `{ x: any; y: any; isScrolling: any; arrivedState: any; directions: any; measure(): void; }`
- **Calls**:
  - `useScroll (from ../useScroll)`

---

## Interfaces

### `UseWindowScrollOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseWindowScrollOptions extends ConfigurableWindow, UseScrollOptions {
}
```
</details>


---

## Type Aliases

### `UseWindowScrollReturn`

```ts
type UseWindowScrollReturn = ReturnType<typeof useWindowScroll>;
```


---