# react-native-blobular
The [Man in Blue](https://www.themaninblue.com)'s awesome Blobular, ported to React Native. Find the original experiment [here](https://themaninblue.com/experiment/Blobular/)!

<p align="center">
  <img src="./bin/out.gif" width="300" height="633">
</p>

## 🚀 Getting Started

Using [`npm`]():

```sh
npm install --save react-native-blobular
```

Using [`yarn`]():

```sh
yarn add react-native-blobular
```

This project depends on [react-native-svg](https://github.com/react-native-community/react-native-svg), so be sure that the library has been [linked](https://github.com/react-native-community/react-native-svg#installation) if you're running anything less than [react-native@0.60](https://facebook.github.io/react-native/blog/2019/07/03/version-60).

## ✍️ Example
It's pretty simple, just embed a `<Blobular />` inside your `render` method, then listen for the `onBlobular` callback, where you can allocate a number of `Blob`s for your user to play around with.

```javascript
import React from 'react';
import { Dimensions } from 'react-native';
import uuidv4 from 'uuid/v4';

import Blobular, { Blob } from 'react-native-blobular';

const { width, height } = Dimensions
  .get('window');

export default () => (
  <Blobular
    onBlobular={({ putBlob }) => putBlob(
      new Blob(
        uuidv4(), // unique id
        100, // radius
        75, // viscosity
        50, // min radius
      ),
      width * 0.5,
      height * 0.5,
    )}
  />
);
```

You can also suppress user interaction by supplying `pointerEvents="none"` to your `<Blobular />` component, and instead use the `blobular` instance returned in the callback to programmatically manipulate what's on screen.

## 📌 Props

Property | Type | Required | Description
:--- | :--- | :--- | :--- 
width|number|no|Width of the view.
height|number|no|Height of the view.
renderBlob|func|no|A function you can pass to define the SVG path.
pointerEvents|string|no|Allow the user to interact, or manipulate programmatically.
onBlobular|func|no|A callback returning you with a `blobular` instance.
onBlobCreated|func|no|A callback for when a new blob has been generated.
onBlobDeleted|func|no|A callback for when an existing blob has been removed.
-----



## ✌️ License
[MIT](https://opensource.org/licenses/MIT)
