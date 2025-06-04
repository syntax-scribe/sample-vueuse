[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 6 |
| 🧱 Classes | 1 |
| 📦 Imports | 21 |
| 📊 Variables & Constants | 5 |
| 🟢 Vue Composition API | 4 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Classes](#classes)

## 🛠️ File Location:
📂 **`packages/rxjs/watchExtractedObservable/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Observable` | `rxjs` |
| `Subject` | `rxjs` |
| `MockedFunction` | `vitest` |
| `ComputedRef` | `vue` |
| `Ref` | `vue` |
| `BehaviorSubject` | `rxjs` |
| `of` | `rxjs` |
| `delay` | `rxjs/operators` |
| `map` | `rxjs/operators` |
| `tap` | `rxjs/operators` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `nextTick` | `vue` |
| `reactive` | `vue` |
| `shallowRef` | `vue` |
| `watchExtractedObservable` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `numRef` | `Ref<number | undefined>` | let/var | `*not shown*` | ✗ |
| `obj` | `ComputedRef<TestWrapper | null>` | let/var | `*not shown*` | ✗ |
| `extractor` | `MockedFunction<(wrapper: TestWrapper) => Observable<number>>` | let/var | `*not shown*` | ✗ |
| `callback` | `MockedFunction<(num: number) => void>` | let/var | `*not shown*` | ✗ |
| `error` | `Error` | let/var | `new Error('Odd number')` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `reactive` | reactive | *none* | *none* |
| `reactive` | reactive | *none* | *none* |
| `reactive` | reactive | *none* | *none* |


---

## Functions

### `TestWrapper.incr(): void`

<details><summary>Code</summary>

```ts
incr() {
    this.obs$.next(++this.num)
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `this.obs$.next`
### `extractor(num: number): any`

<details><summary>Code</summary>

```ts
(num: number) => of(num).pipe(
        tap((n: number) => {
          if (n % 2 === 1)
            throw error
        }),
      )
```
</details>

- **Parameters**:
  - `num: number`
- **Return Type**: `any`
- **Calls**:
  - `of(num).pipe`
### `extractor(args: unknown[]): any`

<details><summary>Code</summary>

```ts
(args: unknown[]) => of(...args)
```
</details>

- **Parameters**:
  - `args: unknown[]`
- **Return Type**: `any`
- **Calls**:
  - `of (from rxjs)`
### `extractor(arr: unknown[]): any`

<details><summary>Code</summary>

```ts
(arr: unknown[]) => of(...arr).pipe(
        delay(1000),
        map(() => 42),
      )
```
</details>

- **Parameters**:
  - `arr: unknown[]`
- **Return Type**: `any`
- **Calls**:
  - `of(...arr).pipe`
### `extractor([abc, def]: [string, string]): any`

<details><summary>Code</summary>

```ts
([abc, def]: [string, string]) => of([abc, def])
```
</details>

- **Parameters**:
  - `[abc, def]: [string, string]`
- **Return Type**: `any`
- **Calls**:
  - `of (from rxjs)`
### `extractor(source: typeof obj): any`

<details><summary>Code</summary>

```ts
(source: typeof obj) => of(`x: ${source.x}, y: ${source.y}, z: ${source.z}`)
```
</details>

- **Parameters**:
  - `source: typeof obj`
- **Return Type**: `any`
- **Calls**:
  - `of (from rxjs)`

---

## Classes

### `TestWrapper`

<details><summary>Class Code</summary>

```ts
class TestWrapper {
  public readonly obs$: Subject<number>

  constructor(private num: number) {
    this.obs$ = new BehaviorSubject<number>(num)
  }

  incr() {
    this.obs$.next(++this.num)
  }
}
```
</details>

#### Methods

##### `incr(): void`

<details><summary>Code</summary>

```ts
incr() {
    this.obs$.next(++this.num)
  }
```
</details>


---