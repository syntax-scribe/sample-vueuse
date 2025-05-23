[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 7
- **Interfaces**: 1
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/rxjs/useSubject/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Subject` | `rxjs` |
| `Ref` | `vue` |
| `UseObservableOptions` | `../useObservable` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `BehaviorSubject` | `rxjs` |
| `deepRef` | `vue` |
| `watch` | `vue` |


---

## Functions

### `useSubject(subject: BehaviorSubject<H>, options: UseSubjectOptions): Ref<H>`

<details><summary>Code</summary>

```ts
export function useSubject<H>(subject: BehaviorSubject<H>, options?: UseSubjectOptions): Ref<H>
```
</details>

- **Parameters**:
  - `subject: BehaviorSubject<H>`
  - `options: UseSubjectOptions`
- **Return Type**: `Ref<H>`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseSubjectOptions<I = undefined>`

<details><summary>Interface Code</summary>

```ts
export interface UseSubjectOptions<I = undefined> extends Omit<UseObservableOptions<I>, 'initialValue'> {
}
```
</details>


---

## Type Aliases

> No type aliases found in this file.


---