<template>
  <div id="app">
    <a-button type="primary">test</a-button>
    <map-container v-bind="map" />
  </div>
</template>

<script>
import MapContainer from './components/MapContainer.vue';

export default {
  name: 'App',
  components: {
    MapContainer
  },
  data () {
    return {
      map: {
        zoom: 12,
        center: [102.74922,25.130916]
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
