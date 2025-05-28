[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 10 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 2 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/rxjs/from/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ObservableInput` | `rxjs` |
| `Subscription` | `rxjs` |
| `MaybeRef` | `vue` |
| `Ref` | `vue` |
| `WatchOptions` | `vue` |
| `fromEventRx` | `rxjs` |
| `fromRxjs` | `rxjs` |
| `Observable` | `rxjs` |
| `isRef` | `vue` |
| `watch` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `innerSub` | `Subscription | undefined` | let/var | `*not shown*` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |
| `watch` | watch | *none* | *none* |


---

## Functions

### `from(value: ObservableInput<T> | Ref<T>, watchOptions: WatchOptions): Observable<T>`

<details><summary>Code</summary>

```ts
export function from<T>(value: ObservableInput<T> | Ref<T>, watchOptions?: WatchOptions): Observable<T> {
  if (isRef<T>(value))
    return new Observable(subscriber => watch(value, val => subscriber.next(val), watchOptions))

  return fromRxjs(value)
}
```
</details>

- **Parameters**:
  - `value: ObservableInput<T> | Ref<T>`
  - `watchOptions: WatchOptions`
- **Return Type**: `Observable<T>`
- **Calls**:
  - `isRef (from vue)`
  - `watch (from vue)`
  - `subscriber.next`
  - `fromRxjs (from rxjs)`
### `fromEvent(value: MaybeRef<T>, event: string): Observable<Event>`

<details><summary>Code</summary>

```ts
export function fromEvent<T extends HTMLElement | null>(value: MaybeRef<T>, event: string): Observable<Event> {
  if (isRef<T>(value)) {
    return new Observable((subscriber) => {
      let innerSub: Subscription | undefined
      return watch(value, (element) => {
        innerSub?.unsubscribe()
        if (element instanceof HTMLElement) {
          innerSub = fromEventRx(element, event).subscribe(subscriber)
          subscriber.add(innerSub)
        }
      }, { immediate: true })
    })
  }
  if (value === null) {
    throw new Error('The value is `null`, and it should be an HTMLElement.')
  }
  return fromEventRx(value, event)
}
```
</details>

- **Parameters**:
  - `value: MaybeRef<T>`
  - `event: string`
- **Return Type**: `Observable<Event>`
- **Calls**:
  - `isRef (from vue)`
  - `watch (from vue)`
  - `innerSub?.unsubscribe`
  - `fromEventRx(element, event).subscribe`
  - `subscriber.add`
  - `fromEventRx (from rxjs)`

---