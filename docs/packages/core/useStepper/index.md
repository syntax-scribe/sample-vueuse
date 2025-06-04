[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 12 |
| 📦 Imports | 5 |
| 🟢 Vue Composition API | 6 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useStepper/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRef` | `vue` |
| `Ref` | `vue` |
| `computed` | `vue` |
| `deepRef` | `vue` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |


---

## Functions

### `useStepper(steps: MaybeRef<T[]>, initialStep: T): UseStepperReturn<T, T[], T>`

<details><summary>Code</summary>

```ts
export function useStepper<T extends string | number>(steps: MaybeRef<T[]>, initialStep?: T): UseStepperReturn<T, T[], T>
```
</details>

- **Parameters**:
  - `steps: MaybeRef<T[]>`
  - `initialStep: T`
- **Return Type**: `UseStepperReturn<T, T[], T>`
### `at(index: number): any`

<details><summary>Code</summary>

```ts
function at(index: number) {
    if (Array.isArray(stepsRef.value))
      return stepsRef.value[index]

    return stepsRef.value[stepNames.value[index]]
  }
```
</details>

- **Parameters**:
  - `index: number`
- **Return Type**: `any`
- **Calls**:
  - `Array.isArray`
### `get(step: any): any`

<details><summary>Code</summary>

```ts
function get(step: any) {
    if (!stepNames.value.includes(step))
      return

    return at(stepNames.value.indexOf(step))
  }
```
</details>

- **Parameters**:
  - `step: any`
- **Return Type**: `any`
- **Calls**:
  - `stepNames.value.includes`
  - `at`
  - `stepNames.value.indexOf`
### `goTo(step: any): void`

<details><summary>Code</summary>

```ts
function goTo(step: any) {
    if (stepNames.value.includes(step))
      index.value = stepNames.value.indexOf(step)
  }
```
</details>

- **Parameters**:
  - `step: any`
- **Return Type**: `void`
- **Calls**:
  - `stepNames.value.includes`
  - `stepNames.value.indexOf`
### `goToNext(): void`

<details><summary>Code</summary>

```ts
function goToNext() {
    if (isLast.value)
      return

    index.value++
  }
```
</details>

- **Return Type**: `void`
### `goToPrevious(): void`

<details><summary>Code</summary>

```ts
function goToPrevious() {
    if (isFirst.value)
      return

    index.value--
  }
```
</details>

- **Return Type**: `void`
### `goBackTo(step: any): void`

<details><summary>Code</summary>

```ts
function goBackTo(step: any) {
    if (isAfter(step))
      goTo(step)
  }
```
</details>

- **Parameters**:
  - `step: any`
- **Return Type**: `void`
- **Calls**:
  - `isAfter`
  - `goTo`
### `isNext(step: any): boolean`

<details><summary>Code</summary>

```ts
function isNext(step: any) {
    return stepNames.value.indexOf(step) === index.value + 1
  }
```
</details>

- **Parameters**:
  - `step: any`
- **Return Type**: `boolean`
- **Calls**:
  - `stepNames.value.indexOf`
### `isPrevious(step: any): boolean`

<details><summary>Code</summary>

```ts
function isPrevious(step: any) {
    return stepNames.value.indexOf(step) === index.value - 1
  }
```
</details>

- **Parameters**:
  - `step: any`
- **Return Type**: `boolean`
- **Calls**:
  - `stepNames.value.indexOf`
### `isCurrent(step: any): boolean`

<details><summary>Code</summary>

```ts
function isCurrent(step: any) {
    return stepNames.value.indexOf(step) === index.value
  }
```
</details>

- **Parameters**:
  - `step: any`
- **Return Type**: `boolean`
- **Calls**:
  - `stepNames.value.indexOf`
### `isBefore(step: any): boolean`

<details><summary>Code</summary>

```ts
function isBefore(step: any) {
    return index.value < stepNames.value.indexOf(step)
  }
```
</details>

- **Parameters**:
  - `step: any`
- **Return Type**: `boolean`
- **Calls**:
  - `stepNames.value.indexOf`
### `isAfter(step: any): boolean`

<details><summary>Code</summary>

```ts
function isAfter(step: any) {
    return index.value > stepNames.value.indexOf(step)
  }
```
</details>

- **Parameters**:
  - `step: any`
- **Return Type**: `boolean`
- **Calls**:
  - `stepNames.value.indexOf`

---

## Interfaces

### `UseStepperReturn<StepName, Steps, Step>`

<details><summary>Interface Code</summary>

```ts
export interface UseStepperReturn<StepName, Steps, Step> {
  /** List of steps. */
  steps: Readonly<Ref<Steps>>
  /** List of step names. */
  stepNames: Readonly<Ref<StepName[]>>
  /** Index of the current step. */
  index: Ref<number>
  /** Current step. */
  current: ComputedRef<Step>
  /** Next step, or undefined if the current step is the last one. */
  next: ComputedRef<StepName | undefined>
  /** Previous step, or undefined if the current step is the first one. */
  previous: ComputedRef<StepName | undefined>
  /** Whether the current step is the first one. */
  isFirst: ComputedRef<boolean>
  /** Whether the current step is the last one. */
  isLast: ComputedRef<boolean>
  /** Get the step at the specified index. */
  at: (index: number) => Step | undefined
  /** Get a step by the specified name. */
  get: (step: StepName) => Step | undefined
  /** Go to the specified step. */
  goTo: (step: StepName) => void
  /** Go to the next step. Does nothing if the current step is the last one. */
  goToNext: () => void
  /** Go to the previous step. Does nothing if the current step is the previous one. */
  goToPrevious: () => void
  /** Go back to the given step, only if the current step is after. */
  goBackTo: (step: StepName) => void
  /** Checks whether the given step is the next step. */
  isNext: (step: StepName) => boolean
  /** Checks whether the given step is the previous step. */
  isPrevious: (step: StepName) => boolean
  /** Checks whether the given step is the current step. */
  isCurrent: (step: StepName) => boolean
  /** Checks if the current step is before the given step. */
  isBefore: (step: StepName) => boolean
  /** Checks if the current step is after the given step. */
  isAfter: (step: StepName) => boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `steps` | `Readonly<Ref<Steps>>` | ✗ |  |
| `stepNames` | `Readonly<Ref<StepName[]>>` | ✗ |  |
| `index` | `Ref<number>` | ✗ |  |
| `current` | `ComputedRef<Step>` | ✗ |  |
| `next` | `ComputedRef<StepName | undefined>` | ✗ |  |
| `previous` | `ComputedRef<StepName | undefined>` | ✗ |  |
| `isFirst` | `ComputedRef<boolean>` | ✗ |  |
| `isLast` | `ComputedRef<boolean>` | ✗ |  |
| `at` | `(index: number) => Step | undefined` | ✗ |  |
| `get` | `(step: StepName) => Step | undefined` | ✗ |  |
| `goTo` | `(step: StepName) => void` | ✗ |  |
| `goToNext` | `() => void` | ✗ |  |
| `goToPrevious` | `() => void` | ✗ |  |
| `goBackTo` | `(step: StepName) => void` | ✗ |  |
| `isNext` | `(step: StepName) => boolean` | ✗ |  |
| `isPrevious` | `(step: StepName) => boolean` | ✗ |  |
| `isCurrent` | `(step: StepName) => boolean` | ✗ |  |
| `isBefore` | `(step: StepName) => boolean` | ✗ |  |
| `isAfter` | `(step: StepName) => boolean` | ✗ |  |


---