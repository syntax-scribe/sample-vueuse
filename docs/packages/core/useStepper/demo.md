[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 18
- **Classes**: 0
- **Imports**: 2
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useStepper/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useStepper` | `@vueuse/core` |
| `reactive` | `vue` |


---

## Functions

### `isValid(): any`

<details><summary>Code</summary>

```ts
() => form.firstName && form.lastName
```
</details>

- **Return Type**: `any`
### `isValid(): any`

<details><summary>Code</summary>

```ts
() => form.firstName && form.lastName
```
</details>

- **Return Type**: `any`
### `isValid(): boolean`

<details><summary>Code</summary>

```ts
() => form.billingAddress?.trim() !== ''
```
</details>

- **Return Type**: `boolean`
### `isValid(): boolean`

<details><summary>Code</summary>

```ts
() => form.billingAddress?.trim() !== ''
```
</details>

- **Return Type**: `boolean`
### `isValid(): boolean`

<details><summary>Code</summary>

```ts
() => form.contractAccepted === true
```
</details>

- **Return Type**: `boolean`
### `isValid(): boolean`

<details><summary>Code</summary>

```ts
() => form.contractAccepted === true
```
</details>

- **Return Type**: `boolean`
### `isValid(): boolean`

<details><summary>Code</summary>

```ts
() => ['credit-card', 'paypal'].includes(form.payment)
```
</details>

- **Return Type**: `boolean`
- **Calls**:
  - `['credit-card', 'paypal'].includes`
### `isValid(): boolean`

<details><summary>Code</summary>

```ts
() => ['credit-card', 'paypal'].includes(form.payment)
```
</details>

- **Return Type**: `boolean`
- **Calls**:
  - `['credit-card', 'paypal'].includes`
### `isValid(): any`

<details><summary>Code</summary>

```ts
() => form.firstName && form.lastName
```
</details>

- **Return Type**: `any`
### `isValid(): any`

<details><summary>Code</summary>

```ts
() => form.firstName && form.lastName
```
</details>

- **Return Type**: `any`
### `isValid(): boolean`

<details><summary>Code</summary>

```ts
() => form.billingAddress?.trim() !== ''
```
</details>

- **Return Type**: `boolean`
### `isValid(): boolean`

<details><summary>Code</summary>

```ts
() => form.billingAddress?.trim() !== ''
```
</details>

- **Return Type**: `boolean`
### `isValid(): boolean`

<details><summary>Code</summary>

```ts
() => form.contractAccepted === true
```
</details>

- **Return Type**: `boolean`
### `isValid(): boolean`

<details><summary>Code</summary>

```ts
() => form.contractAccepted === true
```
</details>

- **Return Type**: `boolean`
### `isValid(): boolean`

<details><summary>Code</summary>

```ts
() => ['credit-card', 'paypal'].includes(form.payment)
```
</details>

- **Return Type**: `boolean`
- **Calls**:
  - `['credit-card', 'paypal'].includes`
### `isValid(): boolean`

<details><summary>Code</summary>

```ts
() => ['credit-card', 'paypal'].includes(form.payment)
```
</details>

- **Return Type**: `boolean`
- **Calls**:
  - `['credit-card', 'paypal'].includes`
### `submit(): void`

<details><summary>Code</summary>

```ts
function submit() {
  if (stepper.current.value.isValid())
    stepper.goToNext()
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `stepper.current.value.isValid`
  - `stepper.goToNext`
### `allStepsBeforeAreValid(index: number): boolean`

<details><summary>Code</summary>

```ts
function allStepsBeforeAreValid(index: number): boolean {
  return !Array.from({ length: index }, () => null)
    .some((_, i) => !stepper.at(i)?.isValid())
}
```
</details>

- **Parameters**:
  - `index: number`
- **Return Type**: `boolean`
- **Calls**:
  - `Array.from({ length: index }, () => null)
    .some`
  - `stepper.at(i)?.isValid`

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