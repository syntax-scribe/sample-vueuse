[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 3 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/electron/useIpcRendererOn/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `IpcRenderer` | `electron` |
| `IpcRendererListener` | `../_types` |
| `tryOnScopeDispose` | `@vueuse/shared` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `ipcRenderer` | `IpcRenderer | undefined` | let/var | `*not shown*` | ✗ |
| `channel` | `string` | let/var | `*not shown*` | ✗ |
| `listener` | `IpcRendererListener` | let/var | `*not shown*` | ✗ |


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