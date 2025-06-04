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
📂 **`packages/electron/useIpcRendererInvoke/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `IpcRenderer` | `electron` |
| `ShallowRef` | `vue` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `ipcRenderer` | `IpcRenderer | undefined` | let/var | `*not shown*` | ✗ |
| `channel` | `string` | let/var | `*not shown*` | ✗ |
| `invokeArgs` | `any[]` | let/var | `*not shown*` | ✗ |


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