<template>
  <div id="app">
    <MapView @feature-selected="selectedFeature = $event" />
    <FeatureCard :feature="selectedFeature" />
  </div>
</template>

<script>
import MapView from './components/MapView.vue';
import FeatureCard from './components/FeatureCard.vue';

export default {
  name: 'App',
  components: {
    MapView,
    FeatureCard
  },
  data() {
    return {
      selectedFeature: null
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin: 20px;
}
</style>
