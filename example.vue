<template>
  <div style="height: 100%; width: 100%">
    <l-map
      style="height: 400px"
      :center="mapCentre"
      :zoom="mapZoom"
      @fullscreenchange="fullscreenChanged"
      ref="map"
    >
      <l-tile-layer
        :url="tileUrl"
        :attribution="tileAttribution"
      />
      <l-control-fullscreen
          position="topleft"
          :options="fullscreenOptions"
      />
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
      fullscreenOptions: {
        title: {
          'false': 'Switch to full-screen view',
          'true': 'Exit full-screen mode',
        },
      },
    };
  },
  methods: {
    fullscreenChanged () {
      if (this.$refs.map.mapObject.isFullscreen()) {
        console.log('Entered full-screen mode');
      } else {
        console.log('Left full-screen mode');
      }
    },
  }
};
</script>

<style>
@import '~leaflet/dist/leaflet.css';
</style>