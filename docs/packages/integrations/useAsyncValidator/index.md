[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 13
- **Interfaces**: 3
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/integrations/useAsyncValidator/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Rules` | `async-validator` |
| `ValidateError` | `async-validator` |
| `ValidateOption` | `async-validator` |
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `ShallowRef` | `vue` |
| `toRef` | `@vueuse/shared` |
| `until` | `@vueuse/shared` |
| `Schema` | `async-validator` |
| `computed` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |


---

## Functions

### `useAsyncValidator(value: MaybeRefOrGetter<Record<string, any>>, rules: MaybeRefOrGetter<Rules>, options: UseAsyncValidatorOptions): UseAsyncValidatorReturn & PromiseLike<UseAsyncValidatorReturn>`

<details><summary>Code</summary>

```ts
export function useAsyncValidator(
  value: MaybeRefOrGetter<Record<string, any>>,
  rules: MaybeRefOrGetter<Rules>,
  options: UseAsyncValidatorOptions = {},
): UseAsyncValidatorReturn & PromiseLike<UseAsyncValidatorReturn> {
  const {
    validateOption = {},
    immediate = true,
    manual = false,
  } = options

  const valueRef = toRef(value)

  const errorInfo = shallowRef<AsyncValidatorError | null>(null)
  const isFinished = shallowRef(true)
  const pass = shallowRef(!immediate || manual)
  const errors = computed(() => errorInfo.value?.errors || [])
  const errorFields = computed(() => errorInfo.value?.fields || {})

  const validator = computed(() => new AsyncValidatorSchema(toValue(rules)))

  const execute = async (): Promise<UseAsyncValidatorExecuteReturn> => {
    isFinished.value = false
    pass.value = false

    try {
      await validator.value.validate(valueRef.value, validateOption)
      pass.value = true
      errorInfo.value = null
    }
    catch (err) {
      errorInfo.value = err as AsyncValidatorError
    }
    finally {
      isFinished.value = true
    }

    return {
      pass: pass.value,
      errorInfo: errorInfo.value,
      errors: errors.value,
      errorFields: errorFields.value,
    }
  }

  if (!manual) {
    watch(
      [valueRef, validator],
      () => execute(),
      { immediate, deep: true },
    )
  }

  const shell = {
    isFinished,
    pass,
    errors,
    errorInfo,
    errorFields,
    execute,
  } as UseAsyncValidatorReturn

  function waitUntilFinished() {
    return new Promise<UseAsyncValidatorReturn>((resolve, reject) => {
      until(isFinished).toBe(true).then(() => resolve(shell)).catch(error => reject(error))
    })
  }

  return {
    ...shell,
    then(onFulfilled, onRejected) {
      return waitUntilFinished()
        .then(onFulfilled, onRejected)
    },
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Wrapper for async-validator.
 *
 * @see https://vueuse.org/useAsyncValidator
 * @see https://github.com/yiminghe/async-validator
 */
```

- **Parameters**:
  - `value: MaybeRefOrGetter<Record<string, any>>`
  - `rules: MaybeRefOrGetter<Rules>`
  - `options: UseAsyncValidatorOptions`
- **Return Type**: `UseAsyncValidatorReturn & PromiseLike<UseAsyncValidatorReturn>`
- **Calls**:
  - `toRef (from @vueuse/shared)`
  - `shallowRef (from vue)`
  - `computed (from vue)`
  - `toValue (from vue)`
  - `validator.value.validate`
  - `watch (from vue)`
  - `execute`
  - `until(isFinished).toBe(true).then(() => resolve(shell)).catch`
  - `reject`
  - `waitUntilFinished()
        .then`
### `execute(): Promise<UseAsyncValidatorExecuteReturn>`

<details><summary>Code</summary>

```ts
async (): Promise<UseAsyncValidatorExecuteReturn> => {
    isFinished.value = false
    pass.value = false

    try {
      await validator.value.validate(valueRef.value, validateOption)
      pass.value = true
      errorInfo.value = null
    }
    catch (err) {
      errorInfo.value = err as AsyncValidatorError
    }
    finally {
      isFinished.value = true
    }

    return {
      pass: pass.value,
      errorInfo: errorInfo.value,
      errors: errors.value,
      errorFields: errorFields.value,
    }
  }
```
</details>

- **Return Type**: `Promise<UseAsyncValidatorExecuteReturn>`
- **Calls**:
  - `validator.value.validate`
### `waitUntilFinished(): Promise<UseAsyncValidatorReturn>`

<details><summary>Code</summary>

```ts
function waitUntilFinished() {
    return new Promise<UseAsyncValidatorReturn>((resolve, reject) => {
      until(isFinished).toBe(true).then(() => resolve(shell)).catch(error => reject(error))
    })
  }
```
</details>

- **Return Type**: `Promise<UseAsyncValidatorReturn>`
- **Calls**:
  - `until(isFinished).toBe(true).then(() => resolve(shell)).catch`
  - `reject`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseAsyncValidatorExecuteReturn`

<details><summary>Interface Code</summary>

```ts
export interface UseAsyncValidatorExecuteReturn {
  pass: boolean
  errors: AsyncValidatorError['errors'] | undefined
  errorInfo: AsyncValidatorError | null
  errorFields: AsyncValidatorError['fields'] | undefined
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `pass` | `boolean` | ✗ |  |
| `errors` | `AsyncValidatorError['errors'] | undefined` | ✗ |  |
| `errorInfo` | `AsyncValidatorError | null` | ✗ |  |
| `errorFields` | `AsyncValidatorError['fields'] | undefined` | ✗ |  |

### `UseAsyncValidatorReturn`

<details><summary>Interface Code</summary>

```ts
export interface UseAsyncValidatorReturn {
  pass: ShallowRef<boolean>
  isFinished: ShallowRef<boolean>
  errors: ComputedRef<AsyncValidatorError['errors'] | undefined>
  errorInfo: ShallowRef<AsyncValidatorError | null>
  errorFields: ComputedRef<AsyncValidatorError['fields'] | undefined>
  execute: () => Promise<UseAsyncValidatorExecuteReturn>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `pass` | `ShallowRef<boolean>` | ✗ |  |
| `isFinished` | `ShallowRef<boolean>` | ✗ |  |
| `errors` | `ComputedRef<AsyncValidatorError['errors'] | undefined>` | ✗ |  |
| `errorInfo` | `ShallowRef<AsyncValidatorError | null>` | ✗ |  |
| `errorFields` | `ComputedRef<AsyncValidatorError['fields'] | undefined>` | ✗ |  |
| `execute` | `() => Promise<UseAsyncValidatorExecuteReturn>` | ✗ |  |

### `UseAsyncValidatorOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseAsyncValidatorOptions {
  /**
   * @see https://github.com/yiminghe/async-validator#options
   */
  validateOption?: ValidateOption
  /**
   * The validation will be triggered right away for the first time.
   * Only works when `manual` is not set to true.
   *
   * @default true
   */
  immediate?: boolean
  /**
   * If set to true, the validation will not be triggered automatically.
   */
  manual?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `validateOption` | `ValidateOption` | ✓ |  |
| `immediate` | `boolean` | ✓ |  |
| `manual` | `boolean` | ✓ |  |


---

## Type Aliases

### `AsyncValidatorError`

```ts
type AsyncValidatorError = Error & {
  errors: ValidateError[]
  fields: Record<string, ValidateError[]>
};
```


---