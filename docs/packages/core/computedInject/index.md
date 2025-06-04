[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 1 |
| 🟢 Vue Composition API | 2 |
| 📐 Interfaces | 2 |
| 📑 Type Aliases | 3 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/computedInject/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `InjectionKey` | `vue` |
| `computed` | `vue` |
| `inject` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `source` | `T` | let/var | `inject(key) as T | undefined` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |


---

## Functions

### `computedInject(key: InjectionKey<T> | string, getter: ComputedInjectGetter<T, K>): ComputedRef<K | undefined>`

<details><summary>Code</summary>

```ts
export function computedInject<T, K = any>(
  key: InjectionKey<T> | string,
  getter: ComputedInjectGetter<T, K>
): ComputedRef<K | undefined>
```
</details>

- **Parameters**:
  - `key: InjectionKey<T> | string`
  - `getter: ComputedInjectGetter<T, K>`
- **Return Type**: `ComputedRef<K | undefined>`
### `get(ctx: any): K`

<details><summary>Code</summary>

```ts
ctx => options.get(source, ctx)
```
</details>

- **Parameters**:
  - `ctx: any`
- **Return Type**: `K`
- **Calls**:
  - `options.get`
### `get(ctx: any): K`

<details><summary>Code</summary>

```ts
ctx => options.get(source, ctx)
```
</details>

- **Parameters**:
  - `ctx: any`
- **Return Type**: `K`
- **Calls**:
  - `options.get`

---

## Interfaces

### `WritableComputedInjectOptions<T, K>`

<details><summary>Interface Code</summary>

```ts
export interface WritableComputedInjectOptions<T, K> {
  get: ComputedInjectGetter<T, K>
  set: ComputedInjectSetter<K>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `get` | `ComputedInjectGetter<T, K>` | ✗ |  |
| `set` | `ComputedInjectSetter<K>` | ✗ |  |

### `WritableComputedInjectOptionsWithDefault<T, K>`

<details><summary>Interface Code</summary>

```ts
export interface WritableComputedInjectOptionsWithDefault<T, K> {
  get: ComputedInjectGetterWithDefault<T, K>
  set: ComputedInjectSetter<K>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `get` | `ComputedInjectGetterWithDefault<T, K>` | ✗ |  |
| `set` | `ComputedInjectSetter<K>` | ✗ |  |


---

## Type Aliases

### `ComputedInjectGetter<T, K>`

```ts
type ComputedInjectGetter<T, K> = (source: T | undefined, ctx?: any) => K;
```

### `ComputedInjectGetterWithDefault<T, K>`

```ts
type ComputedInjectGetterWithDefault<T, K> = (source: T, ctx?: any) => K;
```

### `ComputedInjectSetter<T>`

```ts
type ComputedInjectSetter<T> = (v: T) => void;
```


---