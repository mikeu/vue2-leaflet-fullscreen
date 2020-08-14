# vue2-leaflet-fullscreen

This is a [Vue2Leaflet](https://github.com/KoRiGaN/Vue2Leaflet) plugin to provide the
[Leaflet.fullscreen](https://github.com/Leaflet/Leaflet.fullscreen) control
on [Leaflet](https://leafletjs.com/) maps in [Vue](https://vuejs.org/) applications.


## Installation
```bash
npm install --save vue2-leaflet-fullscreen
```

## Local demo
```bash
git clone git@github.com:mikeu/vue2-leaflet-fullscreen.git
cd vue2-leaflet-fullscreen

npm install
npm run example
```
You should then be able to visit http://localhost:4000 to see a leaflet map with the fullscreen control.


## Usage

### Adding the component to a map

With the `LControlFullscreen` component loaded into Vue (see below), simply add the
`l-control-fullscreen` element inside an `l-map`, optionally providing it with an
`options` object to specify the initial setup of the control, or the
[Leaflet Control position](https://leafletjs.com/reference-1.4.0.html#control-position)
in which to display the control.
For example,
```html
<l-map>
  <l-control-fullscreen :options="{ 'false': 'Go big!', 'true': 'Be regular' }" position="topleft"/>
  <!-- other map components -->
</l-map>
```

#### Screen-mode change events

The fullscreen control fires the `fullscreenchange` event from the map to which it has been added.
In Vue, these can be listened for in the standard fashion, by adding event handlers the the `LMap`
control within which the `LControlFullscreen` is being used:
```html
<l-map @fullscreenchange="handleToggle">
  <l-control-fullscreen/>
  <!-- other map components -->
</l-map>
```
Of course, the `handleToggle` method must be defined within the Vue component that is calling them.


### Loading the Vue component

You can either install the control globally within your application at the point where you initially
configure Vue, or import the control only within the components that require it.


#### Option 1: Local import

In the `<script>` of a Vue component,
```js
import LControlFullscreen from 'vue2-leaflet-fullscreen';
// ...
export default {
  // ...
  components: {
    LControlFullscreen,
    // ...
  },
  // ...
};
```


#### Option 2: Global install

Where you load and configure your Vue environment,
```js
import Vue from 'vue';
import LControlFullscreen from 'vue2-leaflet-fullscreen';
// ...
Vue.component('l-control-fullscreen', LControlFullscreen);
// ...
```


## Credit

The majority of the credit for this plugin goes to the author of and contributors to the underlying
[Leaflet.fullscreen control](https://github.com/Leaflet/Leaflet.fullscreen), and of course
the plugin wouldn't be possible without Vue, Leaflet, and Vue2Leaflet.


### Plugin author

Michael Underwood


## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
