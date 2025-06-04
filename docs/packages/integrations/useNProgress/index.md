[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 11 |
| 📦 Imports | 8 |
| 📊 Variables & Constants | 1 |
| 🟢 Vue Composition API | 1 |
| 📑 Type Aliases | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/integrations/useNProgress/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `NProgressOptions` | `nprogress` |
| `MaybeRefOrGetter` | `vue` |
| `isClient` | `@vueuse/shared` |
| `toRef` | `@vueuse/shared` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `nprogress` | `nprogress` |
| `computed` | `vue` |
| `watchEffect` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `setProgress` | `any` | const | `nprogress.set` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `useNProgress(currentProgress: MaybeRefOrGetter<number | null | undefined>, options: UseNProgressOptions): { isLoading: any; progress: any; start: any; done: any; remove: () => void; }`

<details><summary>Code</summary>

```ts
export function useNProgress(
  currentProgress: MaybeRefOrGetter<number | null | undefined> = null,
  options?: UseNProgressOptions,
) {
  const progress = toRef(currentProgress)
  const isLoading = computed({
    set: load => load ? nprogress.start() : nprogress.done(),
    get: () => typeof progress.value === 'number' && progress.value < 1,
  })

  if (options)
    nprogress.configure(options)

  const setProgress = nprogress.set
  nprogress.set = (n: number) => {
    progress.value = n
    return setProgress.call(nprogress, n)
  }

  watchEffect(() => {
    if (typeof progress.value === 'number' && isClient)
      setProgress.call(nprogress, progress.value)
  })

  tryOnScopeDispose(nprogress.remove)

  return {
    isLoading,
    progress,
    start: nprogress.start,
    done: nprogress.done,
    remove: () => {
      progress.value = null
      nprogress.remove()
    },
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive progress bar.
 *
 * @see https://vueuse.org/useNProgress
 */
```

- **Parameters**:
  - `currentProgress: MaybeRefOrGetter<number | null | undefined>`
  - `options: UseNProgressOptions`
- **Return Type**: `{ isLoading: any; progress: any; start: any; done: any; remove: () => void; }`
- **Calls**:
  - `toRef (from @vueuse/shared)`
  - `computed (from vue)`
  - `nprogress.start`
  - `nprogress.done`
  - `nprogress.configure`
  - `setProgress.call`
  - `watchEffect (from vue)`
  - `tryOnScopeDispose (from @vueuse/shared)`
  - `nprogress.remove`
### `set(load: any): any`

<details><summary>Code</summary>

```ts
load => load ? nprogress.start() : nprogress.done()
```
</details>

- **Parameters**:
  - `load: any`
- **Return Type**: `any`
### `get(): boolean`

<details><summary>Code</summary>

```ts
() => typeof progress.value === 'number' && progress.value < 1
```
</details>

- **Return Type**: `boolean`
### `set(load: any): any`

<details><summary>Code</summary>

```ts
load => load ? nprogress.start() : nprogress.done()
```
</details>

- **Parameters**:
  - `load: any`
- **Return Type**: `any`
### `get(): boolean`

<details><summary>Code</summary>

```ts
() => typeof progress.value === 'number' && progress.value < 1
```
</details>

- **Return Type**: `boolean`
### `set(load: any): any`

<details><summary>Code</summary>

```ts
load => load ? nprogress.start() : nprogress.done()
```
</details>

- **Parameters**:
  - `load: any`
- **Return Type**: `any`
### `get(): boolean`

<details><summary>Code</summary>

```ts
() => typeof progress.value === 'number' && progress.value < 1
```
</details>

- **Return Type**: `boolean`
### `set(load: any): any`

<details><summary>Code</summary>

```ts
load => load ? nprogress.start() : nprogress.done()
```
</details>

- **Parameters**:
  - `load: any`
- **Return Type**: `any`
### `get(): boolean`

<details><summary>Code</summary>

```ts
() => typeof progress.value === 'number' && progress.value < 1
```
</details>

- **Return Type**: `boolean`
### `remove(): void`

<details><summary>Code</summary>

```ts
() => {
      progress.value = null
      nprogress.remove()
    }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `nprogress.remove`
### `remove(): void`

<details><summary>Code</summary>

```ts
() => {
      progress.value = null
      nprogress.remove()
    }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `nprogress.remove`

---

## Type Aliases

### `UseNProgressOptions`

```ts
type UseNProgressOptions = Partial<NProgressOptions>;
```

### `UseNProgressReturn`

```ts
type UseNProgressReturn = ReturnType<typeof useNProgress>;
```


---