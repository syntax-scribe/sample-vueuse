[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 7
- **Classes**: 0
- **Imports**: 16
- **Interfaces**: 4
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useMediaControls/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Fn` | `@vueuse/shared` |
| `MaybeRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `ConfigurableDocument` | `../_configurable` |
| `createEventHook` | `@vueuse/shared` |
| `isObject` | `@vueuse/shared` |
| `toRef` | `@vueuse/shared` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `watchIgnorable` | `@vueuse/shared` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `watchEffect` | `vue` |
| `defaultDocument` | `../_configurable` |
| `useEventListener` | `../useEventListener` |


---

## Functions

### `usingElRef(source: MaybeRefOrGetter<any>, cb: (el: T) => void): void`

<details><summary>Code</summary>

```ts
function usingElRef<T = any>(source: MaybeRefOrGetter<any>, cb: (el: T) => void) {
  if (toValue(source))
    cb(toValue(source))
}
```
</details>

- **JSDoc**:
```ts
/**
 * Automatically check if the ref exists and if it does run the cb fn
 */
```

- **Parameters**:
  - `source: MaybeRefOrGetter<any>`
  - `cb: (el: T) => void`
- **Return Type**: `void`
- **Calls**:
  - `toValue (from vue)`
  - `cb`
### `timeRangeToArray(timeRanges: TimeRanges): [number, number][]`

<details><summary>Code</summary>

```ts
function timeRangeToArray(timeRanges: TimeRanges) {
  let ranges: [number, number][] = []

  for (let i = 0; i < timeRanges.length; ++i)
    ranges = [...ranges, [timeRanges.start(i), timeRanges.end(i)]]

  return ranges
}
```
</details>

- **JSDoc**:
```ts
/**
 * Converts a TimeRange object to an array
 */
```

- **Parameters**:
  - `timeRanges: TimeRanges`
- **Return Type**: `[number, number][]`
- **Calls**:
  - `timeRanges.start`
  - `timeRanges.end`
### `tracksToArray(tracks: TextTrackList): UseMediaTextTrack[]`

<details><summary>Code</summary>

```ts
function tracksToArray(tracks: TextTrackList): UseMediaTextTrack[] {
  return Array.from(tracks)
    .map(({ label, kind, language, mode, activeCues, cues, inBandMetadataTrackDispatchType }, id) => ({ id, label, kind, language, mode, activeCues, cues, inBandMetadataTrackDispatchType }))
}
```
</details>

- **JSDoc**:
```ts
/**
 * Converts a TextTrackList object to an array of `UseMediaTextTrack`
 */
```

- **Parameters**:
  - `tracks: TextTrackList`
- **Return Type**: `UseMediaTextTrack[]`
- **Calls**:
  - `Array.from(tracks)
    .map`
### `useMediaControls(target: MaybeRef<HTMLMediaElement | null | undefined>, options: UseMediaControlsOptions): { currentTime: any; duration: any; waiting: any; seeking: any; ended: any; stalled: any; buffered: any; playing: any; rate: any; volume: any; muted: any; tracks: any; selectedTrack: any; enableTrack: (track: number | UseMediaTextTrack, disableTracks?: boolean) => void; ... 5 more ...; onPlaybackError: any; }`

<details><summary>Code</summary>

```ts
export function useMediaControls(target: MaybeRef<HTMLMediaElement | null | undefined>, options: UseMediaControlsOptions = {}) {
  target = toRef(target)
  options = {
    ...defaultOptions,
    ...options,
  }

  const {
    document = defaultDocument,
  } = options

  const listenerOptions = { passive: true }

  const currentTime = shallowRef(0)
  const duration = shallowRef(0)
  const seeking = shallowRef(false)
  const volume = shallowRef(1)
  const waiting = shallowRef(false)
  const ended = shallowRef(false)
  const playing = shallowRef(false)
  const rate = shallowRef(1)
  const stalled = shallowRef(false)
  const buffered = deepRef<[number, number][]>([])
  const tracks = deepRef<UseMediaTextTrack[]>([])
  const selectedTrack = shallowRef<number>(-1)
  const isPictureInPicture = shallowRef(false)
  const muted = shallowRef(false)

  const supportsPictureInPicture = document && 'pictureInPictureEnabled' in document

  // Events
  const sourceErrorEvent = createEventHook<Event>()
  const playbackErrorEvent = createEventHook<Event>()

  /**
   * Disables the specified track. If no track is specified then
   * all tracks will be disabled
   *
   * @param track The id of the track to disable
   */
  const disableTrack = (track?: number | UseMediaTextTrack) => {
    usingElRef<HTMLMediaElement>(target, (el) => {
      if (track) {
        const id = typeof track === 'number' ? track : track.id
        el.textTracks[id].mode = 'disabled'
      }
      else {
        for (let i = 0; i < el.textTracks.length; ++i)
          el.textTracks[i].mode = 'disabled'
      }

      selectedTrack.value = -1
    })
  }

  /**
   * Enables the specified track and disables the
   * other tracks unless otherwise specified
   *
   * @param track The track of the id of the track to enable
   * @param disableTracks Disable all other tracks
   */
  const enableTrack = (track: number | UseMediaTextTrack, disableTracks = true) => {
    usingElRef<HTMLMediaElement>(target, (el) => {
      const id = typeof track === 'number' ? track : track.id

      if (disableTracks)
        disableTrack()

      el.textTracks[id].mode = 'showing'
      selectedTrack.value = id
    })
  }
  /**
   * Toggle picture in picture mode for the player.
   */
  const togglePictureInPicture = () => {
    return new Promise((resolve, reject) => {
      usingElRef<HTMLVideoElement>(target, async (el) => {
        if (supportsPictureInPicture) {
          if (!isPictureInPicture.value) {
            (el as any).requestPictureInPicture().then(resolve).catch(reject)
          }
          else {
            (document as any).exitPictureInPicture().then(resolve).catch(reject)
          }
        }
      })
    })
  }

  /**
   * This will automatically inject sources to the media element. The sources will be
   * appended as children to the media element as `<source>` elements.
   */
  watchEffect(() => {
    if (!document)
      return

    const el = toValue(target)
    if (!el)
      return

    const src = toValue(options.src)
    let sources: UseMediaSource[] = []

    if (!src)
      return

    // Merge sources into an array
    if (typeof src === 'string')
      sources = [{ src }]
    else if (Array.isArray(src))
      sources = src
    else if (isObject(src))
      sources = [src]

    // Clear the sources
    el.querySelectorAll('source').forEach((e) => {
      e.remove()
    })

    // Add new sources
    sources.forEach(({ src, type, media }) => {
      const source = document.createElement('source')

      source.setAttribute('src', src)
      source.setAttribute('type', type || '')
      source.setAttribute('media', media || '')

      useEventListener(source, 'error', sourceErrorEvent.trigger, listenerOptions)

      el.appendChild(source)
    })

    // Finally, load the new sources.
    el.load()
  })

  /**
   * Apply composable state to the element, also when element is changed
   */
  watch([target, volume], () => {
    const el = toValue(target)
    if (!el)
      return

    el.volume = volume.value
  })

  watch([target, muted], () => {
    const el = toValue(target)
    if (!el)
      return

    el.muted = muted.value
  })

  watch([target, rate], () => {
    const el = toValue(target)
    if (!el)
      return

    el.playbackRate = rate.value
  })

  /**
   * Load Tracks
   */
  watchEffect(() => {
    if (!document)
      return

    const textTracks = toValue(options.tracks)
    const el = toValue(target)

    if (!textTracks || !textTracks.length || !el)
      return

    /**
     * The MediaAPI provides an API for adding text tracks, but they don't currently
     * have an API for removing text tracks, so instead we will just create and remove
     * the tracks manually using the HTML api.
     */
    el.querySelectorAll('track').forEach(e => e.remove())

    textTracks.forEach(({ default: isDefault, kind, label, src, srcLang }, i) => {
      const track = document.createElement('track')

      track.default = isDefault || false
      track.kind = kind
      track.label = label
      track.src = src
      track.srclang = srcLang

      if (track.default)
        selectedTrack.value = i

      el.appendChild(track)
    })
  })

  /**
   * This will allow us to update the current time from the timeupdate event
   * without setting the medias current position, but if the user changes the
   * current time via the ref, then the media will seek.
   *
   * If we did not use an ignorable watch, then the current time update from
   * the timeupdate event would cause the media to stutter.
   */
  const { ignoreUpdates: ignoreCurrentTimeUpdates } = watchIgnorable(currentTime, (time) => {
    const el = toValue(target)
    if (!el)
      return

    el.currentTime = time
  })

  /**
   * Using an ignorable watch so we can control the play state using a ref and not
   * a function
   */
  const { ignoreUpdates: ignorePlayingUpdates } = watchIgnorable(playing, (isPlaying) => {
    const el = toValue(target)
    if (!el)
      return

    if (isPlaying) {
      el.play().catch((e) => {
        playbackErrorEvent.trigger(e)
        throw e
      })
    }
    else {
      el.pause()
    }
  })

  useEventListener(
    target,
    'timeupdate',
    () => ignoreCurrentTimeUpdates(() => currentTime.value = (toValue(target))!.currentTime),
    listenerOptions,
  )
  useEventListener(
    target,
    'durationchange',
    () => duration.value = (toValue(target))!.duration,
    listenerOptions,
  )
  useEventListener(
    target,
    'progress',
    () => buffered.value = timeRangeToArray((toValue(target))!.buffered),
    listenerOptions,
  )
  useEventListener(
    target,
    'seeking',
    () => seeking.value = true,
    listenerOptions,
  )
  useEventListener(
    target,
    'seeked',
    () => seeking.value = false,
    listenerOptions,
  )
  useEventListener(
    target,
    ['waiting', 'loadstart'],
    () => {
      waiting.value = true
      ignorePlayingUpdates(() => playing.value = false)
    },
    listenerOptions,
  )
  useEventListener(
    target,
    'loadeddata',
    () => waiting.value = false,
    listenerOptions,
  )
  useEventListener(
    target,
    'playing',
    () => {
      waiting.value = false
      ended.value = false
      ignorePlayingUpdates(() => playing.value = true)
    },
    listenerOptions,
  )
  useEventListener(
    target,
    'ratechange',
    () => rate.value = (toValue(target))!.playbackRate,
    listenerOptions,
  )
  useEventListener(
    target,
    'stalled',
    () => stalled.value = true,
    listenerOptions,
  )
  useEventListener(
    target,
    'ended',
    () => ended.value = true,
    listenerOptions,
  )
  useEventListener(
    target,
    'pause',
    () => ignorePlayingUpdates(() => playing.value = false),
    listenerOptions,
  )
  useEventListener(
    target,
    'play',
    () => ignorePlayingUpdates(() => playing.value = true),
    listenerOptions,
  )
  useEventListener(
    target,
    'enterpictureinpicture',
    () => isPictureInPicture.value = true,
    listenerOptions,
  )
  useEventListener(
    target,
    'leavepictureinpicture',
    () => isPictureInPicture.value = false,
    listenerOptions,
  )
  useEventListener(
    target,
    'volumechange',
    () => {
      const el = toValue(target)
      if (!el)
        return

      volume.value = el.volume
      muted.value = el.muted
    },
    listenerOptions,
  )

  /**
   * The following listeners need to listen to a nested
   * object on the target, so we will have to use a nested
   * watch and manually remove the listeners
   */
  const listeners: Fn[] = []

  const stop = watch([target], () => {
    const el = toValue(target)
    if (!el)
      return

    stop()

    listeners[0] = useEventListener(el.textTracks, 'addtrack', () => tracks.value = tracksToArray(el.textTracks), listenerOptions)
    listeners[1] = useEventListener(el.textTracks, 'removetrack', () => tracks.value = tracksToArray(el.textTracks), listenerOptions)
    listeners[2] = useEventListener(el.textTracks, 'change', () => tracks.value = tracksToArray(el.textTracks), listenerOptions)
  })

  // Remove text track listeners
  tryOnScopeDispose(() => listeners.forEach(listener => listener()))

  return {
    currentTime,
    duration,
    waiting,
    seeking,
    ended,
    stalled,
    buffered,
    playing,
    rate,

    // Volume
    volume,
    muted,

    // Tracks
    tracks,
    selectedTrack,
    enableTrack,
    disableTrack,

    // Picture in Picture
    supportsPictureInPicture,
    togglePictureInPicture,
    isPictureInPicture,

    // Events
    onSourceError: sourceErrorEvent.on,
    onPlaybackError: playbackErrorEvent.on,
  }
}
```
</details>

- **Parameters**:
  - `target: MaybeRef<HTMLMediaElement | null | undefined>`
  - `options: UseMediaControlsOptions`
- **Return Type**: `{ currentTime: any; duration: any; waiting: any; seeking: any; ended: any; stalled: any; buffered: any; playing: any; rate: any; volume: any; muted: any; tracks: any; selectedTrack: any; enableTrack: (track: number | UseMediaTextTrack, disableTracks?: boolean) => void; ... 5 more ...; onPlaybackError: any; }`
- **Calls**:
  - `toRef (from @vueuse/shared)`
  - `shallowRef (from vue)`
  - `deepRef (from vue)`
  - `createEventHook (from @vueuse/shared)`
  - `usingElRef`
  - `disableTrack`
  - `(el as any).requestPictureInPicture().then(resolve).catch`
  - `(document as any).exitPictureInPicture().then(resolve).catch`
  - `watchEffect (from vue)`
  - `toValue (from vue)`
  - `Array.isArray`
  - `isObject (from @vueuse/shared)`
  - `el.querySelectorAll('source').forEach`
  - `e.remove`
  - `sources.forEach`
  - `document.createElement`
  - `source.setAttribute`
  - `useEventListener (from ../useEventListener)`
  - `el.appendChild`
  - `el.load`
  - `watch (from vue)`
  - `el.querySelectorAll('track').forEach`
  - `textTracks.forEach`
  - `watchIgnorable (from @vueuse/shared)`
  - `el.play().catch`
  - `playbackErrorEvent.trigger`
  - `el.pause`
  - `ignoreCurrentTimeUpdates`
  - `timeRangeToArray`
  - `ignorePlayingUpdates`
  - `stop`
  - `tracksToArray`
  - `tryOnScopeDispose (from @vueuse/shared)`
  - `listeners.forEach`
  - `listener`
- **Internal Comments**:
```
// Events (x4)
/**
   * Disables the specified track. If no track is specified then
   * all tracks will be disabled
   *
   * @param track The id of the track to disable
   */ (x2)
/**
   * Enables the specified track and disables the
   * other tracks unless otherwise specified
   *
   * @param track The track of the id of the track to enable
   * @param disableTracks Disable all other tracks
   */ (x2)
/**
   * Toggle picture in picture mode for the player.
   */ (x2)
/**
   * This will automatically inject sources to the media element. The sources will be
   * appended as children to the media element as `<source>` elements.
   */ (x3)
// Merge sources into an array
// Clear the sources (x6)
// Add new sources (x4)
// Finally, load the new sources. (x4)
/**
   * Apply composable state to the element, also when element is changed
   */ (x3)
/**
   * Load Tracks
   */ (x3)
/**
     * The MediaAPI provides an API for adding text tracks, but they don't currently
     * have an API for removing text tracks, so instead we will just create and remove
     * the tracks manually using the HTML api.
     */ (x6)
/**
   * This will allow us to update the current time from the timeupdate event
   * without setting the medias current position, but if the user changes the
   * current time via the ref, then the media will seek.
   *
   * If we did not use an ignorable watch, then the current time update from
   * the timeupdate event would cause the media to stutter.
   */ (x2)
/**
   * Using an ignorable watch so we can control the play state using a ref and not
   * a function
   */ (x2)
/**
   * The following listeners need to listen to a nested
   * object on the target, so we will have to use a nested
   * watch and manually remove the listeners
   */ (x2)
// Remove text track listeners (x3)
// Volume (x2)
// Tracks (x2)
// Picture in Picture (x2)
```

### `disableTrack(track: number | UseMediaTextTrack): void`

<details><summary>Code</summary>

```ts
(track?: number | UseMediaTextTrack) => {
    usingElRef<HTMLMediaElement>(target, (el) => {
      if (track) {
        const id = typeof track === 'number' ? track : track.id
        el.textTracks[id].mode = 'disabled'
      }
      else {
        for (let i = 0; i < el.textTracks.length; ++i)
          el.textTracks[i].mode = 'disabled'
      }

      selectedTrack.value = -1
    })
  }
```
</details>

- **Parameters**:
  - `track: number | UseMediaTextTrack`
- **Return Type**: `void`
- **Calls**:
  - `usingElRef`
### `enableTrack(track: number | UseMediaTextTrack, disableTracks: boolean): void`

<details><summary>Code</summary>

```ts
(track: number | UseMediaTextTrack, disableTracks = true) => {
    usingElRef<HTMLMediaElement>(target, (el) => {
      const id = typeof track === 'number' ? track : track.id

      if (disableTracks)
        disableTrack()

      el.textTracks[id].mode = 'showing'
      selectedTrack.value = id
    })
  }
```
</details>

- **Parameters**:
  - `track: number | UseMediaTextTrack`
  - `disableTracks: boolean`
- **Return Type**: `void`
- **Calls**:
  - `usingElRef`
  - `disableTrack`
### `togglePictureInPicture(): Promise<unknown>`

<details><summary>Code</summary>

```ts
() => {
    return new Promise((resolve, reject) => {
      usingElRef<HTMLVideoElement>(target, async (el) => {
        if (supportsPictureInPicture) {
          if (!isPictureInPicture.value) {
            (el as any).requestPictureInPicture().then(resolve).catch(reject)
          }
          else {
            (document as any).exitPictureInPicture().then(resolve).catch(reject)
          }
        }
      })
    })
  }
```
</details>

- **Return Type**: `Promise<unknown>`
- **Calls**:
  - `usingElRef`
  - `(el as any).requestPictureInPicture().then(resolve).catch`
  - `(document as any).exitPictureInPicture().then(resolve).catch`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseMediaSource`

<details><summary>Interface Code</summary>

```ts
export interface UseMediaSource {
  /**
   * The source url for the media
   */
  src: string

  /**
   * The media codec type
   */
  type?: string

  /**
   * Specifies the media query for the resource's intended media.
   */
  media?: string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `src` | `string` | ✗ |  |
| `type` | `string` | ✓ |  |
| `media` | `string` | ✓ |  |

### `UseMediaTextTrackSource`

<details><summary>Interface Code</summary>

```ts
export interface UseMediaTextTrackSource {
  /**
   * Indicates that the track should be enabled unless the user's preferences indicate
   * that another track is more appropriate
   */
  default?: boolean

  /**
   * How the text track is meant to be used. If omitted the default kind is subtitles.
   */
  kind: TextTrackKind

  /**
   * A user-readable title of the text track which is used by the browser
   * when listing available text tracks.
   */
  label: string

  /**
   * Address of the track (.vtt file). Must be a valid URL. This attribute
   * must be specified and its URL value must have the same origin as the document
   */
  src: string

  /**
   * Language of the track text data. It must be a valid BCP 47 language tag.
   * If the kind attribute is set to subtitles, then srclang must be defined.
   */
  srcLang: string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `default` | `boolean` | ✓ |  |
| `kind` | `TextTrackKind` | ✗ |  |
| `label` | `string` | ✗ |  |
| `src` | `string` | ✗ |  |
| `srcLang` | `string` | ✗ |  |

### `UseMediaControlsOptions`

<details><summary>Interface Code</summary>

```ts
interface UseMediaControlsOptions extends ConfigurableDocument {
  /**
   * The source for the media, may either be a string, a `UseMediaSource` object, or a list
   * of `UseMediaSource` objects.
   */
  src?: MaybeRefOrGetter<string | UseMediaSource | UseMediaSource[]>

  /**
   * A list of text tracks for the media
   */
  tracks?: MaybeRefOrGetter<UseMediaTextTrackSource[]>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `src` | `MaybeRefOrGetter<string | UseMediaSource | UseMediaSource[]>` | ✓ |  |
| `tracks` | `MaybeRefOrGetter<UseMediaTextTrackSource[]>` | ✓ |  |

### `UseMediaTextTrack`

<details><summary>Interface Code</summary>

```ts
export interface UseMediaTextTrack {
  /**
   * The index of the text track
   */
  id: number

  /**
   * The text track label
   */
  label: string

  /**
   * Language of the track text data. It must be a valid BCP 47 language tag.
   * If the kind attribute is set to subtitles, then srclang must be defined.
   */
  language: string

  /**
   * Specifies the display mode of the text track, either `disabled`,
   * `hidden`, or `showing`
   */
  mode: TextTrackMode

  /**
   * How the text track is meant to be used. If omitted the default kind is subtitles.
   */
  kind: TextTrackKind

  /**
   * Indicates the track's in-band metadata track dispatch type.
   */
  inBandMetadataTrackDispatchType: string

  /**
   * A list of text track cues
   */
  cues: TextTrackCueList | null

  /**
   * A list of active text track cues
   */
  activeCues: TextTrackCueList | null
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `id` | `number` | ✗ |  |
| `label` | `string` | ✗ |  |
| `language` | `string` | ✗ |  |
| `mode` | `TextTrackMode` | ✗ |  |
| `kind` | `TextTrackKind` | ✗ |  |
| `inBandMetadataTrackDispatchType` | `string` | ✗ |  |
| `cues` | `TextTrackCueList | null` | ✗ |  |
| `activeCues` | `TextTrackCueList | null` | ✗ |  |


---

## Type Aliases

### `UseMediaControlsReturn`

```ts
type UseMediaControlsReturn = ReturnType<typeof useMediaControls>;
```


---