[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 🧱 Classes | 0 |
| 📦 Imports | 10 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 4 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 4 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useWakeLock/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableDocument` | `../_configurable` |
| `ConfigurableNavigator` | `../_configurable` |
| `whenever` | `@vueuse/shared` |
| `computed` | `vue` |
| `shallowRef` | `vue` |
| `defaultDocument` | `../_configurable` |
| `defaultNavigator` | `../_configurable` |
| `useDocumentVisibility` | `../useDocumentVisibility` |
| `useEventListener` | `../useEventListener` |
| `useSupported` | `../useSupported` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `s` | `any` | let/var | `sentinel.value` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| await-expression | `useWakeLock` | sentinel.value?.release(), (navigator as NavigatorWithWakeLock).wakeLock.request(type), forceRequest(type), s?.release() | *none* |
| async-function | `forceRequest` | sentinel.value?.release(), (navigator as NavigatorWithWakeLock).wakeLock.request(type) | *none* |
| async-function | `request` | forceRequest(type) | *none* |
| async-function | `release` | s?.release() | *none* |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `useWakeLock(options: UseWakeLockOptions): { sentinel: any; isSupported: any; isActive: any; request: (type: "screen") => Promise<void>; forceRequest: (type: "screen") => Promise<void>; release: () => Promise<void>; }`

<details><summary>Code</summary>

```ts
export function useWakeLock(options: UseWakeLockOptions = {}) {
  const {
    navigator = defaultNavigator,
    document = defaultDocument,
  } = options
  const requestedType = shallowRef<WakeLockType | false>(false)
  const sentinel = shallowRef<WakeLockSentinel | null>(null)
  const documentVisibility = useDocumentVisibility({ document })
  const isSupported = useSupported(() => navigator && 'wakeLock' in navigator)
  const isActive = computed(() => !!sentinel.value && documentVisibility.value === 'visible')

  if (isSupported.value) {
    useEventListener(sentinel, 'release', () => {
      requestedType.value = sentinel.value?.type ?? false
    }, { passive: true })

    whenever(
      () => documentVisibility.value === 'visible' && document?.visibilityState === 'visible' && requestedType.value,
      (type) => {
        requestedType.value = false
        forceRequest(type)
      },
    )
  }

  async function forceRequest(type: WakeLockType) {
    await sentinel.value?.release()
    sentinel.value = isSupported.value
      ? await (navigator as NavigatorWithWakeLock).wakeLock.request(type)
      : null
  }

  async function request(type: WakeLockType) {
    if (documentVisibility.value === 'visible')
      await forceRequest(type)
    else
      requestedType.value = type
  }

  async function release() {
    requestedType.value = false
    const s = sentinel.value
    sentinel.value = null
    await s?.release()
  }

  return {
    sentinel,
    isSupported,
    isActive,
    request,
    forceRequest,
    release,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive Screen Wake Lock API.
 *
 * @see https://vueuse.org/useWakeLock
 * @param options
 */
```

- **Parameters**:
  - `options: UseWakeLockOptions`
- **Return Type**: `{ sentinel: any; isSupported: any; isActive: any; request: (type: "screen") => Promise<void>; forceRequest: (type: "screen") => Promise<void>; release: () => Promise<void>; }`
- **Calls**:
  - `shallowRef (from vue)`
  - `useDocumentVisibility (from ../useDocumentVisibility)`
  - `useSupported (from ../useSupported)`
  - `computed (from vue)`
  - `useEventListener (from ../useEventListener)`
  - `whenever (from @vueuse/shared)`
  - `forceRequest`
  - `sentinel.value?.release`
  - `(navigator as NavigatorWithWakeLock).wakeLock.request`
  - `s?.release`
### `forceRequest(type: WakeLockType): Promise<void>`

<details><summary>Code</summary>

```ts
async function forceRequest(type: WakeLockType) {
    await sentinel.value?.release()
    sentinel.value = isSupported.value
      ? await (navigator as NavigatorWithWakeLock).wakeLock.request(type)
      : null
  }
```
</details>

- **Parameters**:
  - `type: WakeLockType`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `sentinel.value?.release`
  - `(navigator as NavigatorWithWakeLock).wakeLock.request`
### `request(type: WakeLockType): Promise<void>`

<details><summary>Code</summary>

```ts
async function request(type: WakeLockType) {
    if (documentVisibility.value === 'visible')
      await forceRequest(type)
    else
      requestedType.value = type
  }
```
</details>

- **Parameters**:
  - `type: WakeLockType`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `forceRequest`
### `release(): Promise<void>`

<details><summary>Code</summary>

```ts
async function release() {
    requestedType.value = false
    const s = sentinel.value
    sentinel.value = null
    await s?.release()
  }
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `s?.release`

---

## Interfaces

### `WakeLockSentinel`

<details><summary>Interface Code</summary>

```ts
export interface WakeLockSentinel extends EventTarget {
  type: WakeLockType
  released: boolean
  release: () => Promise<void>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `type` | `WakeLockType` | ✗ |  |
| `released` | `boolean` | ✗ |  |
| `release` | `() => Promise<void>` | ✗ |  |


---

## Type Aliases

### `WakeLockType`

```ts
type WakeLockType = 'screen';
```

### `NavigatorWithWakeLock`

```ts
type NavigatorWithWakeLock = Navigator & {
  wakeLock: { request: (type: WakeLockType) => Promise<WakeLockSentinel> }
};
```

### `UseWakeLockOptions`

```ts
type UseWakeLockOptions = ConfigurableNavigator & ConfigurableDocument;
```

### `UseWakeLockReturn`

```ts
type UseWakeLockReturn = ReturnType<typeof useWakeLock>;
```


---