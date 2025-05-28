[⬅️ Back to Table of Contents](../index.md)

# 📄 `changelog.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 5 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 3 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`scripts/changelog.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `CommitInfo` | `@vueuse/metadata` |
| `ContributorInfo` | `@vueuse/metadata` |
| `md5` | `md5` |
| `Git` | `simple-git` |
| `functions` | `../packages/metadata/metadata` |
| `uniq` | `./utils` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `cache` | `CommitInfo[] | undefined` | let/var | `*not shown*` | ✗ |
| `logs` | `CommitInfo[]` | let/var | `(await git.log({ maxCount: count })).all.filter((i) => {
    return i.message.includes('chore: release')
      || i.message.includes('!')
      || i.message.startsWith('feat')
      || i.message.startsWith('fix')
  }) as CommitInfo[]` | ✗ |
| `raw` | `any` | let/var | `await git.raw(['diff-tree', '--no-commit-id', '--name-only', '-r', log.hash])` | ✗ |
| `map` | `Record<string, ContributorInfo>` | let/var | `{}` | ✗ |
| `result` | `(readonly [string, ContributorInfo[]])[]` | let/var | `await Promise.all(functions.map(async (i) => {
    return [i.name, await getContributorsAt(`packages/${i.package}/${i.name}`)] as const
  }))` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| async-function | `getChangeLog` | git.log({ maxCount: count }), git.raw(['diff-tree', '--no-commit-id', '--name-only', '-r', log.hash]) | *none* |
| async-function | `getContributorsAt` | git.raw(['log', '--pretty=format:"%an|%ae"', '--', path]) | *none* |
| async-function | `getFunctionContributors` | Promise.all(functions.map(async (i) => {
    return [i.name, await getContributorsAt(`packages/${i.package}/${i.name}`)] as const
  })), getContributorsAt(`packages/${i.package}/${i.name}`) | Promise.all |


---

## Functions

### `getChangeLog(count: number): Promise<CommitInfo[]>`

<details><summary>Code</summary>

```ts
export async function getChangeLog(count = 200) {
  if (cache)
    return cache

  const logs = (await git.log({ maxCount: count })).all.filter((i) => {
    return i.message.includes('chore: release')
      || i.message.includes('!')
      || i.message.startsWith('feat')
      || i.message.startsWith('fix')
  }) as CommitInfo[]

  for (const log of logs) {
    if (log.message.includes('chore: release')) {
      log.version = log.message.split(' ')[2].trim()
      continue
    }
    const raw = await git.raw(['diff-tree', '--no-commit-id', '--name-only', '-r', log.hash])
    delete log.body
    const files = raw.replace(/\\/g, '/').trim().split('\n')
    log.functions = uniq(
      files
        .map(i => i.match(/^packages\/\w+\/(\w+)\/\w+\.ts$/)?.[1])
        .filter(Boolean),
    )
  }

  const result = logs.filter(i => i.functions?.length || i.version)
  cache = result
  return result
}
```
</details>

- **Parameters**:
  - `count: number`
- **Return Type**: `Promise<CommitInfo[]>`
- **Calls**:
  - `(await git.log({ maxCount: count })).all.filter`
  - `git.log`
  - `i.message.includes`
  - `i.message.startsWith`
  - `log.message.includes`
  - `log.message.split(' ')[2].trim`
  - `git.raw`
  - `raw.replace(/\\/g, '/').trim().split`
  - `uniq (from ./utils)`
  - `files
        .map(i => i.match(/^packages\/\w+\/(\w+)\/\w+\.ts$/)?.[1])
        .filter`
  - `logs.filter`
### `getContributorsAt(path: string): Promise<ContributorInfo[]>`

<details><summary>Code</summary>

```ts
export async function getContributorsAt(path: string) {
  try {
    const list = (await git.raw(['log', '--pretty=format:"%an|%ae"', '--', path]))
      .split('\n')
      .map(i => i.slice(1, -1).split('|') as [string, string])
    const map: Record<string, ContributorInfo> = {}

    list
      .filter(i => i[1])
      .forEach((i) => {
        if (!map[i[1]]) {
          map[i[1]] = {
            name: i[0],
            count: 0,
            hash: md5(i[1]),
          }
        }
        map[i[1]].count++
      })

    return Object.values(map).sort((a, b) => b.count - a.count)
  }
  catch (e) {
    console.error(e)
    return []
  }
}
```
</details>

- **Parameters**:
  - `path: string`
- **Return Type**: `Promise<ContributorInfo[]>`
- **Calls**:
  - `(await git.raw(['log', '--pretty=format:"%an|%ae"', '--', path]))
      .split('\n')
      .map`
  - `i.slice(1, -1).split`
  - `list
      .filter(i => i[1])
      .forEach`
  - `md5 (from md5)`
  - `Object.values(map).sort`
  - `console.error`
### `getFunctionContributors(): Promise<{ [k: string]: ContributorInfo[]; }>`

<details><summary>Code</summary>

```ts
export async function getFunctionContributors() {
  const result = await Promise.all(functions.map(async (i) => {
    return [i.name, await getContributorsAt(`packages/${i.package}/${i.name}`)] as const
  }))
  return Object.fromEntries(result)
}
```
</details>

- **Return Type**: `Promise<{ [k: string]: ContributorInfo[]; }>`
- **Calls**:
  - `Promise.all`
  - `functions.map`
  - `getContributorsAt`
  - `Object.fromEntries`

---