[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 4
- **Classes**: 0
- **Imports**: 8
- **Interfaces**: 1
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useConfirmDialog/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `EventHook` | `@vueuse/shared` |
| `EventHookOn` | `@vueuse/shared` |
| `ComputedRef` | `vue` |
| `ShallowRef` | `vue` |
| `createEventHook` | `@vueuse/shared` |
| `noop` | `@vueuse/shared` |
| `computed` | `vue` |
| `shallowRef` | `vue` |


---

## Functions

### `useConfirmDialog(revealed: ShallowRef<boolean>): UseConfirmDialogReturn<RevealData, ConfirmData, CancelData>`

<details><summary>Code</summary>

```ts
export function useConfirmDialog<
  RevealData = any,
  ConfirmData = any,
  CancelData = any,
>(
  revealed: ShallowRef<boolean> = shallowRef(false),
): UseConfirmDialogReturn<RevealData, ConfirmData, CancelData> {
  const confirmHook: EventHook = createEventHook<ConfirmData>()
  const cancelHook: EventHook = createEventHook<CancelData>()
  const revealHook: EventHook = createEventHook<RevealData>()

  let _resolve: (arg0: UseConfirmDialogRevealResult<ConfirmData, CancelData>) => void = noop

  const reveal = (data?: RevealData) => {
    revealHook.trigger(data)
    revealed.value = true

    return new Promise<UseConfirmDialogRevealResult<ConfirmData, CancelData>>((resolve) => {
      _resolve = resolve
    })
  }

  const confirm = (data?: ConfirmData) => {
    revealed.value = false
    confirmHook.trigger(data)

    _resolve({ data, isCanceled: false })
  }

  const cancel = (data?: CancelData) => {
    revealed.value = false
    cancelHook.trigger(data)
    _resolve({ data, isCanceled: true })
  }

  return {
    isRevealed: computed(() => revealed.value),
    reveal,
    confirm,
    cancel,
    onReveal: revealHook.on,
    onConfirm: confirmHook.on,
    onCancel: cancelHook.on,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Hooks for creating confirm dialogs. Useful for modal windows, popups and logins.
 *
 * @see https://vueuse.org/useConfirmDialog/
 * @param revealed `boolean` `ref` that handles a modal window
 */
```

- **Parameters**:
  - `revealed: ShallowRef<boolean>`
- **Return Type**: `UseConfirmDialogReturn<RevealData, ConfirmData, CancelData>`
- **Calls**:
  - `createEventHook (from @vueuse/shared)`
  - `revealHook.trigger`
  - `confirmHook.trigger`
  - `_resolve`
  - `cancelHook.trigger`
  - `computed (from vue)`
### `reveal(data: RevealData): Promise<UseConfirmDialogRevealResult<ConfirmData, CancelData>>`

<details><summary>Code</summary>

```ts
(data?: RevealData) => {
    revealHook.trigger(data)
    revealed.value = true

    return new Promise<UseConfirmDialogRevealResult<ConfirmData, CancelData>>((resolve) => {
      _resolve = resolve
    })
  }
```
</details>

- **Parameters**:
  - `data: RevealData`
- **Return Type**: `Promise<UseConfirmDialogRevealResult<ConfirmData, CancelData>>`
- **Calls**:
  - `revealHook.trigger`
### `confirm(data: ConfirmData): void`

<details><summary>Code</summary>

```ts
(data?: ConfirmData) => {
    revealed.value = false
    confirmHook.trigger(data)

    _resolve({ data, isCanceled: false })
  }
```
</details>

- **Parameters**:
  - `data: ConfirmData`
- **Return Type**: `void`
- **Calls**:
  - `confirmHook.trigger`
  - `_resolve`
### `cancel(data: CancelData): void`

<details><summary>Code</summary>

```ts
(data?: CancelData) => {
    revealed.value = false
    cancelHook.trigger(data)
    _resolve({ data, isCanceled: true })
  }
```
</details>

- **Parameters**:
  - `data: CancelData`
- **Return Type**: `void`
- **Calls**:
  - `cancelHook.trigger`
  - `_resolve`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseConfirmDialogReturn<RevealData, ConfirmData, CancelData>`

<details><summary>Interface Code</summary>

```ts
export interface UseConfirmDialogReturn<RevealData, ConfirmData, CancelData> {
  /**
   * Revealing state
   */
  isRevealed: ComputedRef<boolean>

  /**
   * Opens the dialog.
   * Create promise and return it. Triggers `onReveal` hook.
   */
  reveal: (data?: RevealData) => Promise<UseConfirmDialogRevealResult<ConfirmData, CancelData>>

  /**
   * Confirms and closes the dialog. Triggers a callback inside `onConfirm` hook.
   * Resolves promise from `reveal()` with `data` and `isCanceled` ref with `false` value.
   * Can accept any data and to pass it to `onConfirm` hook.
   */
  confirm: (data?: ConfirmData) => void

  /**
   * Cancels and closes the dialog. Triggers a callback inside `onCancel` hook.
   * Resolves promise from `reveal()` with `data` and `isCanceled` ref with `true` value.
   * Can accept any data and to pass it to `onCancel` hook.
   */
  cancel: (data?: CancelData) => void

  /**
   * Event Hook to be triggered right before dialog creating.
   */
  onReveal: EventHookOn<RevealData>

  /**
   * Event Hook to be called on `confirm()`.
   * Gets data object from `confirm` function.
   */
  onConfirm: EventHookOn<ConfirmData>

  /**
   * Event Hook to be called on `cancel()`.
   * Gets data object from `cancel` function.
   */
  onCancel: EventHookOn<CancelData>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `isRevealed` | `ComputedRef<boolean>` | ✗ |  |
| `reveal` | `(data?: RevealData) => Promise<UseConfirmDialogRevealResult<ConfirmData, CancelData>>` | ✗ |  |
| `confirm` | `(data?: ConfirmData) => void` | ✗ |  |
| `cancel` | `(data?: CancelData) => void` | ✗ |  |
| `onReveal` | `EventHookOn<RevealData>` | ✗ |  |
| `onConfirm` | `EventHookOn<ConfirmData>` | ✗ |  |
| `onCancel` | `EventHookOn<CancelData>` | ✗ |  |


---

## Type Aliases

### `UseConfirmDialogRevealResult<C, D>`

```ts
type UseConfirmDialogRevealResult<C, D> = {
    data?: C
    isCanceled: false
  } | {
    data?: D
    isCanceled: true
  };
```


---