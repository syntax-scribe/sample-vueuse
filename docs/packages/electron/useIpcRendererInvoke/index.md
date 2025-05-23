[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/electron/useIpcRendererInvoke/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `IpcRenderer` | `electron` |
| `ShallowRef` | `vue` |
| `shallowRef` | `vue` |


---

## Functions

### `useIpcRendererInvoke(ipcRenderer: IpcRenderer, channel: string, args: any[]): ShallowRef<T | null>`

<details><summary>Code</summary>

```ts
export function useIpcRendererInvoke<T>(ipcRenderer: IpcRenderer, channel: string, ...args: any[]): ShallowRef<T | null>
```
</details>

- **JSDoc**:
```ts
/**
 * Returns Promise<any> - Resolves with the response from the main process.
 *
 * Send a message to the main process via channel and expect a result ~~asynchronously~~. As composition-api, it makes asynchronous operations look like synchronous.
 *
 * You need to provide `ipcRenderer` to this function.
 *
 * @see https://www.electronjs.org/docs/api/ipc-renderer#ipcrendererinvokechannel-args
 * @see https://vueuse.org/useIpcRendererInvoke
 */
```

- **Parameters**:
  - `ipcRenderer: IpcRenderer`
  - `channel: string`
  - `args: any[]`
- **Return Type**: `ShallowRef<T | null>`

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