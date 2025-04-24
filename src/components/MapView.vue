<template>
  <div id="map" class="map-container"></div>
</template>

<script>
import L from 'leaflet';

export default {
  name: 'MapView',
  emits: ['feature-selected'],
  mounted() {
    this.initMap();
  },
  methods: {
    initMap() {
      this.map = L.map('map').setView([20.5937, 78.9629], 5);

      L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
        attribution: '© OpenStreetMap contributors'
      }).addTo(this.map);

      this.loadData();
    },
    async loadData() {
      // Replace with your actual API
      const data = {
        points: [{ id: 1, lat: 28.6139, lng: 77.2090, type: 'Point' }],
        polygons: [{ id: 2, coordinates: [[ [28.7, 77.1], [28.7, 77.3], [28.6, 77.2] ]], type: 'Polygon' }]
      };

      // Points
      data.points.forEach(point => {
        L.marker([point.lat, point.lng])
          .addTo(this.map)
          .on('click', () => this.$emit('feature-selected', point));
      });

      // Polygons
      data.polygons.forEach(polygon => {
        L.polygon(polygon.coordinates)
          .addTo(this.map)
          .on('click', () => this.$emit('feature-selected', polygon));
      });
    }
  }
}
</script>

<style scoped>
.map-container {
  height: 500px;
  width: 100%;
}
</style>
