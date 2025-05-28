[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 🧱 Classes | 0 |
| 📦 Imports | 11 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/onElementRemoval/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Fn` | `@vueuse/shared` |
| `WatchOptionsBase` | `vue` |
| `ConfigurableDocumentOrShadowRoot` | `../_configurable` |
| `ConfigurableWindow` | `../_configurable` |
| `MaybeElementRef` | `../unrefElement` |
| `noop` | `@vueuse/shared` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `watchEffect` | `vue` |
| `defaultWindow` | `../_configurable` |
| `unrefElement` | `../unrefElement` |
| `useMutationObserver` | `../useMutationObserver` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `stopFn` | `Fn | undefined` | let/var | `*not shown*` | ✗ |


---

## Functions

### `onElementRemoval(target: MaybeElementRef, callback: (mutationRecords: MutationRecord[]) => void, options: OnElementRemovalOptions): Fn`

<details><summary>Code</summary>

```ts
export function onElementRemoval(
  target: MaybeElementRef,
  callback: (mutationRecords: MutationRecord[]) => void,
  options: OnElementRemovalOptions = {},
): Fn {
  const {
    window = defaultWindow,
    document = window?.document,
    flush = 'sync',
  } = options

  // SSR
  if (!window || !document)
    return noop

  let stopFn: Fn | undefined
  const cleanupAndUpdate = (fn?: Fn) => {
    stopFn?.()
    stopFn = fn
  }

  const stopWatch = watchEffect(() => {
    const el = unrefElement(target)
    if (el) {
      const { stop } = useMutationObserver(
        document as any,
        (mutationsList) => {
          const targetRemoved = mutationsList
            .map(mutation => [...mutation.removedNodes])
            .flat()
            .some(node => node === el || node.contains(el))

          if (targetRemoved) {
            callback(mutationsList)
          }
        },
        {
          window,
          childList: true,
          subtree: true,
        },
      )

      cleanupAndUpdate(stop)
    }
  }, { flush })

  const stopHandle = () => {
    stopWatch()
    cleanupAndUpdate()
  }

  tryOnScopeDispose(stopHandle)

  return stopHandle
}
```
</details>

- **JSDoc**:
```ts
/**
 * Fires when the element or any element containing it is removed.
 *
 * @param target
 * @param callback
 * @param options
 */
```

- **Parameters**:
  - `target: MaybeElementRef`
  - `callback: (mutationRecords: MutationRecord[]) => void`
  - `options: OnElementRemovalOptions`
- **Return Type**: `Fn`
- **Calls**:
  - `stopFn`
  - `watchEffect (from vue)`
  - `unrefElement (from ../unrefElement)`
  - `useMutationObserver (from ../useMutationObserver)`
  - `mutationsList
            .map(mutation => [...mutation.removedNodes])
            .flat()
            .some`
  - `node.contains`
  - `callback`
  - `cleanupAndUpdate`
  - `stopWatch`
  - `tryOnScopeDispose (from @vueuse/shared)`
- **Internal Comments**:
```
// SSR
```

### `cleanupAndUpdate(fn: Fn): void`

<details><summary>Code</summary>

```ts
(fn?: Fn) => {
    stopFn?.()
    stopFn = fn
  }
```
</details>

- **Parameters**:
  - `fn: Fn`
- **Return Type**: `void`
- **Calls**:
  - `stopFn`
### `stopHandle(): void`

<details><summary>Code</summary>

```ts
() => {
    stopWatch()
    cleanupAndUpdate()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `stopWatch`
  - `cleanupAndUpdate`

---

## Interfaces

### `OnElementRemovalOptions`

<details><summary>Interface Code</summary>

```ts
export interface OnElementRemovalOptions
  extends ConfigurableWindow, ConfigurableDocumentOrShadowRoot, WatchOptionsBase { }
```
</details>


---