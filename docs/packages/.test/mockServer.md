[⬅️ Back to Table of Contents](../../index.md)

# 📄 `mockServer.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 7
- **Interfaces**: 0
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---