[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 5
- **Interfaces**: 1
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/rxjs/useObservable/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Observable` | `rxjs` |
| `Ref` | `vue` |
| `UnwrapRef` | `vue` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `deepRef` | `vue` |


---

## Functions

### `useObservable(observable: Observable<H>, options: UseObservableOptions<I | undefined>): Readonly<Ref<H | I>>`

<details><summary>Code</summary>

```ts
export function useObservable<H, I = undefined>(
  observable: Observable<H>,
  options?: UseObservableOptions<I | undefined>,
): Readonly<Ref<H | I>> {
  const value = deepRef<H | I | undefined>(options?.initialValue)
  const subscription = observable.subscribe({
    next: val => (value.value = (val as UnwrapRef<H>)),
    error: options?.onError,
  })
  tryOnScopeDispose(() => {
    subscription.unsubscribe()
  })
  return value as Readonly<Ref<H | I>>
}
```
</details>

- **Parameters**:
  - `observable: Observable<H>`
  - `options: UseObservableOptions<I | undefined>`
- **Return Type**: `Readonly<Ref<H | I>>`
- **Calls**:
  - `deepRef (from vue)`
  - `observable.subscribe`
  - `tryOnScopeDispose (from @vueuse/shared)`
  - `subscription.unsubscribe`
### `next(val: any): UnwrapRef<H>`

<details><summary>Code</summary>

```ts
val => (value.value = (val as UnwrapRef<H>))
```
</details>

- **Parameters**:
  - `val: any`
- **Return Type**: `UnwrapRef<H>`
### `next(val: any): UnwrapRef<H>`

<details><summary>Code</summary>

```ts
val => (value.value = (val as UnwrapRef<H>))
```
</details>

- **Parameters**:
  - `val: any`
- **Return Type**: `UnwrapRef<H>`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseObservableOptions<I>`

<details><summary>Interface Code</summary>

```ts
export interface UseObservableOptions<I> {
  onError?: (err: any) => void
  /**
   * The value that should be set if the observable has not emitted.
   */
  initialValue?: I | undefined
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `onError` | `(err: any) => void` | ✓ |  |
| `initialValue` | `I | undefined` | ✓ |  |


---

## Type Aliases

> No type aliases found in this file.


---