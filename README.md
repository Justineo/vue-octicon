# Vue-Octicon

> Octicon component for Vue.js, using inline SVG.

Vue-Octicon is built upon [Octicons](https://octicons.github.com/) `v5.0.1` and depends on [Vue.js](https://vuejs.org/) `v2.0.1`+.

## Installation

### NPM (Recommended)

```bash
$ npm install vue-octicon
```

### bower

```bash
$ bower install vue-octicon
```

### manual

Just download `dist/vue-octicon.js` and include it in your HTML file:

```html
<script src="path/to/vue-octicon/dist/vue-octicon.js"></script>
```

## Usage

```html
<!-- basic -->
<octicon name="repo"></octicon>

<!-- with options -->
<octicon name="sync" scale="2" spin></octicon>
<octicon name="comment" flip="horizontal"></octicon>
<octicon name="repo-forked" label="Forked Repository"></octicon>
```

### ES Modules with NPM & vue-loader (Recommended)

```js
import Vue from 'vue'
import Octicon from 'vue-octicon/components/Octicon.vue'

// Pick one way betweem the 2 following ways

// only import the icons you use to reduce bundle size
import 'vue-octicon/icons/repo'

// or import all icons if you don't care about bundle size
import 'vue-octicon/icons'
```

**Heads up**

if you are using `vue-cli` to create your project, the `webpack` template may exclude `node_modules` from files to be transpiled by Babel. 

To fix this my creating an exception, edit your webpack config:

#### In older versions of vue-cli: 

Change the `exclude` value from `/node_modules/` to `/node_modules(?![\\/]vue-octicon[\\/])/`.

#### In the latest version of vue-cli (as of Oct. 2017):

```js
// Find where webpack looks for files to run through babel

test: /\.js$/,
        loader: 'babel-loader',
        include: [resolve('src'), resolve('test')]

// and change it to this, so it knows to go get and transpile vue-octicon too

test: /\.js$/,
        loader: 'babel-loader',
        include: [resolve('src'), resolve('test'), resolve('node_modules/vue-octicon')]
```

### CommonJS with NPM without ES Next support

```js
var Vue = require('vue')

// requiring the UMD module
var Octicon = require('vue-octicon')

// or with vue-loader you can require the src directly
var Octicon = require('vue-octicon/components/Octicon.vue')

// register component to use
```

### AMD

```js
require.config({
  paths: {
    'vue-octicon': 'path/to/vue-octicon'
  }
})

require(['vue-octicon'], function (Octicon) {
  // register component to use...
})
```

### Global variable

The component class is exposed as `window.VueOcticon`.

## Local development

```bash
$ npm i
$ npm run dev
```

Open `http://localhost:8080/demo` to see the demo.

### Updating icons

Don't touch files in `src/icons` but update `assets/icons.json` instead and run `npm run icons` to re-generate icon module files.

## Registering custom icons

You can register custom icons like this:

```js
// ES Modules with vue-loader
import Octicon from 'vue-octicon/src/components/Octicon.vue'

Octicon.register({
  taobao: {
    width: 16,
    height: 12.268,
    d: 'M2.786,2.795 C3.580,2.795 4.223,2.223 4.223,1.509 C4.223,0.804 3.580,0.223 2.786,0.223 C1.991,0.223 1.348,0.804 1.348,1.509 C1.348,2.223 1.991,2.795 2.786,2.795 L2.786,2.795 Z M1.589,3.321 L0.688,4.705 L2.357,5.750 C2.357,5.750 3.473,6.313 2.946,7.384 C2.446,8.393 0.018,10.607 0.018,10.607 L2.196,11.964 C3.696,8.696 3.607,9.134 3.982,7.955 C4.366,6.759 4.455,5.839 3.795,5.179 C2.946,4.330 2.848,4.250 1.589,3.321 L1.589,3.321 Z M15.714,2.955 C15.714,2.955 15.250,-0.723 7.196,1.554 C7.536,0.955 7.705,0.563 7.705,0.563 L5.696,0.000 C5.696,0.000 4.884,2.643 3.438,3.884 C3.438,3.884 4.839,4.688 4.821,4.661 C5.223,4.268 5.580,3.857 5.893,3.464 C6.214,3.321 6.527,3.188 6.830,3.063 C6.455,3.741 5.857,4.741 5.250,5.375 L6.098,6.116 C6.098,6.116 6.679,5.554 7.313,4.884 L8.027,4.884 L8.027,6.125 L5.223,6.125 L5.223,7.107 L8.027,7.107 L8.027,9.482 C7.991,9.473 7.955,9.473 7.920,9.473 C7.616,9.455 7.125,9.411 6.946,9.107 C6.714,8.750 6.884,8.080 6.893,7.670 L4.955,7.670 L4.884,7.705 C4.884,7.705 4.179,10.884 6.938,10.813 C9.509,10.884 10.991,10.098 11.696,9.554 L11.982,10.607 L13.571,9.946 L12.491,7.313 L11.205,7.705 L11.446,8.616 C11.116,8.857 10.732,9.045 10.321,9.179 L10.321,7.107 L13.054,7.107 L13.054,6.125 L10.321,6.125 L10.321,4.884 L13.071,4.884 L13.071,3.902 L8.188,3.902 C8.536,3.473 8.813,3.080 8.893,2.830 L8.036,2.598 C11.688,1.295 13.723,1.518 13.705,3.661 L13.705,9.304 C13.705,9.304 13.920,11.241 11.696,11.107 L10.500,10.848 L10.214,11.991 C10.214,11.991 15.402,13.464 15.821,9.482 C16.250,5.491 15.714,2.955 15.714,2.955 L15.714,2.955 Z'
  }
})
```

## Related projects

* [Vue-Awesome](https://github.com/Justineo/vue-awesome) by the same author of Vue-Octicon.
