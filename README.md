# Unswitch

[![npm version](https://img.shields.io/npm/v/unswitch.svg)](https://www.npmjs.com/package/unswitch)
[![gzip size](http://img.badgesize.io/https://unpkg.com/unswitch/dist/unswitch.es.js?compression=gzip)](https://unpkg.com/unswitch)
[![license](https://img.shields.io/npm/l/unswitch.svg)](https://github.com/vaneenige/unswitch/blob/master/LICENSE)
[![dependencies](https://img.shields.io/badge/dependencies-none-ff69b4.svg)](https://github.com/vaneenige/unswitch/blob/master/package.json)

Unswitch is a tiny event handler for Switch controllers on the web based on the Gamepad API. Attach callbacks to button presses (up & down) and the joystick!

通过蓝牙连接 switch 手柄，然后就可以用这个库获取事件了

## Install

```
$ npm install --save unswitch
```

> Use script tags or modules? Check out the version on [unpkg](https://unpkg.com/unswitch)!

## Setup
Connecting a Switch controller is easy: pair it with bluetooth and you're ready to go! This library doesn't listen to `connected` or `disconnected` events but in some cases it might be useful. Here's how you can listen to these events:

```js
window.addEventListener("gamepadconnected", ({ gamepad }) => {});
```

```js
window.addEventListener("gamepaddisconnected", ({ gamepad }) => {});
```

## Usage

```js
// Import the library
import Unswitch from 'unswitch';

// Observe a controller
const unswitch = new Unswitch({
  side: 'L', // or R
  b: p => {},
  a: p => {},
  y: p => {},
  x: p => {},
  sl: p => {},
  sr: p => {},
  minus: p => {},
  plus: p => {},
  lstick: p => {},
  rstick: p => {},
  home: p => {},
  screenshot: p => {},
  bumper: p => {}, // L or R
  trigger: p => {}, // ZL or ZR
  axes: p => {},
});

function render() {
  // Call the update function manually
  unswitch.update();
  requestAnimationFrame(render);
}

render();
```

It's possible to connect up to two controllers at the same time. To make this work `side` is to be passed with either `L` (left) or `R` (right) for the controllers respectively. Calling `unswitch.update()` will check every button for a change in state. If a callback is provided the new state is passed along. The axis works in the same way, but instead of a `boolean` it will return a `number` from 0 to 8. Number 0 to 7 are for the joystick positions going clockwise, number 8 is used as default (center).

> Buttons are mapped based on a single controller positioned horizontally.

## Contribute

Are you excited about this library and have interesting ideas on how to improve it? Please tell me or contribute directly! 🙌

```
npm install > npm run demo > http://localhost:8080
```

## License

MIT © <a href="https://use-the-platform.com">Colin van Eenige</a>


