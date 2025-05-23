[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `_demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Classes](#classes)

## 📊 Analysis Summary

- **Functions**: 4
- **Classes**: 1
- **Imports**: 9
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/rxjs/watchExtractedObservable/_demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Observable` | `rxjs` |
| `watchExtractedObservable` | `@vueuse/rxjs` |
| `fromEvent` | `rxjs` |
| `map` | `rxjs/operators` |
| `skip` | `rxjs/operators` |
| `tap` | `rxjs/operators` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `reactive` | `vue` |


---

## Functions

### `AudioPlayer.togglePlay(): Promise<void>`

<details><summary>Code</summary>

```ts
async togglePlay() {
    if (this.audio.paused)
      return this.play()
    else
      return this.pause()
  }
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `this.play`
  - `this.pause`
### `AudioPlayer.play(): Promise<void>`

<details><summary>Code</summary>

```ts
async play(): Promise<void> {
    if (!this.audio.paused)
      return

    return this.audio.play()
  }
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `this.audio.play`
### `AudioPlayer.pause(): Promise<void>`

<details><summary>Code</summary>

```ts
async pause(): Promise<void> {
    if (this.audio.paused)
      return

    return this.audio.pause()
  }
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `this.audio.pause`
### `AudioPlayer.seek(percentage: number): void`

<details><summary>Code</summary>

```ts
seek(percentage: number) {
    this.audio.currentTime = percentage * this.audio.duration
  }
```
</details>

- **JSDoc**:
```ts
/**
   * @param percentage - A number in the range [0;1]
   */
```

- **Parameters**:
  - `percentage: number`
- **Return Type**: `void`

---

## Classes

### `AudioPlayer`

<details><summary>Class Code</summary>

```ts
class AudioPlayer {
  public readonly reachEnd$: Observable<unknown>

  /**
   * Player progress as a number within [0;1]
   */
  public readonly progress$: Observable<number>

  constructor(
    public readonly audio: HTMLAudioElement,
  ) {
    let _magic = false
    this.reachEnd$ = fromEvent(this.audio, 'ended')
      .pipe(
        tap(() => {
          _magic = !_magic
        }),
        map(() => _magic),
      )

    this.progress$ = fromEvent(this.audio, 'timeupdate')
      .pipe(
        skip(1),
        map(() => this.audio.currentTime / this.audio.duration),
      )
  }

  async togglePlay() {
    if (this.audio.paused)
      return this.play()
    else
      return this.pause()
  }

  async play(): Promise<void> {
    if (!this.audio.paused)
      return

    return this.audio.play()
  }

  async pause(): Promise<void> {
    if (this.audio.paused)
      return

    return this.audio.pause()
  }

  /**
   * @param percentage - A number in the range [0;1]
   */
  seek(percentage: number) {
    this.audio.currentTime = percentage * this.audio.duration
  }
}
```
</details>

#### Methods

##### `togglePlay(): Promise<void>`

<details><summary>Code</summary>

```ts
async togglePlay() {
    if (this.audio.paused)
      return this.play()
    else
      return this.pause()
  }
```
</details>

##### `play(): Promise<void>`

<details><summary>Code</summary>

```ts
async play(): Promise<void> {
    if (!this.audio.paused)
      return

    return this.audio.play()
  }
```
</details>

##### `pause(): Promise<void>`

<details><summary>Code</summary>

```ts
async pause(): Promise<void> {
    if (this.audio.paused)
      return

    return this.audio.pause()
  }
```
</details>

##### `seek(percentage: number): void`

<details><summary>Code</summary>

```ts
seek(percentage: number) {
    this.audio.currentTime = percentage * this.audio.duration
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