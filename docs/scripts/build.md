[⬅️ Back to Table of Contents](../index.md)

# 📄 `build.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 11
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`scripts/build.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `assert` | `node:assert` |
| `exec` | `node:child_process` |
| `path` | `node:path` |
| `process` | `node:process` |
| `fileURLToPath` | `node:url` |
| `consola` | `consola` |
| `YAML` | `yaml` |
| `packages` | `../meta/packages` |
| `version` | `../package.json` |
| `metadata` | `../packages/metadata/metadata` |
| `updateImport` | `./utils` |


---

## Functions

### `buildMetaFiles(): Promise<void>`

<details><summary>Code</summary>

```ts
async function buildMetaFiles() {
  const workspaceData = YAML.parse(await fs.readFile(path.resolve(rootDir, 'pnpm-workspace.yaml'), 'utf-8'))

  for (const { name } of packages) {
    const packageRoot = path.resolve(rootDir, 'packages', name)

    const packageJSON = JSON.parse(await fs.readFile(path.join(packageRoot, 'package.json'), { encoding: 'utf8' }))
    for (const [key, value] of Object.entries(packageJSON.dependencies || {})) {
      if (key.startsWith('@vueuse/')) {
        packageJSON.dependencies[key] = version
      }
      else if ((value as string).startsWith('catalog:')) {
        const resolved = workspaceData.catalog[key as string]
        if (!resolved)
          throw new Error(`Cannot resolve catalog entry for ${key}`)
        packageJSON.dependencies[key] = resolved
      }
    }
    delete packageJSON.devDependencies
  }
}
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `YAML.parse`
  - `fs.readFile`
  - `path.resolve`
  - `JSON.parse`
  - `path.join`
  - `Object.entries`
  - `key.startsWith`
  - `(value as string).startsWith`
### `build(): Promise<void>`

<details><summary>Code</summary>

```ts
async function build() {
  consola.info('Clean up')
  exec('pnpm run clean', { stdio: 'inherit' })

  consola.info('Generate Imports')
  await updateImport(metadata)

  consola.info('Rollup')
  exec(`pnpm run build:rollup${watch ? ' -- --watch' : ''}`, { stdio: 'inherit' })

  await buildMetaFiles()
}
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `consola.info`
  - `exec (from node:child_process)`
  - `updateImport (from ./utils)`
  - `buildMetaFiles`
### `cli(): Promise<void>`

<details><summary>Code</summary>

```ts
async function cli() {
  try {
    await build()
  }
  catch (e) {
    console.error(e)
    process.exit(1)
  }
}
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `build`
  - `console.error`
  - `process.exit`

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