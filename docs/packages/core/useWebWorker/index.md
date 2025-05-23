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
- **Imports**: 7
- **Interfaces**: 1
- **Type Aliases**: 2

## 🛠️ File Location:
📂 **`packages/core/useWebWorker/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `ShallowRef` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |
| `defaultWindow` | `../_configurable` |


---

## Functions

### `useWebWorker(url: string, workerOptions: WorkerOptions, options: ConfigurableWindow): UseWebWorkerReturn<T>`

<details><summary>Code</summary>

```ts
export function useWebWorker<T = any>(
  url: string,
  workerOptions?: WorkerOptions,
  options?: ConfigurableWindow,
): UseWebWorkerReturn<T>
```
</details>

- **JSDoc**:
```ts
/**
 * Simple Web Workers registration and communication.
 *
 * @see https://vueuse.org/useWebWorker
 * @param url
 * @param workerOptions
 * @param options
 */
```

- **Parameters**:
  - `url: string`
  - `workerOptions: WorkerOptions`
  - `options: ConfigurableWindow`
- **Return Type**: `UseWebWorkerReturn<T>`
### `post(args: any[]): void`

<details><summary>Code</summary>

```ts
(...args) => {
    if (!worker.value)
      return

    worker.value.postMessage(...args as Parameters<PostMessage>)
  }
```
</details>

- **Parameters**:
  - `args: any[]`
- **Return Type**: `void`
- **Calls**:
  - `worker.value.postMessage`
### `terminate(): void`

<details><summary>Code</summary>

```ts
function terminate() {
    if (!worker.value)
      return

    worker.value.terminate()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `worker.value.terminate`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseWebWorkerReturn<Data = any>`

<details><summary>Interface Code</summary>

```ts
export interface UseWebWorkerReturn<Data = any> {
  data: Ref<Data>
  post: PostMessage
  terminate: () => void
  worker: ShallowRef<Worker | undefined>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `data` | `Ref<Data>` | ✗ |  |
| `post` | `PostMessage` | ✗ |  |
| `terminate` | `() => void` | ✗ |  |
| `worker` | `ShallowRef<Worker | undefined>` | ✗ |  |


---

## Type Aliases

### `PostMessage`

```ts
type PostMessage = typeof Worker.prototype['postMessage'];
```

### `WorkerFn`

```ts
type WorkerFn = (...args: unknown[]) => Worker;
```


---