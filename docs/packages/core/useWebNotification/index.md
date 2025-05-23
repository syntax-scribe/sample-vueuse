[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 4
- **Classes**: 0
- **Imports**: 11
- **Interfaces**: 2
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useWebNotification/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `EventHook` | `@vueuse/shared` |
| `Ref` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `createEventHook` | `@vueuse/shared` |
| `tryOnMounted` | `@vueuse/shared` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useEventListener` | `../useEventListener` |
| `useSupported` | `../useSupported` |


---

## Functions

### `useWebNotification(options: UseWebNotificationOptions): { isSupported: any; notification: Ref<Notification>; ensurePermissions: () => Promise<any>; permissionGranted: any; show: (overrides?: WebNotificationOptions) => Promise<...>; ... 4 more ...; onClose: EventHook; }`

<details><summary>Code</summary>

```ts
export function useWebNotification(
  options: UseWebNotificationOptions = {},
) {
  const {
    window = defaultWindow,
    requestPermissions: _requestForPermissions = true,
  } = options

  const defaultWebNotificationOptions: WebNotificationOptions = options

  const isSupported = useSupported(() => {
    if (!window || !('Notification' in window))
      return false
    if (Notification.permission === 'granted')
      return true

    // https://stackoverflow.com/questions/29774836/failed-to-construct-notification-illegal-constructor/29895431
    // https://issues.chromium.org/issues/40415865
    try {
      const notification = new Notification('')
      notification.onshow = () => {
        notification.close()
      }
    }
    catch (e) {
      // Android Chrome: Uncaught TypeError: Failed to construct 'Notification': Illegal constructor. Use ServiceWorkerRegistration.showNotification() instead.
      // @ts-expect-error catch TypeError
      if (e.name === 'TypeError')
        return false
    }
    return true
  })

  const permissionGranted = shallowRef(isSupported.value && 'permission' in Notification && Notification.permission === 'granted')

  const notification: Ref<Notification | null> = deepRef(null)

  const ensurePermissions = async () => {
    if (!isSupported.value)
      return

    if (!permissionGranted.value && Notification.permission !== 'denied') {
      const result = await Notification.requestPermission()
      if (result === 'granted')
        permissionGranted.value = true
    }

    return permissionGranted.value
  }

  const { on: onClick, trigger: clickTrigger }: EventHook = createEventHook<Event>()
  const { on: onShow, trigger: showTrigger }: EventHook = createEventHook<Event>()
  const { on: onError, trigger: errorTrigger }: EventHook = createEventHook<Event>()
  const { on: onClose, trigger: closeTrigger }: EventHook = createEventHook<Event>()

  // Show notification method:
  const show = async (overrides?: WebNotificationOptions) => {
    // If either the browser does not support notifications or the user has
    // not granted permission, do nothing:
    if (!isSupported.value || !permissionGranted.value)
      return

    const options = Object.assign({}, defaultWebNotificationOptions, overrides)

    notification.value = new Notification(options.title || '', options)

    notification.value.onclick = clickTrigger
    notification.value.onshow = showTrigger
    notification.value.onerror = errorTrigger
    notification.value.onclose = closeTrigger

    return notification.value
  }

  // Close notification method:
  const close = (): void => {
    if (notification.value)
      notification.value.close()
    notification.value = null
  }

  // On mount, attempt to request permission:
  if (_requestForPermissions)
    tryOnMounted(ensurePermissions)

  // Attempt cleanup of the notification:
  tryOnScopeDispose(close)

  // Use close() to remove a notification that is no longer relevant to to
  // the user (e.g.the user already read the notification on the webpage).
  // Most modern browsers dismiss notifications automatically after a few
  // moments(around four seconds).
  if (isSupported.value && window) {
    const document = window.document
    useEventListener(document, 'visibilitychange', (e: Event) => {
      e.preventDefault()
      if (document.visibilityState === 'visible') {
        // The tab has become visible so clear the now-stale Notification:
        close()
      }
    })
  }

  return {
    isSupported,
    notification,
    ensurePermissions,
    permissionGranted,
    show,
    close,
    onClick,
    onShow,
    onError,
    onClose,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive useWebNotification
 *
 * @see https://vueuse.org/useWebNotification
 * @see https://developer.mozilla.org/en-US/docs/Web/API/notification
 */
```

- **Parameters**:
  - `options: UseWebNotificationOptions`
- **Return Type**: `{ isSupported: any; notification: Ref<Notification>; ensurePermissions: () => Promise<any>; permissionGranted: any; show: (overrides?: WebNotificationOptions) => Promise<...>; ... 4 more ...; onClose: EventHook; }`
- **Calls**:
  - `useSupported (from ../useSupported)`
  - `notification.close`
  - `shallowRef (from vue)`
  - `deepRef (from vue)`
  - `Notification.requestPermission`
  - `createEventHook (from @vueuse/shared)`
  - `Object.assign`
  - `notification.value.close`
  - `tryOnMounted (from @vueuse/shared)`
  - `tryOnScopeDispose (from @vueuse/shared)`
  - `useEventListener (from ../useEventListener)`
  - `e.preventDefault`
  - `close`
- **Internal Comments**:
```
// https://stackoverflow.com/questions/29774836/failed-to-construct-notification-illegal-constructor/29895431
// https://issues.chromium.org/issues/40415865
// Android Chrome: Uncaught TypeError: Failed to construct 'Notification': Illegal constructor. Use ServiceWorkerRegistration.showNotification() instead.
// @ts-expect-error catch TypeError
// Show notification method: (x2)
// If either the browser does not support notifications or the user has
// not granted permission, do nothing:
// Close notification method: (x2)
// On mount, attempt to request permission:
// Attempt cleanup of the notification: (x3)
// Use close() to remove a notification that is no longer relevant to to
// the user (e.g.the user already read the notification on the webpage).
// Most modern browsers dismiss notifications automatically after a few
// moments(around four seconds).
// The tab has become visible so clear the now-stale Notification: (x3)
```

### `ensurePermissions(): Promise<any>`

<details><summary>Code</summary>

```ts
async () => {
    if (!isSupported.value)
      return

    if (!permissionGranted.value && Notification.permission !== 'denied') {
      const result = await Notification.requestPermission()
      if (result === 'granted')
        permissionGranted.value = true
    }

    return permissionGranted.value
  }
```
</details>

- **Return Type**: `Promise<any>`
- **Calls**:
  - `Notification.requestPermission`
### `show(overrides: WebNotificationOptions): Promise<any>`

<details><summary>Code</summary>

```ts
async (overrides?: WebNotificationOptions) => {
    // If either the browser does not support notifications or the user has
    // not granted permission, do nothing:
    if (!isSupported.value || !permissionGranted.value)
      return

    const options = Object.assign({}, defaultWebNotificationOptions, overrides)

    notification.value = new Notification(options.title || '', options)

    notification.value.onclick = clickTrigger
    notification.value.onshow = showTrigger
    notification.value.onerror = errorTrigger
    notification.value.onclose = closeTrigger

    return notification.value
  }
```
</details>

- **Parameters**:
  - `overrides: WebNotificationOptions`
- **Return Type**: `Promise<any>`
- **Calls**:
  - `Object.assign`
- **Internal Comments**:
```
// If either the browser does not support notifications or the user has
// not granted permission, do nothing:
```

### `close(): void`

<details><summary>Code</summary>

```ts
(): void => {
    if (notification.value)
      notification.value.close()
    notification.value = null
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `notification.value.close`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `WebNotificationOptions`

<details><summary>Interface Code</summary>

```ts
export interface WebNotificationOptions {
  /**
   * The title read-only property of the Notification interface indicates
   * the title of the notification
   *
   * @default ''
   */
  title?: string
  /**
   * The body string of the notification as specified in the constructor's
   * options parameter.
   *
   * @default ''
   */
  body?: string
  /**
   * The text direction of the notification as specified in the constructor's
   * options parameter.
   *
   * @default ''
   */
  dir?: 'auto' | 'ltr' | 'rtl'
  /**
   * The language code of the notification as specified in the constructor's
   * options parameter.
   *
   * @default DOMString
   */
  lang?: string
  /**
   * The ID of the notification(if any) as specified in the constructor's options
   * parameter.
   *
   * @default ''
   */
  tag?: string
  /**
   * The URL of the image used as an icon of the notification as specified
   * in the constructor's options parameter.
   *
   * @default ''
   */
  icon?: string
  /**
   * Specifies whether the user should be notified after a new notification
   * replaces an old one.
   *
   * @default false
   */
  renotify?: boolean
  /**
   * A boolean value indicating that a notification should remain active until the
   * user clicks or dismisses it, rather than closing automatically.
   *
   * @default false
   */
  requireInteraction?: boolean
  /**
   * The silent read-only property of the Notification interface specifies
   * whether the notification should be silent, i.e., no sounds or vibrations
   * should be issued, regardless of the device settings.
   *
   * @default false
   */
  silent?: boolean
  /**
   * Specifies a vibration pattern for devices with vibration hardware to emit.
   * A vibration pattern, as specified in the Vibration API spec
   *
   * @see https://w3c.github.io/vibration/
   */
  vibrate?: number[]
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `title` | `string` | ✓ |  |
| `body` | `string` | ✓ |  |
| `dir` | `'auto' | 'ltr' | 'rtl'` | ✓ |  |
| `lang` | `string` | ✓ |  |
| `tag` | `string` | ✓ |  |
| `icon` | `string` | ✓ |  |
| `renotify` | `boolean` | ✓ |  |
| `requireInteraction` | `boolean` | ✓ |  |
| `silent` | `boolean` | ✓ |  |
| `vibrate` | `number[]` | ✓ |  |

### `UseWebNotificationOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseWebNotificationOptions extends ConfigurableWindow, WebNotificationOptions {
  /**
   * Request for permissions onMounted if it's not granted.
   *
   * Can be disabled and calling `ensurePermissions` to grant afterwords.
   *
   * @default true
   */
  requestPermissions?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `requestPermissions` | `boolean` | ✓ |  |


---

## Type Aliases

### `UseWebNotificationReturn`

```ts
type UseWebNotificationReturn = ReturnType<typeof useWebNotification>;
```


---