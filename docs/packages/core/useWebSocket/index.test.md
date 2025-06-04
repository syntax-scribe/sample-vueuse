[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 📦 Imports | 11 |
| 📊 Variables & Constants | 6 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)

## 🛠️ File Location:
📂 **`packages/core/useWebSocket/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `UseWebSocketReturn` | `./index` |
| `afterEach` | `vitest` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `nextTick` | `vue` |
| `shallowRef` | `vue` |
| `useSetup` | `../../.test` |
| `useWebSocket` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `vm` | `ReturnType<typeof useSetup<{ ref: UseWebSocketReturn<any> }>> | null` | let/var | `null` | ✗ |
| `ev` | `MessageEvent<string>` | const | `new MessageEvent('message', {
      data: 'bleep bloop',
    })` | ✗ |
| `ev` | `MessageEvent<string>` | const | `new MessageEvent('message', {
      data: 'bleep bloop',
    })` | ✗ |
| `ev` | `Event` | const | `new Event('error')` | ✗ |
| `ev` | `CloseEvent` | const | `new CloseEvent('close')` | ✗ |
| `ev` | `CloseEvent` | let/var | `new CloseEvent('close')` | ✗ |


---