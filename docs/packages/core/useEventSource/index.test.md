[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Classes](#classes)

## 📊 Analysis Summary

- **Functions**: 4
- **Classes**: 1
- **Imports**: 7
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useEventSource/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `afterEach` | `vitest` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `useEventSource` | `./index` |


---

## Functions

### `MockEventSource.onerror(_ev: Event): void`

<details><summary>Code</summary>

```ts
onerror(_ev: Event) {
  }
```
</details>

- **Parameters**:
  - `_ev: Event`
- **Return Type**: `void`
### `MockEventSource.onmessage(_ev: MessageEvent): void`

<details><summary>Code</summary>

```ts
onmessage(_ev: MessageEvent) {
  }
```
</details>

- **Parameters**:
  - `_ev: MessageEvent`
- **Return Type**: `void`
### `MockEventSource.onopen(_ev: Event): void`

<details><summary>Code</summary>

```ts
onopen(_ev: Event) {
  }
```
</details>

- **Parameters**:
  - `_ev: Event`
- **Return Type**: `void`
### `MockEventSource.close(): void`

<details><summary>Code</summary>

```ts
close() {
    this.readyState = this.CLOSED
  }
```
</details>

- **Return Type**: `void`

---

## Classes

### `MockEventSource`

<details><summary>Class Code</summary>

```ts
class MockEventSource extends EventTarget {
  readyState: number = 0
  url: string = ''
  withCredentials: boolean = false
  readonly CONNECTING = 0 as const
  readonly OPEN = 1 as const
  readonly CLOSED = 2 as const

  constructor() {
    super();
    (this as EventSource).addEventListener('error', this.onerror);
    (this as EventSource).addEventListener('message', this.onmessage)
    this.addEventListener('open', this.onopen)
  }

  onerror(_ev: Event) {
  }

  onmessage(_ev: MessageEvent) {
  }

  onopen(_ev: Event) {
  }

  close() {
    this.readyState = this.CLOSED
  }
}
```
</details>

#### Methods

##### `onerror(_ev: Event): void`

<details><summary>Code</summary>

```ts
onerror(_ev: Event) {
  }
```
</details>

##### `onmessage(_ev: MessageEvent): void`

<details><summary>Code</summary>

```ts
onmessage(_ev: MessageEvent) {
  }
```
</details>

##### `onopen(_ev: Event): void`

<details><summary>Code</summary>

```ts
onopen(_ev: Event) {
  }
```
</details>

##### `close(): void`

<details><summary>Code</summary>

```ts
close() {
    this.readyState = this.CLOSED
  }
```
</details>


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---