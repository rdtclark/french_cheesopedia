<template>
  <div class="cheese-map" v-if="cheeses">
    <l-map :zoom="zoom" :center="center">
      <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
      <l-marker v-for="(cheese, index) in cheeses" :key="index" :value="index" :lat-lng="latLng(cheese.geometry.coordinates[0], cheese.geometry.coordinates[1])"></l-marker>
    </l-map>
  </div>
</template>

<script>
import L from 'leaflet';
import { LMap, LTileLayer, LMarker } from 'vue2-leaflet';

export default {
    name: "cheese-map",
    props: ["cheeses"],
    components: {
        LMap,
        LTileLayer,
        LMarker,
  },
  methods: {
      latLng: function(lat, lng) {
        return L.latLng(lat, lng)
      }
  },
  data() {
    return {
      zoom:12,
      center: L.latLng(47.413220, -1.219482),
      url:'https://tile.thunderforest.com/pioneer/{z}/{x}/{y}.png?apikey=c1569342f24e4ae883057f1e6754f4c5',
      attribution:''
    }
  }
}
</script>

<style>

.cheese-map {
    height: 50vh;
}

</style>