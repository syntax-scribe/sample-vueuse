[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 📦 Imports | 9 |
| 📊 Variables & Constants | 4 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)

## 🛠️ File Location:
📂 **`packages/rxjs/useSubject/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `BehaviorSubject` | `rxjs` |
| `Subject` | `rxjs` |
| `first` | `rxjs/operators` |
| `skip` | `rxjs/operators` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `useInjectedSetup` | `../../.test` |
| `useSubject` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `subject` | `any` | const | `new Subject<boolean>()` | ✗ |
| `subject` | `any` | const | `new BehaviorSubject(false)` | ✗ |
| `subject` | `any` | let/var | `new BehaviorSubject(false)` | ✗ |
| `value` | `unknown` | let/var | `await new Promise((resolve) => {
      subject.pipe(skip(1), first()).subscribe(resolve)

      const subjectRef = useSubject(subject)

      subjectRef.value = true
    })` | ✗ |


---