<template>
  <div class="map">
    <l-map ref="map" :center="center" :zoom="zoom">
      <l-tile-layer :url="url"></l-tile-layer>
      <vue-geoman :map="mapObject" v-if="mapObject" />
      <l-marker v-for="(marker, i) in markers" :key="i"
        draggable :lat-lng="marker">
        <l-tooltip>Olá mundo!</l-tooltip>
        <l-popup>Eu sou um popup!</l-popup>
      </l-marker>
    </l-map>
  </div>
</template>

<script>
import { LPopup, LTooltip } from "vue2-leaflet"
import VueGeoman from './VueGeoman.vue'
export default {
  components: {
    'l-popup': LPopup,
    'l-tooltip': LTooltip,
    'vue-geoman': VueGeoman
  },
  data () {
    return {
      url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
      zoom: 13,
      center: {lat:-7.142305, lng:-34.8572066},
      markers: [
        {lat:-7.162305, lng:-34.8552066},
        {lat:-7.122305, lng:-34.8572066},
        {lat:-7.142305, lng:-34.8672066},
        {lat:-7.148305, lng:-34.8502066},
      ],
      mapObject: null
    };
  },
  mounted() {
    this.mapObject = this.$refs.map.mapObject
  }
}
</script>

<style scoped>
  .map {
    height: 100vh;
    width: 100vw;
  }
</style>