[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 10
- **Interfaces**: 0
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---