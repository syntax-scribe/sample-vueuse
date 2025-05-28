[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `value` | `Ref<H>` | const | `deepRef(
    subject instanceof BehaviorSubject
      ? subject.value
      : undefined,
  ) as typeof subject extends BehaviorSubject<H> ? Ref<H> : Ref<H | undefined>` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


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

## Interfaces

### `UseSubjectOptions<I = undefined>`

<details><summary>Interface Code</summary>

```ts
export interface UseSubjectOptions<I = undefined> extends Omit<UseObservableOptions<I>, 'initialValue'> {
}
```
</details>


---