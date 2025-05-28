[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 3 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

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