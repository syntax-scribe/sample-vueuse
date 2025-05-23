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
📂 **`packages/electron/useIpcRendererOn/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `IpcRenderer` | `electron` |
| `IpcRendererListener` | `../_types` |
| `tryOnScopeDispose` | `@vueuse/shared` |


---

## Functions

### `useIpcRendererOn(ipcRenderer: IpcRenderer, channel: string, listener: IpcRendererListener): IpcRenderer`

<details><summary>Code</summary>

```ts
export function useIpcRendererOn(ipcRenderer: IpcRenderer, channel: string, listener: IpcRendererListener): IpcRenderer
```
</details>

- **JSDoc**:
```ts
/**
 * Listens to channel, when a new message arrives listener would be called with listener(event, args...).
 * [ipcRenderer.removeListener](https://www.electronjs.org/docs/api/ipc-renderer#ipcrendererremovelistenerchannel-listener) automatically on unmounted.
 *
 * You need to provide `ipcRenderer` to this function.
 *
 * @see https://www.electronjs.org/docs/api/ipc-renderer#ipcrendereronchannel-listener
 * @see https://vueuse.org/useIpcRendererOn
 */
```

- **Parameters**:
  - `ipcRenderer: IpcRenderer`
  - `channel: string`
  - `listener: IpcRendererListener`
- **Return Type**: `IpcRenderer`

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