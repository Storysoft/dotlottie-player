# dotLottie Player Web Component

![Awesome Vector Animations](/gitAssets/readmeBanner.svg)

This a fork of [@dotlottie/player-component](https://github.com/dotlottie/player-component), made to address issues with canvas-rendering, aspect-ratio settings, updated Typescript configuration and more effective handlig of compressed dotLotties. It is however still a fork, so credit where credit's due.

## Installation

### In HTML, import from CDN or from the local installation

- Import from CDN.

```html
<script src="https://unpkg.com/@johanaarstein/dotlottie-player@latest/dist/dotlottie-player.js"></script>
```

- Import from local node_modules directory.

```html
<script src="/node_modules/@johanaarstein/dotlottie-player/dist/dotlottie-player.js"></script>
```

### In Javascript or TypeScript

1. Install package using npm or yarn.

```shell
npm install --save @johanaarstein/dotlottie-player
```

2. Import package in your code.

```javascript
import '@johanaarstein/dotlottie-player'
```

## WordPress Plugin
<img align="left" width="100" height="100" src="/gitAssets/wpIcon.svg">

We've made a free WordPress plugin that works with Gutenberg Blocks, Elementor and Divi Builder: [AM LottiePlayer](https://wordpress.org/plugins/am-lottieplayer/). It has all the functionality of this package, with a helpful user interface.

It's also super lightweight – and only loads on pages where it's in use.

## Usage

### The player component

Add the element `dotlottie-player` and set the `src` property to a URL pointing to a Lottie file – either LottieJSON or dotLottie.

```html
<dotlottie-player
  autoplay
  controls
  loop
  mode="normal"
  src="https://storage.googleapis.com/aarsteinmedia/intro.lottie"
  style="width: 320px"
>
</dotlottie-player>
```

You may set and load animations programmatically as well.

```html
<dotlottie-player autoplay controls loop mode="normal" style="width: 320px"> </dotlottie-player>
```

```js
const player = document.querySelector('dotlottie-player')
player.load('https://storage.googleapis.com/aarsteinmedia/intro.lottie')
```

### ReactJS

1. Import the player and use it like this:

```javascript
import '@johanaarstein/dotlottie-player'

function App() {
  return (
    <div className="App">
      <dotlottie-player
        src="https://storage.googleapis.com/aarsteinmedia/intro.lottie"
        autoplay
        loop
        style={{ height: '100%', width: '100%' }}
      />
    </div>
  )
}

export default App
```

### ReactJS + Typescript

1. Import like this:

```javascript
import '@johanaarstein/dotlottie-player'

function App() {
  return (
    <div className="App">
      <dotlottie-player
        src="https://storage.googleapis.com/aarsteinmedia/intro.lottie"
        autoplay
        loop
        style={{ height: '100%', width: '100%' }}
      />
    </div>
  )
}

export default App
```

2. Create a global.d.ts file in your src folder and add the code below:

```javascript
declare namespace JSX {
  interface IntrinsicElements {
    "dotlottie-player": any
  }
}
```

### NextJS

1. To avoid "window is not defined" import the module inside a useEffect hook, like so:

```javascript
import { useEffect } from 'react'

function App() {

  useEffect(() => {
    import('@johanaarstein/dotlottie-player')
  }, [])

  return (
    <div className="App">
      <dotlottie-player
        src="https://storage.googleapis.com/aarsteinmedia/intro.lottie"
        autoplay
        loop
        style={{ height: '100%', width: '100%' }}
      />
    </div>
  )
}

export default App
```

### NuxtJS / VueJS

1. Update the array of plugins in nuxt.config.js file in your root.

```javascript
plugins: [{ src: '~/plugins/lottie-player', mode: 'client' }]
```

2. Create a plugin folder in your root if it doesnt exist already, add a file named e. g. lottie-player.js with the following content.

```javascript
import * as LottiePlayer from '@johanaarstein/dotlottie-player'
```

3. The component can now be used in your pages or components template tag like below – without any imports necessary.

```javascript
<template>
  <dotlottie-player src="https://storage.googleapis.com/aarsteinmedia/intro.lottie" autoplay loop />
</template>
<script>
export default {}
</script>
```

In VueJS the library/player must be declared as a client side plugin module.

## Properties

| Property              | Attribute             | Description                        | Type                                 | Default           |
| --------------------- | --------------------- | ---------------------------------- | ------------------------------------ | ----------------- |
| `autoplay`            | `autoplay`            | Autoplay animation on load.        | `boolean`                            | `false`           |
| `background`          | `background`          | Background color.                  | `string`                             | `undefined`       |
| `controls`            | `controls`            | Show controls.                     | `boolean`                            | `false`           |
| `count`               | `count`               | Number of times to loop animation. | `number`                             | `undefined`       |
| `direction`           | `direction`           | Direction of animation.            | `number`                             | `1`               |
| `hover`               | `hover`               | Whether to play on mouse hover.    | `boolean`                            | `false`           |
| `loop`                | `loop`                | Whether to loop animation.         | `boolean`                            | `false`           |
| `mode`                | `mode`                | Play mode.                         | `PlayMode.Bounce \| PlayMode.Normal` | `PlayMode.Normal` |
| `preserveAspectRatio` | `preserveAspectRatio` | Aspect ratio.                      | `string`                             | `'xMidYMid meet'` |
| `renderer`            | `renderer`            | Renderer to use.                   | `"svg"`                              | `'svg'`           |
| `speed`               | `speed`               | Animation speed.                   | `number`                             | `1`               |
| `src` _(required)_    | `src`                 | URL to .lottie file.               | `string`                             | `undefined`       |

## Methods

### Load

**`load(src: string) => void`**

Load (and play) a given Lottie animation.

#### Parameters

| Name  | Type     | Description            |
| ----- | -------- | ---------------------- |
| `src` | `string` | URL to a .lottie file. |

#### Returns

Type: `void`

### Pause

**`pause() => void`**

Pause animation play.

#### Returns

Type: `void`

### Play

**`play() => void`**

Start playing animation.

#### Returns

Type: `void`

### Set Direction

**`setDirection(value: number) => void`**

Animation play direction.

#### Parameters

| Name    | Type     | Description       |
| ------- | -------- | ----------------- |
| `value` | `number` | Direction values. |

#### Returns

Type: `void`

### Set Looping

**`setLooping(value: boolean) => void`**

Sets the looping of the animation.

#### Parameters

| Name    | Type      | Description                                              |
| ------- | --------- | -------------------------------------------------------- |
| `value` | `boolean` | Whether to enable looping. Boolean true enables looping. |

#### Returns

Type: `void`

### Set speed

**`setSpeed(value?: number) => void`**

Sets animation play speed.

#### Parameters

| Name    | Type     | Description     |
| ------- | -------- | --------------- |
| `value` | `number` | Playback speed. |

#### Returns

Type: `void`

### Stop

**`stop() => void`**

Stops animation play.

#### Returns

Type: `void`

### Seek

**`seek(value: number | string) => void`**

Seek to a given frame. Frame value can be a number or a percent string (e.g. 50%).

#### Returns

Type: `void`

### Snapshot

**`snapshot(download?: boolean) => string`**

Snapshot the current frame as SVG.
If 'download' argument is boolean true, then a download is triggered in browser.

#### Returns

Type: `string`

### Toggle looping

**`toggleLooping() => void`**

Toggles animation looping.

#### Returns

Type: `void`

### Toggle play

**`togglePlay() => void`**

Toggle playing state.

#### Returns

Type: `void`

### Reload

**`reload() => void`**

Reloads Lottie.

#### Returns

Type: `void`

## Events

The following events are exposed and can be listened to via `addEventListener` calls.

| Name       | Description                                                               |
| ---------- | ------------------------------------------------------------------------- |
| `complete` | Animation is complete (all loops completed).                              |
| `destroyed`| Animation data is destroyed.                                              |
| `error`    | An animation source cannot be parsed, fails to load or has format errors. |
| `frame`    | A new frame is entered.                                                   |
| `freeze`   | Animation is paused due to player being invisible.                        |
| `load`     | Animation data is loaded.                                                 |
| `loop`     | An animation loop is completed.                                           |
| `play`     | Animation starts playing.                                                 |
| `pause`    | Animation is paused.                                                      |
| `ready`    | Animation data is loaded and player is ready.                             |
| `stop`     | Animation is stopped.                                                     |

## Styling

| Custom property                              | Description               | Default                |
| -------------------------------------------- | ------------------------- | ---------------------- |
| --dotlottie-player-toolbar-height            | Toolbar height            | 35px                   |
| --dotlottie-player-toolbar-background-color  | Toolbar background color  | #FFF                   |
| --dotlottie-player-toolbar-icon-color        | Toolbar icon color        | #000                   |
| --dotlottie-player-toolbar-icon-hover-color  | Toolbar icon hover color  | #000                   |
| --dotlottie-player-toolbar-icon-active-color | Toolbar icon active color | #4285f4                |
| --dotlottie-player-seeker-track-color        | Seeker track color        | rgba(0, 0, 0, 0.2)     |
| --dotlottie-player-seeker-thumb-color        | Seeker thumb color        | #4285f4                |

By default there is also a mode:
| Custom property                              | Description               | Default                  |
| -------------------------------------------- | ------------------------- | ------------------------ |
| --dotlottie-player-toolbar-background-color  | Toolbar background color  | #000                     |
| --dotlottie-player-toolbar-icon-color        | Toolbar icon color        | #FFF                     |
| --dotlottie-player-toolbar-icon-hover-color  | Toolbar icon hover color  | #FFF                     |
| --dotlottie-player-seeker-track-color        | Seeker track color        | rgba(255, 255, 255, 0.6) |
| --dotlottie-player-seeker-thumb-color        | Seeker thumb color        | #4285f4                  |

## License

GPL-2.0-or-later
