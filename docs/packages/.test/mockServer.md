[⬅️ Back to Table of Contents](../../index.md)

# 📄 `mockServer.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 11 |
| ⚡ Async/Await Patterns | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/.test/mockServer.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `delay` | `msw` |
| `http` | `msw` |
| `HttpResponse` | `msw` |
| `setupServer` | `msw/node` |
| `afterAll` | `vitest` |
| `afterEach` | `vitest` |
| `beforeAll` | `vitest` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `defaultJsonMessage` | `{ hello: string; }` | const | `{ hello: 'world' }` | ✗ |
| `defaultTextMessage` | `"Hello World"` | const | `'Hello World'` | ✗ |
| `baseUrl` | `"https://example.com"` | const | `'https://example.com'` | ✗ |
| `url` | `URL` | let/var | `new URL(req.url)` | ✗ |
| `qs` | `URLSearchParams` | let/var | `url.searchParams` | ✗ |
| `status` | `number` | let/var | `200` | ✗ |
| `url` | `URL` | let/var | `new URL(request.url)` | ✗ |
| `qs` | `URLSearchParams` | let/var | `url.searchParams` | ✗ |
| `status` | `number` | let/var | `200` | ✗ |
| `text` | `any` | let/var | `await request.text()` | ✗ |
| `json` | `any` | let/var | `text.startsWith('{') ? JSON.parse(text) : null` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| async-function | `commonTransformers` | delay(Number(qs.get('delay'))) | *none* |


---

## Functions

### `commonTransformers(req: Request): Promise<any>`

<details><summary>Code</summary>

```ts
async function commonTransformers(req: Request) {
  const url = new URL(req.url)
  const qs = url.searchParams

  let status = 200

  if (qs.get('delay'))
    await delay(Number(qs.get('delay')))
  if (qs.get('status')) {
    status = Number(qs.get('status'))
  }
  if (qs.get('text') != null) {
    return new HttpResponse(qs.get('text') ?? defaultTextMessage, { status })
  }
  else if (qs.get('json') != null) {
    const jsonVal = qs.get('json')
    return HttpResponse.json(jsonVal?.length ? JSON.parse(jsonVal) : defaultJsonMessage, { status })
  }

  return HttpResponse.json(defaultJsonMessage, { status })
}
```
</details>

- **Parameters**:
  - `req: Request`
- **Return Type**: `Promise<any>`
- **Calls**:
  - `qs.get`
  - `delay (from msw)`
  - `Number`
  - `HttpResponse.json`
  - `JSON.parse`

---