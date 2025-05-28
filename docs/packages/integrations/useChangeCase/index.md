[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 8 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 3 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 4 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/integrations/useChangeCase/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Options` | `change-case` |
| `ComputedRef` | `vue` |
| `MaybeRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `WritableComputedRef` | `vue` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `toValue` | `vue` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |


---

## Functions

### `useChangeCase(input: MaybeRef<string>, type: MaybeRefOrGetter<ChangeCaseType>, options: MaybeRefOrGetter<Options> | undefined): WritableComputedRef<string>`

<details><summary>Code</summary>

```ts
export function useChangeCase(input: MaybeRef<string>, type: MaybeRefOrGetter<ChangeCaseType>, options?: MaybeRefOrGetter<Options> | undefined): WritableComputedRef<string>
```
</details>

- **Parameters**:
  - `input: MaybeRef<string>`
  - `type: MaybeRefOrGetter<ChangeCaseType>`
  - `options: MaybeRefOrGetter<Options> | undefined`
- **Return Type**: `WritableComputedRef<string>`

---

## Type Aliases

### `EndsWithCase<T>`

```ts
type EndsWithCase<T> = T extends `${infer _}Case` ? T : never;
```

### `FilterKeys<T>`

```ts
type FilterKeys<T> = { [K in keyof T as K extends string ? K : never]: EndsWithCase<K> };
```

### `ChangeCaseKeys`

```ts
type ChangeCaseKeys = FilterKeys<typeof changeCase>;
```

### `ChangeCaseType`

```ts
type ChangeCaseType = ChangeCaseKeys[keyof ChangeCaseKeys];
```


---