[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 📦 Imports | 9 |
| 📊 Variables & Constants | 5 |
| ⚡ Async/Await Patterns | 3 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/usePointerLock/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableDocument` | `../_configurable` |
| `MaybeElement` | `../unrefElement` |
| `MaybeElementRef` | `../unrefElement` |
| `until` | `@vueuse/shared` |
| `shallowRef` | `vue` |
| `defaultDocument` | `../_configurable` |
| `unrefElement` | `../unrefElement` |
| `useEventListener` | `../useEventListener` |
| `useSupported` | `../useSupported` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `targetElement` | `MaybeElement` | let/var | `*not shown*` | ✗ |
| `listenerOptions` | `{ passive: boolean; }` | const | `{ passive: true }` | ✗ |
| `currentElement` | `any` | const | `document!.pointerLockElement ?? element.value` | ✗ |
| `currentElement` | `any` | const | `document!.pointerLockElement ?? element.value` | ✗ |
| `action` | `"release" | "acquire"` | const | `document!.pointerLockElement ? 'release' : 'acquire'` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| await-expression | `usePointerLock` | until(element).toBe(targetElement), until(element).toBeNull() | *none* |
| async-function | `lock` | until(element).toBe(targetElement) | *none* |
| async-function | `unlock` | until(element).toBeNull() | *none* |


---

## Functions

### `usePointerLock(target: MaybeElementRef, options: UsePointerLockOptions): { isSupported: any; element: any; triggerElement: any; lock: (e: any) => Promise<any>; unlock: () => Promise<boolean>; }`

<details><summary>Code</summary>

```ts
export function usePointerLock(target?: MaybeElementRef, options: UsePointerLockOptions = {}) {
  const { document = defaultDocument } = options

  const isSupported = useSupported(() => document && 'pointerLockElement' in document)

  const element = shallowRef<MaybeElement>()

  const triggerElement = shallowRef<MaybeElement>()

  let targetElement: MaybeElement

  if (isSupported.value) {
    const listenerOptions = { passive: true }

    useEventListener(document, 'pointerlockchange', () => {
      const currentElement = document!.pointerLockElement ?? element.value
      if (targetElement && currentElement === targetElement) {
        element.value = document!.pointerLockElement as MaybeElement
        if (!element.value)
          targetElement = triggerElement.value = null
      }
    }, listenerOptions)

    useEventListener(document, 'pointerlockerror', () => {
      const currentElement = document!.pointerLockElement ?? element.value
      if (targetElement && currentElement === targetElement) {
        const action = document!.pointerLockElement ? 'release' : 'acquire'
        throw new Error(`Failed to ${action} pointer lock.`)
      }
    }, listenerOptions)
  }

  async function lock(
    e: MaybeElementRef | Event,
    // options?: PointerLockOptions,
  ) {
    if (!isSupported.value)
      throw new Error('Pointer Lock API is not supported by your browser.')

    triggerElement.value = e instanceof Event ? <HTMLElement>e.currentTarget : null
    targetElement = e instanceof Event ? unrefElement(target) ?? triggerElement.value : unrefElement(e)
    if (!targetElement)
      throw new Error('Target element undefined.')
    targetElement.requestPointerLock()

    return await until(element).toBe(targetElement)
  }

  async function unlock() {
    if (!element.value)
      return false

    document!.exitPointerLock()

    await until(element).toBeNull()
    return true
  }

  return {
    isSupported,
    element,
    triggerElement,
    lock,
    unlock,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive pointer lock.
 *
 * @see https://vueuse.org/usePointerLock
 * @param target
 * @param options
 */
```

- **Parameters**:
  - `target: MaybeElementRef`
  - `options: UsePointerLockOptions`
- **Return Type**: `{ isSupported: any; element: any; triggerElement: any; lock: (e: any) => Promise<any>; unlock: () => Promise<boolean>; }`
- **Calls**:
  - `useSupported (from ../useSupported)`
  - `shallowRef (from vue)`
  - `useEventListener (from ../useEventListener)`
  - `unrefElement (from ../unrefElement)`
  - `targetElement.requestPointerLock`
  - `until(element).toBe`
  - `document!.exitPointerLock`
  - `until(element).toBeNull`
### `lock(e: MaybeElementRef | Event): Promise<any>`

<details><summary>Code</summary>

```ts
async function lock(
    e: MaybeElementRef | Event,
    // options?: PointerLockOptions,
  ) {
    if (!isSupported.value)
      throw new Error('Pointer Lock API is not supported by your browser.')

    triggerElement.value = e instanceof Event ? <HTMLElement>e.currentTarget : null
    targetElement = e instanceof Event ? unrefElement(target) ?? triggerElement.value : unrefElement(e)
    if (!targetElement)
      throw new Error('Target element undefined.')
    targetElement.requestPointerLock()

    return await until(element).toBe(targetElement)
  }
```
</details>

- **Parameters**:
  - `e: MaybeElementRef | Event`
- **Return Type**: `Promise<any>`
- **Calls**:
  - `unrefElement (from ../unrefElement)`
  - `targetElement.requestPointerLock`
  - `until(element).toBe`
### `unlock(): Promise<boolean>`

<details><summary>Code</summary>

```ts
async function unlock() {
    if (!element.value)
      return false

    document!.exitPointerLock()

    await until(element).toBeNull()
    return true
  }
```
</details>

- **Return Type**: `Promise<boolean>`
- **Calls**:
  - `document!.exitPointerLock`
  - `until(element).toBeNull`

---

## Interfaces

### `UsePointerLockOptions`

<details><summary>Interface Code</summary>

```ts
export interface UsePointerLockOptions extends ConfigurableDocument {
  // pointerLockOptions?: PointerLockOptions
}
```
</details>


---

## Type Aliases

### `UsePointerLockReturn`

```ts
type UsePointerLockReturn = ReturnType<typeof usePointerLock>;
```


---