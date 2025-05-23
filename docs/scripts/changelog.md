[⬅️ Back to Table of Contents](../index.md)

# 📄 `changelog.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 0
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---