[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 9
- **Interfaces**: 2
- **Type Aliases**: 3

## 🛠️ File Location:
📂 **`packages/core/usePermission/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `ShallowRef` | `vue` |
| `ConfigurableNavigator` | `../_configurable` |
| `createSingletonPromise` | `@vueuse/shared` |
| `shallowRef` | `vue` |
| `toRaw` | `vue` |
| `defaultNavigator` | `../_configurable` |
| `useEventListener` | `../useEventListener` |
| `useSupported` | `../useSupported` |


---

## Functions

### `usePermission(permissionDesc: GeneralPermissionDescriptor | GeneralPermissionDescriptor['name'], options: UsePermissionOptions<false>): UsePermissionReturn`

<details><summary>Code</summary>

```ts
export function usePermission(
  permissionDesc: GeneralPermissionDescriptor | GeneralPermissionDescriptor['name'],
  options?: UsePermissionOptions<false>
): UsePermissionReturn
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive Permissions API.
 *
 * @see https://vueuse.org/usePermission
 */
```

- **Parameters**:
  - `permissionDesc: GeneralPermissionDescriptor | GeneralPermissionDescriptor['name']`
  - `options: UsePermissionOptions<false>`
- **Return Type**: `UsePermissionReturn`
### `update(): void`

<details><summary>Code</summary>

```ts
() => {
    state.value = permissionStatus.value?.state ?? 'prompt'
  }
```
</details>

- **Return Type**: `void`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UsePermissionOptions<Controls extends boolean>`

<details><summary>Interface Code</summary>

```ts
export interface UsePermissionOptions<Controls extends boolean> extends ConfigurableNavigator {
  /**
   * Expose more controls
   *
   * @default false
   */
  controls?: Controls
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `controls` | `Controls` | ✓ |  |

### `UsePermissionReturnWithControls`

<details><summary>Interface Code</summary>

```ts
export interface UsePermissionReturnWithControls {
  state: UsePermissionReturn
  isSupported: ComputedRef<boolean>
  query: () => Promise<PermissionStatus | undefined>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `state` | `UsePermissionReturn` | ✗ |  |
| `isSupported` | `ComputedRef<boolean>` | ✗ |  |
| `query` | `() => Promise<PermissionStatus | undefined>` | ✗ |  |


---

## Type Aliases

### `DescriptorNamePolyfill`

```ts
type DescriptorNamePolyfill = 'accelerometer' |
  'accessibility-events' |
  'ambient-light-sensor' |
  'background-sync' |
  'camera' |
  'clipboard-read' |
  'clipboard-write' |
  'gyroscope' |
  'magnetometer' |
  'microphone' |
  'notifications' |
  'payment-handler' |
  'persistent-storage' |
  'push' |
  'speaker' |
  'local-fonts';
```

### `GeneralPermissionDescriptor`

```ts
type GeneralPermissionDescriptor = | PermissionDescriptor
  | { name: DescriptorNamePolyfill };
```

### `UsePermissionReturn`

```ts
type UsePermissionReturn = Readonly<ShallowRef<PermissionState | undefined>>;
```


---