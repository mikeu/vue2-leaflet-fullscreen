<template>
  <div style="height: 100%; width: 100%">
    <l-map
      style="height: 400px"
      :center="mapCentre"
      :zoom="mapZoom"
    >
      <l-tile-layer
        :url="tileUrl"
        :attribution="tileAttribution"
      />
      <l-control-fullscreen position="topleft" />
    </l-map>
  </div>
</template>

<script>
import L from 'leaflet';
import { LMap, LTileLayer } from 'vue2-leaflet';
import LControlFullscreen from './LControlFullscreen.vue';
export default {
  components: {
    LMap,
    LTileLayer,
    LControlFullscreen,
  },
  data () {
    return {
      mapCentre: [51, -114],
      mapZoom: 10,
      tileUrl: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
      tileAttribution: '&copy; <a href="//osm.org/copyright">OpenStreetMap</a> contributors',
    };
  },
};
</script>

<style>
@import '~leaflet/dist/leaflet.css';
</style>