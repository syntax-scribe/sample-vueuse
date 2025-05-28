[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 2 |
| 📊 Variables & Constants | 0 |
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
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/createUnrefFn/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRef` | `vue` |
| `toValue` | `vue` |


---

## Functions

### `createUnrefFn(fn: T): UnrefFn<T>`

<details><summary>Code</summary>

```ts
export function createUnrefFn<T extends Function>(fn: T): UnrefFn<T> {
  return function (this: any, ...args: any[]) {
    return fn.apply(this, args.map(i => toValue(i)))
  } as UnrefFn<T>
}
```
</details>

- **JSDoc**:
```ts
/**
 * Make a plain function accepting ref and raw values as arguments.
 * Returns the same value the unconverted function returns, with proper typing.
 */
```

- **Parameters**:
  - `fn: T`
- **Return Type**: `UnrefFn<T>`
- **Calls**:
  - `fn.apply`
  - `args.map`
  - `toValue (from vue)`

---

## Type Aliases

### `UnrefFn<T>`

```ts
type UnrefFn<T> = T extends (...args: infer A) => infer R
  ? (...args: { [K in keyof A]: MaybeRef<A[K]> }) => R
  : never;
```


---