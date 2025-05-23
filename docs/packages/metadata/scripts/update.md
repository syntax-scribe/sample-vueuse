[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `update.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 14
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/metadata/scripts/update.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `PackageIndexes` | `@vueuse/metadata` |
| `VueUseFunction` | `@vueuse/metadata` |
| `VueUsePackage` | `@vueuse/metadata` |
| `existsSync` | `node:fs` |
| `join` | `node:path` |
| `relative` | `node:path` |
| `resolve` | `node:path` |
| `fileURLToPath` | `node:url` |
| `matter` | `gray-matter` |
| `Git` | `simple-git` |
| `glob` | `tinyglobby` |
| `ecosystemFunctions` | `../../../meta/ecosystem-functions` |
| `packages` | `../../../meta/packages` |
| `getCategories` | `../utils` |


---

## Functions

### `listFunctions(dir: string, ignore: string[]): Promise<any>`

<details><summary>Code</summary>

```ts
export async function listFunctions(dir: string, ignore: string[] = []) {
  const files = await glob('*', {
    onlyDirectories: true,
    cwd: dir,
    ignore: [
      '_*',
      'dist',
      'node_modules',
      ...ignore,
    ],
  })
  files.sort()
  return files.map(path => path.endsWith('/') ? path.slice(0, -1) : path)
}
```
</details>

- **Parameters**:
  - `dir: string`
  - `ignore: string[]`
- **Return Type**: `Promise<any>`
- **Calls**:
  - `glob (from tinyglobby)`
  - `files.sort`
  - `files.map`
  - `path.endsWith`
  - `path.slice`
### `readMetadata(): Promise<PackageIndexes>`

<details><summary>Code</summary>

```ts
export async function readMetadata() {
  const indexes: PackageIndexes = {
    packages: {},
    categories: [],
    functions: [
      ...ecosystemFunctions,
    ],
  }

  for (const info of packages) {
    if (info.utils)
      continue

    const dir = join(DIR_SRC, info.name)

    const functions = await listFunctions(dir)

    const pkg: VueUsePackage = {
      ...info,
      dir: relative(DIR_ROOT, dir).replace(/\\/g, '/'),
      docs: info.addon ? `${DOCS_URL}/${info.name}/README.html` : undefined,
    }

    indexes.packages[info.name] = pkg

    await Promise.all(functions.map(async (fnName) => {
      const mdPath = join(dir, fnName, 'index.md')
      const tsPath = join(dir, fnName, 'index.ts')

      const fn: VueUseFunction = {
        name: fnName,
        package: pkg.name,
        lastUpdated: +await git.raw(['log', '-1', '--format=%at', tsPath]) * 1000,
      }

      if (existsSync(join(dir, fnName, 'component.ts')))
        fn.component = true
      if (existsSync(join(dir, fnName, 'directive.ts')))
        fn.directive = true

      if (!existsSync(mdPath)) {
        fn.internal = true
        indexes.functions.push(fn)
        return
      }

      fn.docs = `${DOCS_URL}/${pkg.name}/${fnName}/`

      const mdRaw = await fs.readFile(mdPath, 'utf-8')

      const { content: md, data: frontmatter } = matter(mdRaw)
      const category = frontmatter.category

      let alias = frontmatter.alias
      if (typeof alias === 'string')
        alias = alias.split(',').map(s => s.trim()).filter(Boolean)
      let related = frontmatter.related
      if (typeof related === 'string')
        related = related.split(',').map(s => s.trim()).filter(Boolean)
      else if (Array.isArray(related))
        related = related.map(s => s.trim()).filter(Boolean)

      let description = (
        md
          // normalize newlines
          .replace(/\r\n/g, '\n')
          // remove ::: tip blocks
          .replace(/(:{3,}(?=[^:\n]*\n))[^\n]*\n[\s\S]*?\1 *(?=\n)/g, '')
          // remove headers
          .match(/#(?=\s).*\n+(.+?)(?:, |\. |\n|\.\n)/) || []
      )[1] || ''

      description = description.trim()
      description = description.charAt(0).toLowerCase() + description.slice(1)

      fn.category = ['core', 'shared'].includes(pkg.name) ? category : `@${pkg.display}`
      fn.description = description

      if (description.includes('DEPRECATED') || frontmatter.deprecated)
        fn.deprecated = true

      if (alias?.length)
        fn.alias = alias

      if (related?.length)
        fn.related = related

      if (pkg.submodules)
        fn.importPath = `${pkg.name}/${fn.name}`

      indexes.functions.push(fn)
    }))
  }

  indexes.functions.sort((a, b) => a.name.localeCompare(b.name))
  indexes.categories = getCategories(indexes.functions)

  // interop related
  indexes.functions.forEach((fn) => {
    if (!fn.related)
      return

    fn.related.forEach((name) => {
      const target = indexes.functions.find(f => f.name === name)
      if (!target)
        throw new Error(`Unknown related function: ${name}`)
      if (!target.related)
        target.related = []
      if (!target.related.includes(fn.name))
        target.related.push(fn.name)
    })
  })
  indexes.functions.forEach(fn => fn.related?.sort())

  return indexes
}
```
</details>

- **Return Type**: `Promise<PackageIndexes>`
- **Calls**:
  - `join (from node:path)`
  - `listFunctions`
  - `relative(DIR_ROOT, dir).replace`
  - `Promise.all`
  - `functions.map`
  - `git.raw`
  - `existsSync (from node:fs)`
  - `indexes.functions.push`
  - `fs.readFile`
  - `matter (from gray-matter)`
  - `alias.split(',').map(s => s.trim()).filter`
  - `related.split(',').map(s => s.trim()).filter`
  - `Array.isArray`
  - `related.map(s => s.trim()).filter`
  - `md
          // normalize newlines
          .replace(/\r\n/g, '\n')
          // remove ::: tip blocks
          .replace(/(:{3,}(?=[^:\n]*\n))[^\n]*\n[\s\S]*?\1 *(?=\n)/g, '')
          // remove headers
          .match`
  - `description.trim`
  - `description.charAt(0).toLowerCase`
  - `description.slice`
  - `['core', 'shared'].includes`
  - `description.includes`
  - `indexes.functions.sort`
  - `a.name.localeCompare`
  - `getCategories (from ../utils)`
  - `indexes.functions.forEach`
  - `fn.related.forEach`
  - `indexes.functions.find`
  - `target.related.includes`
  - `target.related.push`
  - `fn.related?.sort`
- **Internal Comments**:
```
// interop related (x5)
```

### `run(): Promise<void>`

<details><summary>Code</summary>

```ts
async function run() {
  const indexes = await readMetadata()
  await fs.writeFile(join(DIR_PACKAGE, 'index.json'), `${JSON.stringify(indexes, null, 2)}\n`)
}
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `readMetadata`
  - `fs.writeFile`
  - `join (from node:path)`
  - `JSON.stringify`

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