[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 5 |
| 🧱 Classes | 0 |
| 📦 Imports | 11 |
| 📊 Variables & Constants | 2 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 4 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 2 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useSpeechSynthesis/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `toRef` | `@vueuse/shared` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `computed` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useSupported` | `../useSupported` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `synth` | `SpeechSynthesis` | const | `window && (window as any).speechSynthesis as SpeechSynthesis` | ✗ |
| `newUtterance` | `SpeechSynthesisUtterance` | const | `new SpeechSynthesisUtterance(spokenText.value)` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `watch` | watch | *none* | *none* |
| `watch` | watch | *none* | *none* |
| `watch` | watch | *none* | *none* |


---

## Functions

### `useSpeechSynthesis(text: MaybeRefOrGetter<string>, options: UseSpeechSynthesisOptions): { isSupported: any; isPlaying: any; status: any; utterance: any; error: any; stop: () => void; toggle: (value?: boolean) => void; speak: () => void; }`

<details><summary>Code</summary>

```ts
export function useSpeechSynthesis(
  text: MaybeRefOrGetter<string>,
  options: UseSpeechSynthesisOptions = {},
) {
  const {
    pitch = 1,
    rate = 1,
    volume = 1,
    window = defaultWindow,
  } = options

  const synth = window && (window as any).speechSynthesis as SpeechSynthesis
  const isSupported = useSupported(() => synth)

  const isPlaying = shallowRef(false)
  const status = shallowRef<UseSpeechSynthesisStatus>('init')

  const spokenText = toRef(text || '')
  const lang = toRef(options.lang || 'en-US')
  const error = shallowRef<SpeechSynthesisErrorEvent | undefined>(undefined)

  const toggle = (value = !isPlaying.value) => {
    isPlaying.value = value
  }

  const bindEventsForUtterance = (utterance: SpeechSynthesisUtterance) => {
    utterance.lang = toValue(lang)
    utterance.voice = toValue(options.voice) || null
    utterance.pitch = toValue(pitch)
    utterance.rate = toValue(rate)
    utterance.volume = volume

    utterance.onstart = () => {
      isPlaying.value = true
      status.value = 'play'
    }

    utterance.onpause = () => {
      isPlaying.value = false
      status.value = 'pause'
    }

    utterance.onresume = () => {
      isPlaying.value = true
      status.value = 'play'
    }

    utterance.onend = () => {
      isPlaying.value = false
      status.value = 'end'
    }

    utterance.onerror = (event) => {
      error.value = event
    }
  }

  const utterance = computed(() => {
    isPlaying.value = false
    status.value = 'init'
    const newUtterance = new SpeechSynthesisUtterance(spokenText.value)
    bindEventsForUtterance(newUtterance)
    return newUtterance
  })

  const speak = () => {
    synth!.cancel()
    if (utterance)
      synth!.speak(utterance.value)
  }

  const stop = () => {
    synth!.cancel()
    isPlaying.value = false
  }

  if (isSupported.value) {
    bindEventsForUtterance(utterance.value)

    watch(lang, (lang) => {
      if (utterance.value && !isPlaying.value)
        utterance.value.lang = lang
    })

    if (options.voice) {
      watch(options.voice, () => {
        synth!.cancel()
      })
    }

    watch(isPlaying, () => {
      if (isPlaying.value)
        synth!.resume()
      else
        synth!.pause()
    })
  }

  tryOnScopeDispose(() => {
    isPlaying.value = false
  })

  return {
    isSupported,
    isPlaying,
    status,
    utterance,
    error,

    stop,
    toggle,
    speak,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive SpeechSynthesis.
 *
 * @see https://vueuse.org/useSpeechSynthesis
 * @see https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesis SpeechSynthesis
 */
```

- **Parameters**:
  - `text: MaybeRefOrGetter<string>`
  - `options: UseSpeechSynthesisOptions`
- **Return Type**: `{ isSupported: any; isPlaying: any; status: any; utterance: any; error: any; stop: () => void; toggle: (value?: boolean) => void; speak: () => void; }`
- **Calls**:
  - `useSupported (from ../useSupported)`
  - `shallowRef (from vue)`
  - `toRef (from @vueuse/shared)`
  - `toValue (from vue)`
  - `computed (from vue)`
  - `bindEventsForUtterance`
  - `synth!.cancel`
  - `synth!.speak`
  - `watch (from vue)`
  - `synth!.resume`
  - `synth!.pause`
  - `tryOnScopeDispose (from @vueuse/shared)`
### `toggle(value: boolean): void`

<details><summary>Code</summary>

```ts
(value = !isPlaying.value) => {
    isPlaying.value = value
  }
```
</details>

- **Parameters**:
  - `value: boolean`
- **Return Type**: `void`
### `bindEventsForUtterance(utterance: SpeechSynthesisUtterance): void`

<details><summary>Code</summary>

```ts
(utterance: SpeechSynthesisUtterance) => {
    utterance.lang = toValue(lang)
    utterance.voice = toValue(options.voice) || null
    utterance.pitch = toValue(pitch)
    utterance.rate = toValue(rate)
    utterance.volume = volume

    utterance.onstart = () => {
      isPlaying.value = true
      status.value = 'play'
    }

    utterance.onpause = () => {
      isPlaying.value = false
      status.value = 'pause'
    }

    utterance.onresume = () => {
      isPlaying.value = true
      status.value = 'play'
    }

    utterance.onend = () => {
      isPlaying.value = false
      status.value = 'end'
    }

    utterance.onerror = (event) => {
      error.value = event
    }
  }
```
</details>

- **Parameters**:
  - `utterance: SpeechSynthesisUtterance`
- **Return Type**: `void`
- **Calls**:
  - `toValue (from vue)`
### `speak(): void`

<details><summary>Code</summary>

```ts
() => {
    synth!.cancel()
    if (utterance)
      synth!.speak(utterance.value)
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `synth!.cancel`
  - `synth!.speak`
### `stop(): void`

<details><summary>Code</summary>

```ts
() => {
    synth!.cancel()
    isPlaying.value = false
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `synth!.cancel`

---

## Interfaces

### `UseSpeechSynthesisOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseSpeechSynthesisOptions extends ConfigurableWindow {
  /**
   * Language for SpeechSynthesis
   *
   * @default 'en-US'
   */
  lang?: MaybeRefOrGetter<string>
  /**
   * Gets and sets the pitch at which the utterance will be spoken at.
   *
   * @default 1
   */
  pitch?: MaybeRefOrGetter<SpeechSynthesisUtterance['pitch']>
  /**
   * Gets and sets the speed at which the utterance will be spoken at.
   *
   * @default 1
   */
  rate?: MaybeRefOrGetter<SpeechSynthesisUtterance['rate']>
  /**
   * Gets and sets the voice that will be used to speak the utterance.
   */
  voice?: MaybeRef<SpeechSynthesisVoice>
  /**
   * Gets and sets the volume that the utterance will be spoken at.
   *
   * @default 1
   */
  volume?: SpeechSynthesisUtterance['volume']
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `lang` | `MaybeRefOrGetter<string>` | ✓ |  |
| `pitch` | `MaybeRefOrGetter<SpeechSynthesisUtterance['pitch']>` | ✓ |  |
| `rate` | `MaybeRefOrGetter<SpeechSynthesisUtterance['rate']>` | ✓ |  |
| `voice` | `MaybeRef<SpeechSynthesisVoice>` | ✓ |  |
| `volume` | `SpeechSynthesisUtterance['volume']` | ✓ |  |


---

## Type Aliases

### `UseSpeechSynthesisStatus`

```ts
type UseSpeechSynthesisStatus = 'init' | 'play' | 'pause' | 'end';
```

### `UseSpeechSynthesisReturn`

```ts
type UseSpeechSynthesisReturn = ReturnType<typeof useSpeechSynthesis>;
```


---