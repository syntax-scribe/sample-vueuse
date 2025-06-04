[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 5 |
| 📦 Imports | 15 |
| 📊 Variables & Constants | 5 |
| 🟢 Vue Composition API | 3 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/rxjs/useExtractedObservable/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `BehaviorSubject` | `rxjs` |
| `of` | `rxjs` |
| `Subject` | `rxjs` |
| `delay` | `rxjs/operators` |
| `endWith` | `rxjs/operators` |
| `tap` | `rxjs/operators` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `deepRef` | `vue` |
| `nextTick` | `vue` |
| `reactive` | `vue` |
| `shallowRef` | `vue` |
| `useExtractedObservable` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `obs` | `any` | const | `new Subject<number>()` | ✗ |
| `obs` | `any` | let/var | `new Subject<number>()` | ✗ |
| `obs` | `any` | let/var | `new Subject<number>()` | ✗ |
| `obs` | `any` | let/var | `new BehaviorSubject(16)` | ✗ |
| `error` | `Error` | let/var | `new Error('Odd number')` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `reactive` | reactive | *none* | *none* |
| `reactive` | reactive | *none* | *none* |
| `reactive` | reactive | *none* | *none* |


---

## Functions

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
([abc, def]: [string, string]) => of(`${abc}${def}`)
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