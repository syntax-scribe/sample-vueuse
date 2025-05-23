[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 6
- **Classes**: 0
- **Imports**: 7
- **Interfaces**: 1
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/electron/useIpcRenderer/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `IpcRenderer` | `electron` |
| `IpcRendererEvent` | `electron` |
| `ShallowRef` | `vue` |
| `IpcRendererListener` | `../_types` |
| `shallowRef` | `vue` |
| `useIpcRendererInvoke` | `../useIpcRendererInvoke` |
| `useIpcRendererOn` | `../useIpcRendererOn` |


---

## Functions

### `setSendSync(ipcRenderer: IpcRenderer): <T>(channel: string, ...args: any[]) => ShallowRef<T>`

<details><summary>Code</summary>

```ts
function setSendSync(ipcRenderer: IpcRenderer) {
  return <T>(channel: string, ...args: any[]): ShallowRef<T | null> => {
    const result = shallowRef<T | null>(null) as ShallowRef<T | null>
    result.value = ipcRenderer.sendSync(channel, ...args)
    return result
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Create a `sendSync` function
 */
```

- **Parameters**:
  - `ipcRenderer: IpcRenderer`
- **Return Type**: `<T>(channel: string, ...args: any[]) => ShallowRef<T>`
- **Calls**:
  - `shallowRef (from vue)`
  - `ipcRenderer.sendSync`
### `useIpcRenderer(ipcRenderer: IpcRenderer): UseIpcRendererReturn`

<details><summary>Code</summary>

```ts
export function useIpcRenderer(ipcRenderer?: IpcRenderer): UseIpcRendererReturn {
  if (!ipcRenderer)
    ipcRenderer = window?.require('electron').ipcRenderer

  if (!ipcRenderer)
    throw new Error('provide IpcRenderer module or enable nodeIntegration')

  return {
    on: (channel: string, listener: IpcRendererListener) => useIpcRendererOn(channel, listener),
    once: ipcRenderer.once.bind(ipcRenderer),
    removeListener: ipcRenderer.removeListener.bind(ipcRenderer),
    removeAllListeners: ipcRenderer.removeAllListeners.bind(ipcRenderer),
    send: ipcRenderer.send,
    invoke: <T>(channel: string, ...args: any[]) => useIpcRendererInvoke<T>(ipcRenderer!, channel, ...args),
    sendSync: setSendSync(ipcRenderer),
    postMessage: ipcRenderer.postMessage,
    sendTo: ipcRenderer.sendTo,
    sendToHost: ipcRenderer.sendToHost,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Get the `ipcRenderer` module with all APIs.
 *
 * @see https://www.electronjs.org/docs/api/ipc-renderer#ipcrenderersendtohostchannel-args
 * @see https://vueuse.org/useIpcRenderer
 */
```

- **Parameters**:
  - `ipcRenderer: IpcRenderer`
- **Return Type**: `UseIpcRendererReturn`
- **Calls**:
  - `window?.require`
  - `useIpcRendererOn (from ../useIpcRendererOn)`
  - `ipcRenderer.once.bind`
  - `ipcRenderer.removeListener.bind`
  - `ipcRenderer.removeAllListeners.bind`
  - `useIpcRendererInvoke (from ../useIpcRendererInvoke)`
  - `setSendSync`
### `on(channel: string, listener: IpcRendererListener): IpcRenderer`

<details><summary>Code</summary>

```ts
(channel: string, listener: IpcRendererListener) => useIpcRendererOn(channel, listener)
```
</details>

- **Parameters**:
  - `channel: string`
  - `listener: IpcRendererListener`
- **Return Type**: `IpcRenderer`
- **Calls**:
  - `useIpcRendererOn (from ../useIpcRendererOn)`
### `invoke(channel: string, args: any[]): ShallowRef<T>`

<details><summary>Code</summary>

```ts
<T>(channel: string, ...args: any[]) => useIpcRendererInvoke<T>(ipcRenderer!, channel, ...args)
```
</details>

- **Parameters**:
  - `channel: string`
  - `args: any[]`
- **Return Type**: `ShallowRef<T>`
- **Calls**:
  - `useIpcRendererInvoke (from ../useIpcRendererInvoke)`
### `on(channel: string, listener: IpcRendererListener): IpcRenderer`

<details><summary>Code</summary>

```ts
(channel: string, listener: IpcRendererListener) => useIpcRendererOn(channel, listener)
```
</details>

- **Parameters**:
  - `channel: string`
  - `listener: IpcRendererListener`
- **Return Type**: `IpcRenderer`
- **Calls**:
  - `useIpcRendererOn (from ../useIpcRendererOn)`
### `invoke(channel: string, args: any[]): ShallowRef<T>`

<details><summary>Code</summary>

```ts
<T>(channel: string, ...args: any[]) => useIpcRendererInvoke<T>(ipcRenderer!, channel, ...args)
```
</details>

- **Parameters**:
  - `channel: string`
  - `args: any[]`
- **Return Type**: `ShallowRef<T>`
- **Calls**:
  - `useIpcRendererInvoke (from ../useIpcRendererInvoke)`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseIpcRendererReturn`

<details><summary>Interface Code</summary>

```ts
export interface UseIpcRendererReturn {
  /**
   * Listens to channel, when a new message arrives listener would be called with listener(event, args...).
   * [ipcRenderer.removeListener](https://www.electronjs.org/docs/api/ipc-renderer#ipcrendererremovelistenerchannel-listener) automatically on unmounted.
   *
   * @see https://www.electronjs.org/docs/api/ipc-renderer#ipcrendereronchannel-listener
   */
  on: (channel: string, listener: IpcRendererListener) => IpcRenderer

  /**
   * Adds a one time listener function for the event. This listener is invoked only the next time a message is sent to channel, after which it is removed.
   *
   * @see https://www.electronjs.org/docs/api/ipc-renderer#ipcrendereroncechannel-listener
   */
  once: (channel: string, listener: (event: IpcRendererEvent, ...args: any[]) => void) => IpcRenderer

  /**
   * Removes the specified listener from the listener array for the specified channel.
   *
   * @see https://www.electronjs.org/docs/api/ipc-renderer#ipcrendererremovelistenerchannel-listener
   */
  removeListener: (channel: string, listener: (...args: any[]) => void) => IpcRenderer

  /**
   * Removes all listeners, or those of the specified channel.
   *
   * @see https://www.electronjs.org/docs/api/ipc-renderer#ipcrendererremovealllistenerschannel
   */
  removeAllListeners: (channel: string) => IpcRenderer

  /**
   * Send an asynchronous message to the main process via channel, along with arguments.
   *
   * @see https://www.electronjs.org/docs/api/ipc-renderer#ipcrenderersendchannel-args
   */
  send: (channel: string, ...args: any[]) => void

  /**
   * Returns Promise<any> - Resolves with the response from the main process.
   * Send a message to the main process via channel and expect a result ~~asynchronously~~.
   * As composition-api, it makes asynchronous operations look like synchronous.
   *
   * @see https://www.electronjs.org/docs/api/ipc-renderer#ipcrendererinvokechannel-args
   */
  invoke: <T>(channel: string, ...args: any[]) => ShallowRef<T | null>

  /**
   * Returns any - The value sent back by the ipcMain handler.
   * Send a message to the main process via channel and expect a result synchronously.
   *
   * @see https://www.electronjs.org/docs/api/ipc-renderer#ipcrenderersendsyncchannel-args
   */
  sendSync: <T>(channel: string, ...args: any[]) => ShallowRef<T | null>

  /**
   * Send a message to the main process, optionally transferring ownership of zero or more MessagePort objects.
   *
   * @see https://www.electronjs.org/docs/api/ipc-renderer#ipcrendererpostmessagechannel-message-transfer
   */
  postMessage: (channel: string, message: any, transfer?: MessagePort[]) => void

  /**
   * Sends a message to a window with webContentsId via channel.
   *
   * @see https://www.electronjs.org/docs/api/ipc-renderer#ipcrenderersendtowebcontentsid-channel-args
   */
  sendTo: (webContentsId: number, channel: string, ...args: any[]) => void

  /**
   * Like ipcRenderer.send but the event will be sent to the <webview> element in the host page instead of the main process.
   *
   * @see https://www.electronjs.org/docs/api/ipc-renderer#ipcrenderersendtohostchannel-args
   */
  sendToHost: (channel: string, ...args: any[]) => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `on` | `(channel: string, listener: IpcRendererListener) => IpcRenderer` | ✗ |  |
| `once` | `(channel: string, listener: (event: IpcRendererEvent, ...args: any[]) => void) => IpcRenderer` | ✗ |  |
| `removeListener` | `(channel: string, listener: (...args: any[]) => void) => IpcRenderer` | ✗ |  |
| `removeAllListeners` | `(channel: string) => IpcRenderer` | ✗ |  |
| `send` | `(channel: string, ...args: any[]) => void` | ✗ |  |
| `invoke` | `<T>(channel: string, ...args: any[]) => ShallowRef<T | null>` | ✗ |  |
| `sendSync` | `<T>(channel: string, ...args: any[]) => ShallowRef<T | null>` | ✗ |  |
| `postMessage` | `(channel: string, message: any, transfer?: MessagePort[]) => void` | ✗ |  |
| `sendTo` | `(webContentsId: number, channel: string, ...args: any[]) => void` | ✗ |  |
| `sendToHost` | `(channel: string, ...args: any[]) => void` | ✗ |  |


---

## Type Aliases

> No type aliases found in this file.


---